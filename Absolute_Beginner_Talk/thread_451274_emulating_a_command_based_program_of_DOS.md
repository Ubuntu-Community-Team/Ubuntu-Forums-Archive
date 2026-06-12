---
title: "emulating a command based program of DOS?"
date: 2007-05-22
forum: Absolute Beginner Talk
---

### Post by medya on 2007-05-22
I wnt to compile an assembly program using ml.exe program .

dont tell me to use NASM , because I have to re-write my whole programs ...

for compiling  an assembly program in windos and dos I do this :
ml myprog.asm /fl

how I can do that in linux using wine or other tools ?

---

### Post by jtraub on 2007-05-22
dosbox?

---

### Post by anaconda on 2007-05-22
dosbox, or dosemu

wine isn't that good for dos programs..

---

### Post by medya on 2007-05-22
I tried both of them , both say , this program can not run in dos mode.. isnt other way to try?

---

### Post by medya on 2007-05-25
bump

---

### Post by Terl on 2007-05-25
Have you tried Wine?  [WineHQ]("http://www.winehq.org/")

---

### Post by psusi on 2007-05-25
Then ml is actually a windows executable, not dos.  Run it under wine.

---

### Post by medya on 2007-05-25
no ml is a dos program it uses command prompt !
and wine doesnt work I tried it

---

### Post by freebeer on 2007-05-25
Maybe set up a virtual machine (vmware or virtual box, etc), install DOS of your choice, then run the assembler from there?  You can probably also test your code from there as well, I imagine.

---

### Post by psusi on 2007-05-26
Command Prompt != MSDOS.  It says it can't be run in dos mode because it is a windows executable.

---

