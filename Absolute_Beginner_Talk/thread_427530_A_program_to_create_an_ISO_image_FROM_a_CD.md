---
title: "A program to create an ISO image FROM a CD?"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by papuccino1 on 2007-04-29
I have a CD, but I want to to create an exact copy on my computer of it. For backup purposes. What program would I have to use that's free? Needless to say I'm using Ubuntu. Version 7.04

---

### Post by Acglaphotis on 2007-04-29
Use k3b, just go to the terminal and write: 

```
sudo aptitude install -y k3b
```

The -y keeps aptitude from asking Y/n.

-Acgla

---

### Post by annda on 2007-04-29
or you can use a simple command:

```
dd if=/dev/hdc of=image.iso
```

where hdc is the cd-rom device, you might need to change it to fit your system.

---

### Post by mcduck on 2007-04-29
..or Gnomebaker, if you want a graphical tool but don't want to get all that KDE stuff on your nice Gnome machine ;)

---

### Post by papuccino1 on 2007-04-29
Thank you very much for the Gnomebaker and the k3b.

One more question.

What FREE program could I use to the same thing on Windows? I want to back up a Diable 2 CD on my windows machine.

Thanks again for the help.


EDIT: I can't seem to find a link to Gnomebaker download. Where is it? The site in google and wiki, only take me to a directory with nothing in there.

---

### Post by papuccino1 on 2007-04-29
Nevermind I Found It Using Automatix.

Thanks For Everything.

---

### Post by nixclusive on 2007-04-29
enter this at the terminal:```
sudo apt-get install gnomebaker
```This should download and install GnomeBaker for you.

By the way, if you only want to make an ISO image out of a cd the solution given by annda is really useful.```
dd if=/dev/hdc of=$HOME/cd.iso bs=64k 
```This command would create an iso image in you home directory. The argument if=/dev/hdc corresponds to your IDE-CD drive. Replace accordingly:

Primary Master: /dev/hda
Primary Slave: /dev/hdb
Secondary Master: /dev/hdc
Secondary Slave: /dev/hdd

---

### Post by Billy McCann on 2007-04-29
> **papuccino1 said:**
> What FREE program could I use to the same thing on Windows? I want to back up a Diable 2 CD on my windows machine.
Try burnatonce.

---

### Post by rubasub on 2007-07-13
Thanks "annda" for the tip, I was failing to copy and burn an iso using Gnomebaker( gnomebaker is ace for most things ) when I found your simple command, not only did it save an image.iso to my home folder, I right clicked the new file in file manager which then offered to burn it to disk.  what a breeze!

> **annda said:**
> or you can use a simple command:

```
**dd  if=/dev/hdc of=image.iso**
```

where hdc is the cd-rom device, you might need to change it to fit your system.

---

### Post by phr0ze on 2007-07-13
Yeah the DD command is harder to remember but you can make an Menu item which runs this command so next time you pop in a CD you can just click the menu to make an ISO.

I'm not sure of the situation but I believe if you want a true backup you will have to use software that is copy protection aware. If you don't, your backup will not work unless you download a special no cd patch which is not recommended.

I only mention this because if you do ruin your original and you try your backup you may find you are sadly disappointed and have to buy a new copy.

---

### Post by sad_iq on 2007-07-13
> **phr0ze said:**
> 
I'm not sure of the situation but I believe if you want a true backup you will have to use software that is copy protection aware. 
 You are right about dd...copy protection will not work...also copying a Vcd or Svcd will fail as dd can't read them...so here's a link that will enable you to make a copy of such cd's...it's for Playstation cd's but maybe it will work for Pc Games with Copy Protection(I know it works with Vcd's and Svcd's!!!):
   [http://linuxreviews.org/howtos/cdrecording/#toc11](http://linuxreviews.org/howtos/cdrecording/#toc11)
 Hope it helps!!!

---

