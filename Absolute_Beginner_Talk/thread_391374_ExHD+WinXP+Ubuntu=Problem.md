---
title: "ExHD+WinXP+Ubuntu=Problem"
date: 2007-03-23
forum: Absolute Beginner Talk
---

### Post by whiskeysquared on 2007-03-23
So I wanted a dual boot system.  I had windows xp (had, operative term) home edition; went out and bought a new external hard drive (western digital 250 gig my book); and burned an ISO of 6.10 .

I'd call myself a "recreational user" of Ubuntu and I wanted to immerse myself in it, but wanted to keep windows around because I have some apps that are windows only.

What happened next, I think, bricked my system.  Here's the play-by-play:

Backed up everything (reason I got the external drive)
Restarted windows with Ubuntu CD, and selected the install
Per a tutorial, I went with the recommendations by the installer as far as partitions
Linux went off to do its thing, and then Viola
Booted into Ubuntu and for the next 10 hours did nothing but explore

After the 10 hours, I realized I hadn't tried booting into windows yet and so I went.  Restarted, arrowed down, and selected the first entry in grub for windows.  It said "Windows XP Home Edition" then I hit enter.  Then...nothing.  Blackness.  I waited.  Nothing.

I thought that maybe I had selected the wrong entry because there were TWO under "other operating systems" in grub.  So I turned on the machine, that was completely unresponsive, and got to the menu again.  This time I chose the (trying to recall, don't remember exactly) "Win NT, 2000, XP" entry.  Same thing happened.  Nothing.

Then I wondered if it was a problem with the boot order in bios.  I was beginning to grasp at answers at that point.  So I made sure it first boots from disk, then CD...  Tried again, nothing.  Getting a little worried, I tried booting into Ubuntu again, and it was fine.  I found myself staring at my USB hub wondering what could be the problem.

Then I slowly traced the wire up to the external drive.  The green circular light on the my book was blinking away; taunting me.  Doom fell upon me.  I then recounted my adventures 10 hours prior.  You see, as soon as I backed up my files, I restarted windows and I didn't necessarily turn OFF my external drive or disconnect it.  I then realized I had installed Ubuntu with that drive attached.  Not completely SURE this was the problem, I turned it off, and for giggles tried to boot into windows.  Nothing.  Then I tried booting into Ubuntu...  Oh no.

I thought it was fine.  I made it to the login screen of Ubuntu, and typed my username and password, but then it froze and gave up all signs of life on at a blank, Ubuntu dirty sand orange screen.

To test my theory, I turned off the machine, plugged in the external drive and turned it on.  Ubuntu booted fine.

So, the purpose for all of this is perhaps a cautionary tale and a plea for assistance I suppose.

I'm on Ubuntu right now, making this post and it works fine, but if there is any hope of fixing something so I can get into windows and ubuntu and fix the whole external drive must be connected problem, I would be a very happy person.  Obviously, in the end, I don't want to always have to boot with my external drive attached, but I'd like to not make 10 hours of tweaking go to waste and I would like to not reinstall windows.  

And don't worry, as you more experienced Linux users shake your heads in disgust, I too am disgusted with myself.  I've never felt like more of a noob.  Aside from the time I attempted to try out for the basketball team.  But yes, this is embarrassing.

---

### Post by mdsmedia on 2007-03-23
I wouldn't panic at this stage. I can't tell you how to fix it, but I think, MAYBE, you installed Ubuntu on the external drive and it's not yet recognizing your Windows drive. That MAY be all there is to it, and a simple reconfiguration of the GRUB menu might get Windows booting fine.

Don't panic, but that's just my feeling at the moment.

If it's not that simple, your Windows partition/drive will probably be accessible anyway....from Ubuntu....unless you have told Ubuntu to format it on installation. I'd guess your Windows is OK, just not accessible at the moment.

---

### Post by whiskeysquared on 2007-03-23
Here I was getting all, "the end is nigh".  You're a glass is half full kind of person, I can tell.

I thought that maybe, even though the external drive isn't heavily active all the time, that some small (yet obviously important) bit of data was on it; but I took a look around and didn't find anything that I could recognize as being integral to operations.  The only folder/directory that I don't remember being on there after I bought it, and after I placed files on it is a folder named, "System Volume Information".

Sketchy memory and a google search tells me this is some sort of windows restore file.  Now, I'm not sure of the significance of that.  And I'm not sure that it's even relevant, but it's there.

Other than that mildly concerning folder, I don't see anything else on the drive that I didn't put there.  And the capacity remaining on the drive is about were it should be after the amount I put on there.

But from what I've told you, there is something dependent upon the external drive right?

I appreciate your quick response.  And please, if you have any good ideas, share.

---

### Post by poohbear1616 on 2007-03-23
Yes, I figure xp is still there but grub is not picking it up.

Since you can boot Ubuntu (thats a plus) we need this pasted from terminal:

```
less /boot/grub/menu.lst
```

```
fdisk -l
```

---

### Post by whiskeysquared on 2007-03-23
Okay, here it goes, hope I did it right for you:

```

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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         10

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
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
:
title           Ubuntu, kernel 2.6.17-11-generic
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.17-11-generic root=/dev/hda3 ro quiet splash
initrd          /boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot

title           Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.17-11-generic root=/dev/hda3 ro single
initrd          /boot/initrd.img-2.6.17-11-generic
boot

title           Ubuntu, kernel 2.6.17-10-generic
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/hda3 ro quiet splash
initrd          /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title           Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/hda3 ro single
initrd          /boot/initrd.img-2.6.17-10-generic
boot

title           Ubuntu, memtest86+
root            (hd0,2)
kernel          /boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title           Microsoft Windows XP Home Edition
root            (hd0,0)
savedefault
makeactive
chainloader     +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda2
title           Windows NT/2000/XP
root            (hd0,1)
savedefault
makeactive
chainloader     +1



```

And then the fdisk command:

```

 fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       30401   244196001    c  W95 FAT32 (LBA)

```

That's bad huh?  I'm assuming (bad idea for me) that the last command is showing me the drive that's important to the boot process...  And unfortunately that looks like the external drive (it's 250 GB, the hard disk on my computer is a measly 100 or so).

Thanks again for the help, hope I got all the info from the console that you needed, if I didn't let me know.

THANK YOU!

---

### Post by poohbear1616 on 2007-03-24
FAT32 is a windows format.
That means this:
Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       30401   244196001    c  W95 FAT32 (LBA)

is your backup.

At the bottom of your grub it looks like there is 2 windows partitions.???

When you get time boot from live disk and redo:

```
fdisk -l
```

I am cornfused.

Ubuntu is booting from your internal drive!

---

### Post by poohbear1616 on 2007-03-24
Without live disk it is:

```
sudo fdisk -l
```

Sorry
I've been using mepis for a while so that skipped my mind.

---

### Post by whiskeysquared on 2007-03-25
So what you're saying is that I need to do the same thing as last time, by opening a terminal in my current Ubuntu install (not the live disk) and type:

```
sudo fdisk -l
```

And that will give me different data because it has the "sudo" before it?  (Note:  I really need to learn what all this sudo and fdisk stuff means.)

About the two windows partitions...  I know, with a degree of certainty that my machine had a small windows partition before that stored the windows recovery data.  Perhaps that's what that is?  Still, I'm not sure what the breakdown is.

I'm at work right now away from my machine, but as soon as I have access I will post my results.

Once again, I appreciate your efforts, and applaud your patience.

---

### Post by lamalex on 2007-03-25
yes sudo fdisk -l will give different output. sudo means do as root. su = switch user do is the verb, do. switch to root and do the following command. you have two windows partitions because of your manufacturers small recovery partition. past sudo fdisk -l here and we can keep helping

---

### Post by confused57 on 2007-03-25
You might want to burn a copy of the Super Grub Disk(approx 500 kb download):
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
it is capable of booting Windows(this will possibly let you know Windows is still "bootable") or Linux, and can restore your Windows IPL code to the mbr of your internal hd or can reinstall grub.

Your easiest solution may be to reinstall Ubuntu with your external hard drive disconnected, but you might want to explore all other possibilities first.

You're getting some good advice from Iamalex & poohbear1616 about needing the results of "sudo fdisk -l"...you can do this from the live cd, also...may be interesting to run it from the live cd, with & without your external hard drive connected.

you may want to post the output of(from your installed Ubuntu):
```
cat /etc/fstab
cat /boot/grub/device.map
```

Added:  You might need to comment(put a # in front of) your external hd /etc/fstab mountpoint, as well as, your "(hd1) /dev/sda" in your device.map; before your internal drive will boot independently of your external drive...I'm not sure.

---

### Post by david_kt on 2007-03-25
[QUOTE=whiskeysquared;2343266]

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda2
title           Windows NT/2000/XP
root            (hd0,1)
savedefault
makeactive
chainloader     +1


[/CODE]

Could you try to edit your grub above to:


[INDENT]title           Windows NT/2000/XP
unhide          (hd0,1)
root            (hd0,1)
savedefault
makeactive
chainloader     +1[/INDENT]

And then boot again choosing windows NT/2000/XP on startup?

DK

---

### Post by whiskeysquared on 2007-03-25
Here's the output from "sudo fdisk -l"

```

Password:

Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1             487        9192    69930945    7  HPFS/NTFS
/dev/hda2   *           1         486     3903763+   b  W95 FAT32
/dev/hda3            9193       14429    42066202+  83  Linux
/dev/hda4           14430       14593     1317330    5  Extended
/dev/hda5           14430       14593     1317298+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       30401   244196001    c  W95 FAT32 (LBA)

```

---

### Post by poohbear1616 on 2007-03-25
Grub is getting confused by the two windows partitions.
So lets do this.

```
sudo gedit /boot/grub/menu.lst
```

Change this:
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title           Microsoft Windows XP Home Edition
root            (hd0,0)
savedefault
makeactive
chainloader     +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda2
title           Windows NT/2000/XP
root            (hd0,1)
savedefault
makeactive
chainloader     +1

to this:

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title           Microsoft Windows XP Home Edition
unhide (hd0,0)
hide (hd0,1)
rootnoverify (hd0,0)
chainloader +1
makeactive
boot


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda2
#title           Windows NT/2000/XP
#root            (hd0,1)
#savedefault
#makeactive
#chainloader     +1

This should work!

---

### Post by pxwpxw on 2007-03-25
**david_kt**

The original menu.lst and the <sudo fdisk -l> both look OK to me,
The dual windows system was installed to boot XP via the NT partition
hence the title Windows NT/2000/XP and the * in the W95 line

  Device Boot      Start         End      Blocks   Id  System
/dev/hda1             487        9192    69930945    7  HPFS/NTFS
/dev/hda2   *           1         486     3903763+   b  W95 FAT32
/dev/hda3            9193       14429    42066202+  83  Linux
/dev/hda4           14430       14593     1317330    5  Extended
/dev/hda5           14430       14593     1317298+  82  Linux swap / Solaris

If **whiskeysquared** had selected the  Windows NT/2000/XP option
it would have worked with the original configuration I suspect.

**whiskeysquared**

Suggest don't change anything until you have tried selecting the

   Windows NT/2000/XP

which should then allow you to select XP from NT.

---

### Post by whiskeysquared on 2007-03-25
Hey everyone.  Thanks for all the help, unfortunately it doesn't seem to be working.

@poohbear1616
I made the edits you suggested, and I went to restart.  The GRUB menu was only showing the Windows XP Home Edition option this time instead of two windows options as before, but when I selected it, it flashed the "loading" message at the top left of my screen and then went black just like it had done before.

@pxwpxw
Thanks for your post, but I had tried that prior to posting, it did the same thing I mention above.

---

### Post by jerryrw on 2007-03-25
I've had similar probs in the past.  This setup looks alot like a Compaq, Emachine, or Dell default XP setup.  They often use a non standard boot procedure.  There is some code that is in the boot sector that doesn't load NTLD directly.  This can confuse GRUB.  As a guess your Ubuntu got installed on sda1 and your grub stage1.5 or 2 files are on the external drive.  Also that non standard boot loader that some companies "helpfully" install checks th boot sector of hda1 for corruption.  On the Emachine that I have the only way around it was to install a "real" copy of XP.

If you just want to get your XP back and reinstall Linux later you can try to boot off your XP or recovery disks and try a recovery console with a fixboot and fix mbr.

---

### Post by whiskeysquared on 2007-03-26
@confused57
Here's the output that you suggested:

```

~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3
UUID=2fc5fe77-e588-4775-b32d-1b2f8156d1cb /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=d5ba5683-35fe-484e-8699-95d78d945f6c none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

```
```

~$ cat /boot/grub/device.map
(hd0)   /dev/hda
(hd1)   /dev/sda

```

@jerryrw
It **is** a junky emachines box, good call...  And I'm not sure what you mean by *a real* copy of XP.  Are you saying a new install disk?  But regardless, in your opinion, my current install of XP is lost?

---

### Post by pxwpxw on 2007-03-26
@whiskeysquared

I should have read your post more carefully.

But if you don't actually have 2 windows systems, then I'm still
very doubtful about that asterisk * marking the W95 hda2 as  bootable, 
instead of the XP partition. This may have been changed by
the ubuntu installer. I am assuming your XP boot is on hda1, as in the grub menu.

You can toggle the bootable flag from ubuntu 
using either fdisk or parted, just toggle the hda2 flag off
and toggle the hda1 flag on.

---

### Post by poohbear1616 on 2007-03-26
> But regardless, in your opinion, my current install of XP is lost?

It is still there, just not booting.

I would do what pxwpxw suggests first, then if that will not fly we still can unhook the ext. drive and boot the live disk and try re-installing grub on the internal as per:
[http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD]("http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD")

Or it might be just as easy to re-install ubuntu. Then the ext. can be accessed later.
I have never used an ext. drive but from what I have seen some people have smooth sailing with them when installing and others it totally boogers things up.

> ~$ cat /boot/grub/device.map
(hd0)   /dev/hda
(hd1)   /dev/sda

Your ext is just a back up, right??
Then (hd1)   /dev/sda should not be.

---

### Post by whiskeysquared on 2007-03-26
Okay everyone.  Quick question.  Would simply reinstalling Ubuntu solve anything?  If so, what special procedures would need to take place in order to get the boot sequence to go off without a hitch?

I'm not entirely thrilled with Ubuntu, just for the fact that it takes an aweful lot of tweaking to get it to a system I can reliably use to get my work done.  For example...Firefox is pretty useless under Ubuntu, and the fonts are a wreck.  I know there are tweaks to make to get them working, but I don't have the time to do that right now as I need to get some work done and I was able to do my work quite efficiently under XP.  I'm not ranting, but it's not a system that you can install and use right away, it has it's caveats.

I'd like to, later and if the boot problem won't happen again (next time I'll install without the external drive plugged in) experiment with Kubuntu.  But as it stands now, my XP won't boot (the issue i'm here for), my fonts look horrible, flash is sketchy at best, firefox is useless, my printer has been rendered useless, load times are longer than XP, and I've had more screen freezes than I've ever had (specifically firefox).  So the main issue I was going to live with was Macromedia Fireworks (my graphic editor of choice) isn't available for linux, in reality has turned into a host of problems that I can't afford to live with.  So in my case, XP has turned out to be stable (never thought I would say that) compared to Ubuntu.  I want to love Ubuntu, but I don't have time to get it to a usable platform, it's definitely not a quick process (I naively thought it would be) and so I need to get back to my install of XP; so if I install Ubuntu over again, without the external drive, will that solve my boot problems?  If there are special steps during the install process I should follow in this case, what are they?

I appreciate your help, and I don't want this to be mistaken for a rant at all.  I'm just a little frustrated because I was excited about Ubuntu and I don't think I got a fair shake at it.  You guys and the community are great, and Ubuntu I'm sure is great, but it just takes time to get it to where you want it, in the meantime my work is piling up and I hate using my laptop to do it.

---

### Post by confused57 on 2007-03-26
Before you try reinstalling (K)ubuntu, you might want to burn a copy of the Super Grub Disk:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

maybe I missed in an earlier reply, but if you haven't already tried SGD, see if it will boot XP...it's also capable of reinstalling Window's IPL code to the mbr.

You can also use a Win98SE oem boot floppy to restore your mbr:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

Hopefully, you can get a dual boot working or at least get your Window's booting.

---

### Post by whiskeysquared on 2007-03-27
Should I try running super grub disk with or without the external drive connected?

EDIT:  This is irrelevant now...  See post below.

---

### Post by whiskeysquared on 2007-03-27
Okay.  confused57 you rock.  I unplugged the eternal drive and ran super GRUB disk you recommended.  It looks pretty powerful, but I just selected "boot windows" from the menu instead of fooling with the advanced options, and to my surprise I got XP started up.  Now in the spirit of giving an inch and taking a mile, how do I permanently repair the problem.  It looks like this SGD may be the key, but I'm not sure.  There are a lot of options, and seeing since stumbling my own way has gotten me into trouble so far, what is your recommendation?

THANKS again to everyone.

---

### Post by eentonig on 2007-03-27
Quick stupid question.

When you got to the partitioning stage of the install. Did you move the XP partition to the end of your HD? Or to the beginning?

I think Windows always wants to be on the first partition of a HD, if I recall well.

---

### Post by confused57 on 2007-03-27
> **whiskeysquared said:**
> Okay.  confused57 you rock.  I unplugged the eternal drive and ran super GRUB disk you recommended.  It looks pretty powerful, but I just selected "boot windows" from the menu instead of fooling with the advanced options, and to my surprise I got XP started up.  Now in the spirit of giving an inch and taking a mile, how do I permanently repair the problem.  It looks like this SGD may be the key, but I'm not sure.  There are a lot of options, and seeing since stumbling my own way has gotten me into trouble so far, what is your recommendation?

THANKS again to everyone.

Good timing, I just logged on one last time before bedtime.  You may want to use the SGD to restore your mbr, so that you can boot Windows, using Window's IPL code...SGD has saved a lot of people and Herman's tutorial is relatively easy to follow, especially with the included screenshots.  At least you'll have Window's booting, until you decide for sure what you want to do...maybe install Ubuntu to the external drive, without installing grub to your internal hard drive mbr...this could be done(or you  "should" be able to), if you're able to select your USB controller in bios for the external hard drive to boot before the internal hd prior to booting up with the installation cd.

As an alternative, you could reinstall Ubuntu to your internal hard drive with the external drive disconnected & see if this corrects the problems you had before.  You'll have the SGD to restore Window's hard drive mbr, if it doesn't work...great to hear that SGD saved the day.

The first link in my signature is Herman's site & there is an excellent section explaining grub or another section for GAG boot loader.

---

### Post by whiskeysquared on 2007-03-27
> **eentonig said:**
> Quick stupid question.

When you got to the partitioning stage of the install. Did you move the XP partition to the end of your HD? Or to the beginning?

I think Windows always wants to be on the first partition of a HD, if I recall well.

I laughed a little at this question, just because I have no idea how the installer partitioned it.  I let it do it's automatic thing and off it went.  In all honesty, I've not had a lot of "partitioning" experience though I do understand the fundamental basics of it, the exact elements escape me.  But this is something I plan on studying up on, especially now.

@confused57,  I think I'll try installing Ubuntu over again.  As I mentioned before, I experienced a lot of problems with configuring it to...work and look nice.  And I'm now learning that there are two camps to Ubuntu, and Linux in the interface realm..  gnome and KDE so I think I'll give kubuntu a look.  I didn't do anything but make a mess with that install anyway.

Thanks again.  I'll post the results of my adventures when I get some work done and have the opportunity (and the guts) to give that another go.

---

### Post by pxwpxw on 2007-03-27
**whiskeysquared**

There is an alternative to using grub for selecting between XP and Linux, that could work well in this case. That is to use the XP/NT loader to make selection. Search for "NT Bootloader" will find many threads about this.

Having read this thread once again, the W95 FAT32 boot partition is probably grubs downfall, but that small partition is just a separate boot partition for XP. It may be a standard XP configuration (I did one like that at one time), or a 3rd party loader that offers the same possibility as follows.

You should be able to see what is in the W95 boot partition, from windows XP. If there is a "boot.ini" file you have the option to use windows MBR and a boot.ini menu to select XP or Ubuntu (rather than using a gub MBR and menu).

It is done something like this:
(needs details from previous threads)

Reinstall ubuntu as before on the internal drive, with XP, but with the external drive disconnected (or swiched off), grub first stege gets installed to hda MBR as before (temporarily). 

Restart ubuntu and make a copy of the grub MBR to a file on the W95 FAT32 partition.

Then restore the windows MBR (fixmbr ) and edit the boot.ini file to add 
a line, for the grub MBR copy, to the NT boot menu (which appears when you add a 2nd choice). Then you boot to the NT menu, and select XP or Linux.

---

### Post by whiskeysquared on 2007-05-06
Hello all.  Well, I've been using SGD to boot my windows install for a while now, just avoiding the whole try to fix it thing.  But I tried.  I followed the instructions from SDG to a "t", and went through the Fix Windows bit, but nothing.  And now I'm getting 

```

Booting 'Boot Windows'

rootnoverify (hd0,0)
chainloader +1
boot

NTLDR is missing
Press and key to restart

```

So, now SGD won't even boot windows.  I downloaded the ntldr disk and tried all 10 options there to no avail.  Seriously, how can I wipe my system clean of Linux, Grub etc and the extra partitions that were created and go back to having plain old windows?  I'll just continue my experimentation on an old machine I have as I can't see this being very user friendly and it's been a real productivity killer.

I have total faith in your advice as SGD was an awesome tool that at least let me get into Windows so I could work, so I hope you can tell me how to make it all better again.

Thanks!

---

### Post by Herman on 2007-05-07
```
rootnoverify (hd0,0)
[COLOR=Red] makeactive[/COLOR]
chainloader +1
boot
```Hello whiskeysquared,
Make sure the Windows partition is set active (with the makeactive command), and it should boot.
You can also set the boot flag with almost any disk partitioner too.

Have you tried  installing Grub to MBR in your first hard disk?

What exactly are those two Windows partitions anyway? It is unusual that the one in first place in the hard disk is called number 2 in fdisk and your number1 partition is after it. 
maybe that's normal for your brand of computer though. This seems like a very unusual setup. Is the number1 partition a 'boot' partition fro Windows XP in number1 or something odd like that? I noticed your boot flag was toggled to the number2 partition in your fdisk output earlier,

It can happen sometimes that the partition number get changed around by a partitioner accidentally and that can out boot.ini out and give you that 'ntldr is missing' error. Normally that ntlrd disk will boot Windows for you in spite of that.

I'm sorry to read you had so much trouble, I agree you should try again on a different computer. Ubuntu is normally much easier than this, you just got off to a bad start because of bad luck I guess. I can tell you have a very good additude about it all. You would make an excellent Ubuntu user if you try again.

Anyway, to uninstall, all you should have to do normally is pick one of the six methods on this page, [Un-install Page]("http://www.users.bigpond.net.au/hermanzone/p18.htm"), and you should be fine.

Regards, Herman  :)

---

### Post by whiskeysquared on 2007-05-07
Herman, those sound like excellent recommendations...how do I do them?  :-)

How do I need to carry out the makeactive command - and how do I sort out the installation (or reinstallation, because I thought Ubuntu installed GRUB when it installed) of GRUB to the MBR.

Unfortunately I can't diagnose why my partitions are strange, as the whole partitioning issue mildly confuses me at times - which I think is more out of fear of screwing something up rather than the technical details.  But it's nice to know my cheap mainstream, store-bought PC lives up to the stereotype :-)

I'll certainly be installing Ubuntu on an old machine, I'll mess with it until I blow the thing up so I can learn it from the ground up.  Then I'll understand it a little better and not worry so much about installing it on my main system.

Thanks for your help and response.

---

### Post by Herman on 2007-05-07
Apparently, the way I read the story, when you installed with the USB drive plugged in, the 'IPL' for Grub was installed in the MBR of the USB drive instead of to MBR of your internal hard disk.

The reason I think so is because in your first post you said you could boot Ubuntu with your USB drive plugged in, but when the USB drive was unplugged you couldn't.
Now normally, that would be okay, because you should still be able to boot Windows in either case. If your Ubuntu install placed the IPL for Grub in your USB disk, then it didn't touch your internal hard disk's MBR, so when you unplug the USB dirve, Windows should have been able to boot as if Ubuntu didn't exist, as far as your computer is concerned. Plug in USB Ubuntu should boot, unplug USB, Windows should boot. However in this instance Windows seems to be refusing to boot at all. I don't understand that. It seems like you have been battling multiple problems that are all compounding one another.

I think it would be best to take one thing at a time and try to sort it all out and try to make your installation back to something resembling a more normal arrangement and I'm sure we can get it booting properly then. Everyone else's just works. (Well except for a small percentage we have to adjust a bit, there are 1200 computer a day having Ubuntu installed in them I estimate, so the problems are relatively few in proportion).

1) You have the IPL for Grub in your USB drive's MBR, the IPL is just a small 'pointer' to make the MBR point to the right boot loaders in the right partition. When we say you are 'installing Grub to MBR', it is an abbreviated way of saying things, and it is very misleading. Actually, most of Grub is in your Ubuntu partition, which is in your internal hard disk, while the 'IPL', or pointer to it is in your USB disk MBR. (It should work anyway though).
To make things more normal, if you boot your [Super Grub Disk]("http://supergrub.forjamari.linex.org/") and go 'English Menu'-->'Gnu/Linux'-->'Fix Boot of Gnu/Linux (Grub)', that should install the pointer for Grub in your internal hard disk.
After that you should be able to boot both operating systems without any UBS drive plugged in at all. 

2) If that doesn't work (we'll go into possible reasons why later), and you need to boot Windows XP, boot into Super Grub Disk again and press your 'c' key for  [Grub's Command Line Interface]("http://users.bigpond.net.au/hermanzone/p15.htm#cli").
You can boot your computer up very easily by typing the right commands at the command line if you follow the what I have written on that page. It might take a bit of your time to read it all well though.  Actually, you could skip to [                                                                         How To boot Windows using GRUB's 'CLI]("http://users.bigpond.net.au/hermanzone/p15.htm#How_To_boot_Windows_using_GRUBs_CLI"), the commands given there already include the 'makeactive' command, so grub will set your active flag for you. (I don't know why that command seems to be missing from your earlier error report from SuperGrubDIsk).
If your FAT32 partition is a 'boot' partition you should get feedback from the 'find /boot.ini' and 'find /ntldr' commands. If that happens, let me know, you will need to modify the example commands I typed out here below to (hd0,1) for Windows.
If your boot.ini file and your NTLDR bootloader for Windows are in your NTFS partition (hd0,0) like they should be, then you won't get a reply from those commands. I am expecting this to be the case, that will be good.
Carry on and try the rest of the commands to boot your Windows install. It should boot okay that way. For example,
```
grub>  rootnoverify (hd0,0)  
                                                                          
grub>  makeactive
                                                                         
grub>  chainloader +1
                                                                         
grub>  boot_
```If it still doesn't work, try the 'hide' and 'unhide' commands once again. the other posters were all giving you good advice already. For example,
```
grub>  hide (hd0,1)
                                                                     
grub>  unhide (hd0,0)
                                                                         
grub>  root (hd0,0) 
                                                         
grub>  chainloader +1
                                                       
grub>  makeactive

grub>  boot
``` Try that and it should boot for sure. 
If you get the NTLDR is missing error again, use the NTLDR CD, because now Grub has set the boot flag for you, so the NTLDR CD should work this time. That's in case the partition numbers have changed and there's a mistake in Windows' boot.ini.

Regards, Herman. :)

EDIT: One of the reasons why it's helpful to use use [Grub's Command Line Interface]("http://users.bigpond.net.au/hermanzone/p15.htm#cli") is because that way you get feedback. Grub talks back to you. You may find out something interesting and unexpected that will help solve the problem.

---

