---
title: "Setting Up My Brother's 40 GB drive to dual-boot"
date: 2006-08-17
forum: Absolute Beginner Talk
---

### Post by Steggy on 2006-08-17
Hello all,

In the next few days, I'm going to be helping my brother format his computer and set up a dual-boot with Windows XP Pro and Ubuntu 6.06.1. (I tried to talk him into just installing Ubuntu, but he doesn't want to abandon the operating system he knows how to use quite yet.)

The one sticking point I'm having, however, is the fact that he only has a 40 GB drive. The way I want to set up his partitions is this:

* One small NTFS partition for Windows
* One small ext3 partition for /
* One big ext3 partition for /home--this will also be the "shared" partition between the two OSes, using the ext2/3 drivers for Windows

With this plan in mind, I'm unsure of what sizes to make each partition. I don't really know how little space Windows and Ubuntu really need. I'm hoping someone here has some experience with this and can give me some suggestions.

One more thing:  if possible, I'd like to set up the partitions so that, if my brother decides to switch completely to Ubuntu, I won't need to format everything. Instead, I'd like to be able to resize either the / or /home partition to include the Windows partition. Any suggestions on how to set the partitions up so this will be the easiest?

Thank you,
Steggy

---

### Post by aysiu on 2006-08-17
I would do this:
15 GB NTFS 
18 GB /home
6.5 GB /
.5 swap

I've heard mixed things about placing Windows after Ubuntu--some have said Windows has to be first (not just *installed* first but actually *physically* first); others have said it doesn't matter.

If Windows is after your /home partition, you can always delete it and add it to the /home partition.

If Windows is first, you can delete it and mount it as a /data partition.

---

### Post by andrewpmk on 2006-08-17
I should advise you that a Windows NTFS partition is not ideal as a shared partition because Linux does not support writing NTFS partitions properly. Utilities do exist to write NTFS partitions in Linux, but they are buggy and they MAY DELETE YOUR DATA! If you want a true shared partition, create a FAT32 partition for files and an NTFS partition for Windows, but be warned that it cannot handle files larger than 4GB and that it uses space inefficiently. However, if you can read one partition from the other operating system, this is not an issue.

1. If your Windows partition has more than 20 GB of files, move some of them to another computer or delete them if they are not valuable. If you are reformatting your hard drive, you must install Windows before installing Linux. In this case, tell the Windows installer to install itself in a 20GB partition at the start of the drive.

2. Back up any valuable data, like documents, photos, etc. I can't stress this enough, because if you are intending to resize your Windows partition, the Ubuntu installer MAY DELETE YOUR FILES. If you are reformatting your hard drive, it will delete your files.

3. Restart your computer with the Ubuntu live CD. It will boot up to a Ubuntu desktop (it does not install anything at this point).

4. Start up the installer using the Install icon on the desktop. Answer the questions about language, time zones, passwords, etc. Then, it will ask you what you want to do with the hard drive. Click on "Manually edit partition table". A partition editor will appear.

5. Resize (if you haven't already done so) the NTFS partition to 20 GB and ensure that it is at the beginning of the disk. The Ubuntu installer does support NTFS partition resizing, but it may encounter problems. If it does not work, you can use commercial utilities like Partition Magic. Create two ext3 partitions in the remaining space, one for / (I would recommend 5GB), /home (14.5 GB) and swap (0.5 GB). You can change these numbers a bit if you like.

6. Continue the installation. Ubuntu will install GRUB, a boot loader, which will allow you to choose Windows or Linux at startup.

7. Reboot your computer. You should be presented with a menu giving you the choice of booting Linux or Windows. Choose Linux.

---

### Post by bodhi.zazen on 2006-08-17
consider this:

/dev/hda1 15 GB -> Windows C:\.
/dev/hda2 10 GB -> Ubuntu / (root)
/dev/ha3  size = RAM x2 swap
/dev/hda4 size = the rest (14-14.5 GB) /mnt/data

Use /mnt/data, rather then /home, as a shared drive.
I would use NTFS as the file system. If you use a linux native FS (Ext2, Ext3, etc) Windows will likely not be able to have access it (I have not had much luck with windows ext2/3 drivers and Linux uses NTFS just fine). I have used a shared NTFS partition without data loss.

The suggestion of FAT above is also good, second choice.

The idea of backing up the shared drive from time to time is also a good one.

If you need to back up /home just cp -r /home/user /mnt/data/home/user

---

### Post by Steggy on 2006-08-17
Thank you all for the great suggestions and tips! :)

I didn't realize Windows would need that much space. My original thoughts had been a 10/10/19.5/.5 split (Windows/ / / /home / swap.) However, after reading here, I'm think of doing this:

15 GB NTFS Windows partition
10 GB Ext3 / partition
14.5 GB Ext3 /data* partition
.5 GB swap partition (my brother's computer has 256 MB RAM)

*The /data partition will be the shared partition (I've had very good luck with the Windows Ext2/3 drivers, from the time when I was still dual-booting, and I also extremely dislike using FAT32.) In the /data partition, I'll have a directory called ubuntuHome, then I'll set up a link from there to his /home directory. This is what I do on my computer so that I can install other distrobutions to test them, wihle using the same partition as a /home partition with them.

Does this look all right? Anyone see any problems with setting it up like this?

As an additional note, having reinstalled Windows and Ubuntu multiple times, I can say with complete certainity that Windows neither has to be installed first nor be actually physically first on a drive. However, installing Windows first definitely makes the processes of dual-booting easier, since you don't have to go back and restore GRUB to be able to boot into Ubuntu.

Thanks again,
Steggy

---

### Post by aysiu on 2006-08-17
I've had good luck with [http://www.fs-driver.org](http://www.fs-driver.org)

---

### Post by bodhi.zazen on 2006-08-17
Looks good to me. It is not as if Windows needs 15 Gb, it is just if you run out of room on the windows C:\ it is real pain.

I agree with you re: install order. Windows needs a primay partition, does not have to be the first partition on the disk, just not an extended partion. re-installing grub, however, in not so difficult.

---

### Post by anaconda on 2006-08-17
Actually you dont need the data partition at all !!

Because with fs-driver windows can read/write to your linux partititon. So you can use your linux partition also as the data partition.

Really matter of opinion, but here is my suggestion..
WinXP  15,25GB
Ubuntu 24GB
SWAP   0,75GB 

(or just simply)
winXP  19,5GB
Ubuntu 19,5BG
SWAP   1GB

---

### Post by bodhi.zazen on 2006-08-17
No, you do not "need" a data partition. It is just that you "lose" all your data if you need to re-install the OS.

---

