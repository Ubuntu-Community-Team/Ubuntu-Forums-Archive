---
title: "Windows Fanboy Conversion...Ubuntu install problem"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by ben0r on 2007-04-22
Hey guys,

Big time linux newb here.  I've been a windows fanboy all my life and i'm finally ready for something new!

I had windows installed on a 2 x 160gig raid 0.  I deleted the raid, and proceeded to install ubuntu on the first of the 2 drives.  The Ubuntu installer formats the drive into 2 partitions, I believe, and tells me to restart (and reminds me to take out my live cd).  When it restarts, it acts likes its trying to boot off the HDD, but I get nothing but a blinking line-- i left it blinking throughout the 4th quarter of the laker/suns game.

I know my bios is telling it to boot from the correct hdd (as when I change it, it tells me to insert a bootable media)

Right now I'm restarting the installation process on the same drive.

Any ideas to why its not working?

is it screwy since the hdd prolly had all raid data still on there from windows?  

/me twiddles thumbs

---

### Post by lamalex on 2007-04-22
how is your raid set up? does your motherboard have hardware raid? i had a similar problem and it turned out that my disks were plugged into the SATA RAID controller and not the generic SATA controller. Is your bios detecting the disks? did you make sure your partition was bootable when you installed? You might want to try formatting the disks first, dariks boot and nuke does a realllly good job of getting rid of all the data on the disks.

---

### Post by ben0r on 2007-04-22
I guess I jumped the gun, reinstalled and now I'm at the login screen :)

Thanks for reading though!

---

### Post by ben0r on 2007-04-22
> **Iamalex said:**
> how is your raid set up? does your motherboard have hardware raid? i had a similar problem and it turned out that my disks were plugged into the SATA RAID controller and not the generic SATA controller. Is your bios detecting the disks? did you make sure your partition was bootable when you installed? You might want to try formatting the disks first, dariks boot and nuke does a realllly good job of getting rid of all the data on the disks.

Yeah, I made sure the raids were bootable, it just needed to be formatted twice I guess.  

Thanks

---

