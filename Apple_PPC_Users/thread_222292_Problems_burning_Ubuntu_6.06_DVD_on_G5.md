---
title: "Problems burning Ubuntu 6.06 DVD on G5"
date: 2006-07-24
forum: Apple PPC Users
---

### Post by nils. on 2006-07-24
Hi,

I just downloaded the Ubuntu Dapper Drake DVD iso to install on my computer.  I downloaded it with bittorrent and everything seemed to go fine.  Except when I go to Disk Utility to burn it, it always fails, saying there was a 'media write error'.  I've used up three DVDs on it, so I know it wasn't just a single faulty DVD.  Also, I've used DVDs from the same package on the same computer and burned other things, so I know the burner is working.  

I thought maybe it was the iso file, and so I clicked on 'Verify Disk' in DVD and I get the following error.

> **Verifying volume “Ubuntu_PowerPC_dapper”**
Checking HFS volume.
[color=red]Invalid number of allocation blocks
The volume  needs to be repaired.

**Error: The underlying task reported failure on exit**[/color]


[b]1 HFS volume checked
[color=red]Volume needs repair[/color][/b]

I just don't know what this means or how I can fix it.  I've tried deleting and re-downloading the DVD iso, but the same error still occurs.  Do I need to use different software to make it burn correctly?

Any help would be much appreciated!

Nils



The computer works fine and software is completely up-to-date, but here are the specs:
> **POWER MAC G5:**
   Machine Model:  PowerMac7,3
        CPU Type:  PowerPC G5  (2.2)
  Number Of CPUs:  2
       CPU Speed:  1.8 GHz
          Memory:  1.25 GB

      OS Version:  10.4.7

**PIONEER DVD-RW  DVR-107D:**
  Firmware Revision:  A707
       Interconnect:  ATAPI
       Burn Support:  Yes (Apple Shipped/Supported)

---

### Post by catlett on 2006-07-24
First thing is to verify the download . You do this with a md5sum check. The number you get for your iso download should match this number
> 410d766d75a3afaa7f04c0c7dbdfd8da  ubuntu-6.06-desktop-powerpc.iso
I don't know much about macs but I think the disk utility has a md5sum check option. When you put the iso in to burn it, is there an option in the menu that says "checksum"?
If the numbers match then you can rule out a bad download. The next step is to make sure it is burning correctly. The best thing to do is to burn it as slow  as possible. You want to burn the iso at 2-4x if you can adjust the speed.
The last 2 options are hardware. Not all media are good. There are low quality dvd and cd disks from the far east that will not give good burns. You may have crappy media.
The last is that your dvd writer is not working properly.
I would start with the md5sum. Then burn at 2x or 4x and if it still fails go and buy brand name dvds.
If that fails, borrow a friends computer and burn it there. 
Good luck.

---

