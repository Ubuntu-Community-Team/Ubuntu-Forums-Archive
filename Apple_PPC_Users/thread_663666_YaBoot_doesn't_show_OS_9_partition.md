---
title: "YaBoot doesn't show OS 9 partition"
date: 2008-01-10
forum: Apple PPC Users
---

### Post by smileyme on 2008-01-10
I installed OS 9 on 1 Gig  partition and left the rest unformatted.

I ran the live install of Feisty and all went well. However, when I rebooted there wasn't any option for OS 9.

YaBoot is installed and shows Linux and CD-ROM only.

B&W Rev A, 300 MHz, 6.4 GB HDD, 512 MB RAM, CD-ROM.

Any help would be appreciated.

Ric :)

---

### Post by guidop on 2008-01-11
If you installed Feisty (7.04), you may have experienced the problem discussed in this thread, where I believe the (newer) disk partitioning tool corrupts the special OS 9 driver partitions:

[http://ubuntuforums.org/showthread.php?t=495347](http://ubuntuforums.org/showthread.php?t=495347)

I worked around the problem by re-installing OS 9, installing Dapper (6.06), and then upgrading.
I also had to modify yaboot.conf to manually add the OS 9 partition.

I don't know if fkdev's suggestion to try reinstalling the drivers works - maybe try that first and report whether or not it works.

---

### Post by ryanVickers on 2008-01-11
people still use pre OS X? huh! :p

I would bet it's because its the old HFS and not HFS+, and it doesn't support this anymore...

ah, this brings back memories of the days when the Macintosh flat filesystem,.. good times, good times... :p

---

### Post by smileyme on 2008-01-11
Fortunately, this machine is only a test bed. I actually no longer use OS 9 even in classic mode. This was just a test. The machine came to me with the understanding "It will not run OS X". I thought to verify OS 9 and Ubuntu first. That done (even if I can't dual boot) I will reformat and install OS X. See if I can get it to run.

Back to the issue of Dual Boot; when I boot with the OS 9 CD, my only option is to reformat the whole drive. The HFS + partition is gone. Ubuntu shows it as "Untitled", but OS 9 doesn't show it at all. I installed a Firewire card, and tried to boot Tiger from a Firewire drive, but I don't think the B&W can boot to a Firewire drive attached to a PCI card. I know it can't boot from the onboard Firewire. Being a Rev 1 board, I may need to install a PCI ATA card to get OS X running. We'll see.

Rick :)

---

### Post by guidop on 2008-01-11
Your dual-boot issue sounds exactly like the problem I experienced in the thread referenced above.  Linux and OS X will see the HFS partition, **but OS 9 cannot** because the OS 9 drivers are corrupted.  In this state, one can still use mac-on-linux to boot the OS 9 installation, but cannot boot it directly.  The OS 9 install CD (nor any other OS 9 based utilities CD) won't be able to see any partitions on the hard drive.

Since you are just playing with this machine, why not wipe the machine and start over, using one of the work-around methods described in the thread?  You will need to burn a Dapper CD (6.06.1, worked I think) to use the older partitioning tool.

If your machine has Firewire ports, you should be able to install Mac OS 10, up to 10.4.  I think both 10.3 and 10.4 should run decently on that machine, since you have 512 MB RAM.   The relatively low 300 MHz processor speed will probably limit you to only running one "heavy" app at a time, such as watching a small format flash video on the web.  3rd party processor upgrades are still available, but you will likely spend as much ($150-$300) as the machine is currently worth.

---

### Post by bobby b on 2008-01-23
> **guidop said:**
> 
I don't know if fkdev's suggestion to try reinstalling the drivers works - maybe try that first and report whether or not it works.

Installing 7.10 on an old world mac resulted in exactly this problem. Running the disk setup utility and just doing the reinstall drivers options fixed it for me.

---

### Post by stream303 on 2008-01-24
> **guidop said:**
> You will need to burn a Dapper CD (6.06.1, worked I think) to use the older partitioning tool.

Interesting - I just noticed that Dapper 6.06 for PPC is no longer available in the cdimage area - Feisty is the earliest now.  I guess I've been out of the loop, I thought LTS was part of the 6.06 release - even for desktops.  Maybe so, but you can't download it anymore?

---

### Post by guidop on 2008-01-25
Ubuntu Dapper 6.06 and Edgy 6.10 for ppc were supported releases, so the cd images are in the _releases_ directory:

[http://www.cdimage.ubuntu.com/releases/6.06.1/release.1/](http://www.cdimage.ubuntu.com/releases/6.06.1/release.1/)

Feisty and up for ppc  are in the ports directory:

[http://www.cdimage.ubuntu.com/ports/releases/7.04/release/](http://www.cdimage.ubuntu.com/ports/releases/7.04/release/)


If you start at the link below, and follow the appropriate flavor->release|port->version path, you should be able to find what you're looking for:

[http://www.cdimage.ubuntu.com/](http://www.cdimage.ubuntu.com/)

---

### Post by smileyme on 2008-01-25
> **bobby b said:**
> Installing 7.10 on an old world mac resulted in exactly this problem. Running the disk setup utility and just doing the reinstall drivers options fixed it for me.

There was only the option to reformat the entire drive.

Anyway, I've given up, for the time being, and installed OS X and Ubuntu 7.04 on a revision 2 B&W running a 500 MHz G4. I was hoping, and proven right, that the B&W would utilize the L2 cache with out helper software, unlike the Beige  I have, which  runs a G3 at 500 MHz  because of the L2 Cache issue with the G4s.

Rick :)

---

