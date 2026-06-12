---
title: "Installing Windows XP Pro"
date: 2007-08-19
forum: Absolute Beginner Talk
---

### Post by PropheticAngel on 2007-08-19
I've been trying to re-install Windows XP to dual boot.  I'm using a T60, so I don't have a floppy drive and windows won't recognize my hard drive by default.  I tried the guide here: [http://forums.hexus.net/showthread.php?t=20748](http://forums.hexus.net/showthread.php?t=20748)
but my disc just gave me an error about not finding ntldr.  

Is there any better way to get the windows disc to recognize my hard drive when I don't have access to a floppy drive to get the drivers off of?

Thanks,
PropheticAngel

---

### Post by jrusso2 on 2007-08-19
I think windows xp doesn't have the driver for your sata hard drive.  During the install there is a way to add it with a floppy but without a floppy is going to be difficult.  I think the T-60 has a restore partition and if you didn't delete that it should be possible to reinstall xp.  But if you deleted it will need to have backed it up to burned cd's or dvd.

---

### Post by wolfen69 on 2007-08-19
you could try nlite [http://www.nliteos.com/](http://www.nliteos.com/) to integrate the sata drivers onto an xp disk. people have had success with this. it's a fairly easy program to use.

---

### Post by PropheticAngel on 2007-08-19
Is there an easy way to get nlite to work on ubuntu?

All my partitions died when I put on ubuntu, I erased the rest of the drive.

---

### Post by Lucifiel on 2007-08-19
Hmmm... I think slipstreaming on Ubuntu might be kinda difficult. And even if you "succeeded", there might be issues which could plague your Windows installation 'cos Linux has its' own methods for handling filenames and such.  

Your best bet is to maybe set up a virtual machine and install Windows XP within that machine. And then, use Windows to slipstream and stuff. 

That seems a lot less risky to me 'cos if you bork up your Windows installation, you might have issues getting Grub to load Ubuntu.

---

### Post by PropheticAngel on 2007-08-19
I guess I'll try that...

The audio issues with ubuntu are driving me back to installing windows.

---

