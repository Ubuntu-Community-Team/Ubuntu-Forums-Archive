---
title: "binutils/compiler loop problem"
date: 2006-06-12
forum: Absolute Beginner Talk
---

### Post by puterboy on 2006-06-12
I'm a total newbie, with absolutely no Linux experience. I was taught a lil about the terminal. My main problem here is that I need to install my NVidia drivers. For this, I need a binutils program called ln or ld. To install binutils, I need a compiler. Here's the catch: to install the compiler, i need binutils. So where do I start? My buddy who always told me to switch to Linux actually has no knowledge of it himself. I've tried Googling it, but most of it doesn't make sense to me. I just want to start with the basics, get my OS up and running to the point where I can do basics, then branch out from there. So does anyone know what I should do? Thanks in advance

edit: I'm using Ubuntu 6.06

---

### Post by nanotube on 2006-06-12
[QUOTE=puterboy]I'm a total newbie, with absolutely no Linux experience. I was taught a lil about the terminal. My main problem here is that I need to install my NVidia drivers. For this, I need a binutils program called ln or ld. To install binutils, I need a compiler. Here's the catch: to install the compiler, i need binutils. So where do I start? My buddy who always told me to switch to Linux actually has no knowledge of it himself. I've tried Googling it, but most of it doesn't make sense to me. I just want to start with the basics, get my OS up and running to the point where I can do basics, then branch out from there. So does anyone know what I should do? Thanks in advance

edit: I'm using Ubuntu 6.06[/QUOTE]
you need to install the build-essential package. run these commands:
```
sudo aptitude update
sudo aptitude install build-essential
```

but at any rate, you should be able to find the nvidia drivers in the repositories through synaptic. that is much simpler than compiling them from source.

---

### Post by puterboy on 2006-06-12
ok, tried that, but now it won't recognize my cdrom. says "no medium found". i was looking through a bunch of threads, and i saw fstab, but i don't have it. i tried "fstab" and "/etc/fstab". I need to mount the cdrom to install anything, even the nvidia drivers i was looking for in the first place

---

### Post by nanotube on 2006-06-12
[QUOTE=puterboy]ok, tried that, but now it won't recognize my cdrom. says "no medium found". i was looking through a bunch of threads, and i saw fstab, but i don't have it. i tried "fstab" and "/etc/fstab". I need to mount the cdrom to install anything, even the nvidia drivers i was looking for in the first place[/QUOTE]
/etc/fstab is not an executable, it is a text file, so you just need to edit it. (search these forums for editing the fstab)

---

### Post by puterboy on 2006-06-12
[QUOTE=nanotube]/etc/fstab is not an executable, it is a text file, so you just need to edit it. (search these forums for editing the fstab)[/QUOTE]

OK! I couldn't find a lot on fstab without having 1,000,000 of someone's fstab printout.  i got my personal printout, and i changed my dvdrw (the only one that reads) to cdrom0, so now i can install build-essential and binutils. excellent. answers my question. thanks, nanotube!

---

