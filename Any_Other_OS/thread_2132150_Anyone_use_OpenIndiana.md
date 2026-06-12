---
title: "Anyone use OpenIndiana?"
date: 2013-04-03
forum: Any Other OS
---

### Post by slooksterpsv on 2013-04-03
Just wondering if anyone uses OpenIndiana and if there are any benefits with the illumos kernel vs linux kernel.

---

### Post by MadmanRB on 2013-04-04
Probably none as its based on opensolaris

---

### Post by QIII on 2013-04-04
I used it for a time.  It seems development is slow.  Last I checked, some of the included packages were wll out-of-date.

---

### Post by foxmulder881 on 2013-05-18
I am currently attempting to migrate GRUB2 in to the Illumos kernel base.

---

### Post by binaryhermit on 2013-05-20
No offense to anyone, but I don't see any reason to use anything Solaris-based other than ZFS, and I think that's been ported to BSD and is in the process of getting ported to Linux via FUSE (if I recall correctly).

---

### Post by iamkuriouspurpleoranj on 2013-05-20
If you want UNIX, just use FreeBSD. It's as UNIX-y as OS X is.

Being a UNIX is really about licensing and if Apple calls OS X's BSD element "UNIX", it's because they have bought the right to do so. FreeBSD hasn't, so can't and won't, so don't.

You could even buy a Mac. It actually gave me a small pleasure to open the terminal on a display Mac in a shop and find all the "Linux" commands worked there too. Not sure if I could have dd'd it into silicon heaven but that would have just been nasty, not to say "criminal".

---

### Post by Haghiri75 on 2013-05-21
OpenIndiana is a good OS, but it's not compatible with all kind of hardware.

---

### Post by Blue Thunder on 2013-12-12
I've been using OpenIndiana on my NAS's for a few years. I chose it due to its solid support of ZFS and a desktop environment out of the box. At the time Linux and *BSD implementations of ZFS didn't seem stable or didn't support ZFS pool version 28. Though now *BSD does support ZFS pool version 28 and I'm sure stability/version support has improved on the Linux side of things. However, I also need a desktop/GUI and OpenIndiana comes with one by default (there is also a text-only server version) and this is something I haven't yet found in *BSD. However, Linux with BTRFS or ZFS might be a viable alternative for me.

Definitely agree with QIII and this is my main complaint with OpenIndiana: development is slow and the available software is old. As for hardware compatability, I get the impression that OpenIndiana is more picky than Linux but I've been able to run it fine on a few older laptops and relatively new custom built PCs and have most things work, at least according to the "Device Driver Utility". One thing that doesn't work is USB3 and I'm not sure it ever will.

---

