---
title: "Bootcamp partition missing?"
date: 2007-12-16
forum: Apple Intel Users
---

### Post by DMF on 2007-12-16
Hello,

I went through the basic process to install Windows via bootcamp but rather I installed Ubuntu. It works fine. I can dual boot and all is well. My main problem is I can not view my bootcamp partition from the OS X side it does not show up? I am trying to mount my Ubuntu partition/installation in VMware Fusion and having a difficult time with the partition table layout:

sudo fdisk /dev/disk0

Disk: /dev/disk0	geometry: 14593/255/63 [234441648 sectors]
Signature: 0xAA55
                  Starting       Ending
 #: id  cyl   hd  sec  -  cyl  hd sec     [     start -       size]
------------------------------------------------------------------------
 1: EE 1023 254  63 - 1023 254  63 [         1 -     409639] <Unknown ID>
*2: AF 1023 254  63 - 1023 254  63 [    409640 -  190578688] HFS+        
 3: 07 1023 254  63 - 1023 254  63 [ 191250472 -   38566406] HPFS/QNX/AUX
 4: EE 1023 254  63 - 1023 254  63 [         1 -  234111799] <Unknown ID>

./vmware-rawdiskCreator print /dev/disk0
Nr      Start       Size Type Id Sytem                   
-- ---------- ---------- ---- -- ------------------------
 4          1  234111799 BIOS EE Unknown
 1          1     409639 BIOS EE Unknown
 2     409640  190578688 BIOS AF HFS+
 3  191250472   38566406 BIOS  7 HPFS/NTFS

Would like to have a second (or 3rd 4th 5th!) pair of eyes look before I blow away my partition table and start over. sigh!

Thanks a lot!

---

### Post by staticvoid on 2007-12-17
i don't think mac can read ext3....


sv

---

### Post by Zaff on 2007-12-19
Mac OS doesn't read ext3 filesystem natively. You need to install ext2fs : [http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=3964826](http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=3964826)
If you're running Leopard or Tiger you need the dev version (1.4d4).
It is said to be unstable but I've been using it and I've yet to come across a problem. If you're not sure you can always set it to mount your ubuntu partition as read only.
Enjoy

---

### Post by cyberdork33 on 2007-12-19
I think he is trying to use his native Ubuntu install in VMWare Fusion. This is supposedly possible, but I don't know that anyone has got it to fully work yet. I believe that the partition marked NTFS is your Ubuntu partition. (For some reason, Apple's EFI sees Linux partitions as Windows partitions...)

---

