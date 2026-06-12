---
title: "Running into problem while trying to boot with CD and HD"
date: 2007-06-03
forum: Absolute Beginner Talk
---

### Post by LobbyDizzle on 2007-06-03
I recently installed Ubuntu 7.04 with no problem at all. The CD booted up beautifully and I partitioned everything as they recommended. When I went to boot up without the cd, it would sit at the loading screen for a good 5 minutes, then a black screen with an error would read.

[I]BusyBox v1.1.3 (Debian 1:1.1.3-3Ubuntu3) Built-in shell (ash)
Enter 'help' for a list of commands.

/bin/sh:can't access tty; job control turned off
(initramfs)[/I]

I asked on the IRC channel and they said just to reinstall, but when I went to boot up the cd it read the same thing, except the last line read:

*(initramfs) [  112.748674 ata3.00: failed to set xfermode (err_mask=0x4)*

Oh, I have no floppy drive and I had all of the USB drives disconnected.

SPECS:
Pentium D 850
2 gig ddr2
GeForce 6600 256mb
Sound Blaster Audigy

---

### Post by jfinkels on 2007-06-03
> **LobbyDizzle said:**
> I recently installed Ubuntu 7.04 with no problem at all. The CD booted up beautifully and I partitioned everything as they recommended. When I went to boot up without the cd, it would sit at the loading screen for a good 5 minutes, then a black screen with an error would read.

[I]BusyBox v1.1.3 (Debian 1:1.1.3-3Ubuntu3) Built-in shell (ash)
Enter 'help' for a list of commands.

/bin/sh:can't access tty; job control turned off
(initramfs)[/I]

I asked on the IRC channel and they said just to reinstall, but when I went to boot up the cd it read the same thing, except the last line read:

*(initramfs) [  112.748674 ata3.00: failed to set xfermode (err_mask=0x4)*

Oh, I have no floppy drive and I had all of the USB drives disconnected.

SPECS:
Pentium D 850
2 gig ddr2
GeForce 6600 256mb
Sound Blaster Audigy

Have you tried the alternate install cd? [http://releases.ubuntu.com/feisty](http://releases.ubuntu.com/feisty)

---

### Post by LobbyDizzle on 2007-06-03
I haven't, but it says to use the alternate if:

    * creating pre-configured OEM systems;
    * setting up automated deployments;
    * upgrading from older installations without network access;
    * LVM and/or RAID partitioning;
    * installs on systems with less than about 256MB of RAM (although note that low-memory systems may not be able to run a full desktop environment reasonably). 

I do not fall into any of these categories, but I'm downloading it anyway.
And why would the CD work at first, in order for me to get Ubuntu installed, then just crap out on me? The successfully installed Ubuntu does not work.

---

### Post by jfinkels on 2007-06-03
> **LobbyDizzle said:**
> I haven't, but it says to use the alternate if:

    * creating pre-configured OEM systems;
    * setting up automated deployments;
    * upgrading from older installations without network access;
    * LVM and/or RAID partitioning;
    * installs on systems with less than about 256MB of RAM (although note that low-memory systems may not be able to run a full desktop environment reasonably). 

I do not fall into any of these categories, but I'm downloading it anyway.
And why would the CD work at first, in order for me to get Ubuntu installed, then just crap out on me? The successfully installed Ubuntu does not work.

I have no idea, I just suggest the alternate install disc as a panacea :D

---

