---
title: "Installing Wine with Synaptic?"
date: 2007-05-17
forum: Absolute Beginner Talk
---

### Post by doriard on 2007-05-17
I installed Wine from Feisty KDE System Settings/Advanced/Windows Applications and it seems to have installed Wine 0.9.33 instead of the latest 0.9.37.  When I look in Synaptic it shows 0.9.33 and doesn't indicate any choice for the most recent version.  Is it okay to install/uninstall Wine via Synaptic or System Settings?  How can I get the most recent version of Wine to show up in Synaptic?  Should I uninstall (how?) and install the latest version manually?

---

### Post by taurus on 2007-05-17
If you want to get the latest version, here is how.

[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

---

### Post by Nythain on 2007-05-17
after adding the gpg key and sources list entry for bleeding edge wine from the link mentioned above, all you really have to do is
sudo apt-get update
sudo apt-get upgrade
and it should upgrade wine, no need to uninstall/reinstall

---

### Post by doriard on 2007-05-17
I already uninstalled and reinstalled via Synaptic.  It seemed to work okay.  Now I'm trying to figure out how to install a game (Jedi academy).  I think I need to mount the cdrom drive first.  When I put the CD in a windows pops up asking me what I want to do with it (the window also says "Medium Type: Unmounted CD Write", but it's actually a CD/DVD reader.  When I browse to the drive with Konqueror or terminal, it doesn't see any files on the CD.

update:
Oh, cool -- in the window that opened when I put the CD in, I just clicked on "open in new window" and it automatically mounted the CD drive.  Now I will have to see if the mount "sticks" on shutdown.

---

### Post by doriard on 2007-05-17
Okay, I'm having a bit of a problem here .... I'm in the middle of installing Jedi Academy with Wine and I'm stuck trying to put the second CD in.  Jedi Academy installer is asking for the second CD, and Ubunut won't release the CD or eject it.  I tried opening a terminal window and typing "/media/cdrom$ eject, but it says,

umount: /media/cdrom0: device is busy

How do I get the second CD in the drive to finish installation?

---

### Post by zvacet on 2007-05-17
```
sudo umount /media/cdrom0/
```

---

### Post by doriard on 2007-05-17
Using unmount didn't work because the drive was busy.  I made some progress from the page here:
[http://ubuntuforums.org/showthread.php?t=422582&highlight=install+jedi+academy]("http://ubuntuforums.org/showthread.php?t=422582&highlight=install+jedi+academy")

I can now get the drive to release the CD, but now the installation won't continue.  It says it can't find the second CD when I put it in.  Any more ideas?

---

### Post by doriard on 2007-05-17
Okay, more progress.  Wine thought the cd drive was still mounted, so I opened another terminal and remounted the drive (sudo mount /media/cdrom0).  That got the installer to recognize the drive path again.  It's installing now.

---

### Post by doriard on 2007-05-17
I forgot to mention.  I had to  sudo umount -f /media/cdrom0 first before 
sudo mount /media/cdrom0, because Ubuntu thought it was already mounted even though Wine had ejected the CD (wine eject h:)

---

### Post by wilberfan on 2007-05-19
I just installed the latest WINE (v0.9.37) in my 64-bit Feisty...but I'm confused by the fact that I don't see any WINE entries in my Applications / System Tools menu.   (Previous installs included this.)

I just installed foobar2000 and don't see any menu entries for that, either...  (I DID get a desktop icon.)

Has something changed I don't know about?

---

### Post by wilberfan on 2007-05-19
After spending a few minutes in the #wine irc channel, I've learned that the menu items I'm remembering (see attached) are distro specific--NOT a native part of the WINE installation?   And that got me to thinking:  This time I installed via Synaptic--last time, perhaps, was via Automatix??

---

