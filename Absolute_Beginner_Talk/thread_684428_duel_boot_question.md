---
title: "duel boot question"
date: 2008-02-01
forum: Absolute Beginner Talk
---

### Post by Roque2 on 2008-02-01
I have windows xp and ubuntu gutsy installed right now on 2 seperate drives. My question is my windows xp o/s is somewhat messed up and I want to delete and reinstall it, will the grub loader still allow the duel boot.

---

### Post by kpkeerthi on 2008-02-01
Using gparted in Ubuntu Live CD (or google gparted live cd) delete your windows partitions. Then [re-install grub]("http://ubuntuforums.org/showthread.php?t=24113") to get rid of windows entry

---

### Post by oedha on 2008-02-01
when you re-install your winblows...it will delete the grub....but not the linux
later on you have to restore the grub to make it dual boot again

~E~

---

### Post by mikeyphi on 2008-02-01
> **Roque2 said:**
> I have windows xp and ubuntu gutsy installed right now on 2 seperate drives. My question is my windows xp o/s is somewhat messed up and I want to delete and reinstall it, will the grub loader still allow the duel boot.

You will have to reset Grub again after you reinstall XP.
Some info here: [https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)

---

### Post by jan quark on 2008-02-01
nice dual-booting documentation site covering many variants of dual boot
[http://apcmag.com/node/5162/](http://apcmag.com/node/5162/)
some reading for your free time :)

---

### Post by Aurora@FleetBuzz on 2008-02-01
If you are using two hard drives, I recommend you disconnect the power cable for the Ubuntu drive and set the windows drive as master.  Then simply re-install XP.  Afterwards, flip flop the drives and set Ubuntu as master, windows as slave.  If there are any grub issues, you can simply edit the file.  There is a wealth of info on the forum on that.

---

### Post by KMW on 2008-02-01
Nice links folks! I'll use them for sure. 

Anyone know of a good link for duel booting on separate drives? Tried it with 7.10 and XP but couldn't get it to work. Both drivers are identical WDs. Tried 7.10 master, XP slave. Tried CS on both drives. Even tried setting boot order in BIOS to CD, 0 then 1.

---

### Post by g7kse on 2008-02-01
I have 2 identical SATA drives one with XP and one with Ubuntu. Ubuntu is set to be the master so when I had to reinstall windows I did exactly as Aurora@FleetBuzz said, disconnect the ubuntu drive and reinstalled windows.

plugged it all back in again and hey presto it worked (at least for a few weeks!)

---

### Post by Aurora@FleetBuzz on 2008-02-01
> **KMW said:**
> 
Anyone know of a good link for duel booting on separate drives? Tried it with 7.10 and XP but couldn't get it to work. Both drivers are identical WDs. Tried 7.10 master, XP slave. Tried CS on both drives. Even tried setting boot order in BIOS to CD, 0 then 1.

Check out these threads.
[http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902)

[http://ubuntuforums.org/showthread.php?p=677880#post677880](http://ubuntuforums.org/showthread.php?p=677880#post677880)

---

### Post by Roque2 on 2008-02-01
when I do in grub find /boot/grub/stage1 it says error. Any reason for that

---

### Post by dstew on 2008-02-01
You need to run "native" grub for the find command to work correctly. I think grub needs to be able to mount the disk to its own file system to do find. If the disk is your root file system, and already mounted, grub can't search it for the file you are looking for. Try it from a Live CD boot.

---

### Post by KMW on 2008-02-02
Wow, just read through all the links on how to do this and I now believe I'm more confused than ever. So many different ways to do this, might need some help sorting this out as I am still "new" to working with the terminal and command lines.

As a precaution I cloned my XP drive so if I hose this up all I'm out is time spent.
Right now I have Gutsy on the master and XP on the slave and I know I have to change GRUB because XP isn't showing up. I am able to access both partitions on the XP drive as it is now.

Want this to boot to Ubuntu 1st and need to change the time to 10 seconds to select OS. Concerned and confused that one of the descriptions states something about problems after updates. Like RONCO, Hoping to set it and forget it! Just not sure which link and directions to use that are going to be easy for a newb like me.

---

### Post by Aurora@FleetBuzz on 2008-02-03
It seems to me that you will need to edit your grub boot loader, which is not difficult.  Since, you want to boot into Ubuntu by default, perhaps it would be best to list the contents of your etc/fstab file first, so's the folks here can give you the exact language in which to use.  I believe the proper command to list the file contents is:
> cat etc/fstab

---

### Post by bumanie on 2008-02-03
> when I do in grub find /boot/grub/stage1 it says error. Any reason for that
Did you enter into the grub shell before typing that command? If not
> sudo grub
then type the command

---

### Post by KMW on 2008-02-03
> **Aurora@FleetBuzz said:**
> It seems to me that you will need to edit your grub boot loader, which is not difficult.  Since, you want to boot into Ubuntu by default, perhaps it would be best to list the contents of your etc/fstab file first, so's the folks here can give you the exact language in which to use.  I believe the proper command to list the file contents is:
See I'm new. Opened terminal and typed in command and received "command ont in desktop" so I'm sure I did it wrong.

---

### Post by dstew on 2008-02-03
The command should be```
cat /etc/fstab
```I can guess that your problem is you have Ubuntu installed, and it boots from the grub menu, but you do not have a Windows choice on your menu. Is that correct?

---

### Post by KMW on 2008-02-04
> **dstew said:**
> The command should be```
cat /etc/fstab
```I can guess that your problem is you have Ubuntu installed, and it boots from the grub menu, but you do not have a Windows choice on your menu. Is that correct?
Sorry for the long delay in getting back.

Yes you are correct. When I boot and grub is loading I press Esc then when the menu comes up I do not have a listing choice for Windows. Though once inside Ubuntu I can access the 2 partitions on the Widows drive.

---

### Post by dstew on 2008-02-04
I think you will need to add an entry for your Windows partition into the grub configuration file **/boot/grub/menu.lst**. From your Ubuntu desktop, open a terminal and enter the command```
sudo fdisk -l
```That will list the partitions that Ubuntu can see in your system, including your Windows partition. Post the result to the forum and I can tell you how to edit your /boot/grub/menu.lst file to get a Windows entry on the menu.

---

### Post by jaybirdUK on 2008-02-04
Reading through this, all the various sites & information regarding getting a dual boot system has totally scared me off.  I tried creating a dual; boot on 2 drives which was a no go, so I decided to try it on a single drive where my Windows already resides.  But upon going into install the partition manager doesn't make it clear which partition is which & I can't run the risk of wiping my Windows with all my work & files on.  Surely there's a way the Ubunto team can make it so the partition manager on install could let us browse the partitions so we know exactly what is what?

---

### Post by Aurora@FleetBuzz on 2008-02-04
Jaybird, dual booting on the same drive is not that hard, but it matters whether you are using Vista or XP.  If you are using Vista, then you will most likely be better off resizing your Window's partition with Vista's partition manager.  If you are using XP, I recommend Gparted.  Here is a link to some videos that I used when I initially set up to dual boot from a single drive.  

[http://www.linux.com/articles/114157](http://www.linux.com/articles/114157)

Note that you will create partitions in which to install Ubuntu out of Gparted.  When  you are actually installing Ubuntu, it gives you the option of doing a manual install.  There are many, many references on how to do this.  Here's one, but there are likely better tutorials for a manual install on this forum.  As you can see, you actually assign the partions to which Ubuntu will be installed.  Do NOT install to an NTFS partition.  That will be Windows!

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by dstew on 2008-02-04
> so I decided to try it on a single drive where my Windows already resides. But upon going into install the partition manager doesn't make it clear which partition is whichThe partitioner tells you which partition is which. Look for the file formats. Any partition which is an NT file system belongs to Windows (NTFS). You should leave these alone, or shrink them if you need to make room for Ubuntu partitions. The Linux partitions are labeled as such, and have ext3 or swap formats. If you want to see what is on a partition, you can look into it. The partitions are shown as disk icons on the Live CD desktop.

---

### Post by KMW on 2008-02-04
> **dstew said:**
> I think you will need to add an entry for your Windows partition into the grub configuration file **/boot/grub/menu.lst**. From your Ubuntu desktop, open a terminal and enter the command```
sudo fdisk -l
```That will list the partitions that Ubuntu can see in your system, including your Windows partition. Post the result to the forum and I can tell you how to edit your /boot/grub/menu.lst file to get a Windows entry on the menu.
Once again still learning. tried to copy and paste but it didn't work.

fdisk shows 2 drives,
Disk /dev/hda: 13.0 GB, 13022324736 bytes
Disk /dev/hdb: 40.0 GB. 40020664320 bytes

Both show drive parameters. Hope this helps before I look really stupid.

Also, should I start a new thread or just continue this one? Don't want to hijack someone else's thread.

---

### Post by dstew on 2008-02-04
MIght be good to start a new thread. And, post **all** the results of the fdisk command. We need to see the details of the partitions.

---

### Post by KMW on 2008-02-05
> **dstew said:**
> MIght be good to start a new thread. And, post **all** the results of the fdisk command. We need to see the details of the partitions.

Thanks again, new thread started. Didn't mean to hijack this on.

---

