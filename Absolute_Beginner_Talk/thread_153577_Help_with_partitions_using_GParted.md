---
title: "Help with partitions using GParted"
date: 2006-04-01
forum: Absolute Beginner Talk
---

### Post by Jong on 2006-04-01
I've followed this [well-written]("http://www.hezardastan.org/breezy_xp_dualboot/en/") guide on how to create partitions with GParted. However it doesn't explain much  about what each partition is for, and why a partition is located where it is.

In the guide you create the following partitions:

/dev/hda6, logical partition, ext3, /home
/dev/hda7, logical partition, linux-swap, swap
/dev/hda3, primary partition, ext3, /

I assume /dev/hda3 is the root, where the system is installed. I can't though quite figure out what /dev/hda6 is for. I can see there's a directory with that name in the filesystem, and apparently it seems to function alike the document user directory in Windows, or am I wrong? The final directory, /dev/hda7, is causing me a bit problems also. I would assume it's for the boot swap between Linux / Windows, but then again, leaving 1GB off seems much to me.

My next questions is about the actual partitions creating. In the guide it assumes you have an extended /dev/hda2 already. In case you don't have this partition, do you then have to create it for the /home and swap. In case so, why is it nessecary having an extended partition for those logical partitions? Final question, why is the root, /dev/hda3, placed outside the extended partition?

---

### Post by siminone on 2006-04-01
Hi Jong

In Linux, partitions as well as devices are 'mapped' to folders. This is called mounting. This is different in Windows where they are given drive names like D:, E: etc

In your case /dev/hda6 is mounted to /. As you correctly asumed, it is the root, where all the sytem files are stored.

/dev/hda6 is stored as /home. This contains all the user's files and settings. Again like the My Documents section in WinXP.

Finally /dev/hda7 is the swap partition. This is the same  as Windows where the system uses a portion of diskspace as 'more memory'.

The bare minimum partitions that linux needs is a partition for /. I'm not sure if one is required for swap.

You don't need a partition for /home but the beauty of having a seperate partition for this is that if you have problems with your system you can reinstall Ubuntu without losing your personal fiiles!!

---

### Post by Jong on 2006-04-01
Ahh, thanks alot siminone.

So does that mean, I can mount basically any logical partition to /, regardless of its location, as long as I keep the primary partition last?

---

### Post by Sef on 2006-04-01
[So does that mean, I can mount basically any logical partition to /, regardless of its location, as long as I keep the primary partition last?]("So does that mean, I can mount basically any logical partition to /, regardless of its location, as long as I keep the primary partition last?")

The primary partition does not have to be last.

---

### Post by Jong on 2006-04-02
OK, thanks.

---

