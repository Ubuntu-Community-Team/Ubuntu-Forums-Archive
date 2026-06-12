---
title: "Sata Raid drives not available"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by FriscoZR on 2007-04-23
Hi,
I'm trying to add in two drives in a mirrored array.
The drives are on the sata interface where as the system drive in on the ide.
The bios sees the drives as part of a raid set.
The device mgr on the system sees the drives. Mounted and partition fields are false. It does seem to have a flag set that says they are part of a raid set.
In the browers they show as dev/sda, and dev/sdb. These seem to be only accessable by the root and not the user. How do I correct this?

The eventual goal is to make these available as offline storage/backup for my window network.
In that guise, I can see the windows machines and log on to them, but I can see the box but I can't logon the other way around. Any thoughts there would be appreciated too.

Thanks in advance for any help or ideas on what to do would be appreciated.
Regards,
MP

This is on 7.04 desktop for amd64 - thx.

---

### Post by psusi on 2007-04-23
You should read [https://wiki.ubuntu.com/FakeRaidHowto](https://wiki.ubuntu.com/FakeRaidHowto)

---

### Post by FriscoZR on 2007-04-23
Thanks for the reference.
It seem more complicated than I suspect I need since I'm not doing dual boot or going to run my image from the raid array. I already have 7.04 up and running from a dedicated ide drive.

Can you or someone explain what, from that reference, is or is not needed if I'm just wanting to use these raid drives as network storage? The idea here for me is to have these drives hot swappable with other data drives in the future.

Thanks again for the assist.
MP

---

### Post by psusi on 2007-04-23
You can just forgo the bios raid support then and set them up using a linux software ( md ) raid.  The only real reason to use the fakeraid support is so it can be booted from and to dual boot with windows.

---

### Post by epee on 2007-04-25
I have just added 2x320Gb SATA drives to my system - which was installed on an IDE drive.

I followed this : [SATA_RAID_Howto]("http://www.ubuntu-in.org/wiki/SATA_RAID_Howto")

Now that one also assumes booting from the SATA drives - which I didn't want.

So I didn't boot from CD, but worked on my live system. Although I installed dmraid, as instructed, I found that I didn't have gParted - but when I looked in /dev/mapper I found /dev_mapper/nvidia_xxxxxxxx - i.e. the system had already recognised the SATA drives I'd setup in the BIOS.

[I'm not sure if I even needed dmraid now...]

When I ran 
```
sudo dmraid -ay
```
as instructed it informed me there were no changes. As I wanted to use all of the SATA capacity for my /home I wasn't bothered about any further partitioning anyway.

I formatted the partitions using mkfs.ext3 as shown in the howto - that just worked.

At this point, you're done with the above mentioned Howto.

I then moved my current /home onto the new SATA partition and everything is working fine, so far.

---

