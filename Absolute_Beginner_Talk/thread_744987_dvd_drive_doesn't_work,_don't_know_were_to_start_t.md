---
title: "dvd drive doesn't work, don't know were to start to fix it"
date: 2008-04-04
forum: Absolute Beginner Talk
---

### Post by barbedsaber on 2008-04-04
its a cd rw and dvd rw
when I put in a cd or dvd, it flashes led's and spins, but nothing else happens.
it is recognized in windows xp
it has never worked in ubuntu
I am running hardy heron.
What should I do?

---

### Post by TeoBigusGeekus on 2008-04-04
Type in terminal
```
sudo ls /media
```
Does it show up there?

---

### Post by barbedsaber on 2008-04-04
harry@lenovo:~$ sudo ls /media
[sudo] password for harry: 
cdrom  cdrom0  TUX 2
harry@lenovo:~$ 
harry@lenovo:~$ 


(tux 2 is my thumb drive)

how do I mount it? (The cd/dvd drive)

---

### Post by hyper_ch on 2008-04-04
> **barbedsaber said:**
> its a cd rw and dvd rw
when I put in a cd or dvd, it flashes led's and spins, but nothing else happens.

What else should happen?

---

### Post by barbedsaber on 2008-04-04
> **hyper_ch said:**
> What else should happen?

Well, it appering on the desktop, and showing up in nautilus when I click places => computer.

---

### Post by TeoBigusGeekus on 2008-04-04
```
sudo mount /media/cdrom
```
or
```
sudo mount /media/cdrom0
```

---

### Post by barbedsaber on 2008-04-04
harry@lenovo:~$ sudo mount /media/cdrom
[sudo] password for harry: 
Sorry, try again.
[sudo] password for harry: 
mount: special device /dev/scd0 does not exist
harry@lenovo:~$ sudo mount /media/cdrom0
mount: special device /dev/scd0 does not exist
harry@lenovo:~$ 

I'm gong to bed now, will check what I need to do first thing in the morning.

---

### Post by Amarsingh0793 on 2008-04-04
Have you tried force mounting yet? The command is "mount -f". First do a su--login to become root (in a terminal). Then type this:

1. mount -f /media/(your device)  or

2. mount -f /dev/(your device)

Good Luck :)

---

