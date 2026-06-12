---
title: "What does copying files lockup Ubuntu?"
date: 2007-04-17
forum: Absolute Beginner Talk
---

### Post by kc5hwb on 2007-04-17
I have Ubuntu installed on 2 machines, 1 is 6.10 server and the other is 6.10 Edgy.  On both of these machines, anytime I try to copy files over from another drive, CD, DVD or anything, it will start to copy, bring some of the info over, then freeze up my whole system, forcing me to hard shutdown and reboot.

In my server I have 3 secondary drives.  There is info on one drive that I want to copy to another, about 200GB worth.  I try to drag 1 or a few folders at a time, anywhere from 2-10GB and this freeze-up happens.

On my Edgy box, I am trying to copy some MP3s from a dvd onto the HDD.  I tried one folder, which was about 45MB and at the very end, it locked the system up and I had to reboot it with the reset switch on the tower case.

I am afraid I am going to mess up something in my File System by having to reboot like this.  I can't figure out how to end the task without just rebooting.  Does Ubuntu have something like CTRL-ALT-DEL?

Any ideas on what is causing this lockup on 2 machines?

---

### Post by frrobert on 2007-04-18
How were you copying the files? 

 I noticed that with 6.06 Nautilus would lock up with large files but transfers would work find with by copying in the terminal  or with thunar.  So you may want to a different method of copy

---

### Post by Ti_Uhl on 2007-04-18
It sounds like your having problems with your ide controllers. Are you using any exotic hardware to connect those drives ( RAID / SCCI ? ) ? what kind of motherboard do you have ? 
 
Also your dmesg or log file could be of some help and can contain some information as to why your hd read / write operations fails. 
 
I had simular expieriences when using an nforce 4 Raid controller, after disabling the raid controller and use the normal approach, the problem was fixed....

---

### Post by kc5hwb on 2007-04-19
I am running 6.10 Edgy and using the file browser (Nautilus?) to drag files from one location to another.  I am not sure I know the command for Terminal, or have ever done that.  And yes, some of them are large, but I have tried smaller ones and had the same problems.

I am nor running anything strange... SATA drives and IDE drives.  My file server has a IDE drive for the File System main drive (which I am not trying to copy anything to/from) and it has 3 secondary drives, 1 is IDE and the other 2 are SATA.  They aren't RAID.

Which log file would you want?

DMESG:
```
[42949372.960000] Linux version 2.6.17-10-server (root@vernadsky) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Fri Oct 13 18:47:26 UTC 2006 (Ubuntu 2.6.17-10.33-server)
[42949372.960000] BIOS-provided physical RAM map:
[42949372.960000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[42949372.960000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[42949372.960000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[42949372.960000]  BIOS-e820: 0000000000100000 - 000000000fff0000 (usable)
[42949372.960000]  BIOS-e820: 000000000fff0000 - 000000000fff8000 (ACPI data)
[42949372.960000]  BIOS-e820: 000000000fff8000 - 0000000010000000 (ACPI NVS)
[42949372.960000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[42949372.960000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[42949372.960000]  BIOS-e820: 00000000ffee0000 - 00000000fff00000 (reserved)
[42949372.960000]  BIOS-e820: 00000000fffc0000 - 0000000100000000 (reserved)
[42949372.960000] 0MB HIGHMEM available.
[42949372.960000] 255MB LOWMEM available.
[42949372.960000] On node 0 totalpages: 65520
[42949372.960000]   DMA zone: 4096 pages, LIFO batch:0
[42949372.960000]   Normal zone: 61424 pages, LIFO batch:15
[42949372.960000] DMI 2.3 present.
[42949372.960000] ACPI: RSDP (v000 AMI                                   ) @ 0x000fa420

```

---

### Post by kc5hwb on 2007-04-21
Anyone else have an idea on this?

---

### Post by kc5hwb on 2007-04-21
Now when I try to download 7.04 Fiesty, the download goes about half way and then causes Edgy to reboot.  I have tried it about 4 times.

I have about had enough of Ubuntu....

---

### Post by Cariboo1938 on 2007-04-21
> **kc5hwb said:**
> Now when I try to download 7.04 Fiesty, the download goes about half way and then causes Edgy to reboot.  I have tried it about 4 times.
I have about had enough of Ubuntu....
Very interesting....
I also have a problem upgrading as recommended[ HERE]("http://www.ubuntu.com/getubuntu/upgrading"). 
It worked for 234 of 1019 packages and then it stopped...see also this [THREAD.]("http://ubuntuforums.org/showthread.php?p=2505115#post2505115")
Has anybody an idea?

---

### Post by kc5hwb on 2007-04-21
I think that I am just going to download 7.04 in the AMD64 version, and do a fresh install.  I have been having too many other problems with it.

The Edgy version that I am running now isn't the AMD764 version, it is the standard one.  But I have it on a AMD64 box.  Would this cause any issues?

---

### Post by kc5hwb on 2007-04-22
Anyone else?

---

### Post by kc5hwb on 2007-04-25
A wipe of the box and a fresh install of Fiesty 7.04 fixed this problem........ so far.

I have been on  Fiesty for about 24 hours now.  No lock-ups, freezes and everything seems to work.

---

### Post by eentonig on 2007-04-25
what happens if you give nautilus a higher "nice" value?

---

### Post by kc5hwb on 2007-04-25
> **eentonig said:**
> what happens if you give nautilus a higher "nice" value?

Explain what that is....

---

