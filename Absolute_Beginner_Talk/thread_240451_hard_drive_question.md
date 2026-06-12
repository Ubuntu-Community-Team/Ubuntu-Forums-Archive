---
title: "hard drive question"
date: 2006-08-20
forum: Absolute Beginner Talk
---

### Post by cleversleazoid on 2006-08-20
besides my main HD (dev\hda) i also have 2 other hard drives with a slew of partitions for each that was carried over from windows xp. i formatted them all to ex2, but ubuntu refuses to let me write to ANY of my HDs including the one ubuntu is installed to. I can only write to my user directory. Are there some kind of permissions i need to set?

---

### Post by meng on 2006-08-20
Are these other partitions being mounted somewhere, or were you expecting to have read/write access without mounting?

---

### Post by nanotube on 2006-08-20
it seems that you may be having trouble with permissions. you should read through this article first, that will help you:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

basically, unless those drives are mounted specifically to give your user permissions to write to them, you won't be able to, and will have to use "sudo", or remount them for your user.

you can get (a lot) more info on customizing your install in the links in my sig. :)

---

### Post by cleversleazoid on 2006-08-20
> **meng said:**
> Are these other partitions being mounted somewhere, or were you expecting to have read/write access without mounting?

i tried mounting them, it gives me this error


Unable to mount the selected volume. 
error: device /dev/hdd5 is not removable

error: could not execute pmount

---

### Post by meng on 2006-08-20
Okay now I know what the problem is:
[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)
but the type (for you) will be ext2, not vfat or ntfs

---

### Post by cleversleazoid on 2006-08-20
okay, i have them all mounted now, but i still cant write to them. i read the wiki page posted above, but its not very clear (to me atleast). i can log in as root, but i dont have a clue what to do after that to give myself permission to write to the mounted drives.

---

### Post by cleversleazoid on 2006-08-20
sorry to double post, but i was able to create a temporary solution by changing my users home directory to \
if anyone has a REAL solution to this, i'd like to know. until then, i guess i can live with this.

---

### Post by meng on 2006-08-21
[http://www.psychocats.net/ubuntu/mountlinux.html](http://www.psychocats.net/ubuntu/mountlinux.html)
especially the bit -
sudo chown -R marie:marie /storage
sudo chmod -R 755 /storage

---

### Post by shlomy1979 on 2006-08-21
hi i need help i install ubuntu 6 on my primary HDD and i have another HDD in NTFS i tried to undestend the guide but not working for me if some one here know hebrew please help me 
my english is weak sorry

tnx
shlomi baruch

---

