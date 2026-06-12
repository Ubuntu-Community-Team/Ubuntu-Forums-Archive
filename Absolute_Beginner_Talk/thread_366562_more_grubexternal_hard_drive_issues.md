---
title: "more grub/external hard drive issues"
date: 2007-02-21
forum: Absolute Beginner Talk
---

### Post by andy! on 2007-02-21
hi, first of all im so sorry if this has been posted/resolved before, ive been reading forums for hours getting little tips here and there (and learning little by little) but i havnt found anything that accurately represents my situation and im kind of fried and confused from reading everything. but i will say in the few hours ive been using ubuntu im loving it, despite my ignorance and uncertainty with it

so anyway here goes

i have a dell inspiron 1100 laptop, that has windows xp on it. thats kind of irrelevent except to explain my situation

i have a 30 gb external hard drive.

i used my friends dell dimension 2400 desktop (windows xp)  to run the ubuntu live cd (because my laptop has issues and the cd rom drive isnt working so i couldnt boot off of that). i wanted to install ubuntu to the external hard drive so i could use it with my laptop.

i correctly partitioned and formatted the external harddrive, but i think i accidentally installed grub to my friends computer, not the external hard drive like i meant to.

when the install was done, i removed the cd, and removed the hard drive, rebooted and i got the grub error 21 code (grub not found). when i plugged the harddrive back in it went to the boot options (ubuntu, ubuntu recovery, windows xp etc)

i figured out how to use command line to make the computer default to windows xp without that menu coming up but it only boots if the external hard drive is plugged in (which isnt always going to be an option) and now im not sure how to get to ubuntu (since it automatically goes to windows xp - though i only tried it once, and it's getting late and im getitng tired and losing focus)

so my questions are:

how do i get grub from the dell dimension to my laptop or to the external hard drive so it will boot off of the hard drive  (my bios support usb booting)

how do i make it so my friends computer starts without that error message?

i think i read something about using a windows xp restore cd to restore the master boot record BUT i dont have my friends restore cd's around, and all i have for my laptop is the dell restore cd. is there another way?

i hope i was clear, and i hope i can be helped. thanks!

---

### Post by bernied on 2007-02-21
Hello

You have two separate issues:
1:
> how do i get grub from the dell dimension to my laptop or to the external hard drive so it will boot off of the hard drive (my bios support usb booting)
You need to be able to have access to the grub console and you need to know what grub thinks your external drive is called (this name will change depending on how you start grub). 

To get access to the grub console, you can either (i) boot a machine that uses grub as a bootloader, interrupt the boot when you get to the menu (this could be a problem if you have set the timeout to 0 and you can't manage to interrupt it), then hit the 'c' (for console or command) key. Or (ii) start Ubuntu or some other live linux that has grub installed, then get a terminal and type:
```
sudo grub
```
Once you are in a grub console, you need to know how grub refers to the drive, this will be one of (hd0), (hd1), (hd2) etc. To do this, use the TAB-completion feature of grub (this works very similarly to that in linux command shells), so you'd type:
```
root (hd
```then hit TAB (not ENTER).
This should give you a list of drives as grub sees them. Choose one (say hd0), by hitting 0, then the TAB key again.
It will now give you a list of partitions. Choose one, hit TAB, then hit ENTER.
Now, to find out what's on the drive (this is how you will identify it), type:
```
cat /
```then the TAB key again (not ENTER).
This will give you a list of files and folders in the root directory of that partition. 

Note that it may not be a good idea to actually complete that 'cat' command if you are not sure whether the file is a text file. It is fine to use for text files, such as your menu.lst file. Just backspace if you are unsure.

So repeat this from the 'root' command until you know what is what (according to grub).

So what you are trying to do here is find the drive (hdx) and partition (hdx,y) of your external drive's linux install (specifically the location of the menu.lst file for that install). Bear in mind that if you are doing this from another Ubuntu install then you might find the files from that install as well.

Once you have found your target partition, it is easy. Still in the grub console:
```
root (hdx,y)
setup (hdx)
```Does it say it was successful? If yes, then hit the Esc key, if you did this from the startup grub, or type 'quit' (or is it 'exit'?) to get out of grub.

Does this work?

And 2:
> how do i make it so my friends computer starts without that error message?As you have guessed you have installed the grub master boot record (mbr) onto your friend's computer (what are friends for? - hehehe).
> i think i read something about using a windows xp restore cd to restore the master boot record BUT i dont have my friends restore cd's around, and all i have for my laptop is the dell restore cd. is there another way?You just need the application called 'fixmbr' from the cd and a way to run it in a DOS/Windows environment (so a Windows live/restore cd is the obvious choice). Your dell cd might have this application. Alternatively, this is available from an OS called [FreeDOS](http://www.freedos.org/), which is basically a command shell for Windows.

So start up a DOS session, get a command line, and type 'fixmbr'.

---

### Post by bernied on 2007-02-21
You can also use the 'find' command in the grub console to find where your install is - this might speed up the TAB-completion part:
```
find menu.lst
```
But I still recommend learning how to use the TAB-completion feature in grub. It can be very useful knowledge.

---

### Post by andy! on 2007-02-21
ok heres whats happening

i did the sudo grub command and did the tab commands... heres what i got

grub> root (hd
possible disks are: hd0, hd1

(hd0, 
possible partitions are
partition num: 0, filesystem type unknown, partition type 0xde
partition num: 1, filesystem type unknown, partition type 0x7

(hd1,
possible partitions are
partition num: 0, filesystem type unknown, partition type 0x7
partition num: 1, filesystem type is ext2fs, partition type 0x83
partition num: 4, filesystem type unknown, partition type 0x82

if i type the cat / command then press tab in either (hd0,0) (hd0,1) (hd 1,0) or (hd1,4) i get a message saying "error 17: cannot mount selected partition"

if i type it in (hd1,1) i get "possible files are: lost+found var etc media cdrom bin boot dev home initrd lib mnt opt proc root sbin srv sys tmp usr vmlinuz initrd.img


so does this mean that hd1,1 is my linux partition on my external drive?


then i tried

root (hd1,1) setup (hd1) and hit enter
i didnt get any messages, the command line just went down one and said grub>

am i doing something wrong?

---

### Post by andy! on 2007-02-21
after doing that, now if i try to load ubuntu at startup i get a message saying

error 18: selected cylinder exceeds maximum supported by bios
press any key to continue

then it brings me back to where i can select windows xp, grub, etc and i can get a command line

ugh

---

### Post by bernied on 2007-02-21
You may not see it this way, but this is looking good to me. Booting from a usb drive is not a trivial thing, and you are getting there. It took me a week to make this work the first time I tried it.

Can you clarify a few things?
Which machine did you use to do the stuff in your last two posts?
What device is set to boot on that machine? 
If it is set to boot usb first, then can you change it back to boot the hard drive first? Then see if you can get your ubuntu back up? (Or maybe you've fixed up his windows mbr by now?)
If you can get a linux terminal, can you show us the output from (with the usb drive plugged in)
```
sudo fdisk -l
```this command just lists all partitions on all drives.
And, if you can get access to the usb drive, can you find the file /boot/grub/menu.lst (this is grub's configuration file, it describes the boot menu and what should happen when you make a boot selection)? Can you post this file? In the command line you can use 'cat' to display the contents of a file, but you need to find it first.
An easy way to get access to the usb drive would be to run the live cd, then plug in the usb drive, you should then get a friendly popup window asking whether you want to open a browser window (you do). If you have to resort to writing things down, I only need to know the lines in the menu.lst file that do not have a '#' at the start.

Have you tried to boot directly from the usb drive yet (from a machine with bios that will boot from a usb device)? What happens?

The complicated thing with booting from usb drives is that these drives are seen by grub as hard drives. This means they will be named differently depending on how you boot up. I'm guessing that when you did the above, it was from your friend's machine, which boots from the hard drive where the mbr points to a partition on the the external drive. In this configuration, grub thinks the hard drive is hd0 (you couldn't access it through grub because it is using ntfs filesystem, it's windows right?), and the external drive is hd1. But, when you boot directly to the external drive (from the mbr on the external drive pointing to a partition on the external drive), then grub will see the external drive as hd0.

So this means that all your grub configuration (menu.lst) entries will only work in one configuration, because they refer to absolute locations on drives, like (hd1,1), but that location would become (hd0,1) if you booted from the usb drive. And I'm also guessing that grub is currently configured to work only when it is the second drive, not the first. So when you did that setup (hd1) command, you created a bootable mbr on the usb drive that was not there before, so when you rebooted, grub booted from the usb drive, not the hard drive, so suddenly the menu.lst file was meaningless and grub could not find your ubuntu install. 

How's your head?

Anyway, see if you can answer some of the above, and chill.

You might want to google about for things like 'grub tutorial' and 'dual-booting'. See what you can find. Remember what you are doing is not easy, but you are doing it.

---

### Post by andy! on 2007-02-21
> You may not see it this way, but this is looking good to me. Booting from a usb drive is not a trivial thing, and you are getting there. It took me a week to make this work the first time I tried it.

i believe it. i understand im jumping headfirst into an operating system i know zero about just so i can learn it. i just wish the problems were all on my laptop and not occuring on my friends computer


> Can you clarify a few things?
Which machine did you use to do the stuff in your last two posts?

i used my friends dell.

> What device is set to boot on that machine?

the boot order is floppy->hard drive->cd->usb
> If it is set to boot usb first, then can you change it back to boot the hard drive first? Then see if you can get your ubuntu back up? [/I][I](Or maybe you've fixed up his windows mbr by now?)

mbr is not fixed yet, the external hard drive is still required to be plugged in in order to even get to the boot options. right now i am booted in ubuntu off of the live cd.

> If you can get a linux terminal, can you show us the output from (with the usb drive plugged in)
```
sudo fdisk -l
```

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System 
/dev/hda1               1           4       32098+  de  Dell Utility
/dev/hda2   *           5        9725    78083932+   7  HPFS/NTFS

Disk /dev/sda: 30.7 GB, 30735581184 bytes
255 heads, 63 sectors/track, 3736 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1207     9695196    7  HPFS/NTFS
/dev/sda2   *        1208        3643    19567170   83  Linux 
/dev/sda3            3644        3736      747022+   5  Extended
/dev/sda5            3644        3736      746991   82  Linux swap / Solaris
ubuntu@ubuntu:~$ 




> this command just lists all partitions on all drives.
And, if you can get access to the usb drive, can you find the file /boot/grub/menu.lst (this is grub's configuration file, it describes the boot menu and what should happen when you make a boot selection)? Can you post this file? In the command line you can use 'cat' to display the contents of a file, but you need to find it first.
An easy way to get access to the usb drive would be to run the live cd, then plug in the usb drive, you should then get a friendly popup window asking whether you want to open a browser window (you do). If you have to resort to writing things down, I only need to know the lines in the menu.lst file that do not have a '#' at the start.

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
default        0 

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        5

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
# title        Windows 95/98/NT/2000
# root        (hd0,0) 
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=e1fe3c4c-cc50-469a-9a65-fe649cf9d940 ro
# kopt_2_6=root=/dev/sda2 ro

## default grub root device 
## e.g. groot=(hd0,0)
# groot=(hd1,1)

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

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda2 
title        Microsoft Windows XP Home Edition
root        (hd0,1)
savedefault
makeactive
chainloader    +1

## ## End Default Options ##

title        Ubuntu, kernel 2.6.17-10-generic
root        (hd1,1) 
kernel        /boot/vmlinuz-2.6.17-10-generic root=/dev/sda2 ro quiet splash
initrd        /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title        Ubuntu, kernel 2.6.17-10-generic (recovery mode) 
root        (hd1,1)
kernel        /boot/vmlinuz-2.6.17-10-generic root=/dev/sda2 ro single
initrd        /boot/initrd.img-2.6.17-10-generic
boot

title        Ubuntu, memtest86+
root        (hd1,1)
kernel        /boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems: 
root


> 
Have you tried to boot directly from the usb drive yet (from a machine with bios that will boot from a usb device)? What happens?

no. after i post this i will try that.

> The complicated thing with booting from usb drives is that these drives are seen by grub as hard drives. This means they will be named differently depending on how you boot up. I'm guessing that when you did the above, it was from your friend's machine, which boots from the hard drive where the mbr points to a partition on the the external drive. In this configuration, grub thinks the hard drive is hd0 (you couldn't access it through grub because it is using ntfs filesystem, it's windows right?), and the external drive is hd1. But, when you boot directly to the external drive (from the mbr on the external drive pointing to a partition on the external drive), then grub will see the external drive as hd0.

So this means that all your grub configuration (menu.lst) entries will only work in one configuration, because they refer to absolute locations on drives, like (hd1,1), but that location would become (hd0,1) if you booted from the usb drive. And I'm also guessing that grub is currently configured to work only when it is the second drive, not the first. So when you did that setup (hd1) command, you created a bootable mbr on the usb drive that was not there before, so when you rebooted, grub booted from the usb drive, not the hard drive, so suddenly the menu.lst file was meaningless and grub could not find your ubuntu install. 

How's your head?

Anyway, see if you can answer some of the above, and chill.

that actually made sense and after i post this and try to reboot im gonna take a little walk away from the computer and let my brain process everything then come back and try to tinker.



> You might want to google about for things like 'grub tutorial' and 'dual-booting'. See what you can find. Remember what you are doing is not easy, but you are doing it.


hah yeah last night i was googling for hours and i had like 15 different tabs open with about 15 different approaches of what to do (all with scenarios varying from mine) so i figured id come right here to the ubuntu forum and try to get some personalized help. thanks for everything so far, and here's to the future! hah

---

### Post by andy! on 2007-02-21
> 
Quote:
Have you tried to boot directly from the usb drive yet (from a machine with bios that will boot from a usb device)? What happens?
no. after i post this i will try that.

i tried booting on my laptop with the usb drive plugged in and i got a message saying "operating system not found"

im thinking thats due to grub not being present on the usb drive? instead its on the desktop im trying return to its state prior to me tinkering with it

---

### Post by bernied on 2007-02-21
> i tried booting on my laptop with the usb drive plugged in and i got a message saying "operating system not found"

im thinking thats due to grub not being present on the usb drive? instead its on the desktop im trying return to its state prior to me tinkering with it
This is from a couple of posts back (yours):> ...then i tried

root (hd1,1) setup (hd1) and hit enter
i didnt get any messages, the command line just went down one and said grub>That should have been two separate commands, sorry I wasn't clear. That might account for the lack of feedback from grub.
```
root (hd1,1) <Enter>
setup (hd1) <Enter>
```
Only use those exact commands if you're sure that the usb disk is still called hd1
These commands should put the grub mbr onto the usb disk, pointing at the second partition on the usb disk (the one with your ubuntu on it). This should make it bootable.
What happens now?

This is from your menu.lst file:> title Ubuntu, kernel 2.6.17-10-generic
root (hd1,1)
kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/sda2 ro quiet splash
initrd /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
bootThis is the second entry, so would be the second line on the menu. A couple of points about this:
- you can use these commands on the grub command line when you boot up (you can use some of them on the grub console that you get from 'sudo grub'), so write down those commands in that entry, reboot grub, hit 'c' to get a command line, and see if you can get your ubuntu to start. This way you will see at what stage things go wrong.
- use TAB-completion if you are looking for a particular file or directory
- it might be best to leave out the quiet option in the kernel line, and the line that just says quiet - these reduce output, which is not useful when you're having grief
- it might be best to leave out the savedefault command - this writes your default grub choice to disk, which might be problematic on the usb disk
- so you need a command for each of 'root' (tells grub where to look for files), 'kernel' (loads the kernel into memory, ready to execute), 'initrd' (loads a ramdisk image into memory, this provides the linux kernel with a basic set of files that it needs to get going, before it can access files on disk), and 'boot' (start). If that all works, we're down to dealing with Ubuntu, not grub.
- how far do you get?

I'm off to get some sleep - good luck.
Bernie

---

### Post by dwblas on 2007-02-21
> im thinking thats due to grub not being present on the usb driveCorrect> root (hd1,1) setup (hd1) and hit enter
i didnt get any messages, the command line just went down one and said grub>So far, this appears to be correct, except you key in "root (hd1,1)" then enter, "setup (hd0)" then enter, which updates the MBR, then "quit" and enter, and you should be ok to reboot.  If you key in "setup (hd1)" it will put the boot info on the hd1 (hdb)  drive.  I don't know if that is what you want or not, but it sounds like you do want hd1.  If that doesn't work, you can always change it.

Edit: I found this link in the forums for booting from a floppy and installing via the internet if that is more to your liking.  Post back if you use it.  I'm sure others may want to try it.  [http://www.ubuntuforums.org/showthread.php?p=145618](http://www.ubuntuforums.org/showthread.php?p=145618)

---

### Post by bernied on 2007-02-22
> So far, this appears to be correct, except you key in "root (hd1,1)" then enter, "setup (hd0)" then enterMaybe not a good idea - this is how he toasted his friend's mbr. The aim is to have the mbr on the usb disk pointing to ubuntu partition on the usb disk. The above would have the mbr on the first hard drive pointing at the ubuntu install on the usb disk, which is the current situation.

Be very careful.

---

### Post by dwblas on 2007-02-22
Exactly.  Which is why I explained both options.> If you key in "setup (hd1)" it will put the boot info on the hd1 (hdb) drive. I don't know if that is what you want or not, but it sounds like you do want hd1. If that doesn't work, you can always change it.

---

### Post by andy! on 2007-02-25
ok im back after spending the weekend away.

i have procured a windows xp disk, and the mbr is repaired.

now im about to work on installing grub to the hard drive PROPERLY

haha
thanks for all your help!

---

