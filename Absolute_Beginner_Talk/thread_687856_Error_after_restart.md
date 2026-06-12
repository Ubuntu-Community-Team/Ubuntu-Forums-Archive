---
title: "Error after restart"
date: 2008-02-04
forum: Absolute Beginner Talk
---

### Post by TMpBG on 2008-02-04
After some upgrade and restart  this is what I see now:

> Starting up...
[   71.057837] Kernel panic - not Syncing: VFS: Unable to mount root fs on unknow - block(0,0)

---

### Post by jan quark on 2008-02-04
a little old but the same problem

don't know exactly if the solution presented will be helpful but just as food for thought

[http://ubuntuforums.org/showthread.php?t=27709&page=2](http://ubuntuforums.org/showthread.php?t=27709&page=2)

---

### Post by Marianne_S on 2008-02-05
I got exactly the same error message this morning after updating (right before i went to work). I noticed that the updates were linux kernel "somethings".


  - i found this post too:

[ Kernel Panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)]("http://ubuntuforums.org/showthread.php?t=576087") 

it is newer - and to me the suggestions seem more easier (the previous suggestion confused me - i don't know what kind of kernel i have etc) -  however i haven't been able to try it myself though, cos i am still at work.

I sure hope this will fix it - cos i have stuff on my computer i need which i haven't had the time to backup - this couldn't happen at worse time - so i am abit panicy right now.

---

### Post by PmDematagoda on 2008-02-05
Are you able to boot Ubuntu in the previous kernels? 

If so, post the output of:-
```
cat /boot/grub/menu.lst
```

---

### Post by TMpBG on 2008-02-05
> Are you able to boot Ubuntu in the previous kernels? 

Sorry but how to do this... I am new linux user

---

### Post by PmDematagoda on 2008-02-05
When you start the PC you must be greeted by a menu, go down this menu and choose a different kernel version to try and boot Ubuntu with.

---

### Post by TMpBG on 2008-02-05
I have 

Ubuntu 7.10, kernel 2.6.22-14 -generic
Ubuntu 7.10, kernel 2.6.22-14 -generic (recovery mode)

and a test of some sort

and win xp

only win xp and the test ting run...

I shared my ubuntu cd with a friend.And now I am downloading it.So in the moment I can't run Live CD.

---

### Post by Marianne_S on 2008-02-05
> **TMpBG said:**
> I have 

Ubuntu 7.10, kernel 2.6.22-14 -generic
Ubuntu 7.10, kernel 2.6.22-14 -generic (recovery mode)

.

i have this too plus: 

Ubuntu 7.10, kernel 2.6.20-16 -generic
Ubuntu 7.10, kernel 2.6.20-16 -generic (recovery mode)

if i boot from Ubuntu 7.10, kernel 2.6.22-14 -generic (recovery mode) - i get the beforementioned kernel panic error message

if i boot from Ubuntu 7.10, kernel 2.6.20-16 -generic (recovery mode) i get root:# -

is this where i should put in the code ```
cat /boot/grub/menu.lst 
```

---

### Post by Marianne_S on 2008-02-05
oh and btw does it have something to say that i  have raiserfs ?

---

### Post by TMpBG on 2008-02-05
I am going just to reinstall ubuntu...
"Marianne_S" I hope you will find a way to save your system.
And if you run in  Live CD you can access your files...

---

### Post by Marianne_S on 2008-02-05
thank you - i just managed to log on in safe graphics mode via the 2.6.20-16 generic kernel - but everything is really wonky, including keyboard settings - very hard to write 

 - i will do some backup at least. 


anyways i did manage to post that code and what i got was this

> 
m@m-desktop:~$ cat /boot/grub/menu.lst
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
timeout         3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

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
# kernel        /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=ac1e85ec-3b51-42be-acd4-bbf5787808c3 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=ac1e85ec-3b51-42be-acd4-bbf5787808c3 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=ac1e85ec-3b51-42be-acd4-bbf5787808c3 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, kernel 2.6.20-16-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=ac1e85ec-3b51-42be-acd4-bbf5787808c3 ro quiet splash
initrd          /boot/initrd.img-2.6.20-16-generic
quiet

title           Ubuntu 7.10, kernel 2.6.20-16-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=ac1e85ec-3b51-42be-acd4-bbf5787808c3 ro single
initrd          /boot/initrd.img-2.6.20-16-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST


how should i go about for recovery?

has it got anything to do with[ this]("http://ubuntuforums.org/showpost.php?p=3604926&postcount=13")?

---

### Post by rkd on 2008-02-05
Marianne: Yes, I think the problem you are having is the same as the one described in the thread you pointed to. I doubt it matters which filesystem you are using.

Backing up your important files is a very good idea. Finish doing that before trying to repair the system.

Your Grub menu identifies the root partitions differently than was done in the thread you pointed to, so we are going to have to fix things a little differently than is described in that thread. I hope someone who understands this a bit better than I do comes along to show you how it is done, but if no one else comes along to help, I think I can get you through it if you are patient with me.

If things go badly while trying to recover, you might have to give up and install 7.10 from scratch, so do be sure you have all the files you care about backed up!

I think that once you have backed up your files, the first bit of information to collect and post is the output from the commands:```
sudo fdisk -l
sudo blkid
```If you type the commands by hand rather than copy and paste, that is a small L in the fdisk command.

---

### Post by Marianne_S on 2008-02-05
i fixed it! by sheer intuition.

TMpBG - i dont think this will help you - but this is what i did

i ran the system through Ubuntu 7.10, kernel 2.6.20-16 -generic

then - since this happened because my pc crashed during an update - i went to system - administration- update manager. then i chose check and i got a message asking me to run > dpkg --configure -a - i ran > sudo dpkg --configure -a.

This restored the update, and my system was fixed - phiew. Now the only thing missing is restoring the proper language for my keyboard - iow please forgive me if i lack some punctuation - i cant seem to find colon for one....


PmDematagoda and rkd - thank you for trying to help both of you! luckily i didnt have to boot from cd and do all those scary commands

---

### Post by Marianne_S on 2008-02-05
i just noticed i didn't mention that my problem happend after my pc crashed during the update - such vital information - how could i have forgotten it? bad bad bad!

 just showes which panicy state i was in i guess. 

thank you guys anyways

---

### Post by rkd on 2008-02-05
Good! I'm glad you got it solved so easily.

It would have been good to mention that you had the crash during the update. But it all worked out okay for you.

---

### Post by Marianne_S on 2008-02-05
> **rkd said:**
> 

It would have been good to mention that you had the crash during the update. But it all worked out okay for you.

Yes it would - and all i can say is : *sorry*

---

### Post by mtngun on 2008-02-05
Similar problem here.   I tried to update Gutsy this morning, and got an error saying I had to run "dpkg--configure-a".

So I ran it, and that gave some more errors.

The PC locked up, so I powered down and tried to restart -- but it wouldn't boot into linux.

Tried recovery mode, it said my linux partition contains errors.  It tried to run fsck but it died with exit status 4, whatever that is.

Then it asked me for a root password for maintenance, but wouldn't take my sudo password (is the maintenance password the same).   I'm not even sure my keyboard was responding.

At that point I gave up and booted into Windows.

I'm going to try using the CD to check for obvious errors, but since I am a relative noobie, I doubt if I will be smart enough to figure it out.

Since I am not the only one having this sort of problem after updating, it seems like there may be a bug in today's updates.

---

### Post by rkd on 2008-02-05
When you boot the computer, how many Ubuntu choices does the boot menu give you? I would expect something like:

Ubuntu 7.10, kernel 2.6.22-14-generic
Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
Ubuntu 7.10, kernel 2.6.20-16-generic
Ubuntu 7.10, kernel 2.6.20-16-generic (recovery mode)

plus your memtest and Windows choices. Try booting to the regular (not the recovery) of the 2.6.20-16 kernel. Then run the ```
sudo dpkg --configure -a
``` in that system. If it gets an error, try it several more times before giving up on it.

If you get stuck, tell us as much as you can about what you did and what the results were, and we'll try to help you.

---

### Post by mtngun on 2008-02-05
I'm fixed -- for the moment.

I booted the gutsy CD and ran gparted to check the linux partition and fix errors.   That seemed to go without a hitch.   Then I rebooted and linux actually worked.

So either there was an error on my disk that had nothing to do with the updates, or else the update process corrupted some files.  I suspect the latter, since I am not the only one having a problem with today's updates.

I still have not installed two of the updates --  linux headers and linux headers generic.  I'm going to do some more backing up and follow this thread to see if more light is shed on this problem.

And my grub menu only gives me two linux choices -- linux and linux recovery.  There is no version 14 vs. 16 option.

---

### Post by MadEarThInk on 2008-02-06
For the record.  My kernel update problem (which I fixed very easily this time, because the last time it took me 16 hours) was this: for some reason the kernel update changes my boot options from noapic to no=apci (or something close to that) these two options do very different things on an HP tx1000 series laptop.  If you have one, beware of kernel updates and your boot options.

---

### Post by Marianne_S on 2008-02-06
> **MadEarThInk said:**
> For the record.  My kernel update problem (which I fixed very easily this time, because the last time it took me 16 hours) was this: for some reason the kernel update changes my boot options from noapic to no=apci (or something close to that) these two options do very different things on an HP tx1000 series laptop.  If you have one, beware of kernel updates and your boot options.

- Hm could this happen to other hp-computers too? i have a hp - how could i find out?

---

### Post by MadEarThInk on 2008-02-06
I don't know how you can find out, but I suggest you copy your /boot/grub/menu.lst and your xorg.conf file before you do a kernel update.

---

### Post by Marianne_S on 2008-02-07
I will - thank you :)

---

### Post by doug-M on 2008-02-08
I put a solution to a similar issue in this thread. If someone is searching later perhaps it will help them.

Kernal panic -Not syncing :VFS : Unable to mount root fs on unknown-block (0,0)
[http://ubuntuforums.org/showthread.php?t=689051&highlight=kernel+panic+vfs](http://ubuntuforums.org/showthread.php?t=689051&highlight=kernel+panic+vfs)

---

