---
title: "Need help with &quot;clever mounting&quot; of HFS+ partition"
date: 2006-12-22
forum: Apple PPC Users
---

### Post by bogoliubov on 2006-12-22
Hello. On my iBook I have added the possibility to mount my OS X partition. But I'd like to only mount my own folders (/Users/username) and not the entire partition. Is this possible somehow?

Here's the relevant line in my fstab:

# Mac OS X Disc
/dev/hda3 /media/macos hfsplus noauto,user,rw 0 0

---

### Post by kidders on 2006-12-23
No, I'm afraid not. If you were thinking ahead, you could have maybe put /Users on a partition by itself (like me!) ... Doing this has certain advantages.

The other issue you're likely to encounter is that the UIDs in use in Ubuntu and MacOS won't match up. This is more serious, as it affects file accessibility on both platforms. Ideally, you would put your MacOS "/Users" directory and Ubuntu "/home" directory on partitions by themselves, and match up the UIDs of the users on your system. That way, access to files would be pretty seamless, no matter which OS you happened to be booted into. If you were feeling really brave, you could of course merge them both together, and use the same /etc/fstab line in Ubuntu & MacOS :-P

---

### Post by bogoliubov on 2006-12-26
I knew I should have created a special /Users partition... 
Thanks for the help!

---

### Post by kidders on 2006-12-26
No problem :-)

You can still do that, if you want to. Boot OSX in single user mode, rename /Users and edit /etc/fstab, much as you would with a Linux box. Then, you would manually mount /Users, _copy_ (not move ... just in case!) all the original stuff into the new partition, and reboot. Two things to remember though...

[LIST=1]
[*]Don't journalise the /Users partition.
[*]Change your UID either in OSX or Ubuntu, so both OSs match.
[/LIST]

---

