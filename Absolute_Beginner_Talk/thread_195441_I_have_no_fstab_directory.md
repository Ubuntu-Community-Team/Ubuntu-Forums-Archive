---
title: "I have no fstab directory"
date: 2006-06-12
forum: Absolute Beginner Talk
---

### Post by puterboy on 2006-06-12
I'm trying to mount a bunch of stuff, and everytime I try to find fstab, it says there is no /etc/fstab

running ubuntu 64-bit 6.06

---

### Post by Jucato on 2006-06-12
there is no fstab directory. 
fstab is a file under the /etc directory.

---

### Post by taurus on 2006-06-12
[QUOTE=puterboy]I'm trying to mount a bunch of stuff, and everytime I try to find fstab, it says there is no /etc/fstab

running ubuntu 64-bit 6.06[/QUOTE]
If you don't have /etc/fstab, then how the system knows where to mount anything!!!  What is the output of this command, from a terminal?
```

ls -la /etc/fstab

```

---

### Post by puterboy on 2006-06-13
[QUOTE=Fenyx]there is no fstab directory. 
fstab is a file under the /etc directory.[/QUOTE]

that solves a lot of problems......i looked for some sort of fstab help on the threads, but all it was was ppl's fstab files, no actual help. thnx. i'm starting to get the hang of it here....

---

### Post by joe bocan on 2008-06-24
hi i have the same problem then putter.  i have  no fstab file under etc or anywhere else.  I have to say i am a total dummy in linux since i've installed it two days ago.

here's what i have from this command
ls -la /etc/fstab

-rw-r--r-- 1 root root 631 2008-06-21 18:18 /etc/fstab

i guess this means that it's been created at the installation

---

### Post by Victormd on 2008-06-24
> **joe bocan said:**
> hi i have the same problem then putter.  i have  no fstab file under etc or anywhere else.  I have to say i am a total dummy in linux since i've installed it two days ago.

here's what i have from this command
ls -la /etc/fstab

-rw-r--r-- 1 root root 631 2008-06-21 18:18 /etc/fstab

i guess this means that it's been created at the installation
so that means that you do have the file. To open it, open a terminal and type:
```
sudo gedit /etc/fstab
```
If you're going to edit it, I would suggest that you create a copy first
```
sudo cp /etc/fstab /etc/fstab.backup
```

If you're having problems automatically mounting your partitions, take a look at the link on my signature... :)

---

### Post by joe bocan on 2008-06-24
first thank you for answering so fast i am amazed
i have made the backup seemed to have worked
but here what happens next

""""@ubuntu:~$ sudo gedit /etc/fstab
sudo: gedit: command not found

---

### Post by forestpixie on 2008-06-24
If you don't run ubuntu then you wont have gedit

kubuntu - replace with kate
xubuntu - replace with mousepad

It might also be better if you were to use the new forum's and not dig up a 2 year old thread from the archive :)

---

### Post by Victormd on 2008-06-24
Hahahaha... Just noticed this is a 2yr old thread! :)
Well, it wasn't marked as solved so Joe has a good point in trying to fix his issue. :)

---

### Post by joe bocan on 2008-06-25
aight thank you guys
i'LL try it out when i have a minute

---

### Post by joe bocan on 2008-06-25
> **forestpixie said:**
> If you don't run ubuntu then you wont have gedit

kubuntu - replace with kate
xubuntu - replace with mousepad

It might also be better if you were to use the new forum's and not dig up a 2 year old thread from the archive :)



so the command should look like this?

sudo mousepad  etc fstab


p.s.  where the hell is the slash button on the french canadian keyboard?
somebody knows?

---

