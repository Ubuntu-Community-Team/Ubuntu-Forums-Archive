---
title: "Computer won't boot at GRUB: Error 17"
date: 2007-02-02
forum: Absolute Beginner Talk
---

### Post by Mega_Fauna on 2007-02-02
And now my comp won't boot into either Ubuntu or XP. I get past the Dell screen, it initiates GRUB and tells me that GRUB has failed, "Error 17".

I'm posting this by running the Ubuntu Live DVD (which ran fine previously and still does).

Also, just in case, when I installed Ubuntu I partitioned by second drive (an IDE slave) to make space for it. I didn't do it manually and didn't touch (to my knowledge) the C: Drive with XP on it.

Please help, life w/o a comp / yadda yadda yadda.

Thanks,

---

### Post by old_geekster on 2007-02-03
GRUB error 17 indicates that it is seeing the drive, but doesn't recognize the file system. Since you don't have a computer, I would suggest that you do another fresh install.

Here is a link to a guide to help you with the install:

[http://www.debianadmin.com/ubuntu-edgy-eft-desktop-installation-with-screenshots.html](http://www.debianadmin.com/ubuntu-edgy-eft-desktop-installation-with-screenshots.html)

It has screen shots, so it is very easy to follow.  I used it when I did my install.

I recommend using the manual partitioning option.  The main thing is to make sure that you are formatting the correct drive.  If not, you will delete Windows.

---

### Post by Mega_Fauna on 2007-02-03
Thanks for the reply. I will try it tonight after work. Hope it works!

---

### Post by Sean Heron on 2007-02-03
I don´t have much Idea about Linux or ubuntu (only installed yesterday), however, if I remeber correctly, I got Grub error 17 at boot at first as well (but Im not sure about the number). Anyway, I managed to fix it by changing the boot order in my Bios, so I´ll just mess that up now, and see what error it gives me :D. Be back in 10 minutes with the results of my experiment :D.

Edit: yes it was error 17. The reason I got it was not due to a faulty install, but because my SCSI Harddrive had been "renamed/reorded" after I had installed Kubuntu. The whole story: I have 2 SCSI hard drive (one with Windows) and one IDE harddrive. After installing Kubuntu, on booting, Windows still ran automatically. I thought I might have to change the boot order of my SCSI drives (I had installed kubuntu on the other drive), so I did that in my SCSI manager. Now nothing started. Then I thought I might have to enable booting from my IDE drive in BIOS, because Grubs might be installed there. That turned out to be right, and Grubs now gave me error 17 :) . I then figured out I hadn´t swiched back my SCSI drives to standard booting order, so I did that and it works fine since then :D. Sorry, I guess all this is probably not going to help you :/ .

---

### Post by Mega_Fauna on 2007-02-03
old_geekster

Hi, I've tried following the instructions (and not), have set up the same file system as in the screencaps but my computer still won't boot. I still get the same error 17.

I googled the problem and someone recommended using the Ultimate Boot Disc to fix the problem but they didn't say what to do. Can anyone detail this for me?

How can I get the comp to boot into XP if Ubuntu won't boot? At this stage I'll take either one.

Thanks

---

### Post by Mega_Fauna on 2007-02-03
> **Sean Heron said:**
> I don´t have much Idea about Linux or ubuntu (only installed yesterday), however, if I remeber correctly, I got Grub error 17 at boot at first as well (but Im not sure about the number). Anyway, I managed to fix it by changing the boot order in my Bios, so I´ll just mess that up now, and see what error it gives me :D. Be back in 10 minutes with the results of my experiment :D.

Edit: yes it was error 17. The reason I got it was not due to a faulty install, but because my SCSI Harddrive had been "renamed/reorded" after I had installed Kubuntu. The whole story: I have 2 SCSI hard drive (one with Windows) and one IDE harddrive. After installing Kubuntu, on booting, Windows still ran automatically. I thought I might have to change the boot order of my SCSI drives (I had installed kubuntu on the other drive), so I did that in my SCSI manager. Now nothing started. Then I thought I might have to enable booting from my IDE drive in BIOS, because Grubs might be installed there. That turned out to be right, and Grubs now gave me error 17 :) . I then figured out I hadn´t swiched back my SCSI drives to standard booting order, so I did that and it works fine since then :D. Sorry, I guess all this is probably not going to help you :/ .



Hi,

I actually read and deciphered your post (I'm not that much of a techie). I got into the Dell setup screen by hitting F2 and tried to change the order of the drives but to no avail, it only showed the C:\ drive and the opticals. I turnt off the C:\ in the hope that the computer would pick up the slave drive and boot from it but then I didn't even get to the Grub problem. Not sure if I read your post right now that I think about it....

Thanks for the post anyways though.

---

### Post by confused57 on 2007-02-03
You probably have a newer Dell, but on my Dimension 4550, the master hard drive is listed as hd0, and the slave as hd1...I had to make sure that the slave(hd1) was set to "auto".

You might want to boot up with the livd DVD, open a terminal(Applications---Accessories---Terminal), enter:
```
sudo fdisk -l
```
The -l is a small "L".

Post the output & maybe it'll give a clue to what's going on.

---

### Post by Mega_Fauna on 2007-02-03
Hi, I can't believe the speed of the reply. Here is my info.


ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        7294    58589023+   7  HPFS/NTFS

Disk /dev/hdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       20710   166353043+   7  HPFS/NTFS
/dev/hdb2           22948       23046      795217+   f  W95 Ext'd (LBA)
/dev/hdb3   *       20711       21985    10241437+  83  Linux
/dev/hdb4           23047       24321    10241437+  83  Linux
/dev/hdb5           22948       23046      795154+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       24321   195358401    7  HPFS/NTFS
ubuntu@ubuntu:~$

---

### Post by confused57 on 2007-02-03
What you might want to do is restore your Windows mbr:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

The Super Grub Disk can also do this:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
see the section about Situations where SGD is useful.

Once you're able to boot into Windows from Windows mbr, you might want to consider setting your system up this way:
[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

I think that grub was installed on the Windows mbr on your first hard drive...grub can be reinstalled with the live cd:
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

You can do what you would like, but I recommend trying to restore your Windows mbr first.

---

### Post by Mega_Fauna on 2007-02-03
Hi thanks, I  shall dedicate tomorrow afternoon to that. Thanks for the specifics. I knew this linux installation would be fun but not quite as much as this:-)

---

### Post by Mega_Fauna on 2007-02-04
> **confused57 said:**
> What you might want to do is restore your Windows mbr:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

The Super Grub Disk can also do this:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
see the section about Situations where SGD is useful.


Hi, I restored my XP boot with the Super Grub Disk. The link you sent me was excellent and easy to follow, I'm now posting with XP (and Firefox). Thanks for the help. The worst part of the adventure was having to drive to the Dollar store to buy a blank CDR...

Next step I guess is to figure out how to set up the dual boot with your following 2 links. I'm surprised Ubuntu didn't do that automatically, I thought it was going to. Still a newb at this obviously.

Thanks again

---

### Post by evoloution on 2007-04-26
I have the same problem... Ubuntu/Kubuntu 7.04

I am not a guru myself either but I did see a difference comparing to other Ubuntu/Kubuntu installation that may help.

During the installation I observed that it recognised all my disks as scsi although they are all ide!!!!

I get Error 17 when I try lanching Kubuntu and "NTLDR is missing" when I try to launch Windows

I went to the Windows recovery console and it seemed to recognize 1.C:\Windows well so the partitions are intact. Moreover fixboot command did not fix the problem so my idea is that mislabeled mapping of ide disks as scsi from installation cause grub to malfunction

I would use the fixmbr command from the recovery console but I am afraid that I might harm a needed partition in my first disc

I hope this helps in finding the solution

Hardware (disks):

IDE 1: Master -> 120GB (5 partitions 2x  NTFS, 2x ext3, 1x Swap) The 1 NTFS should remain intact - valuable data
           Slave -> 200GB
IDE 2: Master -> DVD-RW
           Slave -> 200GB
Sata Controller -> 250GB

---

### Post by confused57 on 2007-04-26
> **evoloution said:**
> I have the same problem... Ubuntu/Kubuntu 7.04

I am not a guru myself either but I did see a difference comparing to other Ubuntu/Kubuntu installation that may help.

During the installation I observed that it recognised all my disks as scsi although they are all ide!!!!

I get Error 17 when I try lanching Kubuntu and "NTLDR is missing" when I try to launch Windows

I went to the Windows recovery console and it seemed to recognize 1.C:\Windows well so the partitions are intact. Moreover fixboot command did not fix the problem so my idea is that mislabeled mapping of ide disks as scsi from installation cause grub to malfunction

I would use the fixmbr command from the recovery console but I am afraid that I might harm a needed partition in my first disc

I hope this helps in finding the solution

Hardware (disks):

IDE 1: Master -> 120GB (5 partitions 2x  NTFS, 2x ext3, 1x Swap) The 1 NTFS should remain intact - valuable data
           Slave -> 200GB
IDE 2: Master -> DVD-RW
           Slave -> 200GB
Sata Controller -> 250GB
Boot the live cd, open a terminal(Applications---Accessories---Terminal),enter:
```
sudo fdisk -l
```
the -l is a small "L"

Post the output of this command and maybe someone will be able to help figure out what's happening.  I don't use Kubuntu, but you may need to use Konsole instead of Terminal.

---

### Post by evoloution on 2007-04-28
[COLOR="Red"]I reinstalled Kubuntu 6.06.1 and the booting is normal again, the results are:[/COLOR]

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       30401   244196001    7  HPFS/NTFS

Disk /dev/hda: 120.0 GB, 120000000000 bytes
255 heads, 63 sectors/track, 14589 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        6527    52428096    7  HPFS/NTFS
/dev/hda2            6528       14588    64749982+   f  W95 Ext'd (LBA)
/dev/hda5            9139       14588    43777093+   7  HPFS/NTFS
/dev/hda6            6528        7292     6144799+  83  Linux
/dev/hda7            7293        7547     2048256   82  Linux swap / Solaris
/dev/hda8            7548        9138    12779676   83  Linux

Partition table entries are not in disk order

Disk /dev/hdb: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       24792   199141708+   7  HPFS/NTFS

Disk /dev/hdd: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1               1       24792   199141708+   7  HPFS/NTFS

[COLOR="red"]On the other hand in Kubutu 7.04 live CD:[/COLOR]

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       30401   244196001    7  HPFS/NTFS

Disk /dev/sdb: 120.0 GB, 120000000000 bytes
255 heads, 63 sectors/track, 14589 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        6527    52428096    7  HPFS/NTFS
/dev/sdb2            6528       14588    64749982+   f  W95 Ext'd (LBA)
/dev/sdb5            9139       14588    43777093+   7  HPFS/NTFS
/dev/sdb6            6528        7292     6144799+  83  Linux
/dev/sdb7            7293        7547     2048256   82  Linux swap / Solaris
/dev/sdb8            7548        9138    12779676   83  Linux

Partition table entries are not in disk order

Disk /dev/sdc: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       24792   199141708+   7  HPFS/NTFS

Disk /dev/sdd: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       24792   199141708+   7  HPFS/NTFS
[COLOR="red"]
So you can see that it recognizes them differently, why???[/COLOR]

---

### Post by eltorodeoro on 2007-04-29
@ evolution:

> I would use the fixmbr command from the recovery console but I am afraid that I might harm a needed partition in my first disc

don't know if you're still messing with this, but i used it this afternoon and my partitions are still ok.

@ whomever:

I'm a bit frustrated with all of it at this point.  I had dual-booting working fine under dapper, edgy, and most recently SUSE 10.2.  but feisty has broken it.

at first, feisty didn't like my having a CD-RW and CD/DVD-RW on the same bus, so I **_*UNPLUGGED*_** the CD-RW (slave).  she wouldn't even boot the live cd before i did this.  picky, picky.

after this, installation proceeded as normal.  then on the reboot, instead of the GRUB menu, I get this **NTLDR Missing ** stuff.  As I said, the XP recovery console command FIXMBR works fine to restore the Windows boot.

so I try to follow the directions for re-installing GRUB.  Everything looks and acts the way the posts show.  I still get the **NTLDR missing** error.

I guess I just don't understand what happened with this release?  I've installed this distro twice on this machine, as well as many other machines without issue.  I've also installed other distros on this machine without any problems.  why? why?

stellaaaaaa!!!!

ok...  sorry for venting.  i'll go back to looking for answers now.

---

### Post by eltorodeoro on 2007-04-29
so i feel stupid.

thanks to confused57 for pointing us towards SuperGRUBDisk.  absolutely fantastic utility.

i discovered using SGD that my grub setup and MBR were all working splendidly, which led me back to the BIOS.  come to find out, my BIOS was attempting to load from my slave SATA drive.  no wonder there was no NTLDR!  i put the two drives in proper order, and everything is hunky-dory.\\:D/ 

so, back to my initial frustrations:  despite my ridiculous setup, dapper, edgy, suse and fedora never had a problem loading.  why does feisty?

oh, well.  thanks again to confused57 - you are hereby dubbed the grub/dual-boot/MBR master! =D>

---

