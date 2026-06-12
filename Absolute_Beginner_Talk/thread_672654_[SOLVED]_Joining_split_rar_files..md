---
title: "[SOLVED] Joining split rar files."
date: 2008-01-19
forum: Absolute Beginner Talk
---

### Post by happysmileman on 2008-01-19
I have, in a folder, a bunch of rar files and an "sfv" file, lke this:
> Bleh.part01.rar
Bleh.part01.sfv
Bleh.part02.rar
Bleh.part03.rar
Bleh.part04.rar
...
Bleh.part23.rar

All of the rar files are 14.3MB except the last one (part 23) which is 14.1MB, how exactly am I supposed to go about unpacking these, does anyone know?

---

### Post by Mze on 2008-01-19
rar x -y Bleh.part01.rar

for more commands and switches: type rar in the terminal

---

### Post by doorknob60 on 2008-01-19
Or if you scared of the terminal you can run the Windows version of WinRAR in wine, it works just fine :)

---

### Post by happysmileman on 2008-01-19
> **Mze said:**
> rar x -y Bleh.part01.rar

for more commands and switches: type rar in the terminal

Wouldn't that just unpack the first rar file? They're all suppose to unpack into one large file

---

### Post by RomeReactor on 2008-01-19
Hi. In cse you don't have unrar installed, look for it in Synaptic (System->Administration->Synaptic); or, to install from the terminal:
```
sudo aptitude install unrar
```
Once it's installed, you can double-click on the first .rar file and it will open up in Archive Manager; then just click 'Extract'.

> **happysmileman said:**
> [QUOTE=Mze;4169788]rar x -y Bleh.part01.rar

for more commands and switches: type rar in the terminal

Wouldn't that just unpack the first rar file? They're all suppose to unpack into one large file[/QUOTE]
That will join the rest of the files.

---

### Post by Mze on 2008-01-19
give it a try , happysmileyman and post results. if it doesn't work let's know.

---

### Post by happysmileman on 2008-01-19
> **Mze said:**
> give it a try , happysmileyman and post results. if it doesn't work let's know.

Well I can't test it out, not at that computer right now, and not sure when I will be, could be a few days from now, but I'll post back if I encounter any problems with it.

Edit: I'll mark this as solved since I don't think it needs any more answers at this point and I can't test it for a few days probably.

---

