---
title: "USB Automount in Terminal"
date: 2007-07-03
forum: Absolute Beginner Talk
---

### Post by mrsticks on 2007-07-03
I have one of my servers running 6.06 - Dapper.  I hardly ever use the gui ( Gnome ) to do anything with the servers.

I have an external USB Drive. I sit at my Putty window, plug in the drive, and nothing happens.  I would expect it to automount, just as it does when I do use the gui.  I put an entry in the fstab to tell it where to mount, and it still doesnt mount.

Now if I do login to the gui, and plug it in, BAMN, it shows up on the desktop, mounts where I would expect it to mount ( /media/PARTITION ).

When I do plug it in, in the terminal, the logs ( dmesg and syslog ) show nothing is wrong with the partition or anything, though syslog says that the drive has been mounted 43 times and a fsck is needed.  So I am currently running that.

So I guess my main question is, why do these drives mount normal if I am logged into the gui, but not if I am only logged into the terminal?

Thanks

-peter

---

### Post by thornomad on 2007-07-03
I believe the automounting feature is a product of some of the packages that come with the GUI.  There are ways to automount with a non-GUI server edition, though I haven't tried any of them:

[http://ubuntuforums.org/showthread.php?t=99345&highlight=automount+usb+server](http://ubuntuforums.org/showthread.php?t=99345&highlight=automount+usb+server)

D

---

### Post by mrsticks on 2007-07-03
My mistake, I was a little unclear.  Though this is installed on a server, we actually used the Desktop Edition of Dapper and installed the packages as we needed them.

So all the suggestions in the posted thread were good ones, but were already installed on my box.

Any other thoughts?

Thanks

-peter

---

### Post by Nikron on 2007-07-03
I think, I mean, I am just guessing, hal only mounts these things when graphical programs navigate to them.  And then promptly umounts it.  Which is fine for a desktop.  Any way, why do you need to it to automount?  Mounting is as easy as 'sudo mount /dev/sdb1 /mnt/usbdrive'.  ('sudo fdisk -l' lists possible hard drives)

---

### Post by mrsticks on 2007-07-03
Agreed, hal probably only mounts it as needed in the gui.  As to why I want it to automount... because I'm lazy.  Trying to make life a little easier.  I can just hard code a mount into a script and be done with it.

Thanks all.

-peter

---

