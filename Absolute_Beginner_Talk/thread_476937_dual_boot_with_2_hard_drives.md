---
title: "dual boot with 2 hard drives?"
date: 2007-06-17
forum: Absolute Beginner Talk
---

### Post by stonerrob420 on 2007-06-17
I've got ubuntu dapper installed on a 80 GB western digital HD and knoppix 5.1.1 installed on a 12 GB hardrive. Can I setup grub up to make them dual boot off one or the other of the drives? I have grown tired of switching the IDE cable back and forth to boot which OS I want to work with. Any help would be much appreciated. :p

---

### Post by Sonofmoog on 2007-06-17
Look into BootItNG.  It's not free, but for the price you get a shareware Partition Magic, Norton Ghost, *and the bootloader*  I wouldn't be without it.  Google BootItNG and Terabytes for the webpage, if interested.

---

### Post by w4ett on 2007-06-17
Sure can...grub will do this for you....I have a dual boot, 2 HDD system...XP and Ubuntu.

---

### Post by stonerrob420 on 2007-06-17
I've looked at alot of pages and none of them clearly explain how to edit the grub to make dual boot from 2 HDs. They are all linux and windows dual boot not linux and linux dual boot like I'm wanting to do. My setup is liteon dvd burner "primary master" western digital 80 GB HD "secondary master" and quantum bigfoot 12 GB HD "primary slave". ubuntu dapper is installed on the secondary master 80 GB HD and knoppix 5.1.1 on the primary slave.

---

### Post by freebird54 on 2007-06-17
It doesn't matter which way you go - but choose one to be your 'master boot'  then follow the Grub directions from this page:  [http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

Everything you'll need to know is in there!  Item 9 is a good place to start... :)

---

### Post by stonerrob420 on 2007-06-19
I followed the instructions on that page but things didn't turn out too good.......my computer will not boot it freezes right before the grub menu comes up...I've got the menu.1st file backed up in a file on the desktop to restore just in case something went wrong it but I can't mount the hardrive running from the live cd...If I could mount the drive fixing it would be pretty simple. I tried super grub but that didn't work. So how am I going to get out of this situation? anybody got any ideas?

---

### Post by Sonofmoog on 2007-06-19
> **stonerrob420 said:**
> I followed the instructions on that page but things didn't turn out too good.......my computer will not boot it freezes right before the grub menu comes up...I've got the menu.1st file backed up in a file on the desktop to restore just in case something went wrong it but I can't mount the hardrive running from the live cd...If I could mount the drive fixing it would be pretty simple. I tried super grub but that didn't work. So how am I going to get out of this situation? anybody got any ideas?

Just one:  you have the wrong *active *partition.  Your situation sounds similar to my experience.  There are any number of tools that will tell you which is your active partition, both Linux and Windows.  You need the answer to three questions, four actually:

1) Which is your active partition?
2) Where is root mounted?
3) Where is GRUB installed?

and, the most important of all,

4) are the answers to 1-3 above *the same?*

---

### Post by stonerrob420 on 2007-06-19
Here my fdisk -l output from the terminal.

 ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1        9541    76638051   83  Linux
/dev/hdc2            9542        9729     1510110    5  Extended
/dev/hdc5            9542        9729     1510078+  82  Linux swap / Solaris

 Where do I go from here? I removed the HD with knoppix.
 
 How do I go about mounting the drive to get access to it?

---

### Post by Sonofmoog on 2007-06-19
From the output of your fdisk command, it appears my earlier suggestion was worthless.  It appears you have one primary partition mounted on / and a swap file.  If that's the case, it seems unlikely that GRUB is not installed properly.  

There is a way to boot from a LiveCD, then transfer to a Linux system on the hard drive, as if you had booted from it originally, but advising you how to do this is beyond my expertise, I'm afraid.

---

### Post by stonerrob420 on 2007-06-19
Would you have any idea if I could edit /etc/fstab to make the disk mount?

---

### Post by Sonofmoog on 2007-06-19
> **stonerrob420 said:**
> Would you have any idea if I could edit /etc/fstab to make the disk mount?

I don't recommend that.  You might try mounting the disk while running the LiveCD.  Create a mount point, then issue the command 

mount /dev/hdc1 /<mount point>

If you can't mount the drive from the command line, nothing you do in /etc/fstab is going to help, and trying will likely cause more ills than it cures.

---

### Post by stonerrob420 on 2007-06-20
Here's what I get when I try to mount with that command.

 ubuntu@ubuntu:~$ sudo mount /dev/hdc1 /root
mount: wrong fs type, bad option, bad superblock on /dev/hdc1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
 
 exactly what does that mean? Can it be fixed?

---

### Post by Sonofmoog on 2007-06-20
My bad ..

Try mount -t ext /dev/hdc1 /root

and, do man mount before that to become familiar with the switches and options of using mount.  Sorry 'bout that, but I'm a bit of a newbie myself, and just now it's showing ..

---

### Post by stonerrob420 on 2007-06-20
OK here it is : 

 ubuntu@ubuntu:~$ mount -t ext /dev/hdc1 /root
 mount: only root can do that


 Here it is with sudo:

 ubuntu@ubuntu:~$ sudo mount -t ext /dev/hdc1 /root
 mount: unknown filesystem type 'ext'

 Then here it is done differently: 

 ubuntu@ubuntu:~$ sudo  mount -t ext3 /dev/hdc1 /root
 mount: wrong fs type, bad option, bad superblock on /dev/hdc1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
 
 I am trying to do it different ways none of them seem to work.....

---

### Post by Sonofmoog on 2007-06-21
> **stonerrob420 said:**
>  I am trying to do it different ways none of them seem to work.....

I'm sorry, but this is beyond my limited abilities.  My best advice at this point is to google for help at [http://www.google.com/linux]("http://www.google.com/linux")

You might also look into booting the LiveCD in Rescue mode.

Good luck, and sorry I couldn't be more help ..

---

### Post by stonerrob420 on 2007-06-24
I found a solution to my problem. I just formatted the HD and installed feisty. I can get most of what had after a few weeks of downloading......easy come easy go.....lol....thanks for the help.

---

### Post by RealG187 on 2007-06-24
I used to tri boot. On HD had WinXP and the other had Ubuntu and Win 98. You can just use your BIOS to pick the drive that has the Operating System(s) you wanna boot. 
If I wanted XP I coud booth IDE0, if Ubutnu IDE1 and wait, if I wanted 98 IDE2 and select 98 at grub before it started Ubuntu..

---

