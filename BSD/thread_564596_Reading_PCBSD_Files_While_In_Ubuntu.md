---
title: "Reading PCBSD Files While In Ubuntu"
date: 2007-10-01
forum: BSD
---

### Post by Eddie Wilson on 2007-10-01
Good Day All,
I've installed PCBSD 1.4 and I like it. I had to configure Grub so I could start the bsd system. No problem but I was wanting to know how I can access the bsd file system while I'm in Ubuntu? I know Ubuntu will see the file system but not know what it is because I had to edit fstab in order for Ubuntu to finish booting up automatically. Thank you for any help you can give on this.
Eddie

PS: I did check the PCBSD forums I but wanted to get advice from Ubuntu  users.

---

### Post by maybeway36 on 2007-10-01
I know that the FreeBSD filesystem is called UFS, but I've never tired mounting it with Linux.

---

### Post by theonlyrealperson on 2007-10-01
I've used both BSD and Linux for about a year now, and I haven't met a Linux distro yet that has been able to read the UFS system. A small minority even recognize it as a UFS system...

Good luck, post it if you ever find out differently...

---

### Post by John.Michael.Kane on 2007-10-02
This info may point in you in the direction you need.
[http://www.webservertalk.com/message1741887.html](http://www.webservertalk.com/message1741887.html)
[http://gentoo-wiki.com/HOWTO_Mount_UFS_partitions](http://gentoo-wiki.com/HOWTO_Mount_UFS_partitions)
[http://tldp.org/HOWTO/Linux+FreeBSD-5.html](http://tldp.org/HOWTO/Linux+FreeBSD-5.html)
[How to mount a PC-BSD partition under Linux?]("http://64.233.169.104/search?q=cache:XDlJ7e7jLEEJ:faqs.pcbsd.org/9_292_en.html+Mounting+FreeBSD+Partition+on+Linux&hl=en&ct=clnk&cd=5&gl=us&client=firefox-a")

Note:From reading around. kernel devs describe linux support for UFS write as 'dangerous' however you should be able to get read support.

---

### Post by Bachstelze on 2007-10-03
The thing that is known to confuse most new uses is that only the BSD partition appears for example in *fdisk -l* :

```
firas@Ana ~ $ sudo fdisk -l

Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8f800100

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1           8       64228+  83  Linux
/dev/hda2   *           9        1224     9767520   83  Linux
/dev/hda3            1225        2427     9663097+  a6  OpenBSD
/dev/hda4            2428       14593    97723395    5  Extended
/dev/hda5           14532       14593      498015   82  Linux swap / Solaris
/dev/hda6            2428       12299    79296777   83  Linux
/dev/hda7           13227       13291      522081   83  Linux
/dev/hda8           13292       13356      522081   83  Linux
/dev/hda9           13357       14400     8385898+  83  Linux
/dev/hda10          14401       14531     1052226   83  Linux
/dev/hda11          12300       13226     7446096   83  Linux

Partition table entries are not in disk order

```

(here /dev/hda3). And this partition contains no filesystem of it's own and is therefore not mountable. However, your actual BSD partitions (that contain your UFS filesystems) appear for example in /proc/partitions :

```
firas@Ana ~ $ cat /proc/partitions
major minor  #blocks  name

   3     0  117220824 hda
   3     1      64228 hda1
   3     2    9767520 hda2
   3     3    9663097 hda3
   3     4          1 hda4
   3     5     498015 hda5
   3     6   79296777 hda6
   3     7     522081 hda7
   3     8     522081 hda8
   3     9    8385898 hda9
   3    10    1052226 hda10
   3    11    7446096 hda11
   3    12     136552 hda12
   3    13     530145 hda13
   3    14     265072 hda14
   3    15     136552 hda15
   3    16    8594775 hda16

```

(here, /dev/hda12 to /dev/hda16). Then, to mount them, simply do a

```
sudo mount /dev/something -t ufs -o ro,ufstype=ufs2 /somewhere
```

or add a relevant line in your fstab. Attention, ufs2 is the UFS filesystem type used by FreeBSD, which PC-BSD is based on. Other BSDs use different types (for my OpenBSD partitions, for instance, I use *ufstype=44bsd*).

---

### Post by carloslosgrande on 2008-02-11
Hi HymnToLife, that was very clear and a great help. Just 1 question - the last line - > mount /dev.....etc, etc....../somewhere
What would be a good place to mount it?
clearly */home* isn't a good idea, (just tried).
Thanks.

---

### Post by Bachstelze on 2008-02-12
Usually, filesystems which do not belong to the system currently in use are mounted under /mnt, so I guess a good place would be /mnt/pcbsd (don't forget to create that directory before).

---

### Post by carloslosgrande on 2008-02-12
[FONT="Comic Sans MS"]Thanks HymnToLife, I didn't know that was the usual practice,.... learn something every day.[/FONT]

---

