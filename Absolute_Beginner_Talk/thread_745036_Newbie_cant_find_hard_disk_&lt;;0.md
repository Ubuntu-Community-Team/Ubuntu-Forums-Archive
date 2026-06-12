---
title: "Newbie cant find hard disk &lt;|;0"
date: 2008-04-04
forum: Absolute Beginner Talk
---

### Post by Deety on 2008-04-04
Hello.
I installed Ubuntu 7.1 about a few hours ago so am a  total noob. I have 2 hard disks, the system drive which is there ok, and another which doesn't show up wherever I look. I've also just installed a freebie Avast virus checker and I cant find that either! Any help would be appreciated, especially links to good basic info on Linux|Ubuntu.
Sorry for the low brow question. ;')   :oops:
Cheers.

---

### Post by stoodleysnow on 2008-04-04
OK. Have you checked the cables - are they plugged in, correctly, the right way round?
Are your drives SATA or IDE? 
If IDE:
Have you set the drive jumpers so one is master (on the end of the IDE Cable) and one is Slave (in the middle of the IDE Cable)

Also, are they both detected properly by the BIOS?
How old are the drives, how much space on them?
How are they partitioned?

As for the Virus checker, you don't need it unless completely paranoid. There are no working viruses for Linux and there haven't been any for several years.

---

### Post by oedha on 2008-04-04
didnt shown up....could be you shutdown windows unproperly...(dod you have windows ?)
can you open terminal :==> applications - accesories - terminal
type :==> sudo fdisk -l
post the output here...thx :)

about antivirus....*nix doesnt need it so far CMIIW

EDIT : here's links for you to read
[www.**psychocat](www.**psychocat)**s.net/ubuntu/
[http://help.ubuntu.com/community](http://help.ubuntu.com/community)

---

### Post by Deety on 2008-04-05
Thanks for the replies.
I had windows on this sytstem but haven't got it on now as I thought a clean install of Linux would give me a better idea of what it could do.

Here is the fdisk output:-
Disk /dev/sda: 13.6 GB, 13664550912 bytes
255 heads, 63 sectors/track, 1661 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x21052105

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1585    12731481   83  Linux
/dev/sda2            1586        1661      610470    5  Extended
/dev/sda5            1586        1661      610438+  82  Linux swap / Solaris

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4e2c4e2b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       24320   195350368+   7  HPFS/NTFS


I point out again that I have absolutely no idea what I am doing here.

---

