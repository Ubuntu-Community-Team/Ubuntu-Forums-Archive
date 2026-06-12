---
title: "Use Linux for Backup/Restore Windows partition?"
date: 2007-08-31
forum: Absolute Beginner Talk
---

### Post by bme on 2007-08-31
Is there a linux software for backup/restore of windows partition similar to ghost or acronis?

---

### Post by jombeewoof on 2007-08-31
dd

disk dump. 
usage

dd if=/dev/hda1 of=/destination

assuming /dev/hda1 is the partition you want to make an image of.
also works for cds and dvds

dd if=/dev/cdrom of=/file.iso

---

### Post by bme on 2007-09-01
very dangerous command this dd!

---

### Post by capink on 2007-09-01
Partimage is a good alternative especially if you are using FAT. It stills works for NTFS, but last time I checked their website it said the ntfs support is not as reliable as other filesystems.

---

### Post by carusoswi on 2007-09-01
> **bme said:**
> very dangerous command this dd!

Why is it dangerous, bme?  What problems has it caused you?

Thanks,

Caruso

---

### Post by MinstrelBoy on 2007-09-01
if = in file   of = out file

If you point 'of' at the wrong disk or partition you could lose everything. Be very careful !

---

### Post by bme on 2007-09-03
> **carusoswi said:**
> Why is it dangerous, bme?  What problems has it caused you?

Thanks,

Caruso

I am not used to command line.I am a lousy typist.and not a linux expert either. All these reasons make me reluctant to use very powerful commands like dd.

---

