---
title: "yaboot, G3, where is root system?"
date: 2011-02-09
forum: Apple Hardware Users
---

### Post by knottulf on 2011-02-09
I have installed ubuntu server 10.04 onto a G3 ibook with yaboot. Apparently yaboot works, but I end up with an error message, mentioned in several threads: 
"Gave up waiting for root device."
- Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/mapper/ubuntuserver-root does not exist. Dropping to a shell!

And then BusyBox v1.13.3 takes over the show.

This is where I got stuck.
I tried mount, with this result:
rootfs on / type rootfs (rw)
none on /sys type sysfs (rw, nosuid nodev, noexec, relatime)
none on /proc type proc (rw, nosuid nodev, noexec, relatime)
none on /dev type devtmpfs (rw, relatime,size=185504k,nr_inodes=46376,mode=755)
none on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)

How can I read or edit lvm.conf og yaboot.conf?
Or are there other actions I should perform?

---

### Post by knottulf on 2011-04-26
I have given up on this issue. G3 and yaboot gives me to much trouble, and there does not seem to exist any userbase anymore.

---

### Post by linuxopjemac on 2011-04-26
Try MintPPC.

---

### Post by pauljwells on 2011-04-26
> **linuxopjemac said:**
> Try MintPPC.

It's a bit terse, I know, and on the face of it doesn't appear very helpful, but linuxopjemac has put a LOT of work into making a Debian flavour that works well on older macs.

G3s are *seriously* old kit these days! Take a look at the MintPPC site, register and do yourself a favour!

[http://mintppc.org/]("http://mintppc.org/")

Good Luck, there are still a few PPCers out there!

---

