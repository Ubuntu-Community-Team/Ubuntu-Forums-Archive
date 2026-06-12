---
title: "Cannot get ubuntu 6.10 to recognise motherboard raid"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by bertram_wooster on 2007-04-19
Hi,

I can't seem to get any of ubuntu's install packages to recognise my RAID array.

I have the following basic hardward setup:

MSI Platinum p965 mobo
Pentium Core 2 Duo processor
2 SATA seagate 300Gb disks
1Gb RAM

and I have used the on board drivers (ICH8R) to setup a single RAID0 across the two disks.

I have then installed Windows XP on the machine (not without some trouble) and used it to partition my RAID0 into a few partitions meant for OSs (one for XP, one for ubuntu etc) and a large partition for file storage. The reason I did it this way is that I was told that Windows doesn't recognise linux partitions, and that doing it this way was safer.

I now wish to install ubuntu on the machine, but none of the install CDs seemed able to recognise the RAID array and hence the partitions. I have tried the x86, the alternate install and even the amd64 version, but without success.

From reading around the subject I am beginning to get the feeling that I have done things wrong, and that there is no chance of getting ubuntu working on the RAID array, but have a maturing install of XP now and would prefer not to scratch it. Can anyone give me some guidance?

Thanks in advance,
Bertie

---

### Post by leibowitz on 2007-04-29
I don't have any RAID device here. But found this:

[http://www.linuxcompatible.org/compatdbprint15951.html](http://www.linuxcompatible.org/compatdbprint15951.html)

>  Everything working except:
JMB361 RAID Controller- SATA port works. PATA port does not work.
Issue present in Ubuntu 6.10 and Ubuntu 7.04. Recommended solution is do either get a PATA->SATA adapter for your IDE devices, or do not buy this board for your linux PC. 

---

### Post by jeblinux on 2007-05-28
Almost no desktop motherboard chipsets support true (hardware) raid. They are almost all software raid devices. A special driver in combination with the BIOS implements the functionality of RAID. As far as I know no chipset makers have released these drivers for Linux.

If you want hardware RAID, buy a RAID controller card and add it to you computer. If you want software RAID look for information on mdadm.

The [libata]("http://linux-ata.org/faq-sata-raid.html") Web page has more detailed information.

---

### Post by misfitpierce on 2007-05-28
Did you try maybe clicking install or run ubuntu from disc with driver software from the menu with disc in at boot? That might be how to load RAID drivers but I dislike raid and am not 100% sure

---

### Post by bertram_wooster on 2007-06-05
Hi All,

I have since posted another (more informed request) here;

[http://ubuntuforums.org/showthread.php?t=419621](http://ubuntuforums.org/showthread.php?t=419621)

Thanks,
Bertie

---

