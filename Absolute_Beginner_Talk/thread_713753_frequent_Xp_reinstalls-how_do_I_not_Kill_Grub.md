---
title: "frequent Xp reinstalls-how do I not Kill Grub?"
date: 2008-03-03
forum: Absolute Beginner Talk
---

### Post by regbsn on 2008-03-03
I reinstall Windows XP every several months when XP gets sluggish from installing and uninstalling trial and other programs. I try out new things on this laptop before touching my family's computers.
I was wondering if there is a way to continue with this practice without killing grub and having to repair it every time.

I have XP Home on a 7G part and 12g to use for Ubuntu. I don't know how to do this with the 4 partition limit as I want a separate "/ home" partition. I don't understand "extended" and "logical" partitions in relation to "primary" partitions.

---

### Post by zxscooby on 2008-03-03
You can put grub on its own partition.
that will keep windoze from wiping it. 
[http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_Grub_Partition_](http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_Grub_Partition_)

---

### Post by regbsn on 2008-03-03
How do I handle the 4 partition rule?

XP           = Primary Partition (NTFS)
"/"           = ??????? partition (ext3)
"/ home" = ??????? partition (ext3) - also shared data by using the ext2|something.exe install on XP partition
"L Swap  = ??????? partition (????)
GRUB      = ??????? partition (????)

Please help me understand!

---

### Post by chochem on 2008-03-03
Instead of reinstalling windows (which will overwrite the Master Boot Record) just use some imaging software to make an image of a new Windows install. Then when you need to 'go back' you just use the same imaging program to reestablish the windows partition the way it was. [Acronis True Image]("http://en.wikipedia.org/wiki/Acronis_True_Image") workd very well for me and allows you to reestablish the partition with or without reestablishing the master boot record.

And you don't need to make the /home patition a primary partition. Use the partition editor to make it an extended/logical partition.

---

### Post by regbsn on 2008-03-03
So by making an image of my XP partition with True Image, I can "restore" my eventually bloated XP and XP registry to the image by overwriting with the True Image XP image I made. (Does that make since?:))

If I use the Partition Editor to make "/ home" an extended or logical partition, will it's data still be safe if i do a freah install of 8.04 when it comes out?

PS...where is the partition editor?

---

### Post by chochem on 2008-03-03
Uhm I'm not sure I understand your question perfectly, but what a program like Acronis TrueImage (or Norton Ghost or the open source G4L) does, is to build a file that shows exactly what your windows (or linux) partition looked like at the time. That file you store somewhere, on another partition or an external harddrive or a usb pendrive, somewhere anywhere. Whenever you want to you can tell the program to restore the partition in the file.  This will then delete your current windows partition (make sure to backup anything important....) and reestablish the partition the way it was when you build the image file.

The advantage here (apart from time saving since it's faster than installing) is that restoring the windows partition will not overwrite the MBR (which is where grub is by default) and so no more grub reinstall.

If you do want to give grub a separate partition, you're quite right, that you're only allowed four primary partitions. I don't know for sure exactly what partitions need and which do not need to be primary but the /home one does not. So depending on where you are in the process (do you already have a /home directory filled with files? or are you about to install ubuntu and want to know how to go ahead beforehand?) you could choose to have your /home partition as an extended-logical partition.

The partition editor is included in the Live CD so if you're about to install, you will come acros it as part of the install. Otherwise it can be installed by 
sudo apt-get install gparted
But beware: If your home partition is already in existence and a primary partition you can't convert it to an extended one, except by copying the contents somewhere else, deleting it and subsequently making a new one (using the partition editor).

---

### Post by regbsn on 2008-03-03
G4L open source partition imager sounds like a viable option.

The only other question I have is if the "/ home is on an extended-logical drive, can I still wipe the "/" partition and do a fresh install to upgrade Ubunto or if i mess up and need to re-install it?

---

### Post by chochem on 2008-03-03
G4L soesn't appear to be in the repos but Partimage (which does the same thing) is, so you could backup your windows partition from your ubuntu partition (otherwise you'ld need to use a livecd, like [the system rescue cd]("http://www.sysresccd.org/")) 

Uhm if I understand you correctly, you're asking if deleting/formatting your root partition would delete your home partition, given that the home directory wouldn't actually be on the root partition. And I can safely say that it wouldn't, so it would be perfectly safe to do a clean install (and have that mount your home partition, same as the old install).

---

### Post by stchman on 2008-03-03
> **regbsn said:**
> I reinstall Windows XP every several months when XP gets sluggish from installing and uninstalling trial and other programs. I try out new things on this laptop before touching my family's computers.
I was wondering if there is a way to continue with this practice without killing grub and having to repair it every time.

I have XP Home on a 7G part and 12g to use for Ubuntu. I don't know how to do this with the 4 partition limit as I want a separate "/ home" partition. I don't understand "extended" and "logical" partitions in relation to "primary" partitions.

I know XP can kind of suck, but every few months?!??!!!  I recommend that on your XP install run your user as a limited account and have an administrator account.  Avoid installing and uninstalling programs for the heck of it as well.

---

