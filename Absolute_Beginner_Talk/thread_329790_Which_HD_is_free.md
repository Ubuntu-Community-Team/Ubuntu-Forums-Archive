---
title: "Which HD is free?"
date: 2007-01-02
forum: Absolute Beginner Talk
---

### Post by bluetailfly on 2007-01-02
I am trying to install Ubuntu 6.06 on the free hard disk of 2 HD's. Windows XP is on one, which is formatted NTFS. The other disk is FAT.  Both are 160 GB. I want to install Ubuntu on the FAT disk, but how do I know which disk WinXP is on? It did not come preinstalled and XP installed it on the disk of its choosing, but SATA HD's are not designated Master/Slave like the IDE's I am more accustomed to.

1. Should I just assume XP is on SATA0? How can I be sure that is correct before I proceed?

2.  Ubuntu gives me the choice of installing on 
/dev/sda:SCSI1 or /dev/sdb:SCSI2. 

Does sda:SCSI1=SATA0 and sdb:SCSI2=SATA1, 
or vice versa?

I don't want to screw up and have to reinstall XP.

Anyone have a solution?

Thanks.

---

### Post by Lord Illidan on 2007-01-02
Are on the live cd or on the alternate cd?

And can't you see if the drives are partitioned NTFS or FAT?

---

### Post by bluetailfly on 2007-01-02
Are on the live cd or on the alternate cd?

*I only have one cd.

And can't you see if the drives are partitioned NTFS or FAT?
Reply With Quote

*Where do I look to see that? BIOS doesn't specify.

---

### Post by smoker on 2007-01-02
gparted should tell you which is which, you should be able to run it off the live-cd, or else download a bootable version from sourceforge.net

---

### Post by bluetailfly on 2007-01-02
*Where do I look to see that? BIOS doesn't specify.

*Of course it wouldn't. Don't know why I said that. I have never needed to tell before. Windows gives me the option when I install and I chose NTFS for XP. Isn't FAT better for Linux? How do I tell which SATA drive has the XP install on it? I cannot just assume it is the master because there is no master.

---

### Post by mips on 2007-01-02
If you are certain that XP is on the NTFS formatted drive then it is easy.
Start the installer and at some point the partitioner will aks you where to install ubuntu. From the partitioner you should be able to see the drives and their file systems. Pick the one that is not NTFS.

> **bluetailfly said:**
> I am trying to install Ubuntu 6.06 on the free hard disk of 2 HD's. Windows XP is on one, which is formatted NTFS. The other disk is FAT.  Both are 160 GB. I want to install Ubuntu on the FAT disk, but how do I know which disk WinXP is on? It did not come preinstalled and XP installed it on the disk of its choosing, but SATA HD's are not designated Master/Slave like the IDE's I am more accustomed to.

1. Should I just assume XP is on SATA0? How can I be sure that is correct before I proceed?

2.  Ubuntu gives me the choice of installing on 
/dev/sda:SCSI1 or /dev/sdb:SCSI2. 

Does sda:SCSI1=SATA0 and sdb:SCSI2=SATA1, 
or vice versa?

I don't want to screw up and have to reinstall XP.

Anyone have a solution?

Thanks.

---

### Post by mips on 2007-01-02
> **bluetailfly said:**
> *Where do I look to see that? BIOS doesn't specify.

*Of course it wouldn't. Don't know why I said that. I have never needed to tell before. Windows gives me the option when I install and I chose NTFS for XP. Isn't FAT better for Linux? How do I tell which SATA drive has the XP install on it? I cannot just assume it is the master because there is no master.

You are going in circles here, read what people are telling you.

You cannot install Linux on FAT or NTFS. You have to reformat them to ext3, xfs, reiser etc.

---

### Post by bluetailfly on 2007-01-02
You are going in circles here, read what people are telling you.

You cannot install Linux on FAT or NTFS. You have to reformat them to ext3, xfs, reiser etc.

*Um, you are the first person to tell me that.

---

### Post by bluetailfly on 2007-01-02
If you are certain that XP is on the NTFS formatted drive then it is easy.
Start the installer and at some point the partitioner will aks you where to install ubuntu. From the partitioner you should be able to see the drives and their file systems. Pick the one that is not NTFS.

*I'll try again if you promise me it is safe. I didn't go that far first time because I can't get to the partition part until *a-f-t-e-r* I choose which drive scsi1 or scsi2 that I want to install on. If I choose the wrong one,  will Ubuntu mess something up there before I can cancel the install? Has anyone done an install before on a 2 SATA HD system with Windows already installed on one of them? If the drives were different sizes, I could tell them apart, but they are not.

---

### Post by bluetailfly on 2007-01-02
gparted should tell you which is which, you should be able to run it off the live-cd, or else download a bootable version from sourceforge.net

*gparted isn't on the printed list of programs that are supposed to be on the disk, although maybe it's there anyway. Yet even if it is, there's the catch22 that I won't be able to access it until *after* I install Ubuntu. 

So I went to sourceforge and I see that gparted is a disk partitioner. I assume I will have to choose the disk that I (don't) want to partition before it gives me the info. That's okay, provided if I accidentally choose the XP disk first it won't actually modify anything in addition to giving me access to the partitioning info on the disk. Is there any risk?

I know the disk with the Windows install is partitioned NTFS  because I chose that when I did the XP install, and also because I know where to verify the info after I start up XP--but I don't know how to tell whether the drive is SATA0 or SATA1, or how to tell which SATA drive is SCSI1 and SCSI2. I would have thought there would be a really simple way to do both those things.

---

### Post by Lord Illidan on 2007-01-02
On the Live CD, go to System -> Administration -> Gnome Partition Editor

---

### Post by bluetailfly on 2007-01-02
gparted should tell you which is which, you should be able to run it off the live-cd, or else download a bootable version from sourceforge.net

*Ah, the live CD.  I was going to go straight to the install, but if I have to use the live part first to access gpart, and gpart isn't going to modify something before I can get the info I need from it (it won't, will it?), then I'll try that--assuming gpart is on the CD I have. Gee, I didn't know I was going to have to do so much  preliminary  stuff *before* I can install the OS.

---

### Post by bluetailfly on 2007-01-02
On the Live CD, go to System -> Administration -> Gnome Partition Editor

*Okay, I can't do it now but I'll try later today, although I was hoping I could bypass playing around with the pre-install tryout and do all that exploratory stuff after I installed the system.  I'll have to keep reminding myself--it's Linux, not Windows, so don't expect simplicity.

---

### Post by mips on 2007-01-02
> **bluetailfly said:**
>   I'll have to keep reminding myself--it's Linux, not Windows, so don't expect simplicity.

I'm no linux zealot but i must say the ubuntu install is much easier than windows and faster as well.

Why don't you use the 'quote' feature of the forum, makes your posts easier to read.

---

### Post by mips on 2007-01-02
> **bluetailfly said:**
> You are going in circles here, read what people are telling you.

You cannot install Linux on FAT or NTFS. You have to reformat them to ext3, xfs, reiser etc.

*Um, you are the first person to tell me that.

Apologies but i was referring to the people pointing you towards the partitioner.

I added the rest in reference to you mentioning you wanting to install on the FAt filesystem.

I think you should read the install guides here, [SIZE=-1]www.psychocats.net/ubuntu/index[/SIZE]

---

### Post by gn2 on 2007-01-02
Doing it by this way will remove any uncertainty: [http://www.ubuntuforums.org/showthread.php?t=275728](http://www.ubuntuforums.org/showthread.php?t=275728)

---

