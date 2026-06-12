---
title: "Booting yaboot on a headless powermac"
date: 2009-03-25
forum: Apple Hardware Users
---

### Post by tompouce on 2009-03-25
Hi!

It's been a month since I'm trying to make my PowerMac 867mhz boot without a monitor.

At first I thought it was because of my version of linux, then I thought it was because I did not had any mac partition on it... But now I really know that it's due to yaboot.

Here's my config:
```
boot=/dev/hda2
device=/pci@f2000000/mac-io@17/ata-4@1f000/disk@0:
partition=4
root=/dev/hda4
timeout=1
install=/usr/lib/yaboot/yaboot
magicboot=/usr/lib/yaboot/ofboot
enablecdboot
enableofboot
macosx=/dev/hda3

image=/boot/vmlinux
        label=Linux
        read-only
        initrd=/boot/initrd.img
        append="nosplash video=radeonfb:1024x768-24@60"

image=/boot/vmlinux.old
        label=old
        read-only
        initrd=/boot/initrd.img.old
        append="nosplash video=radeonfb:1024x768-24@60"
```

I wonder what's wrong, but when I boot headless, it does not go to linux at all (no logs at all are created).

Any ideas about this issue? Thanks!

---

### Post by weelzekib on 2010-10-26
See this: [http://www.drbottkg.com/prod/ghead.html](http://www.drbottkg.com/prod/ghead.html)

---

