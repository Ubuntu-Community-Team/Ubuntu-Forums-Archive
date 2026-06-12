---
title: "Is there a program like Wubi that is as simple but completely wipes Windows?"
date: 2007-08-01
forum: Absolute Beginner Talk
---

### Post by ajskhan on 2007-08-01
So I installed and ran Wubi ([http://ubuntuforums.org/showthread.php?t=515352](http://ubuntuforums.org/showthread.php?t=515352) - didn't work, need help with errors, but...)

It was nice but I really didn't want the virtual HD or whatever Wubi gives. I wanted a complete format, then Ubuntu. Is there a type of program that would install from WITHIN XP (without any need for CDs) then boot directly to Ubuntu? (CD drives don't work)... and completely do away with XP?

Sorry for asking a stupid question. Thanks :lolflag:

---

### Post by dpar on 2007-08-01
lol......Interesting concept.....I may be wrong, but I relly don't think it's possible. Kind of like killing your creator.....lol. Why don't the drives work?Just broken? They are pretty cheap now.

---

### Post by wolfen69 on 2007-08-01
you could always dual boot. but ive always been one to have a seperate drive for each OS. (havnt booted to xp in months)

---

### Post by dpar on 2007-08-01
His cd drives don't work, i think, so he can't install without windows.

ajskhan:  Windows would probably treat a program like that as a virus.:biggrin:

---

### Post by ajskhan on 2007-08-01
dual boot, thats where it goes up and you get to select between ubuntu and windows right? in the black and grey part of boot up?

i think thats what i have - it wont boot, see link in op

---

### Post by ajskhan on 2007-08-01
exactly
sick and tired of XP - slow as heck, minimum 10mins to boot up to desktop
no viruses,ad-aware, nothing.

ill find a way - muhahahah

---

### Post by aysiu on 2007-08-01
Maybe this might help:
[HOWTO: Install Ubuntu Linux without burning a cd](http://ubuntuforums.org/showthread.php?t=28948)

---

### Post by Paulmd on 2007-08-02
DBAN

dban.sourceforge.net

It doesn't work within windows, but it installs to a floppy (hey, it's not  CD), which you boot form. 

WARNING: this WILL wipe your hard drive, and all hard drives on the machine. That's what it does.

---

### Post by tuxcantfly on 2007-08-02
If you already have a Wubi install, you can transfer to a real partition using LVPM (see the third link in my sig) and remove Windows afterwards.

Also, for reference, if anybody wants to do a simple no-cd installation from Windows, this one out, it's my simple double-click-and-reboot installer; it uses netboot so you can tell it to dual-boot or wipe out Windows:

[http://ubuntuforums.org/showthread.php?t=427540](http://ubuntuforums.org/showthread.php?t=427540)

---

### Post by mrzaius on 2008-06-01
I can't believe this wasn't brought up - 

Instlux does everything you're trying to do, right out of the box. Just gives you a clean installer - no crazy loopback devices.

---

### Post by fidamehran on 2008-06-17
I got interested seeing "Wubi" talk. I installed Ubuntu from Within Windows through "Wubi". Now I Dual Boot (that's what happened by default) with Windows XP. I have 2 questions.

1. Is there a program with which I can start a virtualized session of Windows XP while inside Ubuntu? (kind of like using Wine to run Windows XP from boot up scratch/ OS load point).... Very weird idea, I must say.

2. What will happen if my Windows crashes? As far as I know Ubuntu has been installed like a program within Windows. So, then what? What do I do then? Re-install Win XP? Re-install Ubuntu by booting from CD? (which I didn't do the first time to avoid the drive partitioning hassle). What to do then?

One Bonus Question:
3. Is it possible that a virus or malware will infect while I am running Windows and affects the Ubuntu part of the hard disk, or affect Windows Files and parts when I am in Ubuntu?

I am a COMPLETE newbie, so I'm very much nosy. I hope Ubuntu Gurus won't mind.

---

