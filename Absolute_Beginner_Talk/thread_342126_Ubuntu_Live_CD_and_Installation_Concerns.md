---
title: "Ubuntu Live CD and Installation Concerns"
date: 2007-01-19
forum: Absolute Beginner Talk
---

### Post by tuningproblem on 2007-01-19
This is the first time I've ever used Linux or a Live CD, so I'm confused on a few matters:  It doesn't write to the hard drive at all, right?  I'm using a laptop that absolutely CANNOT lose it's data, so I can't risk it.  If it does write to the hard drive, does it know parts can be written over and some parts can? 

      I'd like to install vlc, but if I do will it just give me an error, or will it erase part of something potentially important, or will it write over a free space?  On a semi-related note, I would like to install Ubuntu, does it give me the option to create a partiton?  Ideally, I'd like to have the option to start up Windows or Ubuntu at startup.  Unfortunately, I don't think I can create a partition in Windows, because I have very few user rights. 

      Thanks for the help in advance, sorry if I sound like a total idiot.

---

### Post by GI_Josh on 2007-01-19
Hi!  Using the live Cd doesn't install anything onto your HD, no worries.  You can play around with ubunut as much as you want without changing a thing.  Nothing installs until you click "install" on the desktop of your live CD environment.

As for installing stuff, I assume you mean in windows, just throw your Ubuntu CD in in windows and a friendly window will pop up.  From here you can select several free programs to install on your windows computer.  This works like a normal install and won't overwrite anything you want to keep, so no worries.

---

### Post by Sef on 2007-01-19
> This is the first time I've ever used Linux or a Live CD, so I'm confused on a few matters: It doesn't write to the hard drive at all, right?

The Live CD doesn't write to the hard drive, unless you install it.

> I'm using a laptop that absolutely CANNOT lose it's data, so I can't risk it. If it does write to the hard drive, does it know parts can be written over and some parts can?

a)Before installing, **back up** your data.  It is always good to back your data in any case, at least once a week if not sooner.

b) The Live CD will not write anything on your hard drive, unless you install it.   If you have only NTFS, then it can't write to it, so no way any data would be affected.

> I'd like to install vlc, but if I do will it just give me an error, or will it erase part of something potentially important, or will it write over a free space?

It will write over free space.

> On a semi-related note, I would like to install Ubuntu, does it give me the option to create a partiton?

You can create a partition.

> Ideally, I'd like to have the option to start up Windows or Ubuntu at startup.

Ubuntu is the default, but you can boot into Windows.

>  Thanks for the help in advance, sorry if I sound like a total idiot.


You don't sound like an idiot: just a person with some valid concerns.

Read [Psychocat's installing]("http://www.psychocats.net/ubuntu/installing") for installing from the Live CD.

Final note:  I would get another computer and practice installing on that because there are no 100% guarantees that everything will go well on your computer.

---

### Post by igknighted on 2007-01-19
If you are extremely concerned about messing up on the install I would recommend using the alternate install disk when you decide to do the install.  It may not look as nice, but it is more stable (not to imply that the live installer is unsafe, but if I had my life's work on a HD and was installing Ubuntu, I would use the alternate disk).

---

### Post by MeeMaw on 2007-01-19
The live disk loads itself into the memory, and does not write to the hard drive. 
It is a great way to try different distributions to check hardware compatibility and see which distribution appeals to you.  If you decide to install (after backing everything up, of course....) there is a program which allows you to partition the hard drive and install Linux to the unused part of the drive. The installer lets you set it up so you can "dual-boot" (choose to start either Windows or Linux.) Do LOTS of research! These forums are a wealth of information.

Welcome to Linux!!!   =D>

---

### Post by smile_sunshine on 2007-01-19
you shouldnt write over anything using the live cd :) 
the main thing when you come to install is when you get to the  "Prepare disk space" screen make sure you choose "resize.......... and use free space" not "erase entire disk"  !!  ( theres a picture here [http://www.psychocats.net/ubuntu/installing]("http://www.psychocats.net/ubuntu/installing")
but yeah its always a good idea to back up your data first just in case
:)

---

### Post by tuningproblem on 2007-01-19
Maybe I need to clarify: when I talked about installing vlc, I meant in the Live CD environment, not from an actually installed version of Ubuntu.  After these positive replies, I tried saving something to the desktop.  Firefox said "done", but when I looked at my desktop it wasn't there.  I tried making a new folder, again in firefox, but it once again didn't show up.  All of this doesn't really meld with the previous replies, which said that it writes to free space.  Another side-note:  Is it pretty easy to uninstall Ubuntu, without any evidence it was ever there, including removing its partition?  You've been much more helpful than I expected, thanks.

Edit: Backing up my data is unfortunately not much of and option, just how large is the risk of data deletion?

---

### Post by yanqui on 2007-01-19
Hi, tuningproblem!  I have a laptop, as well, with windows and data that is critical to my work.  well other stuff too.  but I installed ubuntu onto a hard drive that I put into an aluminum hard drive enclosure that connects to the laptop via usb drive.  I am NOT, I repeat, NOT a linux guru--this was my first successful foray into linux.  I used instructions I found on this forum, [ right here ](http://www.ubuntuforums.org/showthread.php?t=80811).  I have used it several times, done the process several times, mostly to make sure I could do it, once to get from ubuntu to kubuntu (yeah, there are probably easier ways to do that); but I have to give a presentation on it in February, so I needed to be able to do it and know it works.  There are some other tips not mentioned in that other post; like, my usb hard drive is recognized in BIOS as a hard drive, not as a USB device.  ALSO, every time i disconnect the drive from the laptop, I have to go in and reset it as the first hard drive to boot from in BIOS.  Since my laptop recognizes it as a hard drive, yours may or may not, and you may or may not need to be able to boot from a usb device if recognized as a hard drive.  oh, and one install was when I tried to install mepis and it not only didn't work, it hosed the ubuntu installation.

And if you're going to try the usb thing, don't use the live cd, use the alternate install.  something about trying to do the install while the live is running won't work well with the usb effort.

good luck--as I said, it was exactly what I needed and has worked consistently for me.

---

### Post by yanqui on 2007-01-19
> **tuningproblem said:**
> 
Edit: Backing up my data is unfortunately not much of and option, just how large is the risk of data deletion?

big enough--don't try it.

spend a few bucks on a hard drive and usb enclosure and try the installation above.

---

### Post by smile_sunshine on 2007-01-19
just thought i'd point out the live cd will be a lot slower to run than when its installed.  the xubuntu live cd would be a bit faster (it uses XFCE instead of gnome as window manager)

---

