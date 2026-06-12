---
title: "Encrypted partition/volume OS X &lt;-&gt; Linux... options?"
date: 2010-10-06
forum: Apple Hardware Users
---

### Post by jwhendy on 2010-10-06
Hi,


I'm about to take the plunge, reinstall OS X and Linux with encryption... but don't know what my options are with respect to sharing.

Am I limited to TrueCrypt? Is that it?

I'd go the dm-crypt/LUKS option but don't know if there's anything that can open that in OS X.  [OSXCrpyt]("http://www.osxcrypt.org/") says that because of their framework, "Implementing dm-cryppt on mac, for example, is now trivially easy" but I have seen nothing to suggest that it's actually feasible at present.

Based on the [WIKI]("http://en.wikipedia.org/wiki/Comparison_of_disk_encryption_software") comparing encryption software, it doesn't seem like there's anything... am I right in seeing this? I see two commercial options that work on Linux/OS X and PGP disk that works on Win/OS X.

If there really is nothing, I'm open to suggestions from other dual booters on how one might work around this... I dislike the idea of two home directories because it just botches my ability to backup nicely -- I have redundancy and have to merge directories and such. I have to admit, though, I haven't tackled the whole backup-with-encryption deal anyway, yet.

Nuff from me. Thoughts? Suggestions? What others are doing?

Thanks!

---

### Post by jwhendy on 2010-10-07
Well, after reading a whole bunch last night... here are my refined thoughts:

--( Option 1 )--
> sda1: GUID partition table
> sda2: HFS+ volume for OS X
>>> TrueCrypt volume to be created and mounted at /home
> sda3: /boot for Linux
> sda4: Linux with dm-crypt/LUKS
>>> just / (no LVM making separate partitions)
>>> mount the OS X TrueCrypt volume for filesharing between OSs

**Notes:** I don't like this for a couple of reasons.
- I have to kind of guess at how much OS X will accumulate over time and make my TC volume for /home accordingly. If I ever run into issues... I'll have to backup, delete, make a new and larger TC volume and then copy it all over


--( Option 2 )--
> sda1: GUID partition table
> sda2: OS X
>>> FireVault used on /home
> sda3: /boot for Linux
> sda4: Linux with dm-crypt/LUKS
>>> take the plunge and just start keeping all my files on Linux instead of OS X (everything used to be on OS X and I'd just mount the HFS+ drive in Linux to access things)
>>> perhaps create a TC volume file that can be used to share files between partitions via the OS X /Shared directory?

**Notes:** I like this better. Everything is encrypted and thus I can just estimate like 15-20GB for OS X and only keep OS X specific files there (iWork, i* files, etc.) and then make the rest of the disk available for Linux. Since dm-crypt can be used for the whole Linux partition I can let everything (/usr, /var, /home) grow however it wants and not worry about my bad partition size/TC container size predictions.


**Remaining issues/questions:**
- Still bummed that I can't just keep everything on one OS or the other and share unless I go the TrueCrypt container for OS X home route
- Unanswered question remains of whether I can mount logical volumes on both OSs. If I have a logical HFS+ volume in an extended partition, can Linux mount that and vice versa (assuming the filesystem is readable by both, that is)?
- How others get around the issue of making partition size predictions when creating separate partitions for /home vs. /, /usr, etc.
- What partitions are nice to have on their own (besides /home)?

---

### Post by Iowan on 2010-10-07
Moved by request. :)

---

