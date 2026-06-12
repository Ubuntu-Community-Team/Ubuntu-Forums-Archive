---
title: "Unable to Boot Windows"
date: 2008-04-08
forum: Absolute Beginner Talk
---

### Post by Dragonlaw on 2008-04-08
Hello, I'm sorry about asking this but I need to because my family members want to use windows XP very badly. 

The problem is that after I used the option to partition entire disk on Ubuntu's Live CD, I am unable to boot up to windows. When I boot up the computer, it will launch Ubuntu automatically. When I press Esc on the Grub menu, I only see the options to boot Ubuntu, ubuntu in safe mode or to check memory. There isn't the option of booting up windows!

But when I check the hard disk there is sdb! When I set the boot menu to run it first, it is unable to run.

I don't want to uninstall Ubuntu, I just want the option to dual boot.

Is there anything i can do?

---

### Post by Zralou on 2008-04-08
When you say "option to partition entire disk", is this the hard drive that windows was installed on?.

Sara Lou

---

### Post by philinux on 2008-04-08
Open a terminal and post the output of.

cat /etc/fstab

---

### Post by Dragonlaw on 2008-04-08
Yes it is. There's a sda and sdb partition now.

---

### Post by Dragonlaw on 2008-04-08
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=0234d0a1-9212-4c1d-9307-7b3e94d8672f /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=10288ef7-d8dc-4a14-a66e-f9f0b703b948 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
justin@justin-desktop:~$

---

### Post by philinux on 2008-04-08
Copy and paste this and post back the output. thats a lower case L at the end.

sudo fdisk -l

---

### Post by HereInOz on 2008-04-08
Sorry old fella, by partitioning the entire hard disk, I reckon you would have totally wiped Windows XP.  

I cannot explain the sdb without further information, but if you partitioned the entire hard disk, which was the one which contained Windows, then your Windows installation is probably gone.

---

### Post by Dragonlaw on 2008-04-08
Philinux  it says this


Disk /dev/sda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x04260425

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9930    79762693+  83  Linux
/dev/sda2            9931       10011      650632+   5  Extended
/dev/sda5            9931       10011      650601   82  Linux swap / Solaris
justin@justin-desktop:~$

---

### Post by kolisikepu on 2008-04-08
> **Dragonlaw said:**
> Philinux  it says this


Disk /dev/sda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x04260425

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9930    79762693+  83  Linux
/dev/sda2            9931       10011      650632+   5  Extended
/dev/sda5            9931       10011      650601   82  Linux swap / Solaris
justin@justin-desktop:~$

Oh oooh... I don't see a Windows partition anywhere in this output.  Where is sdb as mentioned?

---

### Post by Dragonlaw on 2008-04-08
It appears when I reinstalled Ubuntu and was repartitioning the hard disk again? 

Then the option to repartition sda and sdb appeared. 

My desktop has 160gb on its hard disk so I think the other partition is still there?

---

### Post by kolisikepu on 2008-04-08
> **Dragonlaw said:**
> It appears when I reinstalled Ubuntu and was repartitioning the hard disk again? 

Then the option to repartition sda and sdb appeared. 

My desktop has 160gb on its hard disk so I think the other partition is still there?

You'll know if it's still there when Ubuntu can see it and mount it on your desktop.  Can you confirm that?

---

### Post by Boyohazard on 2008-04-08
Ooer, you installed Ubuntu again along with another re-partition?

Sorry mate but it looks like the same mistake I made, Windows is no more.

Did Ubuntu ask you to import Windows users when you installed it?

---

### Post by philinux on 2008-04-08
Before assuming it's wiped tere must be a way to check what's on the other 80 gigs of the hard drive. 

Gparted live cd maybe or testdisk.

---

### Post by kolisikepu on 2008-04-08
> **Dragonlaw said:**
> Hello, I'm sorry about asking this but I need to because my family members want to use windows XP very badly.

Why does the family need to use Windows XP so badly anyways??  Do they need to use the net?  Show them Firefox in Ubuntu.  Do they need to use email?  If possible, Imap email account through Evolution or install Thunderbird and Imap in Thunderbird.

What's in XP that your installation of Ubuntu can't do? :p  Use some selling skills and sell them Ubuntu, so much better than XP.  It took me a while to convince the wife... :lolflag:

---

### Post by Boyohazard on 2008-04-08
> **philinux said:**
> Before assuming it's wiped tere must be a way to check what's on the other 80 gigs of the hard drive. 

Gparted live cd maybe or testdisk.

Good catch didn't notice the 80gig discrepency!

---

### Post by Zralou on 2008-04-08
sda and sdb would denote two hard drives wouldn't it?.

Sara Lou

---

### Post by Dragonlaw on 2008-04-08
I ran testdisk and it said this.

Note: Disk capacity must be correctly detected for a successful recovery.
If a disk listed above has incorrect size, check HD jumper settings, BIOS
detection, and install the latest OS patches and disk drivers.

How do I check the HD jumper settings?

---

### Post by Zralou on 2008-04-08
Is the hard drive IDE or SATA?, if its SATA, I don't think they have jumpers.  If its IDE, next to the IDE ribbon cable there will be a row of pins with a small jumper, somewhere on the hard drive will be a diagram showing which pins need to be jumpered for 'Master', 'Slave" or 'Cable select'.

Sara Lou

---

### Post by Dragonlaw on 2008-04-08
Mine is SATA. When I check the Bios setup i got this

IDE Channel 2 Master [HDS728080PLA380]. This is the one that contains the other 80gb

---

### Post by Zralou on 2008-04-09
Does your computer have one hard drive, or two?

Sara Lou

---

### Post by Dragonlaw on 2008-04-09
It has one.

---

### Post by thebutters on 2008-04-09
The Hard Drive number that you gave us is an Hitachi 80 GB hard drive.  Are you sure that you only have one hard drive and that it is 160 GB?

You might want to check this page out... it appears that this guy did almost the same thing as you.  [I believe you wrote over top of your windows partition.]("http://ecmarchitect.com/archives/2006/07/27/700")

---

### Post by Dragonlaw on 2008-04-10
Ok I will try it out and get back to you. Thank you very much

---

### Post by Dragonlaw on 2008-04-14
I made a mistake. It is 80gb. But I am still unable to get back Windows

---

### Post by Tatty on 2008-04-14
> **Dragonlaw said:**
> I made a mistake. It is 80gb. But I am still unable to get back Windows

Unfortunately it sounds as though you have installed over you windows partition.  Everything that was on your windows drive has been lost.  You will need to re-install windows if you want to use windows.

If there is any valuable data you have lost then there is a -small chance- that you might be able to use a recovery tool to scan your drive for any deleted files which have not yet been overwritten by new data.  I do not know the names of any software which does this, but im sure another poster may be able to help.  The best thing you can do now -if there is data you want to save- is to use your computer a little as possible, as each time you write to the hard drive, it may potentially be writing over the data.

---

