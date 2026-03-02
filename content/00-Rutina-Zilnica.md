Sigur — copy/paste direct:

```md
# 00 - Rutina zilnică (Git + Quartz)

## Scop
Public notele din Obsidian pe `notes.radiogpt.online` rapid și sigur, fără haos.

---

## Flux standard (de fiecare dată)

```bash
cd F:\Obsidian\radiogpt-lab
git add .
git commit -m "update notes"
git pull --rebase origin main
git push
```

### Ce face fiecare linie
- `git add .` → pregătește toate schimbările.
- `git commit -m "..."` → salvează local o versiune clară.
- `git pull --rebase origin main` → ia ce e nou de pe GitHub înainte de upload.
- `git push` → urcă schimbările (site-ul se actualizează prin Actions).

---

## Cazuri frecvente

### 1) `nothing to commit`
Nu e eroare. Înseamnă că nu ai schimbări noi.
Rulează:
```bash
git pull --rebase origin main
git push
```

### 2) `rejected (fetch first)` / `non-fast-forward`
Ai rămas în urmă față de GitHub.
Rulează:
```bash
git pull --rebase origin main
git push
```

### 3) `cannot pull with rebase: You have unstaged changes`
Nu ai făcut commit înainte de pull.
Rulează:
```bash
git add .
git commit -m "save local changes"
git pull --rebase origin main
git push
```

### 4) Se deschide editor la `rebase --continue`
E normal.
- Save
- Close
- apoi:
```bash
git push
```

### 5) Mesajul: `credential-manager-core is not a git command`
Dacă `git push` merge, ignoră mesajul.
Dacă push nu merge, fă autentificare GitHub și reîncearcă.

---

## Reguli simple de siguranță
- 1 schimbare importantă = 1 commit.
- Nu combina modificări mari + workflow YAML + rebase în același pas.
- Dacă ceva pică, întâi `git status`, apoi acțiune.

---

## Verificare publicare
După `git push`, verific:
- GitHub → Actions (run verde)
- `https://notes.radiogpt.online`

---

## Format recomandat pentru commit messages
- `SRR: update Model Operational AI section`
- `SRR: refine Faza 0 principles`
- `Utilitare: reprioritize backlog`
- `Status: weekly update`
- `Fix: diacritics in SRR notes`
```