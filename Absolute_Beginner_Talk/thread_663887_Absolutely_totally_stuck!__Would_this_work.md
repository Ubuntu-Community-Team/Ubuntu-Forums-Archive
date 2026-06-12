---
title: "Absolutely totally stuck!  Would this work?"
date: 2008-01-10
forum: Absolute Beginner Talk
---

### Post by Upstart Blogger on 2008-01-10
I have a Sony Vaio laptop with a dodgy CD drive.

I installed Ubuntu from a CD and the installation dropped about around half way through.  I tried again, and again, until the CD drive finally gave up.  It is now totally useless.

Now the machine will boot into Linux but won't give me any sort of desktop.  It asks for my username and password and then I've got a command line, thats all.

So, I bought an external DVD drive and tried to install from that but the machine won't boot from a USB DVD drive.  Even though there is a BIOS option to enable external booting the drive is not then listed on the boot order list in the BIOS.  I have no idea why it can't see the drive.

Is it possible to access the USB DVD drive from the Linux command line?  If so, will it work without any drivers?

The only other thing I can think of now is to remove the SATA laptop drive, put it in a caddy and connect it to a desktop PC (currently running windows but I could install Linux on this if it makes it easier) via USB and then install on that.  Then take it out of the caddy and put it back into the laptop.

Would that work?  Any other ideas?

---

### Post by Pevichaey5 on 2008-01-10
if you have a broken cd drive, it will be under warranty, so you should get it replaced

on the whole, you don't need drivers for Linux, if you only want basic functionality of a device, and depending on how far the installation got, you may be able to do a reinstall of ubuntu using your external dvd drive

---

### Post by Upstart Blogger on 2008-01-10
Its not under warranty.  Its about 3 years old.  If I don't need drivers is it possible to access the DVD drive from the command line and then reinstall from that?

---

### Post by kvonb on 2008-01-10
-
.

---

### Post by kvonb on 2008-01-10
-

---

### Post by tigerplug on 2008-01-10
I've had an experience with Sony Vaio where they are locked down and will not let you boot from CD.

---

### Post by Upstart Blogger on 2008-01-10
Thanks for all the help you're giving me, it really is appreciated.  Ok, so lets assume I can mount the DVD drive.  Is it then a simple case of locating a file on the installation CD / DVD and re-installing from there?

---

### Post by kwacka on 2008-01-10
You said in your first post that you have a command line, so possibly forget about CD/DVD for now.

Do you have an internet connection? 

If yes, try entering:
sudo apt-get install ubuntu-desktop

(it might even work for your external drive) which will give you a graphic display, auto-recognition (hopefully) of external drives and world conquest (possibly)..

If you get an error, come back and let us know what it is (e.g. it asks for CD),

---

### Post by Pevichaey5 on 2008-01-10
> **kwacka said:**
> You said in your first post that you have a command line, so possibly forget about CD/DVD for now.


sorry but you have more access to the system on a cli than you do on a gui

cli was the first computer interface i believe, gui didn't come til years later

---

### Post by Upstart Blogger on 2008-01-10
> **kwacka said:**
> You said in your first post that you have a command line, so possibly forget about CD/DVD for now.

Do you have an internet connection? 

If yes, try entering:
sudo apt-get install ubuntu-desktop

(it might even work for your external drive) which will give you a graphic display, auto-recognition (hopefully) of external drives and world conquest (possibly)..

If you get an error, come back and let us know what it is (e.g. it asks for CD),

Yes, I do have a connection.  The laptop in question has a wireless card.  But if that isn't something that is going to be available I could easily just connect it to my router using an ethernet cable.

I'll try it and let you know what happens.

---

### Post by Upstart Blogger on 2008-01-11
> **kwacka said:**
> You said in your first post that you have a command line, so possibly forget about CD/DVD for now.

Do you have an internet connection? 

If yes, try entering:
sudo apt-get install ubuntu-desktop

(it might even work for your external drive) which will give you a graphic display, auto-recognition (hopefully) of external drives and world conquest (possibly)..

If you get an error, come back and let us know what it is (e.g. it asks for CD),

It asked for the CD, which was already in the USB DVD drive, so I guess it couldn't see it.  I tried sudo fdisk -l and only got the hard drive reported, or at least I think so, it could see sda1, sda2 and sda5.  No sign of the USB DVD drive.

What's the next move?

---

### Post by perlluver on 2008-01-11
Run ```
sudo gedit /etc/apt/sources.list
``` find where it says CD-Rom and put a # sing in front of it.  Then run ```
sudo apt-get update
``` then try to install ubuntu desktop again.

---

### Post by kvonb on 2008-01-11
-

---

### Post by Upstart Blogger on 2008-01-11
Thanks.  I'll try both of those things in a moment.  I have an ethernet connection to the laptop.  Is there a simple way to install linux using that?  Can the missing files be downloaded?  Or am I barking up a very difficult tree?

---

### Post by Upstart Blogger on 2008-01-11
> **perlluver said:**
> Run ```
sudo gedit /etc/apt/sources.list
``` find where it says CD-Rom and put a # sing in front of it.  Then run ```
sudo apt-get update
``` then try to install ubuntu desktop again.

I get a sudo: gedit: command not found when I try that.

---

### Post by perlluver on 2008-01-11
Try ```
sudo nano /etc/apt/sources.list
```, I kind of forgot that you didn't have gnome installed yet.

---

