---
title: "Problem with external HDD?"
date: 2013-09-08
forum: Any Other OS
---

### Post by Jamie_Edwards on 2013-09-08
Hi guys,

So I recently bought a Western Digital Elements External HDD and because it didn't play well with my server I formatted it to EXT4, all went well for a little while and finally it played well.

Now my dad wanted to use it as a backup with Windows WITHOUT having to access the server so I unplugged it from there and tried accessing it from within windows to no avail. (It wouldn't read from the hard drive) I thought it may have been because the drive was in an EXT4 format, so I reformatted to NTFS.

Now here's the weird part...

I can access the drive (Which is now NTFS) from my Linux distro, but when it comes to Windows 7, it has the same problem as before the reformat. ( where windows won't even read from the drive).

Any ideas on what's going on and how I could fix it?

Thanks.

Jamie

---

### Post by orb9220 on 2013-09-08
Did you do a real formating drive or just Quick format?
Always do true format and uncheck the Quick format option. 

I would first go to the drive partition and examine what kind of partitions are on the drive and Delete the partition. 
Then create new partition and format it NTFS.

Can do this from Windows Admin tools Disk manager. Or boot up with a live CD and use gparted on the drive.

And yes Windows doesn't do ext4 out of the box you have to install special 3rd party to give windows ext4 abilities.
Easier tho to keep all external usb drives as Ntfs as Linux & Windows can then access without headaches or hoops to jump thru.
.
.

---

### Post by Jamie_Edwards on 2013-09-18
The problem I have is that I don't think that the drive is actually being picked up by Win7?

---

