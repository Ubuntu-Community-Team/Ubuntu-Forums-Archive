---
title: "problem with mounting usb key as rw filesystem"
date: 2008-01-05
forum: Absolute Beginner Talk
---

### Post by Cippa Lippa on 2008-01-05
Dear all

I know this might upset someone as
1) this is not a complicated problem, I assume
2) I am not using Ubuntu

I am using Arch linux at the moment and it doesn't seem to want to mount my usb key as a rw filesystem
I can mount it and see the files with mount /dev/sdb1 /media/mydrive but it is mounted as a read-only filesystem

I tried to chmod 777 the directory to no avail as root
I tried to use pmount as I don't have a specific entry in fstab for this kind of thing and it still mounts as read-only

The thing I hate is that I never had such problem with Ubuntu. What is the script that allows ubuntu to mount the same usb key automatically as rw while I can't mount it in arch?

P.S. by the way I can mount safely and correctly a firewire external harddrive formatted as ext3

Cheers

Cippa

---

### Post by ~LoKe on 2008-01-05
[Here](http://bbs.archlinux.org/).

They have forums, too.

---

### Post by Cippa Lippa on 2008-01-05
yes, I know... but I liked your community so much... ok... anyway... I thought I could get some help anyway. I guess things have changed in the community since 6 months ago...

cheers

---

### Post by ~LoKe on 2008-01-05
> **Cippa Lippa said:**
> yes, I know... but I liked your community so much... ok... anyway... I thought I could get some help anyway. I guess things have changed in the community since 6 months ago...

cheers

I'm not saying you can't get help, just suggesting you check out their forums.  As you said, it works in Ubuntu but not in Arch, I just don't understand how you expect us to figure it out when it works properly on our end.

---

