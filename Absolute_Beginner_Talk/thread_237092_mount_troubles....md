---
title: "mount troubles..."
date: 2006-08-15
forum: Absolute Beginner Talk
---

### Post by dillbertdabomb on 2006-08-15
i was trying to access my hard drive and it said this:

error: device /dev/hd2 is not removable
error: could not execute pmount

whats wrong?

im using the normal version on a 64 bit processor - could that be it?
and will it stop  me from installing?

---

### Post by meng on 2006-08-15
Most likely nothing is wrong.

Are you referring to hda2? hdb2? hdc2?

In any case, either edit your /etc/fstab to automatically mount /dev/hd(whatever)2 to a fixed mountpoint, or else manually mount it by:

(sudo) mount /dev/hd(whatever2) [whatever mountpoint you desire]

---

### Post by dillbertdabomb on 2006-08-15
all i got was 
mount: can't find /dev/hda2 in /ect/fstab or ect/mtab

and it says the same message for all drives

but thats the only problem I have...

---

### Post by meng on 2006-08-15
You have to choose a mountpoint!
e.g.
mount dev/hda2 /mnt/tmp
OR
mount dev/hda2 /home/dillbert/otherdrive

or whatever you choose
so long as that mountpoint exists as a directory

---

### Post by dillbertdabomb on 2006-08-15
it did'nt work, it said the directory did'nt work...

could it be the fact that im using the intel x6 version on my amd 64?

or 512 mb of ram?

---

### Post by meng on 2006-08-15
I think neither of those would explain it. What do you mean by "the directory didn't work"? That could not have been the exact error message. Are you sure the directory exists in the first place. If not, you have to "mkdir" it. As a general rule, in these forums it is a good idea to post the commands you tried, and the output returned.

---

### Post by dillbertdabomb on 2006-08-15
the directory didn't exist?

---

### Post by meng on 2006-08-15
Well then at the prompt type
mkdir /full/path/of/directory

(Yes, you can mkdir relative as well as absolute names, but this is the most straightforward instruction I can give you.)

then mount. You can only mount to an existing directory, not a nonexistent one.

---

