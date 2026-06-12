---
title: "I'm going to re-install the latest Ubuntu"
date: 2007-12-02
forum: Absolute Beginner Talk
---

### Post by dhar2112 on 2007-12-02
I have XP running on a previously partioned hard drive.  I just simply want to install Ubuntu over the current installed copy (as posted earlier, I think I have a corrupt copy).  I downloaded and burned a new ISO (which I'm using now as a Live CD).  I did a Checksum and checked the CD for defects, so it appears I have a very clean, non-corrupt copy.  So, I still want the ability to dual boot into XP, but this time I would like to have a smaller partition for Ubuntu.  When I'm installing it and prompted to select an option, I assume I want the first option, which is the guided partition with the slider to select partition size.  Correct?  Does this automatically detect the existing Windows partition and will I still have the dual boot option?  Thanks for the assistance!

---

### Post by candtalan on 2007-12-03
> **dhar2112 said:**
> I have XP running on a previously partioned hard drive.  I just simply want to install Ubuntu over the current installed copy (as posted earlier, I think I have a corrupt copy).  I downloaded and burned a new ISO (which I'm using now as a Live CD).  I did a Checksum and checked the CD for defects, so it appears I have a very clean, non-corrupt copy.  So, I still want the ability to dual boot into XP, but this time I would like to have a smaller partition for Ubuntu.  When I'm installing it and prompted to select an option, I assume I want the first option, which is the guided partition with the slider to select partition size.  Correct?  Does this automatically detect the existing Windows partition and will I still have the dual boot option?  Thanks for the assistance!

(Having got a good CD - have you given it a self check in the cd drive in the target machine - this will verify that the drive will read the good cd ok?)

Install: It is not exactly straightforward here. if you try to use the automatic installer in ubuntu it will not go into an existing used partition, but it will try to resize  something and things might not work, you may get a mess. So do not use the automatic method without more advice and care.

Note that you have a dual boot machine already. This means that you are using the ubuntu (partition) as part of the boot up process - the boot manager in addition to the MBR which now points to the boot manager in ubuntu.

What you want to get is not difficult, but can be achieved in several stages though. It depends what you think is easiest for you  with what you know.

Part of the complication comes because you want to re size partitions. This is best done initially I guess. My approach would be to use a live CD for partitioning such as parted magic or gparted, they are small to download, and have a good gui. You could maybe aim to resize the linux partitions - this is probably within an extended partition at the end of the drive. I am not sure though if it is possible to resize an extended partition which contains existing logical partitions.

If you delete the linux partitions and then immediately try to run windows, then windows will not boot up unless you repair (reset) the MBR using mbrfix dos command which can be done various ways.

However, if you first delete the linux partitions using parted magic, and, still using the parted magic live cd, then resize the windows partition, then leave the unpartitioned space on the drive without making any partition at all, just leave space, then the ubuntu live CD installer will give the easy option of 'Install into largest uncommitted space on the drive'. This is  then all automatic, and it will continue to give you a dual boot machine.
hth

---

### Post by mikewhatever on 2007-12-03
> **dhar2112 said:**
> I have XP running on a previously partioned hard drive.  I just simply want to install Ubuntu over the current installed copy (as posted earlier, I think I have a corrupt copy).  I downloaded and burned a new ISO (which I'm using now as a Live CD).  I did a Checksum and checked the CD for defects, so it appears I have a very clean, non-corrupt copy.  So, I still want the ability to dual boot into XP, but this time I would like to have a smaller partition for Ubuntu.  When I'm installing it and prompted to select an option, I assume I want the first option, which is the guided partition with the slider to select partition size.  Correct?  Does this automatically detect the existing Windows partition and will I still have the dual boot option?  Thanks for the assistance!

By the latest Ubuntu, I hope you mean Gutsy Gibbon, because the very latest alpha release is yet far far away from the final product.
Do not choose the guided option. I would only shrink one of the existing partitions and once again create a pair of root and swap. You have to manually edit your partitions this time.

---

### Post by dadawan on 2007-12-03
dhar,
   
   They are right, you have to be careful here.   Your Grub boot loader references files in your Linux partition, you don't want to nuke it or your machine will not boot from the hard drive any more.

  Here is what I would do.

1.) Make sure you Ubuntu live CD will boot and get all the way to the desktop succesfully.

2.) Remove Grub from your Master  Boot Record:
[Here is a typical link on how to do that.]("http://www.wikihow.com/Uninstall-the-Grub-Bootloader-from-a-Dual-Boot-XP-System-With-an-XP-CD")

3.) Make sure Windows boots ok now.

4.)  Boot the Ubuntu Live CD and run the Partition Editor from the System:Administration menu.

5.)  Delete and reallocate your Linux parition.

6.)  Install Ubuntu, and choose manual when you must choose about partitions.

  I have some [tutorials]("http://www.bornthree.com/HowTo/Gutsy2ndDriveInstall/Dell2ndHardDriveInstallPart2.html") on my site on how to do this if you are an absolute beginner, but it sounds like you are advanced enough to make the partitions without step-by-step guidance.  

Hope that it works out for you,
-Kevin

---

