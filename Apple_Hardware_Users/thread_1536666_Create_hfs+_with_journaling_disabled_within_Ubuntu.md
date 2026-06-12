---
title: "Create hfs+ with journaling disabled within Ubuntu"
date: 2010-07-22
forum: Apple Hardware Users
---

### Post by unckybob on 2010-07-22
I'm trying to make an iso from a dmg file. I'm using directions at: 

[https://help.ubuntu.com/community/ManageDiscImages#DMG%20Images](https://help.ubuntu.com/community/ManageDiscImages#DMG%20Images) 

Here's what I did: a

# dmg2img /path/to/example.dmg /path/to/example.img 
# sudo mkdir /media/example 
# sudo modprobe hfsplus
# sudo mount -t hfsplus -o loop example.img /media/example 
mount: wrong fs type, bad option, bad superblock on /dev/loop0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

# dmesg | tail
[26680.771684] ISO 9660 Extensions: Microsoft Joliet Level 1
[26680.771724] ISO 9660 Extensions: IEEE_P1282
[27124.100425] ISO 9660 Extensions: Microsoft Joliet Level 1
[27124.100468] ISO 9660 Extensions: IEEE_P1282
[28357.335773] ISO 9660 Extensions: Microsoft Joliet Level 1
[28357.335815] ISO 9660 Extensions: IEEE_P1282
[28450.349967] hfs: unable to find HFS+ superblock
[28561.190876] ISO 9660 Extensions: Microsoft Joliet Level 1
[28561.190917] ISO 9660 Extensions: IEEE_P1282
[29185.381953] hfs: unable to find HFS+ superbloc

I'm doing all this on an ext2 partition if that matters. 

I don't have any experience with this kind of thing. Can someone help?

---

### Post by unckybob on 2010-07-22
Bump

---

### Post by conundrumx on 2010-07-23
Do you have access to OSX?

---

### Post by unckybob on 2010-07-24
No. 

I used:

# sudo mount -o loop example.img /media/example

Instead of:

# sudo mount -t hfsplus -o loop example.img /media/example

That I used above. I guess the "-t hfsplus" option means that the file your trying to mount is an hfs+ filesystem. The file "example.img" was actually on a linux partition. I thought "example.img" was supposed to be on an hfs+ filesystem. Oh well! 

Thanks for trying to help.

---

