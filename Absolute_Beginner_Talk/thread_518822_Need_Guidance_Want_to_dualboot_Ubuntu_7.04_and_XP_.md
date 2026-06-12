---
title: "Need Guidance: Want to dualboot Ubuntu 7.04 and XP on multiple hard drives"
date: 2007-08-06
forum: Absolute Beginner Talk
---

### Post by haley183 on 2007-08-06
I want to setup an htpc running Ubuntu 7.04  with the option to occasionally boot to windows xp. I have two 40gb hard drives and one 500gb hard drive. i want linux on one 40gb hard drive and windows on the other and use the 500 for storage. i am new to linux in general and want advice on the best way to do this and what file systems to use.

from what i have read so far i am thinking about not using the grub loader and just using the bios boot selector to ocassionally boot to windows when i want... since i will not be using windows that much. windows will mainly be there just in case i ever need or want it. i am only installing it because i have the extra 40 gig hard drive laying around!

when i do boot to windows though i want to be able to retrieve the data from the 500gb hard drive if i want. i am not sure though if i should have another partition just for file sharing between os (like a second partition on the linux 40 gig drive)  or have the 500 capable of that.

thanks in advance for any help!!

---

### Post by Inxsible on 2007-08-06
1) Install Windows before you install Ubuntu

2) Any particular reason for not using GRUB?

3) You can easily use the 500GB as your storage drive in both OSes

4) You do not need any file sharing partition, since you already have the 500GB drive

---

### Post by Inxsible on 2007-08-06
The file system to use would be.

1) NTFS for the windows install

2) EXT3 for the Linux install

3) Your choice of EXT3 or NTFS or FAT32 for the 500 GB storage

You can have read/write access to EXT3 drives in Windows by installing Fs-Driver
You can have write access to NTFS drives in Linux by installing ntfs-3g. Read access for NTFS is default in Linux.
FAT32 have read/write access in both Linux and Windows by default.

Check these links for further info on installing and partitioning
[Partitioning]("http://www.psychocats.net/ubuntu/partitioning")
[Installing]("http://www.psychocats.net/ubuntu/installing")

---

### Post by haley183 on 2007-08-06
Thanks for the quick reply!

From the little bit of research I have done, I have read mixed things about using grub. Some people say its easy while others have some difficulty with it. Since I am new to Linux I am afrad i will have some difficulty with it. Plus since I won't be using windows that much, so i dont nessesarily need to be asked every time i boot up weather i want to boot to linux or windows. if it is simple then i would be glad to try it. one thing though is most posts i have read tell how to use grub with booting windows automatically, where i want linux to be the default. is changing the default very hard?

about the file systems, is there much difference between the write speed for ntfs, fat32 and ext3? or differences in how they work? i dont know much about these things other that fat32 is the old way and ntfs is the new way. since i have always been a windows user i have always just used ntfs by default and never really gave another thought about it. since this is going ot be a htpc it will be used for storing lots of video and music and such.

---

### Post by Inxsible on 2007-08-06
GRUB, IMHO, is very easy. You can change default OS easily, by simply modifying one line in the menu file. You can also make Linux to be your default.

Opinions differ however on whether it is easy or not.

EXT3 is a journaled file system. Read more about journaled filesystems [here]("http://en.wikipedia.org/wiki/Journaling_file_system").

---

### Post by hyper_ch on 2007-08-06
Grub is only a problem if you have both IDE and SATA drives in your computer... Grub does then (at least for me) not make the correct entry for booting.

---

### Post by haley183 on 2007-08-06
the two 40's are ide while the 500 is sata... therefore i shouldnt have a problem since the two 40's are the only ones i will be booting from...right?

---

### Post by Inxsible on 2007-08-06
Doesn't Feisty recognize all drives as SATA now ?

My ide's are all named sda1 sda2 etc

---

### Post by haley183 on 2007-08-06
so what about using ext4 versus ext3? aparently 4 its a little better than 3. i probably woudnt be able to tell the difference between the two, but im a little curious...

---

### Post by Inxsible on 2007-08-06
> **haley183 said:**
> so what about using ext4 versus ext3? aparently 4 its a little better than 3. i probably woudnt be able to tell the difference between the two, but im a little curious...

EXT4 is new and improved EXT3. Its very new. Gparted available with Ubuntu Live CD does not allow drives to be formatted with EXT4. at least I haven't noticed it.

Also, since its new, you never know what other problems it might have, if any. some apps might not be able to read those drives, others might. So I would use caution, before changing over completely to EXT4. Maybe, it will have full support in Gusty which releases in October 07.

---

### Post by BDNiner on 2007-08-06
I gave up on dual booting with XP and Linux. I just built a 2nd comptuer out of some unused parts that i had laying around.

---

### Post by hyper_ch on 2007-08-07
well, I just always had the problem with my two sata and two ide drives, that Grub does not apply to correct hd-numbering for its boot entires... I always had to manually correct them... it's not a big deal but you must be prepared to it. I'm not sure if I'm the only one who encounters that behaviour.

---

