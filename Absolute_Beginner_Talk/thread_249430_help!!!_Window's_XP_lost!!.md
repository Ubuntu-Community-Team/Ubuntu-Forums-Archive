---
title: "help!!! Window's XP lost!!"
date: 2006-09-02
forum: Absolute Beginner Talk
---

### Post by dal2k5 on 2006-09-02
:sad: :sad: :sad: :sad: :sad: plez help i go to the grub screen were u can pick ur OS and window's is not there... plez somone help me..:sad: :sad:

---

### Post by dal2k5 on 2006-09-02
ppl plez help me!!

---

### Post by bastiegast on 2006-09-02
You will need to add your XP installation manually to grub, you can do this by editing you grub configuration:

[INDENT]gedit /boot/grub/menu.lst[/INDENT]

The following works for me:

title		Microsoft Windows XP Professional
root		(hd2,0)
savedefault
makeactive
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1

You should change the two's and zero's to respectively the number of the hard drive and the partition you windows installation is on. However there are plenty of howtos for dual booting XP and Ubuntu, just search google.

---

### Post by insane_alien on 2006-09-02
1. check hda1. if XP isn't there then you'll have to reinstall.
2.check your menu file.
3. learn to type in proper english
4. have some patience man.

---

### Post by HAARP on 2006-09-02
Is there an icon with your Windows disk on the desktop?

---

### Post by bastiegast on 2006-09-02
> Is there an icon with your Windows disk on the desktop?

If its properly detected and mounted by you ubuntu installation there should be.

---

### Post by dal2k5 on 2006-09-02
> **bastiegast said:**
> If its properly detected and mounted by you ubuntu installation there should be.
ummm no...... and i tryed to add window's to the grub menu and this happened
[http://i67.photobucket.com/albums/h314/geexo777/grub.png](http://i67.photobucket.com/albums/h314/geexo777/grub.png)

---

### Post by phansiizwe on 2006-09-02
You need to edit the file as root.

From a terminal run:

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
```

In order to make a backup of your file (just to be certain), then:

```
sudo gedit /boot/grub/menu.lst
```

and try to edit and save the file again.

---

### Post by annda on 2006-09-02
two questions though before you edit grub configuration: are you SURE you haven't told the ubuntu installer to use the whole disk for partitioning? in that case, windows is gone.

if you haven't, you need to know what disk/partition it was on. if you had only one unpartitioned drive before (only c: ), you will need to write hd0,0 not hd2,0 to menu.lst

good luck!

---

### Post by nero2150 on 2006-09-02
The correct line would be

sudo gedit /boot/grub/menu.lst 
It will ask for password
and enter something like that

title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

At the bottom of file you can move it where you want to anyway
[COLOR="Red"]but backup your menu.lst first before any change you can save the file like
menubak.lst with sudo gedit if you want to[/COLOR]

---

### Post by catlett on 2006-09-02
First of all, just because you do not have windows in the grub menu doesn't mean windows isn't there.
First use gparted to see your partitions. It is located under System<Administration<Gnome Partition Editor. If it isn't there, just install it with this command. ```
sudo apt-get install gparted
``` When you go into gparted your hard drive will be displayed as a bar graph. Look for an ntfs partition.
You can use gparted to find the windows partition or enter this command to list your partitions. Actuallt copy/paste the reply to this command and we'll get you the grub entry and we'lll mount windows from the terminal so you cxan browse the partition and make sure your files are there. Enter ```
sudo fdisk -l
```Post the reply.

---

### Post by dal2k5 on 2006-09-02
here's wat i got

Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       18748   150593278+  83  Linux
/dev/sda2           29694       30401     5687010    5  Extended
/dev/sda3   *       18749       29693    87915712+  83  Linux
/dev/sda5           30048       30401     2843473+  82  Linux swap / Solaris/dev/sda6           29694       30047     2843442   82  Linux swap / Solaris

---

### Post by catlett on 2006-09-02
Is that all that sudo fdisk -l returned? Was there any other drive listed? Do you have more than one drive?
I am asking because the drive /dev/sda that is listed by fdisk does not have windows XP on it. It only has linux partitions. It has your ubuntu install om /dev/sda3, your swap is a logical partition /dev/sda5 inside of the extended partition /dev/sda2 and there is a partition formatted at /dev/sda1 with a linux style filesystem ext3 BUT there isn't a partition for XP. It would have been listed as  HPFS/NTFS or as  W95 FAT32 (LBA)


Do you know for sure you only have 1 hard drive

---

### Post by dal2k5 on 2006-09-02
> **catlett said:**
> Is that all that sudo fdisk -l returned? Was there any other drive listed? Do you have more than one drive?
I am asking because the drive /dev/sda that is listed by fdisk does not have windows XP on it. It only has linux partitions. It has your ubuntu install om /dev/sda3, your swap is a logical partition /dev/sda5 inside of the extended partition /dev/sda2 and there is a partition formatted at /dev/sda1 with a linux style filesystem ext3 BUT there isn't a partition for XP. It would have been listed as  HPFS/NTFS or as  W95 FAT32 (LBA)


Do you know for sure you only have 1 hard drive
maybe i have more wat do i do to check the other one??

---

### Post by catlett on 2006-09-02
sda is a sata drive's label. It also is a label for external drives. So do you know what type of drive you have?
The easiest way is to go to  the top panel and enter into System<Administration<Disks. It will ask for a password, just enter the one you log in with. When it opens, it will have icons for your hard drives on the left. When you select one , it will have 2 tabs on the right. One for properties and one for partitions. 
The obvious would be if there is only one icon on the left. If you have more than one, select a drive and then select the partitiopns tab. What you will be looking for is a partition with the filesystem listed as "windows" ntfs. If you find a partition like that, your windows install is there. If you do not, I am afraid you chose the installation method that gives the entire hard drive to ubuntu and the drive was formatted during the install and formatting erases all data on the drive.

---

### Post by ddeen on 2006-09-02
Assuming WinXP is still there somewhere, you could boot the winXP install cd and chose the recovery option.  Then when you get to c:\windows or where ever your install is then type "fixmbr"

That should get rid of grub and restore your WinXP booting, but if you installed Ubuntu on top of WinXP your out of luck unless you did a full backup with the floppy recovery disk.

Duane

---

### Post by dal2k5 on 2006-09-02
i think itz gone(windows) how do i get it back??

---

### Post by dal2k5 on 2006-09-02
> **ddeen said:**
> Assuming WinXP is still there somewhere, you could boot the winXP install cd and chose the recovery option.  Then when you get to c:\windows or where ever your install is then type "fixmbr"

That should get rid of grub and restore your WinXP booting, but if you installed Ubuntu on top of WinXP your out of luck unless you did a full backup with the floppy recovery disk.

Duane okay thnx

---

### Post by catlett on 2006-09-02
Are you experienced with computers. I only ask because this is a bit advanced . If you are adept at windows you will be alright but if you are not you might want to ask someone you know for help.
This ocurred in another thread. It was similar but not exactly the same. What I am hoping is that your /dev/sda1 partition that is not part of your install is XP reformatted but not overwritten with ubujntu.
Anyways the other poster had luck with this [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk) His reply was this 
> Problem solved! I put the harddrive as slave in my other XP box and managed to recover the whole partion using TestDisk!!! After fixing the partion table and restoring the MBR I just put the drive back in its computer and booted right back into the old installation ^
The thread is here. [http://www.ubuntuforums.org/showthread.php?t=226836](http://www.ubuntuforums.org/showthread.php?t=226836) I did nothing to help so do not bother reading my replies. Azz and the original poster _a are the 2 you want to read.

There might be other options. If you are confident in your abilities then proceed if not, find someone who can work on this with you. You ned another computer to put this drive in as slave and the software ti run the recovery. 
How valuable is the data. Because your other option is to reinstall XP from your recovery disks (or the xp installation disk, which ever one you have), but if you have critical data you will not get it back with reinstaling, you would just have a fresh install of XP without any of your personal data.

---

### Post by dal2k5 on 2006-09-02
oh well look's like i'm stuck wit linux....better get used to it lol

---

### Post by halitech on 2006-09-03
dal2k5, being "stuck" with Linux isn't neccessarily a bad thing :) think about what you've lost, virii, adware, blue screens of death, paying for upgrades, and the list goes on :)

on a more serious note, good luck, don't be afraid to ask questions and learn new things with it :(

---

### Post by dal2k5 on 2006-09-03
ya i got flash and java games working for my sis and wine for halo for my older bro it feel's like windows but 10x better!!!!!!

VIVA LA LINUX!!!!:D :D :D :D

---

### Post by catlett on 2006-09-03
If you have ubuntu (I assume you do but there is xubuntu and kubuntu) there is the Dapper Guide to help you configure multimedia etc [http://doc.gwos.org/index.php/DapperGuide](http://doc.gwos.org/index.php/DapperGuide)
Or if you have trouble, there is a script that installs just about everything you need,  it is Automatix. It use to have a forum here at ubuntu forums but it has grown so much it has it's own site now. [http://getautomatix.com/wiki/index.php?title=Installation&Itemid=38](http://getautomatix.com/wiki/index.php?title=Installation&Itemid=38)

I set up a dual boot in the beginning because I thought I wouldn't be able to do "everything" with linux. I would boot into XP but after a couple of months I never went back in. You'll hate how limited you are in windows once you understand what you can do in linux.
Well sounds like you have been bitten by the bug as it is :-D  There is something gratifying about setting up your system, your way. Take care.

---

