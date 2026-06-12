---
title: "Questions about Raid and read-only system"
date: 2008-04-06
forum: Absolute Beginner Talk
---

### Post by digitalfreak on 2008-04-06
Hi,

I just set up an ubuntu server. I realy like working with linux that way ;).
But now I have some questions.
I am using 2 250 GB HDD with a softraid mirror. 160 GB in a raid1 and the rest as "normal" space.
Now my question. If have to replace one of the HDD some day. Can I use a bigger hdd and just make a 160GB partition or will there be problems if the new hdd has a larger blocksize?

The system itself has been installed on an 4 GB CF-Card. To minimize writing access to this device i later want to use it read only. What do I need to do to make the system read only and still using it normaly?
I want to link or mount directories that need to written to the hdd, but the system should still start if the hdd is not present.
Another option is that I use ramdisks. At startup I mount the ramdisks copy the data of directorys that need to be writable to it, mount it over the directory. And once a day I writ the data back to the cf-card.
So what directories need I to make writeble? I think /proc is one of them...

so long...

---

### Post by Soundman2 on 2008-04-08
> **digitalfreak said:**
> If have to replace one of the HDD some day. Can I use a bigger hdd and just make a 160GB partition or will there be problems if the new hdd has a larger blocksize?

Yes.  I have done this before.  You should be able to replace either drive in the mirror, as long as you can carve out a partition from the new drive that is at least as big as one stripe of the current mirror.  Any block device will do.

> **digitalfreak said:**
> The system itself has been installed on an 4 GB CF-Card. To minimize writing access to this device i later want to use it read only. What do I need to do to make the system read only and still using it normaly?
I want to link or mount directories that need to written to the hdd, but the system should still start if the hdd is not present.

This is really an unrelated question... might be best to post independently?  Anyway, I have not done this before, but it sounds like it would be similar to making a custom Ubuntu Live CD except that you want the OS image stored on a USB drive instead of a CD.

I see many hits for "ubuntu custom live cd" on google.  Here is one:
[https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization)

And, here are instructions to put a "Live CD" .iso image onto a bootable flash drive:
[http://www.pendrivelinux.com/2007/01/25/usb-x-ubuntu-610/](http://www.pendrivelinux.com/2007/01/25/usb-x-ubuntu-610/)

You probably want to leave out the part about making a second "writeable" partition called casper-rw on the thumbdrive for persistent settings.  Better yet, make this partition on your hard disk instead.

Again, this is untested by me, but should work in principle.

Regards,
Soundman2

---

### Post by digitalfreak on 2008-04-09
> **Soundman2 said:**
> 
This is really an unrelated question... might be best to post independently? 

OK I will make a new thread.

The raid is running now ;)

---

