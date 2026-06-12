---
title: "Unusual instillation problems - typical remedies failed"
date: 2013-05-14
forum: Apple Hardware Users
---

### Post by adruffd on 2013-05-14
I am new to linux systems and command-line interfaces but luckily I am a quick study. You may need to help me connect the dots on this. I have been diligent about backing up my system bc I know I will screw something up at some point.

Background info: Running on a MBP 8,2. Initially installed linux Mint via [this]("http://www.maclife.com/article/howtos/install_linux_your_mac") guide.  Ran into problems with mint on my MBP (ran really hot, jupiter did not help too much and had other connectivity issues) and decided to uninstall it (or rather delete the drives via gparted/disk utility). After deleting the drives the linux icon in refit remained which was curious to me. Re-installed refit and have the same issues.

Attempted to install Ubuntu (12-1.04.2) anyway, using gparted to partition the drives (similar to the guide above). Long story short the install did not take and I have 2 linux icons in reefit (one to boot from HD, the other to boot from partition 4) and both of them give the "grub rescue error" unknown file system. I have tried deleting the drives and starting from scratch again and the same problem occurs (tried formatting ubuntu drive in ex3 and ex4)

I have tried to use boot-repair to no avail ([boot info script]("http://paste.ubuntu.com/5663564/")). I noticed something in the boot script that didnt look right at around line 575.


[COLOR=#FF0000]Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0has been opened read-only.                                                                          Error: Can't have a partition outside the disk![/COLOR]So I did some research and it seemed that Ubuntu was trying to boot from MBR instead of GPT and followed this [guide]("http://www.rodsbooks.com/linux-fs-code/index.html") to repair using gdisk. Below is some of the script

[FONT=arial]------------------------------------------------------------------------------------------------
[/FONT][FONT=arial]ubuntu@ubuntu:~$ sudo gdisk /dev/sda[/FONT]
[FONT=arial]GPT fdisk (gdisk) version 0.8.1[/FONT]

[FONT=arial]Partition table scan:[/FONT]
[FONT=arial]  MBR: hybrid[/FONT]
[FONT=arial]  BSD: not present[/FONT]
[FONT=arial]  APM: not present[/FONT]
[FONT=arial]  GPT: present[/FONT]

[FONT=arial]Found valid GPT with hybrid MBR; using GPT.[/FONT]

[FONT=arial]Command (? for help): p[/FONT]
[FONT=arial]Disk /dev/sda: 1465149168 sectors, 698.6 GiB[/FONT]
[FONT=arial]Logical sector size: 512 bytes[/FONT]
[FONT=arial]Disk identifier (GUID): 00002034-450B-0000-E337-[/FONT][FONT=arial]0000AF010000[/FONT]
[FONT=arial]Partition table holds up to 128 entries[/FONT]
[FONT=arial]First usable sector is 34, last usable sector is 1465149134[/FONT]
[FONT=arial]Partitions will be aligned on 8-sector boundaries[/FONT]
[FONT=arial]Total free space is 2172165 sectors (1.0 GiB)[/FONT]

[FONT=arial]Number  Start (sector)    End (sector)  Size       Code  Name[/FONT]
[FONT=arial]   1              40          [/FONT][409639   200.0]("tel:409639%C2%A0%C2%A0%20200.0")[FONT=arial] MiB   EF00  EFI system partition[/FONT]
[FONT=arial]   2          409640      1264904879   603.0 GiB   AF00  Customer[/FONT]
[FONT=arial]   3      1264904880      1266174415   619.9 MiB   AB00  Recovery HD[/FONT]
[FONT=arial]   4      1266176000      1440255999   83.0 GiB    0700  [/FONT]
[FONT=arial]   5      1440256000      1462783999   10.7 GiB    8200  [/FONT]
[FONT=arial]   6      1462784000      1462978559   95.0 MiB    EF02  [/FONT]

[FONT=arial]Command (? for help): t[/FONT]
[FONT=arial]Partition number (1-6): 4[/FONT]
[FONT=arial]Current type is 'Microsoft basic data'[/FONT]
[FONT=arial]Hex code or GUID (L to show codes, Enter = 8300): 8300[/FONT]
[FONT=arial]Changed type of partition to 'Linux filesystem'

[/FONT][FONT=arial]Command (? for help): sudo gdisk /dev/sda[/FONT]
[FONT=arial]You may need to edit /etc/fstab and/or your boot loader configuration![/FONT]

[FONT=arial]Command (? for help): w[/FONT]

[FONT=arial]Final checks complete. About to write GPT data. THIS WILL OVERWRITE EXISTING[/FONT]
[FONT=arial]PARTITIONS!![/FONT]
[FONT=arial]------------------------------------------------------------------------------------------------[/FONT]

[FONT=arial]Partition 4 = ubuntu[/FONT]
[FONT=arial]Partition 5= linux swap[/FONT]
[FONT=arial]Partition 6 = bios[/FONT]

[FONT=arial]As you can tell I could really use some help on this. My apologies in advance for the poor description of my problem, still learning - let me know what other info would be helpful.[/FONT]

---

### Post by adruffd on 2013-05-16
[COLOR=#ff0000]_**UPDATE:**_ [/COLOR]

I eventually tried to boot in mac's "Startup Manager" and chose the windows drive. What do you know? It worked. To make things even stranger when I did a reboot the extra Linux icon in refind disappeared and is now working perfectly.

My next question is about peripheral compatibility. After some experimenting & research it appears that my wireless keyboard and magic mouse are not too friendly with my mbp in ubuntu especially when switching between OS. If there was an easy solution to this I would have already found it but is a true duel boot setup even possible with this hardware? I am willing to spend some time on this; if not are there any bluetooth input devices that work well with this or are all mbp's?

---

