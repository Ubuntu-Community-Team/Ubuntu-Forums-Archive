---
title: "LVM Pvcreate error"
date: 2007-09-01
forum: Absolute Beginner Talk
---

### Post by mohnkern on 2007-09-01
I recently install a 500 GB SATA drive, and I'm having a problem adding it to my current logical volumes.

Here's the steps I took:

1. Created 1 partition on /dev/sda called /dev/sda1 (/dev/sda is the new drive)

2. Changed the partition type to "8e"

3. wrote out the table.

4. The drive mounted, which is a little strange.

5.  Unmounted the partition /dev/sda1

6. Ran sudo partprobe

7. Ran mkfs.ext3  /dev/sda1

(This ran flawlessly)

8. Ran pvcreate /dev/sda1

I get an error here saying 

$ sudo pvcreate /dev/sda1
  Device /dev/sda1 not found (or ignored by filtering).
$

---

### Post by mohnkern on 2007-09-03
I ran dd if=/dev/zero of=/dev/sda and then re partition the volume.

Still no joy.

---

### Post by mohnkern on 2007-09-04
Discovered problem:

/etc/lvm/lvm.conf by default in ubuntu contains the following line:

filter = [ "a|/dev/hd[ab]|", "r/.*/" ]

This either needs to be changed to:

filter = [ "a|/dev/[hs]d[ab]|", "r/.*/" ]

or

# filter = [ "a|/dev/hd[ab]|", "r/.*/" ]

(i.e. commented out)

---

