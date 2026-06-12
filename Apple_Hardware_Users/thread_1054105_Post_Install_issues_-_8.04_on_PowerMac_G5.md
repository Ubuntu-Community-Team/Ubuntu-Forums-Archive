---
title: "Post Install issues - 8.04 on PowerMac G5"
date: 2009-01-29
forum: Apple Hardware Users
---

### Post by dank28 on 2009-01-29
Hello everyone.  I've read a lot of things on the boards regarding what seem like similar issues to mine, but the solutions varied from re-installing grub to installations of graphical drivers to xconf files to aligning partitions and "blessing" things.  Most of those are over my head at this point, so I'm hoping someone can point me in the right direction for this particular issue:

I'm attempting to run Hardy (mostly because there is a live disk for 8.04, might try to go to 8.10 once this is worked out.)  I'm using a PowerMac G5 1.8 ghz, 4gb ram.

I successfully repartitioned the drive and reinstalled OS X, then installed Hardy via live-powerpc64 using Guided Install - Free space.  No problems up to this point.

Once I restarted I saw "Stage 1 boot" : l for linux, x for OS X, c for CD ROM.  (Looks a little different than grub for i86, but pretty intuitive, or so I thought.)

I chose "l" for ubuntu, but was taken to a blank white screen.  Thought maybe it needed some time to boot up at first, but no changes when I let it sit there a few minutes.  Rebooting and choosing "x" for Leopard brought me to the same white screen.

I rebooted holding down the option key (Boot Menu startup) and chose Mac OS X, and that booted fine.  Now whenever I reboot it goes directly into Leopard, no Stage 1 Boot options.  If I choose the Linux startup disk during a Boot Menu startup it goes black for a second and then returns me to the Boot Menu.

Anyone have clues on the white screen issue, or how to get the dual boot setup working correctly?  I apologize if this is a repost of a previous issue. Thanks in advance for any pointers!

---

### Post by tiresia on 2009-01-29
Like a PC has BIOS to identify the hardware before booting a System, a PowerPC has 'Open Firmware', that as a similar function (well, it is more powerfull). 

GRUB is the Linux Kernel bootloader on PC (x86), Yaboot is the Linux Bootloader for (NewWorld) PowerPC. 
What you see, when you boot your Mac G5, is the first prompt of Yaboot, that is asking you which System, you would like to boot.

Your problem is a well known issue on powerpc64 with Ubuntu Hardy. When you install it, the installer fails to detect correctly the Open Firmware Path, so that when you restart, Yaboot doesn't know where to look for the linux kernel. 

There is a work around that you can find here, together with other infos about Yaboot
[http://ubuntuforums.org/showthread.php?t=994882](http://ubuntuforums.org/showthread.php?t=994882)
The point [6] is what interests you.

Or if you don't want to deal with it, download the Ubuntu Intrepid Installer 8.10 and install it after erasing the partions for Ubuntu Hardy. 

I would try to set correctly what you already installed, it is also a good exercise.
Let us know, how it is going.

---

### Post by dank28 on 2009-01-29
Thanks so much, tiresia!

I'll give that a shot and let you know how it goes.  :D

---

### Post by tiresia on 2009-01-29
I forgot to tell you, that the Intrepid Installer 8.10 has another issue (for every ppc).
Here is the workaround for it
[http://ubuntuforums.org/showthread.php?t=964904](http://ubuntuforums.org/showthread.php?t=964904)

---

### Post by dank28 on 2009-01-31
So I'm trying out the yaboot fix detailed in the other post linked, but running into an error:

```
ubuntu@ubuntu:~$ ofpath /dev/sda2
/disk@0:2
ubuntu@ubuntu:~$ zcat Desktop/ofpath.gz > Desktop/ofpath
ubuntu@ubuntu:~$ sudo cp Desktop/ofpath /usr/sbin/ofpath
ubuntu@ubuntu:~$ ofpath /dev/sda2
/ht@0,f2000000/pci@7/k2-sata-root@c/k2-sata@0/disk@0:2
ubuntu@ubuntu:~$ sudo yabootconfig -v -b /dev/sda2 -r /dev/sda4
yabootconfig: unrecognized option `-v'
Try `yabootconfig --help' for more information.
ubuntu@ubuntu:~$ yabootconfig --help
Usage: yabootconfig [OPTION]...
Generate a working /etc/yaboot.conf.

  -t, --chroot               set root directory yabootconfig should work from
  -r, --root                 set root partition, Example: /dev/hda3
			       default: determined from {chroot}/etc/fstab
  -b, --boot                 set bootstrap partition, Example: /dev/hda2
			       default: first type: Apple_Bootstrap partition
      --kernel-args          add an append= line with specified arguments
  -q, --quiet                don't ask any questions/confirmation
      --noinstall            don't automatically run mkofboot
  -h, --help                 display this help and exit
  -V, --version              output version information and exit
ubuntu@ubuntu:~$ sudo yabootconfig -V -b /dev/sda2 -r /dev/sda4
yabootconfig 1.0.8
Written by Ethan Benson

Copyright (C) 2001, 2002, 2003 Ethan Benson
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
ubuntu@ubuntu:~$ sudo yabootconfig -b /dev/sda2 -r /dev/sda4
yaboot is the Linux Loader for PowerPC.  yabootconfig sets up your system to boot directly
from your hard disk, without the need for a boot CD, floppy or a network boot.
Install yaboot bootstrap on /dev/sda2 to boot Linux from /dev/sda4? [Yes] Yes
Creating a simple /etc/yaboot.conf...
yabootconfig: Could not determine necessary information, aborting...
yabootconfig: Are you using chroot yabootconfig instead of yabootconfig --chroot ?

```

I wasn't gleaning too much info from the ofpath output, but I verified in GParted that /dev/sda2 is my boot partition (hfs), /dev/sda3 is my Mac OSX partition (hfs+), and /dev/sda/4 is ubuntu (ext3)

Can you pinpoint where I've gone astray?  Thanks!

---

### Post by tiresia on 2009-01-31
Actually, it looks ok - the patched ofpath is working good for you.
But, are you doing this from a Live CD?
Try again the last step after having mounted /dev/sda4 
(just go the 'Places' and click on the Icon of your partition)

Let me know, how it works

---

### Post by dank28 on 2009-02-01
Hey tiresia, thank you for your continued assistance on this.

I am booting from the the live cd to make the changes (can't boot into the installed system - yet)

I tried going through the steps again and mounting the drive before I ran "sudo yabootconfig -b /dev/sda2 -r /dev/sda4", but got the same error:

```
yabootconfig: Could not determine necessary information, aborting...
yabootconfig: Are you using chroot yabootconfig instead of yabootconfig --chroot ?
```

After reading a few other threads on here, as well as the "man ybin" and "man yabootcofig" files, I decided to play a bit.

I navigated to the yaboot.conf file on my ubuntu partition.  I had to use the terminal to first create a backup and then create a copy on the live Desktop for editing, then but manually changed the path lines as follows:

From:
```
device=/disk@0:2
```
To:
```
device=/ht@0,f2000000/pci@7/k2-sata-root@c/k2-sata@0/disk@0:2
```

I also added the line "defaultos=macosx" to the file, and then used the terminal to overwrite the original file with my edited version.  I've pasted the new yaboot.conf file in below.

```
## yaboot.conf generated by the Ubuntu installer
##
## run: "man yaboot.conf" for details. Do not make changes until you have!!
## see also: /usr/share/doc/yaboot/examples for example configurations.
##
## For a dual-boot menu, add one or more of:
## bsd=/dev/hdaX, macos=/dev/hdaY, macosx=/dev/hdaZ

boot=/dev/sda2
device=/ht@0,f2000000/pci@7/k2-sata-root@c/k2-sata@0/disk@0:2
partition=4
root=/dev/sda4
timeout=100
install=/usr/lib/yaboot/yaboot
magicboot=/usr/lib/yaboot/ofboot
macosx=/dev/sda3
defaultos=macosx
enablecdboot

image=/boot/vmlinux
	label=Linux
	read-only
	initrd=/boot/initrd.img
	append="quiet splash"

image=/boot/vmlinux.old
	label=old
	read-only
	initrd=/boot/initrd.img.old
	append="quiet splash"
```

After all of that, however, I am unable to run "ybin -v" to update yaboot because it cannot find the correct file.  Can you advise on how I can point ybin to the correct path to finish the ofpath correction?

Thanks, again!

---

### Post by dank28 on 2009-02-01
Ok, so I played a little more and got it to work by following the process listed in #6 at the linked thread, but running the following command for the last step:

```
sudo yabootconfig -b /dev/sda2 -t /media/disk
```

I had to use chroot to point yabootconfig to the correct directory (and /media/disk is what it was calling my ubuntu partition, not /dev/sda4)

Thanks again for all of your help!  :D  Now I'm off to set my default os, turn on my ubuntu splash page, and then get my second display working...once the initial system updates are complete.  ;-)

---

### Post by tiresia on 2009-02-01
Ok, great. I was just thinking to propose you to access the HD with Open Firmware. But so it's easier. In few words, you can use in OF the command boot followed by the of path (or the alias for it) to boot yaboot.

Don't forget to fix the ofpath on your system!
The patched ofpath, that you used on the LiveCD was just stored in the RAM...
Just download from launchpad the patched ofpath on your Desktop and overwrite the buggy on (repeat the first step).
That's because, if in the future you need for any reason to reinstall yaboot, you will get the same problem

Enjoy your new linux-ppc

---

### Post by stream303 on 2009-02-02
Interesting - I thought yabootconfig didn't work on G5's - only G3's and G4's.

Most of the time we end up manually editing /etc/yaboot.conf ourselves, and then following up with

```
sudo ybin -v -C /etc/yaboot.conf
```

To make the system aware of the changes.

Many just use ybin -v, but I prefer the longer command that actually specifies the location of the file following -C. (capital C)  This might help out in the future.

You'll most likely have to manually edit your /etc/X11/xorg.conf to take into account your monitor's specific horizontal / vertical frequencies, as well as native resolution, as well as forcing the video driver, ie ati, r128, nv, etc.

It can be done - I believe I've seen a few references to the single-cpu powermac here and in the ppc-archive forums..

---

### Post by dank28 on 2009-02-02
Well, I fixed it just long enough to break it again...

Once I had the ran all of the 8.04 updates, I went back to make OX X my default.  It looks like using the chroot command in yabootconfig created a generic yaboot.conf file that didn't mention my osx partition at all.

I manually edited the file, and then ran "sudo ybin -v".  It ran (gotta love the output line "Blessing /dev/sda with Holy Penguin Pee") and I rebooted...back to where I started from.  Yaboot brings me to a blank screen, and I had to use the mac firmware to select osx.

I thought I double checked the ofpath to ensure it was correct in my revised yaboot.conf, but I'll have to check again tonight.

Thanks again for everyone's help.  It's not all settled yet, but I have confidence I'm getting closer. :)  I will probably upgrade to 8.10 after this is all done, but I don't want to just give up and install it direct.  I've already gained a much deeper level of understanding about yaboot, ybin, and the terminal in general through this process.

tiresia, you have me a little confused with this post:
> The patched ofpath, that you used on the LiveCD was just stored in the RAM...
Just download from launchpad the patched ofpath on your Desktop and overwrite the buggy on (repeat the first step).
That's because, if in the future you need for any reason to reinstall yaboot, you will get the same problem

Perhaps this is the missing key I needed in the first place.  Would you recommend I use yabootconfig -t (chroot) again to be able to boot into ubuntu and then apply the ofpath fix?  And once I have that fixed try to make osx the default?

stream303, I was actually able to find my monitor's model while using the live disk, but I needed to restart before applying the changes, so I needed to get all of the boot issues worked out first.  I don't exactly recall how I got to the configuration utility (it's a command in the terminal I pulled from a Ubuntu book.)  I'll find that tonight and post it here.

If that doesn't work I'll look into the xorg.conf edits you mentioned.  The monitor is detected during the boot process (I see text in it fine) but once I'm in the system it's just a while screen with some corruption on it.  It's the second monitor, so not a high priority to fix yet.

---

### Post by tiresia on 2009-02-03
> **dank28 said:**
> 
tiresia, you have me a little confused with this post:

Perhaps this is the missing key I needed in the first place.  Would you recommend I use yabootconfig -t (chroot) again to be able to boot into ubuntu and then apply the ofpath fix?  And once I have that fixed try to make osx the default?

dank28, sorry for making you confused - my english is not always enough clear... I try again.

When you boot your g5 from the LiveCD, the working root and system are, of course, not those one, that you installed on /dev/sda4.
Therefore when you copy the patched utility ofpath to /usr/sbin/, you are overwriting the ofpath of the working system (the LiveCD, that is working just on the RAM),
not that one installed (and that will not correctly work).

If you want to overwrite the installed ofpath, you should copy it like this (I assume that /dev/sda4 is mounted on /media/disk)
```
sudo cp Desktop/ofpath /media/disk/usr/sbin/ofpath
```  
You can chroot the installed System
```
sudo chroot /media/disk/
```
Now you are 'inside' the installed System, and you can use the patched ofpath. Check if it works correctly
```
ofpath /dev/sda2
```
Install a correctly configured yaboot
```
yabootconfig -b /dev/sda2 -r /dev/sda4
```
Check and change your new yaboot.conf (defaultos=macosx)
```
nano /etc/yaboot.conf
```
Update that change
```
ybin -v
```
Done. Restart your computer

---

### Post by dank28 on 2009-02-05
Thanks, tiresia.  I'm sure your advice would have worked if I had been patient enough to wait for it.  :(

Instead I repeated the entire process (boot from live disk, use the ofpath patch using "sudo yabootconfig -b /dev/sda2 -t /media/disk" at the last step, then booting back into my system and using the ofpath patch again to make sure my system (and not just the RAM) was corrected.

THEN I started playing with the screens and graphics utility.
```
gksu displayconfig-gtk
```

I was able to get my second monitor recognized, or so I thought.  I logged out as prompted and ended up having to log back into a CML-only system.  After I figured out how to shut down (sudo shutdown now) I booted back up into the same CML system, but the entire screen was flashing this time.

Realizing I was in over my head, I booted with the live disk, wiped the ubuntu partition, and installed Intrepid.  (Had to use the No CD-ROM workaround, but otherwise no problems.)

So I thank you again for all of your help and guidance!! :KS  Hopefully this thread will help another PowerMac G5 user in the future.

I'll continue playing with the dual monitor settings, but I'll use the steps documented TwinView threads and proceed with more caution in the future.  ;)

Once the "Solved" marker comes back to the forums I'll mark this thread as such.

---

