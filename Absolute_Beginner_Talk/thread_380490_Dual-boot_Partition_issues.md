---
title: "Dual-boot Partition issues"
date: 2007-03-09
forum: Absolute Beginner Talk
---

### Post by witt on 2007-03-09
I've installed both windows XP and Ubuntu Edgy 6.10 on my laptop in a 160Gb hard drive, and the partitions I have are as follows:
/dev/hda1 30Gb NTFS *Boot
/dev/hda2 20Gb ext3 Linux
/dev/hda5 2Gb swap 
/dev/hda6 100Gb FAT32

Basically after installation I had the Windows NTFS recognised as hda1, which i could read but not write. My first question is how do I make the NTFS drive read and write from Ubuntu?

And the 2nd question; I mounted (or I think I mounted) the FAT32 drive. I can read / write files onto the folder specified when editing /etc/fstab which was /media/share. But it still doesnt show up as a hard drive, in the same way as hda1 (windows partition) does in the screenshot below. How can I make it show up in this same way?

I have 2 screenies with the output from fdisk -l and the /etc/fstab file:
[fstab.png]("http://clientes.netvisao.pt/jrg13/fstab.png")
[fdisk.png]("http://clientes.netvisao.pt/jrg13/fdisk.png")

Any help is appreciated. Cheers ;)

---

### Post by Obor on 2007-03-09
Writing to NTFS was not 100% without problems, I think it's supposed to be stable now. [This is how to get it done.]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_users_read_and_write_access")

I'm not sure if I understand your second question but if you want to show it as hda3 instead of share just create folder /media/hda3 and change share to hda3 in the fstab

---

### Post by witt on 2007-03-09
thanks for the reply, i'll try setting up the NTFS partition tomorrow.

what i mean with the 2nd question is that in my home directory hda1 (ntfs) shows up as a hard drive along the linux file system, but the Fat32 partition doesnt. all i have is a shortcut in my desktop to /home/share, so my intention isnt changing the folder name, it's mounting it as a hard drive

---

