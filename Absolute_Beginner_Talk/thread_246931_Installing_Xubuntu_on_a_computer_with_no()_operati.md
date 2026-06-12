---
title: "Installing Xubuntu on a computer with no(?) operating system..."
date: 2006-08-30
forum: Absolute Beginner Talk
---

### Post by TheInvisMan on 2006-08-30
One of the computers in my house is very old.  Somewhere between eight and ten years.  I didn't use it much, because it stopped connecting to the internet... but I recently managed to fix that problem, so I decided to start using it again.  But first, I wanted to reformat and reinstall Windows 95, since it's got a lot of junk on it.

So, I reformatted and reinstalled.  But I ran into an error of some sort, because I made a stupid mistake during installation.  So, I reformatted and tried again.  Then the installation couldn't complete because my disc got scratched sometime after the first re-installation.  So I reformatted again.  But I still can't install Windows 95.  So, my computer has no operating system, I think.

Making matters worse... now my Windows 95 boot floppy doesn't even work.  Worse yet, I haven't even been able to make a new one because the other two computers in my house (Windows XP) refuse to recognize either of my floppy drives.  One did for a brief period, but not anymore.  (If anyone could help me with that, too, it'd be nice.)

Since my computer has absolutely no operating system anymore, I decided to try Linux, just so that my computer could actually be running with something.  I've heard it might have a steep learning curve, especially for someone like me who's used Windows all their life... but I figure I can get some guides (and help from places like this) online, once I get the thing up and running.


So, here's my problem... I've burned a copy of Xubuntu to CD already.  I've changed the BIOS settings to boot from CD. But when I boot up my computer, it doesn't recognize the CD in the drive.  It doesn't even say it's an "Invalid System Disk" like it does with my Win95 floppy disk - it just ignores my CD altogether.

I know it's not the disk drive, which works fine in other computers (and is recognized by the system during bootup)... my computer simply doesn't recognize the CD.  So... how would I go about getting it to recognize my CD?  Or, alternately, if I could install Linux by hooking my hard drive up to one of my other computers, how would I do that?

And, finally... my old system has a 200MHz processor and 64MB of RAM.  I have two hard drives; one is 2GB, and I think the other is 40GB (though I need to reformat that one).  Are my system requirements too low to use Xubuntu anyway?

---

### Post by jISh on 2006-08-30
Alright, first of all when you burned your Xubuntu CD, did you just copy the .iso file to the disc, or did you use something like Nero or ImgBurn to actually write the CONTENTS of the .ISO to the disc?

Second of all, your requirements are far too low to be able to install Xubuntu through the LiveCD. You can still install and run it, but you need to use the alternate install CD, which provides a text based install. Reason being the regular LiveCD will actually boot you into Linux, with a graphical installer that requires 192MB RAM. This alternate install CD is available [here]("http://cdimage.ubuntu.com/xubuntu/releases/6.06.1/release.1/xubuntu-6.06.1-alternate-i386.iso").

I'm really not sure how fast the system will run, even with a light distro such as Xubuntu. If it does run too slow, there are many other distros, geared towards slower computers or people looking for performance, that may interest you, notably Puppy Linux and Damn Small Linux.

---

### Post by Greycloak on 2006-08-30
Damn Small Linux will run on damn near everything.  I put it on a really old laptop with 32mb of ram and it runs fine.

---

### Post by goatflyer on 2006-08-30
... or try Feather linux if you can't get xubuntu to work.  Feather is only slightly bigger than DSL, but has many more apps including Firefox if you dare (but Dillo makes old computers look pretty fast).  Feather didn't care about breaking the 50MB size limit, they went for a more complete 128 MB distro.


How to boot (applies to all):  Make yourself a floppy containing the SmartBootManager image.  There is a copy somewhere on the ubuntu iso, but you can also find it here:

[http://btmgr.webframe.org/](http://btmgr.webframe.org/)

There are instructions on how to make the floppy from either Linux or Windows.  Whats nice is it contains its own cd drivers, so you may be able to boot a CD on machines which don't even have the BIOS option to do so.  Very nice utility.

3rd tip: many Linux installs work better when there is a preexisting swap partition already present on the disk.  500MB will do wonders.  To create such a partition, you can use the command-line fdisk on the Feather CD unless you know a better way.

Last possibility: Puppy Linux.  It is a live CD only, but it wants to store a small .PUP file somewhere on the hard disk to record your changes.  If you really can't succeed in installing any distro, use Puppy.  Puppy also works better if you create a swap partition.

---

