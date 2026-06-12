---
title: "I wiped my HDD with fdisk.. did I mess up?"
date: 2014-09-30
forum: Any Other OS
---

### Post by sebastian28 on 2014-09-30
Hey everyone

I just got a brand new acer laptop today and it came with Linpus Linus installed. I want to have windows on it and I read on Microsoft's site that in order to install windows, you're first supposed to delete your linux partitions with fdisk.. so I ran fdisk and found out that all of my harddisk's 1TB was on dev/sda.. I put "d" for delete in the command promt and it said something like "device 1 selected".. then I put in "w" in the commans prompt as per the instructions on MS's page.. then I reboot my laptop and I get a "No bootable device screen"... even though I am positive that I have both a bootable CD and a bootable flash disk drive both with windows 7 on them.. no matter how much I keep restarting it, no matter how much I keep going in  bios changing around the boot priorities, I just get that "no bootable device screen"

i know this is not really ubuntu-related but it's linux and I really don't know where else to turn for help.. ans I don't want to send it back if it's something that's fixable and I'm just mssing..

did I mess up by clearing my /dev/sda ?.. can I fix it?.. any help would be apreciated greatly

I'm really freaking out righg now that I may have thrown 700 dollars out the window.. thanks in advance for all the answers :)

---

### Post by nerdtron on 2014-09-30
> so I ran fdisk and found out that all of my harddisk's 1TB was on  dev/sda.. I put "d" for delete in the command promt and it said  something like "device 1 selected".. then I put in "w" in the commans  prompt as per the instructions on MS's page.. then I reboot my laptop  and I get a "No bootable device screen"

You did not messed out. Actually that command completely wiped out the /dev/sda (if that really is the internal hard drive, and not any other usb device)

Anyway, fdisk won't destroy a hard drive (physically) so there's a good chance that you can still install OS on this computer. What is the model of this laptop anyway?

To be sure that you have a bootable media, try booting your USB drive using another computer, just to double check.

---

### Post by Bucky Ball on 2014-09-30
*Thread moved to **Other Operating Systems and Projects**.*

Not a Ubuntu support request. No, you haven't thrown $700 out the window. Sounds like you've wiped the drive and can't install Windows, that's all. Good luck.

You might try booting from a Ubuntu LiveDVD/USB, launching Gparted and creating an NTFS partition on the disk. Windows might like that and behave itself.

---

### Post by yancek on 2014-09-30
I could understand if you had windows already installed and deleted the Linux partition that you would not be able to boot either.  That's because most of the boot files required are on the partition which you deleted, expected behavior.  It doesn't make any sense that a CD/DVD or flash drive would not boot because they would not be accessing the hard drive.  Have you tested the windows CD/flash on another computer to verify that they boot?  Are you sure you saved the changes in the boot priority in the BIOS?  On the Acer I have, you need to tap the F2 key to get into "setup" where you can change this.  Not sure that is the case with every Acer computer.

If you still can't get it to work and since you've already deleted linpux (a good decision) and have nothing on the computer so nothing to lose, you can run the command below from any Linux Live medium from a terminal and it will remove the boot code and partition table from the mbr.  

> dd if=/dev/zero of=/dev/hda bs=512 count=1

---

### Post by UltimateCat on 2014-09-30
A brand new Windows set of disk's for an operating system is expensive isn't it? (I would imagine)

Linux is free sebastian28 -
-:-Maybe considering a fresh installation of Ubuntu on your new machine-:-;)
[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

---

### Post by PondPuppy on 2014-10-01
I don't have an Acer, but on one netbook I have to keep pressing "esc" while powering up in order to boot from a thumb drive. I read that for some Acer laptops you press F12 during power-up to get a "one-time boot menu".

---

### Post by mips on 2014-10-02
Laptop make & model?

---

