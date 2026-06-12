---
title: "2cd Hard drive install? G4"
date: 2004-11-13
forum: Apple PPC Users
---

### Post by MarkV on 2004-11-13
Folks, any idea's?
I have a G4 tower with a boot and storage drive, I want to make the storage drive a ubuntu drive and have a dual boot.. is this possible? G4 500mhz, 896mb, 2- 34gb scsi hd's
Mark

---

### Post by Down8ve on 2004-11-13
By all means.  I have OSX on an 80 gig drive and Ubuntu on a 20 gig.  The 20 gig is configured as "Master" (done through those pug-style connectors on the drive) and the OSX drive is a slave.

During the Ubuntu installation it asks which drive you want to erase and use for Ubuntu.  If your drives are different sizes it will help you tell which is which.  The drive that is highlighted is the one that will be reformatted when you press "Next" or "OK".

The system will default to Ubuntu, but will ask at startup if you want OSX or Linux.  Press "L" for Ubuntu and "X" for OSX.

Works great!

Scott

---

### Post by MarkV on 2004-11-15
Yes, but my OS X hd is my "master" and the hd i want to make Ubuntu is my "slave" drive.. will the installer and boot loader work this way?
Mark

---

### Post by Down8ve on 2004-11-15
I think so.  The reason mine was arranged the way it is had to do with another distro required it to be that way and I never needed to change it back.  You can go ajead and install Ubuntu on the slave, but be sure you know which is hda and hdb!!!

Scott

---

