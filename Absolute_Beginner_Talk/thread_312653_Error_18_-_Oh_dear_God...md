---
title: "Error 18 - Oh dear God.."
date: 2006-12-04
forum: Absolute Beginner Talk
---

### Post by urk_nono on 2006-12-04
When I wanted to install a login-window when choosing OS, I got the error "Could not load selected image etc." press any key..

After a few tries editing my menu.lst (wanting to know wich hd (hd0,0 something) I was to use, wich I haven't figured out yet btw), I came across an error. I couldn't get into any of my OS! This is what came up

**Error 18 - Selected cylinder exceeds maximum supported by BIOS.** 

When I accessed the command line and managed to reboot a voice said "System failed.. CPU overclocking" something..

Now I'm using the Edgy install CD to be able to get in and write this. Anyone got a helping hand? 

I feel screwed :(

---

### Post by urk_nono on 2006-12-04
Anyone? :(

---

### Post by Chinkostu on 2006-12-04
from the command can you edit the menu.lst?

or even see the partition in the live cd to edit it?

---

### Post by urk_nono on 2006-12-04
> **Chinkostu said:**
> from the command can you edit the menu.lst?

or even see the partition in the live cd to edit it?

No :(

---

### Post by bodhi.zazen on 2006-12-04
LOL :lol:

Slow down, don't panic.... All is not lost....

Tell me, what did you do ?

I had a similar problem with a large HD once... the problem is with you bios....

I assume you want to start with restoring windows ?

Restore windows MBR:
Yes boot from the (windows XP) cd.

Windows will come with some screens and look at "repair an existing XP" or something like that.
NOT THE AUTOMATIC REPAIR it will bring you nowhere.

You get three options,install windows,repair an existingt XP or quit.

Yust choose repair you get a black screen where the existing install [a number] is displayed.

Choose that number and then it asks for your administrator password.

Type in ADMINISTRATOR if you don't know otherwise and pray it's the right one.

Then you get a prompt.
Type fixboot and see what it tells you.
If this doesn't work type fixmbr and you get a warning about messing up things,but ignore,and proceed.

This should make your windows bootable again.

---

### Post by gn2 on 2006-12-04
While not a cure for your current difficulty, if you have two hard drives, this may be interesting: [http://www.ubuntuforums.org/showthread.php?t=275728](http://www.ubuntuforums.org/showthread.php?t=275728)

---

### Post by urk_nono on 2006-12-05
> **bodhi.zazen said:**
> LOL :lol:

Slow down, don't panic.... All is not lost....

Tell me, what did you do ?

I had a similar problem with a large HD once... the problem is with you bios....

I assume you want to start with restoring windows ?

Restore windows MBR:
Yes boot from the (windows XP) cd.

Windows will come with some screens and look at "repair an existing XP" or something like that.
NOT THE AUTOMATIC REPAIR it will bring you nowhere.

You get three options,install windows,repair an existingt XP or quit.

Yust choose repair you get a black screen where the existing install [a number] is displayed.

Choose that number and then it asks for your administrator password.

Type in ADMINISTRATOR if you don't know otherwise and pray it's the right one.

Then you get a prompt.
Type fixboot and see what it tells you.
If this doesn't work type fixmbr and you get a warning about messing up things,but ignore,and proceed.

This should make your windows bootable again.


Thanks for the help, but now my body is getting allergic reactions from only being able to boot Windows, hence why I installed Ubuntu in the first place :mrgreen:  

Could you help me out getting my Edgy back?

---

### Post by bodhi.zazen on 2006-12-05
> **urk_nono said:**
> Thanks for the help, but now my body is getting allergic reactions from only being able to boot Windows, hence why I installed Ubuntu in the first place :mrgreen:  

Could you help me out getting my Edgy back?

LOL :lol: Ubuntu fever is it?

Sure, no problem.

First, can you give me you partitioning table ? How many hard drives, how many partitions and how big are they ?

Also check to see if there is an update for your BIOS.

I think the problem is simple, make your windows partition smaller, then put the Ubutnu root partition second, then swap, and last, if needed, a larger data partition to share between windows and Ubuntu.

---

### Post by urk_nono on 2006-12-05
> **bodhi.zazen said:**
> LOL :lol: Ubuntu fever is it?

Sure, no problem.

First, can you give me you partitioning table ? How many hard drives, how many partitions and how big are they ?

Also check to see if there is an update for your BIOS.

I think the problem is simple, make your windows partition smaller, then put the Ubutnu root partition second, then swap, and last, if needed, a larger data partition to share between windows and Ubuntu.

Here's my [HD]("http://img49.imageshack.us/my.php?image=screenshotko2.png")

---

### Post by bodhi.zazen on 2006-12-05
I assume your windows partition is in /dev/sda1. This is OK.

I hope the rest of the drive is available for Ubuntu.

If so, delete /dev/sda2 (and thus /dev/sda5 and /dev/sda6) and make a root partition for Ubuntu of say 20 Gb (you can go smaller if you like). Then make a swap partition of ram X2 or 1 Gb max.

Then allocate the rest of the HD as a data partition. Format it as FAT and you will be able to share it with Ubuntu and Windows.

===========================

More complex:
If you have stuff in the ntfs partition (/dev/sda5)you need to move it to the back end of the drive.

If this is the case, boot to windows, defragment the partition, and then try to re-size it as small as possible. Gparted will do this for you (resize and move).

[Download GParted](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)


You can move the Ubuntu partition, but it may be easier to re-install.
============================

Summary: You need to move your Ubuntu root earlier on the HD.

/dev/sda1 = nfts = 12 Gb (current sda1)
/dev/sda2 = ext3 = 20 Gb (may be as small as 7-10 Gb easily) = Ubuntu root

/dev/sda3 = swap = ram X2, 1 Gb max

/dev/sda4, or extended partion = Rest of HD space = ?FAT

This is the simple scheme, ther are mor complex schemes....

HTH 8)

---

### Post by Sef on 2006-12-05
I don't see a swap partition on your hard drive.  To put one on, use the partioner on your Live CD or download and use [GParted]("http://gparted.sourceforge.net/livecd.php").  Note: The Live CD uses an older version of GParted as its partioner; however, both should do fine for installing a swap file.

Have you read [Restore GRUB]("http://doc.gwos.org/index.php/Restore_Grub")?

---

### Post by bodhi.zazen on 2006-12-05
> **Sef said:**
> I don't see a swap partition on your hard drive.

Have you read [Restore GRUB]("http://doc.gwos.org/index.php/Restore_Grub")?

Hi Sef !

FYI, the problem is with his BIOS.
> Error 18 - Selected cylinder exceeds maximum supported by BIOS.

I think he needs to move the Ubuntu root partition earlier on the HD.

---

### Post by urk_nono on 2006-12-07
> **bodhi.zazen said:**
> Hi Sef !

FYI, the problem is with his BIOS.


I think he needs to move the Ubuntu root partition earlier on the HD.

Yeah, tried the "Restore Grub" method, but when I use the Live-CD I get several options, whereas the first one is: "Start or install Ubuntu". When I select it Ubuntu boots up from the CD. The other two Partitions I got are for Windows. The one 12bg is Windows and programs, the other large one is for games, music and films etc. I don't want to delete those.

The instructions you gave me earlier was not english to me.. :confused:

---

### Post by urk_nono on 2006-12-13
YES! Somehow I managed to get into Edgy!

When I booted up my comp and tried to enter Ubuntu from the dual-boot window it read as usual. 

What I did, I entered command-line by pressing "c" over the Ubuntu-OS and entered:

root (hd0,5)
setup (hd0,5)

instead of reboot, I simply pressed "esc" and pushed "enter" over the Ubuntu OS and frigging YES!

Now I don't dare rebooting...

---

### Post by bodhi.zazen on 2006-12-13
Hey urk_nono, good to see your are back !

Hey, and look at you go !

Open a terminal for us and post the output of:```
sudo fdisk -l
```

and also, if you will, the contents of /boot/grub/menu.lst

My guess is all you need to do is open a terminal and type:```
sudo grub
```

You will get a grub prompt.

I think:```
root (hd0,5)
setup (hd0)
quit
```Will solve your problems, but i would like to see the above information to confirm that ;)

---

### Post by urk_nono on 2006-12-13
Hey, and thanks for caring, really appreciate it!

**fdisk -l**

Disk /dev/sda: 160.0 GB, 160041885696 bytes
102 heads, 51 sectors/track, 60088 cylinders
Units = cylinders of 5202 * 512 = 2663424 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4838    12583612+   7  HPFS/NTFS
/dev/sda2            4839       55633   132117795    f  W95 Ext'd (LBA)
/dev/sda5            4839       51601   121630537+   7  HPFS/NTFS
/dev/sda6           51602       55633    10487206+  83  Linux


What I think I did wrong was that when I wanted to change my dual-boot background image, I didn't jot in the right partition in my menu.lst. I corrected it and now it works fine, even when rebooting, yuppie! :mrgreen:

Don't think I'll be messing about with it any further, until my next project comes up..

---

