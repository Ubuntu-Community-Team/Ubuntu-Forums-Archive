---
title: "Will I need to reformat all of my drives since Linux only supports reading of NTFS?"
date: 2007-02-13
forum: Absolute Beginner Talk
---

### Post by monocongo on 2007-02-13
I have become aware that NTFS is only supported by Linux/Ubuntu for read access, so moving to Linux/Ubuntu will essentially make the ~800Gb of external disk drives I have useless for full read/write until I reformat the drives as ext3 instead of NTFS.  Is this true?  My original assumption was that I could access all of my data without having to do anything with these drives, but it seems that this is not the case and I will have a much harder time converting to Linux from Windows XP.  Am I correct in my understanding of this topic, i.e. on a dual boot machine I can still use my drives as is as long as I am booted into Windows, but if I boot into Linux (Ubuntu) then I can only hope for read access with these drives, and if I want to use my drives with Linux/Ubuntu then they'll need to be reformatted to ext3, making them useless when running Windows?  And if I reformat my drives to ext3 for Linux then these drives will only be recognized by other Linux machines (assuming I don't use some third party software to make the ext3 file systems visible to Windows or Mac machines)?  And if I do decide to make this jump to Linux/Ubuntu then how would I go about transferring the data from the NTFS drives to the reformatted ext3 drives, without burning way too many DVDs as intermediate storage?  Do I need to convert to FAT32 instead, and just endure the loss of the performance/security advantages of NTFS?  This is really making me rethink moving over to Linux -- someone please tell me it's not as bad as it looks.

Thanks in advance for any insight.


--James

---

### Post by guysmiley25 on 2007-02-13
Only have a quick moment, but writing to ntfs from linux can be done.

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_users_read_and_write_access]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_users_read_and_write_access")

You will still need a ext3 or ext2 or something partition for you ubuntu install. and a swap partition usually 2.5 time the amount of your ram.

Other than burning heaps of DVD the only other think I could think of is:

Create your ext3 partition. Move some of your files to your ext3 partition from your ntfs partition. Make your ntfs partition smaller and your ext3 partition bigger. Then move more files etc...

Then use a 3rd party application to access the ext3 partition from windows if you still want to run windows.

---

### Post by eXisor on 2007-02-13
Linux can do read/write of NTFS drives. Search for ntfs-3g to get the howto.

Although the support is not official, I have used ntfs-3g without issue.

---

### Post by Spike-X on 2007-02-13
I've also been using ntfs-3g without a hassle. Files I write to my ntfs drives under Linux are fully usable in both Linux and Windows.

---

