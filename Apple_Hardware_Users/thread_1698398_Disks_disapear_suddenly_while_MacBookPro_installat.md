---
title: "Disks disapear suddenly while MacBookPro installation..."
date: 2011-03-02
forum: Apple Hardware Users
---

### Post by paxsali on 2011-03-02
Hi all,

Im trying to install Ubuntu on my Intel MacBook Pro 13".

When booting from the livecd, Im experiencing strange issues.

Sometimes the partiontable and disks/partitions are not readable
straight away, sometimes you can read them once (when opening gparted
or the install-routine), but then they disappear after it.
Sometimes they remain quite a while and "survive" all parted
and other tools, and then produce I/O errors during install
(after successfull partitioning).

I want to know... are these issues well known or am I the only one with such errors?

Im not doing anything wrong, AFAIK.

The devices just disappear sooner or later until only loop0 (cd-rom) remains.

---

### Post by Colin Rovis on 2011-03-02
When testing your disk with diskutil under OS X, is the S.M.A.R.T-Status ok?

---

### Post by paxsali on 2011-03-03
> **Colin Rovis said:**
> When testing your disk with diskutil under OS X, is the S.M.A.R.T-Status ok?

I assume the status is fine, because when Im booting from Super Rescue CD ([http://www.sysresccd.org](http://www.sysresccd.org), Gentoo based, gparted 0.8.0, recent kernel+xorg) the system is superstable and just fine. No disks disappear, everything just works as expected.

---

### Post by paxsali on 2011-03-03
Its pretty replicateable on my box.

1. download ISO: ubuntu 10.10 amd64

2. Boot

3. terminal -> $ cat /proc/partitions
(/dev/sda, /dev/sda1, /dev/sda2,... all show up)

4. Start Installation (or even gparted, really)
> wait for fsyncing/close error message

5. terminal -> cat /proc/partitions
(onyl loop0 left, all other blockdevices just gone, vanished)

---

