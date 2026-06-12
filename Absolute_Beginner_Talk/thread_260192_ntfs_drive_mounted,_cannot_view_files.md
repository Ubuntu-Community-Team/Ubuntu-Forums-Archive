---
title: "ntfs drive mounted, cannot view files"
date: 2006-09-18
forum: Absolute Beginner Talk
---

### Post by sevenhands on 2006-09-18
Scroll down to avoid backstory;
So I've been a Linux user for about 2 weeks. I have a buddy with a labtop running Windows that has had a LSASS.exe error (go figure Windows breaking itself, because it hates itself). The boot tables are good, the only problem is that computer has reset it's passwords. So I figure I would try and use Ubuntu live CD to copy out data to a firewire connected external hard drive. I mount the drive but I cannot see anything on it.
Question:
Is it possible to copy windows files from one ntfs hard drive to another using Linux or can I dump a newly configured LSASS.exe into the damaged windows drive using Linux.

---

### Post by bulldog on 2006-09-18
It should be possible.

But if the drive is encrypted you can't

Windows reset the password?
Which password?

Your friend is the legimate owner of the laptop?
Then he should contact the manufacturer of the laptop.

They can help you out.

---

### Post by buffy^ on 2006-09-18
There should be no problems reading an NTFS drive as long as you have enabled the NTFS support which last I checked, was still experimental. It might be just as easy for you to slap the disk in to a windows machine and copy it off that.

Or you could plop the XP cd in and reinstall windows over it and load as pernormal, you could try safe mode and system restore.

---

### Post by bulldog on 2006-09-18
> **buffy^ said:**
> There should be no problems reading an NTFS drive as long as you have enabled the NTFS support which last I checked, was still experimental. It might be just as easy for you to slap the disk in to a windows machine and copy it off that.

Or you could plop the XP cd in and reinstall windows over it and load as pernormal, you could try safe mode and system restore.


Reading is fully implemented in Ubuntu writing however is experimental.

I'm always a little precourcious when some body with a laptop wants to copy files.

Specially when the password is missing.

No help from me.

---

### Post by sevenhands on 2006-09-18
The LSASS.exe is the security feature that windows has built in. He is the legimate owner of the laptop no questions asked. In fact just the other weekend I watched him login myself. We have run the repair utility which asks for the admin password, his does not work due to the .exe being corrupt. The laptop is 3 years old and out of warranty. My friend is just trying to get his digital life off the computer. After that I kick him and make him switch to ubuntu.

---

### Post by bulldog on 2006-09-18
If you mount the drive correct you should see the files and you can copy them.

Tell us how you did mount the hdd.

The hdd where you want to copy the files to must be FAT32 not NTFS because you can't write to it.

---

### Post by sevenhands on 2006-09-18
> **bulldog said:**
> Reading is fully implemented in Ubuntu writing however is experimental.

I'm always a little precourcious when some body with a laptop wants to copy files.

Specially when the password is missing.

No help from me.

Not to prove you wrong, just to keep a reputation, after (if) this has been fixed I will make a slideshow with the laptop in question and it's owner from the past few years (he uses it for shows so it won't be hard).

---

### Post by sevenhands on 2006-09-18
I popped in the live CD, booted and it was mounted or so it said when I tried the "mount -t ntfs /dev/hda1 /mnt" command. I just saw something about FUSE, any idea if that's the ticket?

---

### Post by bulldog on 2006-09-18
Mount the hdd as follows

sudo mkdir /mnt/laptop

sudo fdisk -l
And select the name of the desired partition.

sudo mount -t ntfs /dev/??? /mnt/laptop

Where ??? stands for the selected partion found with fdisk.

Now you can go to the laptop dir and see your files.

---

### Post by sevenhands on 2006-09-18
Ok, I will try when I'm off work and post the result, thanks!

---

