---
title: "dual boot problem helppppppppppp"
date: 2007-01-11
forum: Absolute Beginner Talk
---

### Post by broekskw on 2007-01-11
ok started from the beginning and installed win98 first then installed from live cd ubuntu, everything looked like to took untill i try to boot into win98 from the selection screen, it tries to boot into win98 but from the floppy first,since i do not have a floppy in drive a i get a error that comes up

"type the name of the command interpreter (ec, c:\windows\command.com\)

what happened,it tries to find win 98 off my a:drive. and whats with the error code. did i lose my win98 al together, please help someone  thanks:D 

i have 1 30bg h/drive with 256mb memory 1.4 cpu pent

---

### Post by confused57 on 2007-01-11
> **broekskw said:**
> ok started from the beginning and installed win98 first then installed from live cd ubuntu, everything looked like to took untill i try to boot into win98 from the selection screen, it tries to boot into win98 but from the floppy first,since i do not have a floppy in drive a i get a error that comes up

"type the name of the command interpreter (ec, c:\windows\command.com\)

what happened,it tries to find win 98 off my a:drive. and whats with the error code. did i lose my win98 al together, please help someone  thanks:D 

i have 1 30bg h/drive with 256mb memory 1.4 cpu pent

Unless someone else has another suggestion, I'd enter bios setup at boot and set the hard drive to boot before the floppy drive, just to see if you can boot both OS.

---

### Post by rabid emu on 2007-01-11
Not sure why you'd ever want to boot windows 98...

But disregarding that, you need to change your BIOS settings to boot from the hard drive instead of the floppy drive.

---

### Post by louieb on 2007-01-11
So you get to the GRUB menu and can boot Ubuntu, but you can't boot windows correct?
It now a matter of fixing the windows entry in the GRUB configuration file.[LIST]
[*]Open Applications > Accessories > terminal
[*]Backup
[*]```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst-b
```
[*]Edit
[*]```
gksudo gedit /boot/grub/menu.lst
```
[*]Add following below line ### END DEBIAN AUTOMAGIC KERNELS LIST```
title Windows
      rootnoverify (hd0,0)
      makeactive
      chainloader +1
      boot
```[/LIST]
This should work.

---

### Post by broekskw on 2007-01-11
ok thanks all for your reply. here  is a screen shot of my gksudo gedit /boot/grub/menu.lst list after inputing the following line, does that look correct louieb

thanks. will give it a try.the reason i whant to dual boot is that i have a lot of games that will only run on win98

thanks:D

---

### Post by broekskw on 2007-01-11
ok no luck in adding that line still tries to load from a drive, am i screwed then:evil:

---

### Post by broekskw on 2007-01-11
ok after it fails to boot in win98 i am at a a> command, tried everything to get to a c: command but with no luck,how would some one get to a c: command from here??

---

### Post by Ben Sprinkle on 2007-01-11
> **louieb said:**
> So you get to the GRUB menu and can boot Ubuntu, but you can't boot windows correct?
It now a matter of fixing the windows entry in the GRUB configuration file.[LIST]
[*]Open Applications > Accessories > terminal
[*]Backup
[*]```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst-b
```
[*]Edit
[*]```
gksudo gedit /boot/grub/menu.lst
```
[*]Add following below line ### END DEBIAN AUTOMAGIC KERNELS LIST```
title Windows
      rootnoverify (hd0,0)
      makeactive
      chainloader +1
      boot
```[/LIST]
This should work.

I believe this is incorrect, I am at school now but when I get home I'll post my menu.lst, mine is different from that and boots into 98 and XP fine.

---

### Post by Ben Sprinkle on 2007-01-11
Also, broekskw, what partition is your windows on, like your first or second on your hard drive?

---

### Post by broekskw on 2007-01-11
just home for lunch. Goat Spirit my win98 was installed first then ubuntu so i think it's on my first partition.i did the live cd install and let ubuntu select the hard drive space to use for ubuntu to install, did not do partition manualy. so i think win98 is on first partition.

thanks:mrgreen:

---

### Post by confused57 on 2007-01-11
> **broekskw said:**
> just home for lunch. Goat Spirit my win98 was installed first then ubuntu so i think it's on my first partition.i did the live cd install and let ubuntu select the hard drive space to use for ubuntu to install, did not do partition manualy. so i think win98 is on first partition.

thanks:mrgreen:
You can find out by booting into Ubuntu, or you can use the live cd, open a terminal(Applications---Accessories---Terminal), enter:
```
sudo fdisk -l
```
The -l is a small "L".

This will show your partition table.

---

### Post by louieb on 2007-01-11
Yea sudo fdisk -l should help. But I looked at your menu.lst and it looks just fine. The only difference between   the one I gave you and the one Ubuntu installed is I used [COLOR=Purple]rootnoverify[/COLOR] and Ubuntu used [COLOR=Purple]root[/COLOR] - I have seen both work. 
Out of curiosity boot to windows again and at the a:\> prompt type ```
c:
``` this should give you a c:\> prompt  at the c:\> prompt type```
 dir
```  this should list the directories and files on your c: drive. 
If not try ```
c:\windows\command.com
```
and try the dir command again.
If the dir command works then you windows install is probably ok. If not I hope you have  a Win98 CD. A couple of things to download and try is  [Super Grub Disk]("http://supergrub.forjamari.linex.org/") it is reported it can fix a windows boot problems. also another place to try is [bootdisk.com]("http://bootdisk.com/")    
You have a problem I have not run into before with windows booting to an a:> prompt so I am suggesting some things I remember for my days of running DOS.

---

### Post by broekskw on 2007-01-11
thanks will try all out. here is my boot info
Disk /dev/hda: 30.7 GB, 30735581184 bytes
255 heads, 63 sectors/track, 3736 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1965    15783831   44  Unknown
/dev/hda2            1966        3659    13607055   83  Linux
/dev/hda3            3660        3736      618502+   5  Extended
/dev/hda5            3660        3736      618471   82  Linux swap / Solaris
kwasd@kwasd-desktop:~$ 

and louieb have tried the c: and the c:\windows\command.com command but no luck, will try the super grub disk thing an let you know how i make out

thanks:mrgreen:

---

### Post by broekskw on 2007-01-11
ok so how do i use super grub disk. downloaded the  super grub disk english 0.9550.iso. do i need to burn to a cd now.??? or is there a floppy one out there ](*,)

---

### Post by broekskw on 2007-01-12
ok burned iso image to cd and ran all or every possible boot up for win98, final conclusion is it's gone, don't know what happened to my win98 partition gone.

all i did was install win98 first, got it up and running completly and then did the live cd install and let linux set the size of the partition to go onto, linux ubuntu ran great but everytime i try to boot into win98 it tried to boot from floppy(even running in super grud disk) so do i start over and try again or just throw out all my old games and just use ubuntu](*,) ](*,)

---

### Post by netadptr0719 on 2007-01-12
all I can think of is to use
fdisk -l
and look at you list of drives and then go into 
/boot/grub/menu.lst
and make sure that the hd location in fdisk matches what it says it is in menu.lst

---

### Post by louieb on 2007-01-12
Your fdisk output has bad news. ```
dev/hda1   *           1        1965    15783831   44  Unknown
``` You see the 44 unknown. (You should see 0b fat32 or oc fat32). 
That means there is something wrong with the partition table entry for the first partition.
But it may be that fixing the partition type in the table without actually formatting the partition will fix it. Try [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk) or [http://trinityhome.org/Home/index.php?wpid=1&front_id=12](http://trinityhome.org/Home/index.php?wpid=1&front_id=12) and see if one of those can fix it.
 Got to go to work. Good luck. 
Win98 uses type 0b or 0c for fat32

---

### Post by broekskw on 2007-01-13
ok reformated and installed win98 again and checked disc and defraged.now installing ubuntu.
can someone look at this and tell me if this is correct, i thought win98 was on hd0

Language: English
 Keyboard layout: U.S. English
 Name: broeks
 Login name: kwasd
 Location: America/Vancouver
 GRUB will be installed to (hd0)


If you continue, the changes listed below will be written to the disks.
Otherwise, you will be able to make further changes manually.

WARNING: This will destroy all data on any partitions you have removed as
well as on the partitions that are going to be formatted. let 

The partition tables of the following devices are changed:
 IDE1 master (hda)

The following partitions are going to be formatted:
 partition #2 of IDE1 master (hda) as ext3
 partition #5 of IDE1 master (hda) as swap

just give me to go ahead and will push the button:mrgreen:

---

### Post by Ben Sprinkle on 2007-01-13
hd0 means your first hard drive, not first partition.
hd0,1 is your first partition, aka hda1.

---

### Post by broekskw on 2007-01-13
so ok to go and install

---

### Post by broekskw on 2007-01-13
rock on dual boot working great this time. thanks to all that got me going:D 

see my list. looks good this time

kwasd@kwasd-desktop:~$ sudo fdisk -l
Password:

Disk /dev/hda: 30.7 GB, 30735581184 bytes
255 heads, 63 sectors/track, 3736 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1724    13847998+   c  W95 FAT32 (LBA)
/dev/hda2            1725        3650    15470595   83  Linux
/dev/hda3            3651        3736      690795    5  Extended
/dev/hda5            3651        3736      690763+  82  Linux swap / Solaris
kwasd@kwasd-desktop:~$

---

### Post by Ben Sprinkle on 2007-01-13
Glad your happy. ;)

---

