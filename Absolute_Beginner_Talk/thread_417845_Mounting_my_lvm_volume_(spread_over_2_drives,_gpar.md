---
title: "Mounting my lvm volume (spread over 2 drives, gparted says filesystem &quot;unknown&quot;)"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by electric counterpoint on 2007-04-21
Hey, I just made the jump from Slackware to Ubuntu this afternoon. Everything's swell, but I can't mount my main storage volume.

Running Slackware, I had two physical drives. The master (/dev/hda) is subdivided into an ext3 10GB partition (hda1), a small swap partition (hda2), and about 60GB of an xfs volume (hda3). The second drive (/dev/hdb) is entirely part of this lvm xfs volume (hdb1), to the tune of 200GB. Everything was fine.

When I installed Ubuntu, I formatted the 10GB partition (left it as ext3) and mounted it as /, and left the swap partition as it was. I didn't touch the logical volume at all. Gparted was saying that it the filesystem for both hda3 and hdb1 was unknown. Now that Ubuntu's up and running on hda1, Gparted says the same thing, and I can't run something simple like what I'm used to: ```
# mount -t xfs /dev/hdb/ /storage
mount: wrong fs type, bad option, bad superblock on /dev/hdb, missing codepage or other error
In some cases useful info is found in syslog - try dmesg | tail  or so
```This is probably because I'm trying to mount only hdb1 without hda3, but I don't know what command can mount a volume spread across two drives, and the "unknown" filesystem concerns me. Conceptually, I think I need to specify what's in the volume group (hda3 and hdb1), activate it, and mount it. But I don't know how to do that, and all the stuff I see online talks about creating a logical volume from scratch, and I don't want to lose my existing data. Can anyone help?

---

### Post by electric counterpoint on 2007-04-22
bump?

---

### Post by electric counterpoint on 2007-04-23
last bump

---

