---
title: "Windows xp &quot;wipes&quot; the Ubuntu boot"
date: 2007-09-03
forum: Absolute Beginner Talk
---

### Post by johntkucz on 2007-09-03
Okay, some very peculiar behavior when installing windows xp on the internal hd.  I have ubuntu in three partitions on an external hd, but after installing windows xp on the internal hd (detructive install), and I try to boot from that external HD from bios, it says Operating system not found.  It does not boot into grub now, either.  Any suggestions?

Here's the fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=3a79ad82-eb61-4d85-a3b3-08b8e5396b4a /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=eeb84bb0-7e4e-463a-8ad3-916bf67774c1 /home           ext3    defaults        0       2
# /dev/hda1
UUID=9858328CE07FB76E /media/intfs80_hda1   ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda3
UUID=087fa5ff-dd64-478e-9343-257b9765c2f8 none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto     0       0

---

### Post by nbeerbower on 2007-09-03
You could try reinstalling Grub with the Ubuntu Live CD.

---

### Post by johntkucz on 2007-09-03
yeah, hey nbeer, 

I've had a LOT of people suggest that, but I don't know how to do that.  The Live CD just has options such a memory test, install, a driver update or something, I don't see any option to reinstall the grub boot-loader.  Thanks.

---

### Post by philinux on 2007-09-03
Once the Live cd is up and running you need to 

Applications >Accessories >Terminal

Now read this thread

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by johntkucz on 2007-09-03
> **philinux said:**
> Once the Live cd is up and running you need to 

Applications >Accessories >Terminal

Now read this thread

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

philinux,

OHhhh! I always thought reinstall grub from the liveCD Was like one of those boot options.  I'm in xp right now, but will give that thread-tutorial a go.  Thanks a ton!

---

### Post by philinux on 2007-09-03
Thats the beauty of the live cd even if everything goes tits up you can rescue things and even have the internet available.

Its one reason I got the Live cd as a Windoze rescue system :lolflag:.

But ended up liking linux I went dual boot and now dont use windoze,

---

### Post by johntkucz on 2007-09-03
yeah, linux-ubuntu rocks....if only everything went smoother, though.

Problems with that tutorial.

find /boot/grub/stage1

returns Error 15:File not found

the actual stage1 file is /media/disk-1/boot/grub/stage1 but when I punch that in, it still returns Error 15:file not found.  


Also, when it says to 
do
```
setup hd0
``` shoudn't I put in something different, I want grub, installed on the external hd (if possible) not the internal.


From my fstab file is the information I'm looking for sda2??
```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=3a79ad82-eb61-4d85-a3b3-08b8e5396b4a /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=eeb84bb0-7e4e-463a-8ad3-916bf67774c1 /home           ext3    defaults        0       2
# /dev/hda1
/dev/hda1 /media/i80  ntfs    nls=utf8,umask=0222 0       0
# /dev/sda3
```

---

### Post by johntkucz on 2007-09-03
any ideas of what to do?

---

### Post by Duck2006 on 2007-09-03
With your usb drive pluged in. Boot the live CD, and from the Terminal type

sudo grub

At the grub promp type

find /boot/grub/stage1

it will come back with some thing like (hd1,0)
type that in after root

root (hd1,0)

setup (hd0)

quit

then reboot and hope that fixes it for you.

---

### Post by johntkucz on 2007-09-03
> **Duck2006 said:**
> With your usb drive pluged in. Boot the live CD, and from the Terminal type

sudo grub

At the grub promp type

find /boot/grub/stage1

it will come back with some thing like (hd1,0)
type that in after root

root (hd1,0)

setup (hd0)

quit

then reboot and hope that fixes it for you.

Hey duck,
thanks for responding.  However, apparently you didn't read my recent posts.  I tried just that and get the Error 15 thing.  Yes, the drive is plugged in and I can even browse to the stage1 file in nautilus windows.

---

### Post by johntkucz on 2007-09-03
at the grub prompt,

find /boot/grub/stage1

and

find /media/disk-1/boot/grub/stage1 

both return error 15.

---

### Post by nowshining on 2007-09-03
how long have you installed windows - if you just installed it or re-installed your best bet would be to re-install - install windows first then ubuntu because yes one of the other will wipe one out...so again install windows again but first this time install xp then ubuntu - i did find a google writeup on this before as I was searching the net.. i'll post the link if i can find it again..

---

### Post by nowshining on 2007-09-03
edited the startup commands

---

### Post by johntkucz on 2007-09-03
> **nowshining said:**
> how long have you installed windows - if you just installed it or re-installed your best bet would be to re-install - install windows first then ubuntu because yes one of the other will wipe one out...so again install windows again but first this time install xp then ubuntu - i did find a google writeup on this before as I was searching the net.. i'll post the link if i can find it again..

hhmmm...I just reinstalled windows xp about 24 hours ago.  not interested in spending eons doing multiple reinstalls.  I could just reinstall ubuntu onto the external, but I'd prefer to not do that (if all I need to do is, after all, fix the grub).

---

### Post by nowshining on 2007-09-03
hmmm i'll have to read on it some more..please hold for a fix..
 
if you want maybe this might give some reason why your having the problem..
 
[http://bbs.archlinux.org/viewtopic.php?pid=239211](http://bbs.archlinux.org/viewtopic.php?pid=239211)

---

### Post by johntkucz on 2007-09-03
this section worked PERFECTLY....a reboot will only tell if total success, though!

```
Mine was a slightly different story. I couldn't get grub to find the stage1 file or even recognize my drive. So I borrowed some knowledge I picked up while using Gentoo:

You have to mount your root partition using the livecd:
Code:

$
Code:

sudo mkdir /mnt/root

$
Code:

sudo mount -t ext3 /dev/sda6 /mnt/root

Then you have to mount the proc subsystem and udev inside /mnt/root also:
Code:

$
Code:

sudo mount -t proc none /mnt/root/proc

$
Code:

sudo mount -o bind /dev /mnt/root/dev

Doing this allows grub to discover your drives. Next you have to chroot:
Code:

$
Code:

sudo chroot /mnt/root /bin/bash

Now that you're chrooted into your drive as root everything should work.
Code:

#
Code:
```

---

### Post by nowshining on 2007-09-03
awesome :)

---

### Post by johntkucz on 2007-09-03
okay, I got through to the setup (hd0) 
line, and rebooted.  No go.  Error 21.  Now grub is on the internal!! That's not what I wanted!  I need to boot from the external?  What should I do now?  Anyway to install it on that external hd?

find /boot/grub/stage1 returned

hd2,1 for me.

---

### Post by johntkucz on 2007-09-03
now it returns hd1,1

I just did 

setup (hd1) instead of hd0.  will that improve the situation?

How do I uninstall grub from the internal hd? (hd0)?

---

### Post by johntkucz on 2007-09-03
what happens if I delete the "boot.ini" file from the internal xp hd (will that uninstall grub)?

---

### Post by splintercellguy on 2007-09-03
No, and you shouldn't. Try the Super GRUB CD?

---

### Post by johntkucz on 2007-09-03
okay, I got through to the setup (hd0)
line, and rebooted. No go. Error 21. Now grub is on the internal!! That's not what I wanted! I need to boot from the external? What should I do now? Anyway to install it on that external hd?

find /boot/grub/stage1 returned

hd2,1 for me.
__

After reboot,
now it returns hd1,1

I just did

setup (hd1) instead of hd0. will that improve the situation?

How do I uninstall grub from the internal hd? (hd0)?

---

### Post by johntkucz on 2007-09-03
> **splintercellguy said:**
> No, and you shouldn't. Try the Super GRUB CD?

What's that?? Argg...this smells snafued.  I'm trying to avoid a complete xp install then a complete ubuntu install, but I might have to do that!

---

### Post by johntkucz on 2007-09-04
okay, I could have just started an entirely new thread, for this, but it DOES have a strong relation to the original problem of "reinstalling grub on external hd"...

**_NEW PROBLEM:_**

 My recurring problem has been whenever successfully do a dual install (windows xp on the internal) and ubuntu on the internal, (installing xp first, then windows 2nd) grub gets installed on the external so I can't boot into anything (xp nor ubuntu) without lugging around that external hd).

If I change the install sequence to ubuntu on the external first and then install xp, I get back to where I operate, now: xp boots, but the external hd won't boot.

Conclusively, how do I install xp on the internal and ubuntu on the external hd WITH the capacity to boot to xp without the external hd????

---

### Post by johntkucz on 2007-09-04
kay, I could have just started an entirely new thread, for this, but it DOES have a strong relation to the original problem of "reinstalling grub on external hd"...

NEW PROBLEM:

My recurring problem has been whenever successfully do a dual install (windows xp on the internal) and ubuntu on the internal, (installing xp first, then windows 2nd) grub gets installed on the external so I can't boot into anything (xp nor ubuntu) without lugging around that external hd).

If I change the install sequence to ubuntu on the external first and then install xp, I get back to where I operate, now: xp boots, but the external hd won't boot.

Conclusively, how do I install xp on the internal and ubuntu on the external hd WITH the capacity to boot to xp without the external hd????

---

### Post by johntkucz on 2007-09-04
kay, I could have just started an entirely new thread, for this, but it DOES have a strong relation to the original problem of "reinstalling grub on external hd"...

NEW PROBLEM:

My recurring problem has been whenever successfully do a dual install (windows xp on the internal) and ubuntu on the internal, (installing xp first, then windows 2nd) grub gets installed on the external so I can't boot into anything (xp nor ubuntu) without lugging around that external hd).

If I change the install sequence to ubuntu on the external first and then install xp, I get back to where I operate, now: xp boots, but the external hd won't boot.

Conclusively, how do I install xp on the internal and ubuntu on the external hd WITH the capacity to boot to xp without the external hd????

---

### Post by nowshining on 2007-09-04
okay let me get this straight

XP on main drive
Ubuntu on external drive

and xp now works fine from the main drive, however you want to boot ubuntu on the external drive at times as well right??

Just want to make sure..

---

### Post by johntkucz on 2007-09-04
well, technically, now that i did all that setup (hd0) grub stuff, neither boots work.  

I would like to be able to boot from either drive at times; ideally, when booting on he xp internal, without the need of the external hd.  That should be possible, but haven't been able to do that recently.

---

### Post by Gone fishing on 2007-09-04
My PC boots from two hard drives (I run Ubuntu, BeOS and XP) 

I do the grub command from the live CD and place grub on the linux partition rather than the MBR and use a boot loader called GAG [http://gag.sourceforge.net/](http://gag.sourceforge.net/).

---

### Post by igknighted on 2007-09-04
With your windows disk you can easily restore the windows bootloader on the internal.  Simply boot the windows CD, go to the recovery console and type "fixmbr".  Windows bootloader should be back to normal on the internal.

Using (hd1) instead of (hd0) above might do the trick.  Grub is always a little touchy as it has its own method of naming drives that is a little ambiguous, but if you take the time to learn it now, grub is actually fairly easy to figure out.  Another way to simplify this might be to unplug the internal HD and then install grub.  This way you know it is on the proper disk.

It sounds as if you are quite a bit frustrated.  This only leads to mistakes and rash judgment.  I strongly recommend relaxing and waiting for more replies to roll in.

---

### Post by johntkucz on 2007-09-04
> **igknighted said:**
> With your windows disk you can easily restore the windows bootloader on the internal.  Simply boot the windows CD, go to the recovery console and type "fixmbr".  Windows bootloader should be back to normal on the internal.

Using (hd1) instead of (hd0) above might do the trick.  Grub is always a little touchy as it has its own method of naming drives that is a little ambiguous, but if you take the time to learn it now, grub is actually fairly easy to figure out.  Another way to simplify this might be to unplug the internal HD and then install grub.  This way you know it is on the proper disk.

It sounds as if you are quite a bit frustrated.  This only leads to mistakes and rash judgment.  I strongly recommend relaxing and waiting for more replies to roll in.

hey igknighted (nice name, btw),

Unfortunately, I've got a screwy gateway xp boot disk, if I boot from it, it allows (always) no options other than a destructive clean restore (it, strangely takes about 15 minutes to load to the install screen, too).  Something very wrong with that disk.  I don't know how to, therefore, even get to the bootloader of the windows disk.

I reinstall ubuntu on the external and here's my startup sequence.
BIOS loads and Must select the internal HD, then grub loads (even though xp is on the internal), with the menu.lst screen and I can select external (ubuntu) or internal (xp).  The problem is that I can never get to that menu.lst screen of the boot sequence without the external hd (suggestion that its installed on the external?), while cumbersome this is "okay" except for travel, when I can't lug around the external hd.

---

### Post by johntkucz on 2007-09-04
> **nowshining said:**
> hmmm i'll have to read on it some more..please hold for a fix..
 
if you want maybe this might give some reason why your having the problem..
 
[http://bbs.archlinux.org/viewtopic.php?pid=239211](http://bbs.archlinux.org/viewtopic.php?pid=239211)

hey nowshining,

I checked out that link, and either have tried a lot of stuff on it or don;t know how to tweak some other stuff.

Right now, I can get xp to boot without an external hard drive, but then my only access to ubuntu is the livecd.  I do finances with gnuCash so I have to boot off liveCD and then install gnucash everytime I do finances!

I can't just install pure ubuntu on the internal because the wireless nor sound drivers work.

If I do the best compromise, a dual-boot (windows on internal), ubuntu on external, you end up always needing the external hd to get past grub, which is cumbersome, but impossible when I'm on the go and just need the laptop's mobillity!

You'd have to have some seriously warped psychological disroder to NOT find that frustrating!!

---

