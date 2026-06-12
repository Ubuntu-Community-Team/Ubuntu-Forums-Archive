---
title: "A question of kernals - why one boots and two others don't"
date: 2007-05-14
forum: Absolute Beginner Talk
---

### Post by rhageman on 2007-05-14
Hi Gurus,

I'm new to both Ubuntu and Linux but not to OS hopping (approximately one week into this).  I've worked on CP/M, MSDOS, Amiga OS, Windows 98 and XP, and MAC prior to 10.

My question has to due with the GRUB boot choices that I'm offered in my dual boot system.  Grub gives me six choices of Ubuntu kernal:  2.6.20-15-generic, 2.6.17-11-generic, 2.6.17-10-generic and their (safe?) alternatives.  Neither 20-15 nor 17-11 will boot all the way through.  They hang at the black Ubuntu screen with the progress indicator stuck at the start.  17-10 boots all-the-way.

Why the difference?  I'm guessing that 20-15 and 17-11 are newer and therefore - in theory - improved.  Does this mean I need to update something to get them to run?

By-th-way, my system has an Intel dual core running at 3.2 Ghz with 2 GB of RAM.  What used to be drive D: is now the Ubuntu drive (nominal 120 GB).

Thank for any info you can provide.

---

### Post by vtel57 on 2007-05-14
There may be something problematic with the newer installed kernels. Please post a copy of your /boot/grub/menu.lst file. Also, post the output of this terminal command:

```
$ ls -a /boot
```

---

### Post by rhageman on 2007-05-14
The menu.lst looks like this-


# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=c88401dc-c80a-4979-96ef-e98e75f27118 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=c88401dc-c80a-4979-96ef-e98e75f27118 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=c88401dc-c80a-4979-96ef-e98e75f27118 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, kernel 2.6.17-11-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.17-11-generic root=UUID=c88401dc-c80a-4979-96ef-e98e75f27118 ro quiet splash
initrd		/boot/initrd.img-2.6.17-11-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.17-11-generic root=UUID=c88401dc-c80a-4979-96ef-e98e75f27118 ro single
initrd		/boot/initrd.img-2.6.17-11-generic

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=UUID=c88401dc-c80a-4979-96ef-e98e75f27118 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=UUID=c88401dc-c80a-4979-96ef-e98e75f27118 ro single
initrd		/boot/initrd.img-2.6.17-10-generic

title		Ubuntu, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hde1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


=======================================================
The results of "ls -a /boot" are these-


.                             initrd.img-2.6.17-11-generic.bak
..                            initrd.img-2.6.20-15-generic
abi-2.6.17-10-generic         initrd.img-2.6.20-15-generic.bak
abi-2.6.17-11-generic         memtest86+.bin
abi-2.6.20-15-generic         System.map-2.6.17-10-generic
config-2.6.17-10-generic      System.map-2.6.17-11-generic
config-2.6.17-11-generic      System.map-2.6.20-15-generic
config-2.6.20-15-generic      vmlinuz-2.6.17-10-generic
grub                          vmlinuz-2.6.17-11-generic
initrd.img-2.6.17-10-generic  vmlinuz-2.6.20-15-generic
initrd.img-2.6.17-11-generic

---

### Post by vtel57 on 2007-05-14
Hmm... something doesn't look right with the two newest kernel upgrades, 17-11 and 20-15. You can try removing those two kernels in Synaptic. Reboot. Then reinstall the newest of kernel... 20-15 with Synaptic. It should correct the menu.lst for you automatically. Reboot again... this time try to boot into the newly installed 20-15 kernel.

---

### Post by rhageman on 2007-05-15
Willing to give it a try.  I would like to know what doesn't look right about those two entries.  This is how I learn, thanks.

---

### Post by rhageman on 2007-05-15
Checking before I do something dumb.  The entries I'll want to uninstall in Synaptic are the ones labeled "linux-image-(version number)-generic" - correct?

---

### Post by vtel57 on 2007-05-15
I used inaccurate wording, rhageman, to describe what I was trying to say. Nothing in there actually "looks" bad. I'm just threorizing that the upgrade to the newer kernels failed for some reason... corrupt download, bad installation, etc.

Boot to your working kernel. Using Synaptic, "Mark for complete removal"

Linux-kernel 2.6.20-15-generic

and 

Linux-kernel 2.6.17-11-generic

**MAKE SURE** that you are **not** removing your good kernel... 2.6.17-10.

When you remove those others, Synaptic will give you a notice telling you that some other files will be removed also. That's normal. When you do a complete removal of the kernel, it removes the source and the headers also.

You won't hurt anything as long as you don't do anything to your good kernel. Once you've removed these others, you can reboot and then attempt to install the newest kernel again, using synaptic... or just wait a bit and the auto-updater will tell you that the newer kernel is available for upgrade. After it's installed, GRUB should be automatically amended and you can attempt to boot to the newer kernel.

If it works, don't worry about the older "good" kernel. Just leave it alone. It's always good practice to have one older, stable kernel available on your system, just in case.

Luck!

---

### Post by rhageman on 2007-05-15
There are NO installed entries in Synaptic  that are labeled either "Linux-kernel 2.6.20-15-generic" or "Linux-kernel 2.6.17-11-generic".

There ARE installed entries in Synaptic  that are labeled either "Linux-image 2.6.20-15-generic" and "Linux-image 2.6.17-11-generic".

Are these the correct ones to uninstall?



The only other entries are for linux restricted modules.

---

### Post by vtel57 on 2007-05-15
Uh... yes. Sorry 'bout that. Linux-image is correct. Remove those. That should also remove any corresponding headers and source that you have installed for those kernels.

---

### Post by n8bounds on 2007-05-15
Also turning off "quiet" kernel mode options will give you a verbose boot scroll so you can see what is hanging it up in the first place

---

### Post by Adramelech on 2007-05-15
Do you use propietary drivers?

---

### Post by rhageman on 2007-05-16
n8bounds,

If I understand what you're saying, I would modify the following section of menu.lst -

title Ubuntu, kernel 2.6.20-15-generic
root (hd1,0)
kernel /boot/vmlinuz-2.6.20-15-generic root=UUID=c88401dc-c80a-4979-96ef-e98e75f27118 ro quiet splash
initrd /boot/initrd.img-2.6.20-15-generic
quiet
savedefault


- to do what?  Comment out the quiet?

title Ubuntu, kernel 2.6.20-15-generic
root (hd1,0)
kernel /boot/vmlinuz-2.6.20-15-generic root=UUID=c88401dc-c80a-4979-96ef-e98e75f27118 ro quiet splash
initrd /boot/initrd.img-2.6.20-15-generic
# quiet
savedefault

---

### Post by rhageman on 2007-05-16
Adramelsch,

One week into Linux, I would have to say, "What?"

As far as I know,  Ubuntu installed from a 6.10 disk and then did a web based upgrade to 7.04.  After that, I'm finding my way through menu choices, learning how to find command lists for the CLI, trying to find out about why some kernals work and some don't, find out how to get the Deskjet on Linux shared with Windows, understand the philosophy of the Linux directory structure, and umteen other things, etc.

I notice that all three of you are "Carafe" members, which I'm guessing is 100 posts or more.  That is probably backed by one or more years of working with Linux.  I've been there with other operating systems.  Hopefully, I'll be there again with Linux.  In the meantime, remember please that newbies are exactly that.  We don't have anywhere near your knowledge base and don't like to, or can't, make leaps from common reference to exact terms.

Sorry, I'm a retired teacher and that is one of my soapboxes.  Other teachers have heard something similar.

I do want to thank all three of you for your efforts to help.  I do appreciate it.  I hope you can look back to when you started and appreciate why I ask so many questions.  Thank you.

---

### Post by vtel57 on 2007-05-16
He means are you using any third party (non-Ubuntu) drivers on your system, like Nvidia drivers, etc.

You can modify the menu.lst to look like this:

> title Ubuntu, kernel 2.6.20-15-generic
root (hd1,0)
kernel /boot/vmlinuz-2.6.20-15-generic root=UUID=c88401dc-c80a-4979-96ef-e98e75f27118
initrd /boot/initrd.img-2.6.20-15-generic
savedefault

... and then try to boot the kernel. However, if there is a kernel problem, changing those options won't boot it correctly. Give it a try, though. Can't hurt...

By the way, did you attempt to remove/reinstall those kernels like we were talking about earlier?

---

### Post by rhageman on 2007-05-16
Okay Gurus,

Here's where I'm at.

Removed the two two linux-images as per plan.  Note:  removal of 2.6.20.15-generic caused installer to remove several other packages (the restricted modules of the same number).  Rebooted into good kernal.

Reinstalled linux-image for 2.6.20-15-generic.  Note:  tried to tell installer to to reinstall linux-image for 2.6.17-11-generic and it balked.  Reported there was no package for it and that it was only in list to satisfy dependencies.

Rebooted.  Boot hung at the same place - Ubuntu black screen with progress bar.  Rebooted to good kernal.  Edited menu.lst to comment out "quiet" for 2.6.20-15-generic.

Rebooted.  Boot hung at the same place with no extra messages - just hung progress bar.  Rebooted to good kernal.  Came here to report results.

---

### Post by blazercist on 2007-05-16
you have to remove "splash" from the boot line as well.

---

### Post by rhageman on 2007-05-16
I'm back.

Okay, edited menu.lst again.  Removed "ro quiet splash".

Rebooted.  Process seemed to run longer, may just have been text output.  Anyway, it finally stopped with the following.

ALERT!  /dev/disk/by-uuid/c88401dc-e80a-4979-96ef-e98e75f27118 does not exist.  Dropping to a shell!

Then I was in somethingbox.  Rebooted to working kernel.  Came here to report results.

Just looked in /by-uuid, there are eight files, three have red "x' boxes.  One of those is the file mentioned in the alert.  Looking at the file properties, the two files with long hexdecimal names have Link Targets of /dev/hdf1 and /dev/hdf2.  It was the /dev/hdf1 that caused the alert.

Both hdf1 and hdf2 do reside in /dev.

---

### Post by vtel57 on 2007-05-16
Yeeeeeeeeesh! What a PITA this is for you! If this were my box, I'd remove the malfunctioning kernel again and just use the system with the stable kernel. Eventually, there will be another kernel upgrade come down the pike. When it does, hopefully, that kernel will cause you no problems. That's just my opinion on what you could do. There's no harm in continuing to use the stable kernel.

---

### Post by rhageman on 2007-05-16
Erik,

Thanks for the hand holding walk through.  I'll probably take your advice on the kernels.

Now, a PITA - is that Painful Initiation To Administration?

Take care.
Bob

---

### Post by vtel57 on 2007-05-16
Heh! PITA = pain in the rear end area. :)

---

### Post by rhageman on 2007-05-19
Erik,

Thought you might like to know...

I got frustrated with my 7.04 install.  Docs not specific for it, the kernel business, not getting microphone input to work, etc.

I decided to start over and see what a clean install brought.  Used the 6.10 DVD that I had started with.  That came up with the 2.6.17-10 kernel.  Right away there was an update/upgrade notice.  I decided on the update, which among 169 packages included the 2.6.17-11 kernel.  When the upgrade finished, I was able to boot into the 2.6.17-11 kernel.  A step forward with the kernel business anyway.  I'm going to hold off on the upgrade to 7.04 until I'm happy with the progress I'm making on 6.10 - and - until I see more 7.04 specific docs show up.

Take care.
Bob

---

### Post by vtel57 on 2007-05-19
Hey, Bob... long time, no post. I was beginning to wonder what your progress was.

Sometimes a reinstall or a retrograde version install does the trick. I'm still using Ubuntu 6.06.1 on my system. It works. It does everything I need it to do. It's ROCK SOLID stable. What more can you ask? Sometimes, especially with Linux, it's not necessary to be on the bleeding edge. 6.10 was a very good version, too, from what I've read and what friends told me about it. If it works well for you, stick with it.

Glad you're making progress, anyway! :)

Later...

~Eric

---

### Post by rhageman on 2007-05-22
Eric,

I'm learning.  I had a problem with the HDAudio handling of the sound portion of my mother board.  I found the directions for installing new alsa drivers in the kernel.  I've recompiled the kernel and I have wonderful sound.

So, I'm making progress 8^)

Take care.
Bob

---

### Post by vtel57 on 2007-05-22
Man! Look at you go! :)

Believe it or not, just about everything you'll ever want to know about GNU/Linux can be found on the Internet. When I first started to learn it, I actually spent some money (about $200) on books. Some were very useful, others not. However, as time went by, I've found that most, if not all, of the info in those books is available at helpful websites and forums all over.

I made a custom Everything Linux home page that I serve on my own machine. It has loads of GNU/Linux links to goodies. A friend of mine from another Linux forum is serving it on his own server for everyone's use. You can find it [HERE](http://webpages.charter.net/tommyj12/Everything_Linux.html). Pay special attention to the Tutorials and Documents areas.

You'll be a GNU/Linux guru before you know it. :)

---

### Post by rhageman on 2007-05-24
Hey Eric,

I figure you know the answer to this one.  I asked my second question (started a thread) about two commands
that 6.10 reports as missing when I try to follow directions for the tapioca-voip project.  I probably goofed in
describing the subject so i've gotten no responses.

In [http://ubuntuforums.org/showthread.php?t=452041](http://ubuntuforums.org/showthread.php?t=452041), I'm trying to find out which files I need to install to get
the "svn" and "darcs" commands installed.  Could you take a look and see if you know which Synaptic pachages
I should use?

Thanks.
Bob

---

