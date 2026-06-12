---
title: "[SOLVED] failed fsck"
date: 2007-10-25
forum: Absolute Beginner Talk
---

### Post by Sbarton on 2007-10-25
I recently installed 'Gutsy' on hda, On hdb I have 'Feisty'. However since the install of Gutsy when I boot into the hdb drive (feisty) I get a fsck 'Fail', I can boot into it using the CONTROL -D method. This happens each time I boot intohdb.
I have included a couple of attachments which display the result of fsck using the 'live cd'
Any help to resolvr this would be appreciated.
regards

---

### Post by speed145a on 2007-10-25
when this happened to me it was because ubuntu was looking for a different filesystem than the new one I had just installed.

here's what I did:

```
sudo gedit /etc/fstab
```

then I found the partition that was modified by the new install (but feisty was not aware of) and commented it out by placing # marks at the beginning of each line of that device section.

mine looks something like this:

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3
UUID=dc306d0b-51de-4fca-956c-1094e521a92e /               reiserfs notail          0       1
# /dev/hda2
UUID=B88000CB800091D4 /media/hda2     ntfs    defaults,umask=007,gid=46 0       1
# /dev/hda4
UUID=635ded8e-7864-45d6-ba0a-aa7624979bda none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

if I did a new install on /dev/hda2 then I would comment out the "UUID" line just below by placing a # at the beginning

In your case, it looks like you need to comment out the hdb2 lines


hope this helps!

---

### Post by Sbarton on 2007-10-26
speed 145a, thanks for your reply. I tried that and it did not work, As I say, the new install (Gutsy) was on a *different* HDD to existing 'feisty' HDD.The HDD 'Gutsy is now on (hda), originally had 'Dapper' on and I deleted all partitions before installing 'Gutsy'. From what I see, the results of 'blkid' and 'fstab' show the same 'UUID'. I have copied the details of the failed 'UUID' that I get on booting to hdb (feisty drive). They are different! See attachment. I am at a loss at this moment in resolving this problem. Any help to resolve is is appreciated.
regards

---

### Post by MegaJim on 2007-10-26
Its possible there's something wrong with the way uuids are being resolved to partitions.

Just for fun, backup your fstab and replace all the uuid="" with device locations

---

### Post by speed145a on 2007-10-26
can you show me what your fstab looks like right now?

---

### Post by Sbarton on 2007-10-26
> **speed145a said:**
> can you show me what your fstab looks like right now?
 hello speed, the attachment is of 'feisty'now and I am in 'feisty now'replying to your request.

Hi megajim, I am not sure what you mean, could you explain further please.
thanks and regards to you both.

---

### Post by MegaJim on 2007-10-26
Sure, 

Currently your fstab uses UUID tags to identify partitions.  The fsck command is referring to these UUIDs when it boots to check the filesystem

This sometimes doesn't work too well, so for troubleshooting purposes change them to /dev/hda type references.  First, backup your fstab:

```
sudo cp /etc/fstab /etc/fstab.bak
```

next execute the command 

```
sudo blkid
```

to get a list of your /dev/name list next to their respective UUIDs

now open up your fstab in an editor

```
sudo gedit /etc/fstab
```

and change the respective uuid's to /dev/??? entries

for example

```
# /dev/hda3 - Swap Partition
/dev/hda3 	none            swap    	sw              0       0
```

---

### Post by Sbarton on 2007-10-26
magajim, the attachments show you 'blkid', 'fstab', and the boot fail details in 'feisty. The last one is of fstab in 'gutsy'.
regards

---

### Post by MegaJim on 2007-10-26
I see that.

You could still try what I described to you, however, because the automatic boot checks you have enabled are (afaik) the only way to force a fsck at boot-time, and its possible that the way the UUIDs are being resolved is faulty.

---

### Post by speed145a on 2007-10-26
Well all I would suggest is put a # mark at the **beginning** of the two UUID lines that say /media/hda1 and /media/hda3

if that doesn't work then you got me.  That would be the point at which I would install feisty again

---

### Post by Sbarton on 2007-10-27
SOLVED:
Thanks for your input megajim & speed145a.
I tried commenting out which did not result in any change.
So for a temporary solution I set the frequency of fsck to '0' on all partitions except '/'.
I did this in fstab changing the <pass> number.
 Another way I found out would be to change the frequency of fsck to about 100 mounts.
I am still looking at the 'UUID' setup to see if any need to be changed.
Anyway once again thanks to you both for your input.
regards

---

