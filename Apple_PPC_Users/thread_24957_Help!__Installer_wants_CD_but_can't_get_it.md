---
title: "Help!  Installer wants CD but can't get it"
date: 2005-04-08
forum: Apple PPC Users
---

### Post by Tofu on 2005-04-08
I'm doing a clean installation of Hoary on a G4 Sawtooth Powermac, via CD image.

The installation was going fine, up until the installer ejected the CD, it then started booting up off the hard drive. Halfway through it requested that the "Hoary" install CD be reinserted into the CD-ROM drive, so it can install another 350MB of files.

I put the CD into the drive, but it is not recognized. Even when the CD is in there, the installer keeps asking for the CD again.

What can I do? Why can't it read the CD when booting off the hard drive for the first time? It read the CD at the initial part of the install. I thought the CD was dual HFS/ISO.

---

### Post by soul_rebel on 2005-04-10
try to escape to a shell during installation and do a "mount" to see if the cd has been mounted. There should be a console with system messages too.

---

### Post by Tofu on 2005-04-11
Ubuntu Hoary can't read the install CD. It can control the CD drive, I can hear the drive activate and start spinning the disk, but no data can be read.

What kind of CD disk formats can Hoary read? HFS? ISO?  Maybe I should use a different computer to make a new install CD in a different format that Hoary can read.

[QUOTE=soul_rebel]try to escape to a shell during installation and do a "mount" to see if the cd has been mounted. There should be a console with system messages too.[/QUOTE]
Thanks for responding, soul_rebel. I'm a newbie with Linux, so I'm not sure how to do those things. With Hoary, it gets halfway through booting off the hard drive when it asks for the install CD to be inserted. Because it doesn't boot all the way up, I can't reach the console.

---

### Post by soul_rebel on 2005-04-11
if you think the cd is corrupted you can try to download it and burn it again. That may solve the problem.

Also i don't undestand if you completed the first part of install (the cd is verified during that part), and the problem comes when in the second part when booting the hd.

The cd is only needed in the first part, then you should boot from the hd.

Have you simply tryed all the install again? 
PS: to ecape to a shell try ctrl + alt + F2

---

### Post by Tofu on 2005-04-11
[QUOTE=soul_rebel]i don't undestand if you completed the first part of install (the cd is verified during that part), and the problem comes when in the second part when booting the hd.[/QUOTE]
My understanding (which may be wrong) is that when you initially boot off the install CD, it is being handled by the Open Firmware of the Mac, which can read HFS disks and maybe other formats of disk.

When you boot Linux off the hard drive, I don't think Open Firmware is being used. I presume that Linux is then controlling any disks. I don't know what disk formats Linux "Hoary" can read.

[QUOTE=soul_rebel]The cd is only needed in the first part, then you should boot from the hd.[/QUOTE] That's what I thought, but when Hoary boots up for the first time off the hard drive, mid-way though the boot process it wants to install new software from the CD, for some reason.

Strange! I'll try reinstalling and let you know how it went.

---

### Post by Len on 2005-04-11
Since it is a burned CD image I doubt it is magically transformed from ISO 9600 to HFS :P.

You can always check: 
mkdir /media/cdrom (or was it cdrom0?)
mount -t auto /mount/hdb /media/cdrom
(or whatever drive letter your CD ROM drive is assigned to, could be hdc, hdd, etc)

If it complains about "device not found" or something like that you at least know that it isn't the CD but the CD-ROM drive that is not recognised. In that case, use modprobe to load a module for your drive.

---

### Post by Tofu on 2005-04-14
[QUOTE=soul_rebel]try to escape to a shell during installation and do a "mount" to see if the cd has been mounted. There should be a console with system messages too.[/QUOTE]
soul_rebel, thanks for your input. I finally worked out how to get back to the shell and use the 'mount' command.

It returns the message:
> wrong fs type, bad option, bad superblock on /dev/hdc, missing codepage or other error 

Then I typed in dmesg and got the following:
> UDF-fs: No VRS found
Unable to identify CD-ROM format 

I guess all this is a clue as to why it doesn't recognize the install CD. It gives me the impression that the CD is the wrong directory type, but the same CD was successful in the first part of the installation. Only after rebooting it cannot recognize the CD.

Install CD was burned on a different Powermac using Roxio Toast in OS X, using the 'mount image' function.

---

### Post by soul_rebel on 2005-04-14
I don't know if there is any particular way to burn the image on a mac. Have you checked if is there a recommended way of doing it?

---

### Post by Tofu on 2005-04-14
I tried burning the image of the install disk in Toast (commercial disk application) as well as Firestarter, a shareware app. Same result with both.

When burning an ISO disk image, I would have thought that the directory type would already be determined by the disk image.

Alternately, I wonder if it could be a problem with the CD-ROM and its driver software. Whilst endlessly Googling for answers, I found this post on another Linux forum...

> UDF is the Universal Disk Format, and the VRS is the Volume Recognition Sequence, which identifies the type of data on your CD. It means that your CD driver (thru the kernel) doesn't identify the type of file system on the CD you try to mount.
Try to remove in /etc/fstab the type of data for cd drive for it to use autodetect without UDF.
[CENTER][SIZE=1][http://forums1.itrc.hp.com/service/forums/questionanswer.do?admit=716493758+1113475094838+28353475&threadId=724798](http://forums1.itrc.hp.com/service/forums/questionanswer.do?admit=716493758+1113475094838+28353475&threadId=724798)[/SIZE][/CENTER] 
 
I wonder if I can upgrade drivers, or change that file called 'fstab'?

Could it be possible that although Open Firmware recognizes the CD-ROM drive the Linux kernel doesn't? Could the Linux kernel lack the necessary driver to detect the CD? I'm not sure if that's a possibility or not.

CD/DVD combo drive model: MATSHITADVD-ROM SR-8584A

---

### Post by Tofu on 2005-04-15
If I can't get Linux to read the CD, is there any other way to finish the install?

I have command-line access to Linux, but the install doesn't seem to be complete. I have a home network router with a machine running Mac OS X elsewhere on the network.

Would it be possible to put the install CD in the other Mac, then access it via the network from the Linux shell? Could I finish the install that way?

Keep in mind that I'm a newbie to Linux and don't know how to access the network.

---

### Post by soul_rebel on 2005-04-15
please format your partitions and retry install from scratch. cd is only needed when booting from it; all necessary packages are copied to the hd before rebooting.

---

### Post by Tofu on 2005-04-15
[QUOTE=soul_rebel]please format your partitions and retry install from scratch. cd is only needed when booting from it; all necessary packages are copied to the hd before rebooting.[/QUOTE]

Hi soul_rebel. You are right! I reinstalled once more, this time making sure I waited until all packages are copied and unpacked and reconfigured. I'm using a CRT monitor rather than my usual LCD, as I think the LCD was not giving me all the feedback I needed. While installing I also selected the option to erase the hard drive, so I can let Ubuntu reconfigure the partitions.

Reinstalling worked! I've got the Ubuntu desktop up and it looks great! Very exciting.

soul_rebel, I'd like to thank you for helping me through my first steps into Linux and Ubuntu. I'm sure I'll have more questions in the future, but I'm very happy that my system is up and running.

Thanks for adopting my thread!  :)

---

### Post by soul_rebel on 2005-04-16
I know that in the beginning it seems hard, but don't worry, you will get used to it and have a lot of fun. Bye :)

---

### Post by Rxke on 2005-04-16
Aaah! :)
Great!

Have fun exploring, fellow newbie, and remember: re-installing your system is part of the game if you like to tinker, so it's ok, heehee...

---

### Post by accozzaglia on 2005-04-19
I was redirected to this thread from the [original thread](http://ubuntuforums.org/showthread.php?p=136993#post136993)  I started regarding why I'm experiencing nothing after "first stage" CD install beyond a basic console.

As mentioned in that thread, I'm installing Ubuntu 5.04 Hoary release on my Yikes! 350MHz G4 system.  Because of my RasterOps CRT being unable to rescan at the default frequency, I can only use the "video=ofonly" (Open Firmware only) graphics version of the installer (the red screen version, apparently).

Despite the feedback given on this thread, the problem I'm facing isn't really addressed by the above, though my system falls into that "first class" of G4s released in 1999.  I have attempted the install several different ways -- standard, server, and expert mode (for both) -- and have allowed Ubuntu to configure the partitions in some installs while I configured them in others.  The result is the same: the CD install completes and I am prompted to reboot with the CD removed from the drive to allow for hard disk boot and (presumed) activation of a "second stage" script for unpacking, installing and configuring the GNOME GUI components and other daemon functions (like SSH/OpenSSH).  

But this second stage never happens.

And as noted before, that's where the road ends for me.  I'm left to my own (console-only) devices after the reboot.  Has anyone else dealt with this issue?  Has anyone else here installed Hoary in "video=ofonly" mode?  There shouldn't be a functional difference in this alternative video install process, I certainly wouldn't think.  Any reason why there would be?

If you've got a sandbox to play with which happens to be a Yikes! box, would you be up for trying an "ofonly" install and see what comes of it?  I'd be very curious.  Much thanks. :)

>>> edited to append: Alternately, I was thinking that knowing where to look after first hard disk boot to manually kick-start the second stage installer would be another way to work around this.  I glanced through /sbin/ to see if there was a setup.sh script (which would automatically run at system startup time, but nothing was present. <<<

---

