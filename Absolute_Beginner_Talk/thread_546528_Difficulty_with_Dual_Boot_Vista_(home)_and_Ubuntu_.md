---
title: "Difficulty with Dual Boot Vista (home) and Ubuntu 6.10 on Gateway NX570S laptop"
date: 2007-09-08
forum: Absolute Beginner Talk
---

### Post by mitch_scaff on 2007-09-08
I've searched through three or four related threads now without finding a good enough fit to my problem.  I am trying to get to a dual boot machine with the least time from where I am.  

The problem:  After installing Ubuntu 6.10 (live desktop version came with the Ubuntu for Dummies book), when I restart the machine and choose Vista, I either get a black screen directly, or I get the little Microsoft progress indicator.  Sometimes this transitions to a black screen.  Sometimes it continues for more than 10 minutes (I timed it).  

I have read about adding an option to /boot/grub/menu.lst and editing it

the two last "stanzas" read

  title    Windows Vista
  root    (hd0,0)
  savedefault
  makeactive
  chainloader +1

  title     Windows Vista/Longhorn (loader) 
  root    (hd0,1) 
  savedefault
  makeactive
  chainloader +1

neither seems to provoke a different response

I have also read that people are concerned that they have obliterated their vista OS through damaging the NTSF software.  I don't think this is the problem.  

I followed the directions in one of the threads, created a /mnt/vista directory and mounted it to 
sda1 (I think it was sda1 but I'm not sure - mounting a disk was a new idea to me 6 years ago, when I last used unix - so I don't remember how to check it).   Anyway, I used the directory tool suggested by the thread (nautilus?) and was able to see Windows files (I presume, the Vista system files are in there too).  

I'd like to get Vista working again,  with me able to choose whether to boot Vista or Ubuntu whenever I boot up.  

Secondarily, I'd like to understand the process - what needs to be changed, and why. 

Thank you very much for your help. 

  Mitch:|

---

### Post by mitch_scaff on 2007-09-09
P.S. Can this be made to work with Ubuntu 6.10?  I'd like to put off the steps of downloading, burning, and reinstalling for another day if possible.  I had hoped the authors weren't kidding when they said I would be done quickly, much less than a long afternoon.  I've now spent about 6 or 7 hours and want to finish for the evening while I still can.   

If 6.10 is incompatible with Vista, I'll just reinstall Vista and have done for the week.  

And again - thank you very much for your help.

---

### Post by Bethrine on 2007-09-09
I got your message in my thread and have posted a link with the answers you are looking for. Sorry about the unfinished thread!! I know how frustrating it can be, believe me! Here is the link back and at the end you will find a link to the thread that should contain the rest of what you need. Really hope this helps!

[http://ubuntuforums.org/showthread.php?t=538403](http://ubuntuforums.org/showthread.php?t=538403)

---

### Post by Bethrine on 2007-09-09
p.s. after grub boots vista I had to move it to the master boot record for vista (mbr) and then adjust the partition settings accordingly. Your partitions may be labled differently than mine. I also had to edit my boot record while the computer was booting so I suggest getting the settings for the partitions correct (what they will be after you've moved grub) before moving grub to the mbr.

---

### Post by mitch_scaff on 2007-09-09
Thanks - OK, let me see if I can make a bit more progress here.  

First of all, how do I figure out where Vista (is supposed to) boot from?

Also, what is grub? 

 (what are the emoticons for resigned and/or determined?)

---

### Post by asmoore82 on 2007-09-09
> **mitch_scaff said:**
> Also, what is grub?

GRUB = **GR**and **U**nified **B**ootloader

---

### Post by Bethrine on 2007-09-09
I only know how to use the emoticons in a message that is not an "instant reply" except for :) and :( I am kinda new too.

grub is a program that tells your system how and where to boot from. 

I use...

gksudo gedit /boot/grub/menu.lst

to see what grub is doing, please post it then post...

sudo fdisk /dev/hda

to show where everything is.

---

### Post by Bethrine on 2007-09-09
By the way, I believe you are right that Vista was never wiped out.

---

### Post by Bethrine on 2007-09-09
if 

> sudo fdisk /dev/hda

doesn't happen to work (it doesn't for me, I have a SATA drive) put in code...

> sudo fdisk

by itself and try the different /dev/--- options. I have to use /dev/sda which is not on the list in my fdisk list

---

### Post by mitch_scaff on 2007-09-09
I used fdisk - 

/dev/sda1 is bootable, runs from block 1 to block 1053, and HPFS/NTFS  so I am confident that
this is an intact partition with a bootable version of Windows Vista somewhere inside. 

So what's next? :)

---

### Post by mitch_scaff on 2007-09-09
I was not able to open up /dev/hda

---

### Post by Bethrine on 2007-09-09
Sorry, it's

> sudo fdisk -l

here is mine...

> e:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7699    61842186    7  HPFS/NTFS
/dev/sda2            7700       14408    53890042+  83  Linux
/dev/sda3           14409       14593     1486012+   5  Extended
/dev/sda5           14409       14593     1485981   82  Linux swap / Solaris
:~$


grub sees 1 as 0 and sees 2 as 1, etc.

---

### Post by Bethrine on 2007-09-09
you need to plug in the proper numbers for (hd0,0) to tell grub where to boot first. your fdisk -l will give you these numbers. Almost all of these changes are made in the bottom half of the code...

here is my menu.lst

> # menu.lst - See: grub(8), info grub, update-grub(8)
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
timeout		25

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
# kopt=root=/dev/sda3 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

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

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
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

title		Ubuntu, kernel 2.6.15-29-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-29-386 root=/dev/sda2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-29-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-29-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-29-386 root=/dev/sda2 ro single
initrd		/boot/initrd.img-2.6.15-29-386
boot

title		Ubuntu, kernel 2.6.15-28-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-28-386 root=/dev/sda2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-28-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-28-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-28-386 root=/dev/sda2 ro single
initrd		/boot/initrd.img-2.6.15-28-386
boot

title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/sda2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/sda2 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title           Windows Vista
root            (hd0,0)
savedefault
makeactive
chainloader     +1


---

### Post by mitch_scaff on 2007-09-09
in entry #20 of the continuation thread, you said you changed  the line in menu.lst to

  root=/dev/sda2

my line now reads

   root (hd0,0)

What does the root line do?  if the Vista boot intructions are on sda1, should I change the line to read 

  root=/dev/sda1

---

### Post by mitch_scaff on 2007-09-09
Darnit, you can see I'm poking around in the thread while I await replies - which leaves me behind
when I get them.

without the ability to open up /dev/hda, how do I find out what (hd X,Y) should be?

---

### Post by Bethrine on 2007-09-09
I have

> root          (hd0,1)

for all of my linux kernals and

> root          (hd0,0) for my Vista

because my linux partition is on /dev/sda2 (grub sees 2 as 1) and my NTFS on /dev/sda1 (grub sees 1 as 0)

---

### Post by Bethrine on 2007-09-09
> **mitch_scaff said:**
> Darnit, you can see I'm poking around in the thread while I await replies - which leaves me behind
when I get them.

without the ability to open up /dev/hda, how do I find out what (hd X,Y) should be?

Okay, you don't have to open up a partition (/dev/hda1 or 2 or whatever). You have to make the changes in the grub menu.lst

your results of 

> sudo fdisk -l

should give you a list of partitions and which file system is where

Sorry, I will try to slow down.  :)

---

### Post by mitch_scaff on 2007-09-09
that's what I have - 

root (hd0,0)

for my first Vista stanza  and the Vista bootable partition is on /dev/sda1


so I am at a loss.  :( (slightly grumpy harumph like frown)

---

### Post by Bethrine on 2007-09-09
Good! That is what we want. Are your linux stanzas correct?

after it is all correct you will then need to move grub to the master boot record. There is a good thread on how to do this and I am looking for it.

Can anyone help with finding this thread?

---

### Post by Bethrine on 2007-09-09
if you can copy and paste them I could be of better help also

---

### Post by mitch_scaff on 2007-09-09
Do you know how I can refer this to someone who might know more so I can get unstuck?:confused:

---

### Post by Bethrine on 2007-09-09
Well, as long as you have the hd's (all of them) pointing to the correct /dev's you should be fine and all you need to do is move grub to the mbr. I found that thread, here it is...

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

If you post them, I can be sure they are right. If not it is up to you, of course.

DON'T FORGET TO SAVE THE CHANGES TO GRUB FIRST...IF YOU HAD TO MAKE ANY

---

### Post by mitch_scaff on 2007-09-09
Unfortunately I cannot copy and paste - I'm running this forum conversation on a machine (a MAC) that has internet connectivity -which I don't have set up yet on my laptop.

I am pretty sure the menu.lst is now set up (and has been set up) as specified in the threads we have been referring to, (most particularly, this one)

If I understand you correctly, now it's just a matter of moving the menu into the right part of windows/Vista.

(I just got your last few posts all at once - you can disregard my previous two)

---

### Post by mitch_scaff on 2007-09-09
can you remember where in the 190 or so posts on that thread, the part about moving menu.lst to MRB is?

---

### Post by Bethrine on 2007-09-09
I suggest two more changes before you do that, your timeout allotment on bootup and I will post the second in just a minute. To move to the mbr should be in the thread two posts up or so, I provided that link...here is the timeout to change to whatever you are comfortable with....

> ## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		25


just change the 25 (you may have another number there) to what you would like in seconds

---

### Post by Bethrine on 2007-09-09
Courtesy of rsambuca...

> "I looked at your grub/menu.lst a little closer. I think that you will want to change your menu.lst as follows, otherwise this will happen again at the next kernel update.
Code:

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1) "

But you should use your numbers.Remember, hd0,0 is my Vista (the top one) and hd0,1 is my linux (the bottom one)

---

### Post by Bethrine on 2007-09-09
Let me know if you have it working okay. It's late, I need to go. I will check here in the morning.

---

### Post by mitch_scaff on 2007-09-09
OK, let me slow down just a bit.  I get the bit about using my own numbers
but what does ## at the start of a line mean?
what does # at the start of a line mean?

and where should this code snippet go?

Also, was this person using the Ubuntu live from CD?  For me, it's now installed. 

Do we want these changes to menu.lst only in the grub directory, only in the MRB, or in both?

---

### Post by mitch_scaff on 2007-09-09
Ugh.

I still don't have the foggiest idea of where the file goes. I understand the need for sleep, but once I quit tonight, it's going to be (probably) 4 or 5 days before I can come on here again, and in the meantime, I have a useless laptop. (Unless I just want to use Ubuntu). 

Waah.

---

### Post by mitch_scaff on 2007-09-09
Thank you for all your help so far.  I will try hunting through the final thread you mentionned.  I just wish there werent 19 pages of it, much of which is irrelevant. 

Thank you and sleep well.

---

### Post by Bethrine on 2007-09-09
It should all be in the first post of that thread. That is what they are doing. Did you make the timeout changes above? The code is already in grub, you just need to find it and change the numbers. Don't worry about the # and ## right now.

---

### Post by Bethrine on 2007-09-09
I'm sorry, I really must go. I am getting notification on this thread. I will answer asap when it hits my email.

---

