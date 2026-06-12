---
title: "/home on /dev/mapper/xxx not seen after install"
date: 2011-12-09
forum: Asus Ubuntu Support (CLOSED)
---

### Post by rbsbscrp on 2011-12-09
Greetings. I posted the stuff below on the installation forum but got no (knowledgeable) responses. Dunno how long I should wait to give it a bump or ask (whine) again... but this is an issue with my ASUS P8P67 B3 revision mboard so maybe the question belongs here. In any case, I've tried everything and exhausted all google searches for an answer. Any help would be much appreciated.    ===  Hi all, ehem... AHHHHHHHHHHHH! I've run Ubuntu x64 on my laptop for years with few problems. Now I've bought a desktop with an Asus P8P67 mboard with a 64gig SSD and 2x2T sata drives config'd in a raid0. Win7 is on the SSD and works fine. I *tried* to install Ubuntu 11.10 amd64 with /boot, root on the SSD and /home on the raid0 (many times, many ways) and have struck out with what seems like the system not being able to mount the /dev/mapper/xxx partitions. I end up with /dev/mapper/xxx_Volume0 and /dev/mapper/control only. At least I can still choose Win7 from the grub menu and have a computer.  Ok, the live Cd doesn't load, just hangs. So I'm using ubuntu-11.10-alternate-amd64. I disconnected the network so there are no updates. I've tried several other linuxes and earlier releases but no joy.    Then I found boot-repair and ran it and it sent my info to [http://paste.ubuntu.com/764648](http://paste.ubuntu.com/764648) . I tried again (this time choosing the softRAID choice) and the result is pasted on paste.ubuntu.com/764650. I think the problem is that the raid0 is not available. Do I need some kind of (extra/external) driver or something?  All of the info I could google so far deals with different issues except I saw that there used to be a bug (in 9.10 I think) that produced the /dev/mapper/xxx_Volume and /dev/mapper/control situation.    Thanks in advance for any help.  -

---

### Post by oldfred on 2011-12-09
Did Windows install in UEFI mode? or BIOS? You can tell if you have gpt on SSD or MBR partitioning.

I no nothing about FakeRAID which is just a motherboard RAID.
Also for installing on fakeraid (motherboard raid), this might help you:
[https://help.ubuntu.com/community/FakeRaid](https://help.ubuntu.com/community/FakeRaid)
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
[http://ubuntuforums.org/showthread.php?t=1777458](http://ubuntuforums.org/showthread.php?t=1777458)
[http://ubuntuforums.org/showthread.php?t=1338445&page=5](http://ubuntuforums.org/showthread.php?t=1338445&page=5)
Software RAID w/mdadm driver
[https://help.ubuntu.com/11.10/serverguide/C/advanced-installation.html](https://help.ubuntu.com/11.10/serverguide/C/advanced-installation.html)

I still have BIOS, but left another partition at the beginning of the drive for efi, when I do a new build. Then the bios_grub will be obsolete, but it is tiny, so it will not matter.
```
fred@fred-MavericDT:~$ [COLOR=Red]sudo parted /dev/sdd unit s print[/COLOR]
Model: ATA SSD G2 series 64 (scsi)
Disk /dev/sdd: 117231408s
Sector size (logical/physical): 512B/512B
[COLOR=Red]Partition Table: gpt[/COLOR]

Number  Start      End         Size       File system  Name  Flags
 1      2048s      616447s     614400s    fat32              boot
 2      616448s    618495s     2048s                         bios_grub
 3      618496s    58925055s   58306560s  ext4         04
 4      58925056s  117229567s  58304512s  ext4         10



```

---

### Post by rbsbscrp on 2011-12-10
> **oldfred said:**
> Did Windows install in UEFI mode? or BIOS? You can tell if you have gpt on SSD or MBR partitioning.

[/CODE]

I'm looking at the disks with (windows) Minitool Partition Wizard and it shows the raid disks being GPT (naturally). It's silent about the SSD so I think that Windows is installed on the SSD in BIOS mode. Thankfully Windows (dual-boot) still runs so I still have a computer. 

The issues seems to me to be that /dev/mapper/xxx_Volume0p1-7 are available/accessable to the partitioner in the Linux installer but later when I try to boot into Linux I get the 

"/dev/mapper/isw_xxxVolume0pX is not ready yet or not present" error. Then nothing I do can fix/repair it. I ran boot-repair again and the results are posted up at [http://paste.ubuntu.com/765567](http://paste.ubuntu.com/765567).

I'm thinking that although trying to apt-get install dmraid shows that dmraid is already there that it is not being called. Now if I could just figure out how to use it. 

I'll pour over your links. Thx.

---

### Post by rbsbscrp on 2011-12-10
Hey! Look what I found:

[http://ubuntuforums.org/archive/index.php/t-1634793.html](http://ubuntuforums.org/archive/index.php/t-1634793.html)

Hmmm. Ok now I see that my problem is that I should have:

```

/dev/mapper/isw_cgfgaghjea_Volume0 <-- device

partitions:
/dev/mapper/isw_cgfgaghjea_Volume01  Microsoft Reserved Partition (Windows)
/dev/mapper/isw_cgfgaghjea_Volume02  Data partition (Windows/Linux)
/dev/mapper/isw_cgfgaghjea_Volume03  Data partition (Windows/Linux) 
/dev/mapper/isw_cgfgaghjea_Volume04  Swap partition (Linux) 
/dev/mapper/isw_cgfgaghjea_Volume05  Data partition (Windows/Linux) 
/dev/mapper/isw_cgfgaghjea_Volume06  Data partition (Windows/Linux)


```instead I only have 

```
/dev/mapper/isw_cgfgaghjea_Volume0 
```( btw /dev/mapper/isw_cgfgaghjea_Volume0--> ../dm-1 )

however, according to the above link, this 
```

kpartx -a -v /dev/mapper/isw_cgfgaghjea_Volume0 

```should create the missing partition mappings... wish me luck... I'll just double check that kpartx is ok on gpt drives and then I'll give it a try.

==

---

