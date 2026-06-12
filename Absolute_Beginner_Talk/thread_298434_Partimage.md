---
title: "Partimage"
date: 2006-11-12
forum: Absolute Beginner Talk
---

### Post by Oki on 2006-11-12
I am planning to make a image(backup) of my Ubuntu with Partimage([http://www.partimage.org/Main_Page)](http://www.partimage.org/Main_Page)). Tried to load the SystemRescueCd, but got an error message. So now I will try this guide: [http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)

In the guide it stands 
“Keep in mind--the partition to be backed up should not be mounted. The partition you're backing up to should be mounted, though.” But what should I do when all my disk gets mounted by the Live cd?

And; is it possible to run this program when booting Ubuntu; and if no, why?

As always; thanks for your help:-)

---

### Post by jd65pl on 2006-11-12
```
sudo mkdir /mnt/ubuntu
sudo mount /dev/hda1/ /mnt/ubuntu/
```

Substitute hda1for the position of your ubuntu install

---

### Post by djsroknrol on 2006-11-12
> **Oki said:**
> I am planning to make a image(backup) of my Ubuntu with Partimage([http://www.partimage.org/Main_Page)](http://www.partimage.org/Main_Page)). Tried to load the SystemRescueCd, but got an error message. So now I will try this guide: [http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)

In the guide it stands 
“Keep in mind--the partition to be backed up should not be mounted. The partition you're backing up to should be mounted, though.” But what should I do when all my disk gets mounted by the Live cd?

And; is it possible to run this program when booting Ubuntu; and if no, why?

As always; thanks for your help:-)

That's odd...it didn't mount my HD's when I do it...maybe because I'm running my trusty Breezy live CD when I do it?...

No matter..just unmount the drive with the image you're making is all...
In answer to your question, you're booting the drive with the image, so naturally it wouldn't work...;)

---

### Post by JayTee on 2006-11-12
I had no problems using the SystemRescueCD and Partimage. What exactly was the problem with the System Rescue CD? Would it not boot or something else? What was the error message? Sometimes an ISO gets hosed on the download and you need to do a MD5 check against it. Sometimes the ISO is fine but if you burn it at to fast a speed it gets "munged" and won't perform right.

---

### Post by tagra123 on 2006-11-12
SysRescueCd works for me too.

I even loaded it to the hard drive and added a grub entry so that its always easily accessed from the boot menu.

Easy to add to hard drive - only 3 files need copied.  I tried it on an existing partition and then created a 800mb partition and copied the files there.

[http://www.sysresccd.org/Sysresccd-manual-en_Easy_install_SystemRescueCd_on_harddisk](http://www.sysresccd.org/Sysresccd-manual-en_Easy_install_SystemRescueCd_on_harddisk)

---

### Post by wieman01 on 2006-11-13
If you need a Partimage guide, then try this: [http://www.ubuntuforums.org/showthread.php?t=287522]("http://www.ubuntuforums.org/showthread.php?t=287522")

In my opinion, Partimage is the easiest way to make reliable backups.

---

### Post by Oki on 2006-11-13
Hi, and thanks for all the reply s. 

I downloaded the rescue disk again, and this time it works like it should. Perhaps the burning messed it up the first time as you mentioned. Sorry, but I cant remember the error message. 

Can I ask another (dumb)question?

When running Partimage I first choose the partion witch to be saved, then I tell partimage where it should save it. This is my disks and partions(I am running dual boot);
 
DISK 1: 
/dev/sda1:	NTFS for Windows os
/dev/sda5: 	NTFS 

/dev/sda3 	etc3 for Linux
/dev/sda4/ 	Swap for Linux

DISK 2:
/dev/sdb1	NTFS
/dev/sdb2	FAT32, shared disk

I want to save the file(with the image of /dev/sdba3) on the shared disk(since partimage cant save to NTFS), and to a folder I have called Backup1. So would the path look like this? 
/dev/sdb2/backup1

Thanks again:-)

---

### Post by Oki on 2006-11-13
Thanks wieman01

I dont see the need for “create mount-point”, why cant I just tell partimage to save the file on my shared FAT 32 partion(I am new to this!). But I have printed your guide if someone dont answer my question above – so I can try it.

---

### Post by JayTee on 2006-11-13
You will need to create a mount point for your fat32 partition because it is not mounted when you boot from the sysrescue CD and you're essentially running another OS. A partition needs to be mounted before you can read or write to it unless it's the partition that's being backed up since Partimage is doing a byte by byte copy of all allocated blocks in the partition.

---

### Post by wieman01 on 2006-11-13
> **JayTee said:**
> You will need to create a mount point for your fat32 partition because it is not mounted when you boot from the sysrescue CD and you're essentially running another OS. A partition needs to be mounted before you can read or write to it unless it's the partition that's being backed up since Partimage is doing a byte by byte copy of all allocated blocks in the partition.
I could not agree more. The RescueCD does not mount any volumes at all by default. So you need to mount one in the first place. The RescueCD is like the Ubuntu LiveCD and does not install anything on the physical drives. It pretty much leaves the entire system untouched & you need to tell the system what it need to do. But I guess you have figured it out by know.

---

### Post by tagra123 on 2006-11-13
> **wieman01 said:**
> I could not agree more. The RescueCD does not mount any volumes at all by default. So you need to mount one in the first place. The RescueCD is like the Ubuntu LiveCD and does not install anything on the physical drives. It pretty much leaves the entire system untouched & you need to tell the system what it need to do. But I guess you have figured it out by know.

You an also use partimage from the ubuntu live cd although I like using the rescue CD. 

Open a terminal and 

apt-get install partimage

when the install is complete

type

partimage

it will give you an inode error warning/message for each partition just ignore the errors -- it will backup and restore just fine.

Now you can still browse the web while backing up a partition.

I have a homemade ubuntu rescue cd (GUI). I forget at the moment the program I used to create it. The program basically copys the cd and then you can add or remove programs from the cd either though a GUI screen or at the chrooted command line. I eliminated a lot of the packages and added nfs samba and the like, and of course added partimage.  You can even add your own scripts.

---

### Post by tagra123 on 2006-12-22
New system rescue cd released -- whoa  it included gparted.

---

