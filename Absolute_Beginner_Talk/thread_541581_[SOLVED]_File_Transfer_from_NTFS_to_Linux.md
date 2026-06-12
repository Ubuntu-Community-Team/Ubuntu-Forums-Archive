---
title: "[SOLVED] File Transfer from NTFS to Linux"
date: 2007-09-03
forum: Absolute Beginner Talk
---

### Post by High Camp on 2007-09-03
Hi All

I appreciate all the help I've received in the past and hope it will keep coming. I have been searching all day and trying different options but have yet to find something reliable and fast.

I am trying to transfer all of my personal files, which were created under XP, to my new Linux box. I was smart enough to back up all my data on an external (NTFS) hard drive before making the switch. My problem now is that the file system on the hard drive is corrupted and Linux cannot read it but XP can. I have the hard drive plugged into my old XP box and I am trying to transfer the files. The XP box is set up as an FTP server so I have tried ftp, skype, and tried but failed with Windows network. 

My question is this, what is the fastest and most reliable way to transfer many (many) files?

My second and only slightly related question is this, is there a max size for .tar files? I made a tar backup of the drives on my computer. The OS partition was 12gb before and 4gb after and the personal files were 23gb before and 4gb after. Is this because the personal files were compressed more or because the largest a tar can be is 4gb? The reason I ask is because I don't want to go through the effort of transferring a 4gb tar only to find it's corrupted.

EDIT: The reason the Windows network failed is because when I go to open the shared folders on the Linux box I get asked for a user name and password. I have tied everything (including creating them as per a how to article I found) with no luck. And the opposite is also true, I have not been able to access the shared folders on the XP box.

Thanks again for all the help,

---

### Post by cdsboy on 2007-09-03
According to wikipedia, the maximum tar size is 8gb. The compression rate, at least from what i understand, heavily depends on the type of file you are compressing. It does seem a little odd that they both compressed to 4gb, seeing as how the personal files were almost twice as big. Any who if you do go ahead and try it, be sure to post the results.

---

### Post by High Camp on 2007-09-03
Will do, thanks for the reply, didn't even think of Wikipedia.

Thanks,

---

### Post by sonofusion82 on 2007-09-03
if you want to copy files from a windows machine to linux, try HFS [http://www.rejetto.com/hfs/](http://www.rejetto.com/hfs/) simple and avoids the problem with samba..

---

### Post by dwhitney67 on 2007-09-03
Having trouble accessing your external NTFS drive, eh?  Have you followed the instructions listed at this [site]("http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html")?

Alternatively, you could Install an SSH client application onto your windows machine.  Then you can use 'scp' (secure copy) to transfer the files across, providing of course both of your machines are networked.

If I misunderstood your OP and you have a dual boot system, then the suggestion above will not work.

---

### Post by wickstopher on 2007-09-03
If your tar files are maxing out at EXACTLY 4GB, then I would guess that it's actually a fat32 filesystem (more common for external drives, anyways).  The max file size in a fat32 filesystem is 4GB.  I ran into this problem when trying to make backup copies of my DVD collection on a fat32 drive.  I reformatted the drive to ext3 and it worked out.

Why not try just copying the files to your computer or another hard drive in windows, reformatting the drive in fat32 (assuming you don't actually have any files over 4GB in size), which is easily swappable between windows and linux, using the gparted liveCD or some other such tool, and then transferring them to your linux box via the hard drive.

---

### Post by High Camp on 2007-09-03
Hey thanks for the great response. I'll answer you all indivually:

cdsboy:
It did strike me as very odd that both tars compressed to 4.194gb so I really don't trust them and am not even going to bother trying to extract them.

sonofusion82:
I didn't bother with HFS because there number and size of files in not feasible for any sort of normal file transfer. Thanks for the suggestion and I will keep it in mind for future projects.

dwhitney67:
I do not have a dual boot system I have XP on an old machine and Linux on the new one. That being said for whatever reason the file system is corrupted and Linux cannot read it so I will save your suggestion for last resort.

wickstopher:
I suspect you're right about the file sizes.

To all:
I have ended up slowly copying each file to a zip on my local drive. When the zip is big enough I send it via Skype. It's painfully slow but at least it's recovering my files.

Thanks again for everyone's help,

P.S. I've found that file transfer support is not great on Linux Skype. I've sent large files between two MS pc's without problem but the Linux box keeps stalling and failing.

---

