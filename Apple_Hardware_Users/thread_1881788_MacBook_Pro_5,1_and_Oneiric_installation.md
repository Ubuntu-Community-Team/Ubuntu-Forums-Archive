---
title: "MacBook Pro 5,1 and Oneiric installation"
date: 2011-11-16
forum: Apple Hardware Users
---

### Post by kevpatts on 2011-11-16
Okay everyone, I know this has been covered on many threads, but after trying everything I can find (and works for other people) I still can't get Linux to boot.

I have:
[LIST]
[*]Installed rEFIt (latest version)
[*]Shrank my Mac partition by 28Gb using Disk Utility
[*]Booted from the Ubuntu LiveCD (using "acpi=off")
[*]Installed Ubuntu normally but with grub2 installed to /dev/sda4 (root linux partition)
[*]Manually forced a grub2 reinstall (using chroot & apt-get)
[*]Tried installing grub1 instead to /dev/sda4
[*]Fixed my EFI/GPT partition tables many times ([http://ubuntuforums.org/showpost.php?p=11215214&postcount=185](http://ubuntuforums.org/showpost.php?p=11215214&postcount=185))
[*]Tried installing grub to /dev/sda instead of /dev/sda4
[/LIST]

I always end up with the same result:
[LIST]
[*]gptsync and rEFIt both say the tables are synchronised
[*]If I used grub then I get a black screen with "GRUB" in the top left corner
[*]If I used grub1 then I get a black screen with a blinking cursor
[/LIST]

Any help appreciated.

Kevpatts

---

### Post by kevpatts on 2011-11-16
HA! Got it!

Strangely enough, the way to get Grub to work properly was to chroot to the hard drive from the LiveCD and run:```
grub-install /dev/sda
apt-get remove --purge grub
```
Amazingly this made grub1 display perfectly!

Hope this helps others.

---

