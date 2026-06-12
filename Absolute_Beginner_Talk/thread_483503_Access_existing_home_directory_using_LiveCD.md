---
title: "Access existing home directory using LiveCD?"
date: 2007-06-24
forum: Absolute Beginner Talk
---

### Post by Hammock on 2007-06-24
Hi all, 

I just had my upgrade from Edgy to Feisty go bad-- after receiving an error message, the upgrade just hung.  After restarting the machine, I can no longer boot into Kubuntu.  

The problem is, I have some files in my home directory which I *should* have backed up before the upgrade.  Now, I need to get them off the machine before I reinstall Kubuntu.

Is it possible to boot into Kubuntu using the LiveCD, and mount the home directory on my hard drive, mount a USB hard drive and then copy the files from the home directory to the external drive?  

I tried, but was unable to get out of the LiveCD sandbox.  

Thanks in advance for your help!

-Andy.

---

### Post by Nekiruhs on 2007-06-24
I assume you know what partition your home directory is on?  The name of it I mean, it should be something like /dev/hda or /dev/sda or /dev/hdb1 or/dev/sdb2 etc. Then open up a terminal on the Live CD and type ```
sudo mount -t ext3 PartitionName /media/old
``` Then just use Nautilus (or Konqueror if you use Kubuntu) to navigate to /media/old. Your looking at the contents of the partition your home is on. Just go to your home folder and copy the stuff you want.

---

### Post by Hammock on 2007-06-25
Thank you for getting me on track, Nekiruhs.  After working with your suggestion for a while, I was ultimately unable to mount the partition because the device seems to lack a valid filesystem superblock.  So now I am pursuing that issue.  Hopefully it will all turn out alright! 

-Andy.

---

### Post by Nekiruhs on 2007-06-25
Are you sure that you got the Partition name right? If you have an IDE HD it should be like hda1 or hda2 or hda3. If you have SATA HD its sda1, sda2, or sda3. Thats normally. Is the drive ext3? fat32?
If you got that right. From the Live CD try running ```
sudo fsck -t ext3 PartitionName
``` Where partition name is hda1-hda3 or sda1-sda3.

---

### Post by Hammock on 2007-06-25
I did have the name wrong! 

It turned out to be hda5 (I have Kubuntu Edgy Eft set up in a dual boot system with XP Home on a Dell 700M laptop-- I should have mentioned this at the start).  

After I figured this out, I was able to rescue the files I was worried about using your syntax above.

Now that I have recovered my data, I am tempted to try to repair my Edgy installation since it currently will not boot.  However, I suspect that it would be simpler to just install Feisty fresh.

Thank you again for your guidance!

-Andy.

---

