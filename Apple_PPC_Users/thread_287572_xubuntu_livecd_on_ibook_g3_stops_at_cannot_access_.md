---
title: "xubuntu livecd on ibook g3 stops at cannot access tty"
date: 2006-10-28
forum: Apple PPC Users
---

### Post by gerghk on 2006-10-28
trying to install xubuntu on my ibook g3, got the iso, burned it and held 'c' during startup to boot the livecd

once the livecd boots, I'm prompted to choose which image to boot, have tried the default 'live', 'live-powerpc' and basically everything except the powerpc64 ones.

The splash with the xubuntu logo and a progress bar below it displays fine, but after a while it ends at:

Busybox

(initramfs) cannot access tty: job control not turned on

at this point i can't really post any other diagnostics besides that message, since the cd didn't even boot!

As we speak I'm downloading the alternate disc to see what my luck is with that, but has anyone had any luck with booting the livecd on such an ibook before?

I've searched online and there seems to be a lot of people experiencing this cannot access tty problem, primarily people with AMD64.

Just a little more information on my ibook's hardware:

G3 800mhz
384 mb pc-100 sd ram
40gig harddrive with HFS+ partition on it (I plan on resizing it following these instructions:
[http://ubuntuforums.org/showthread.php?t=89960](http://ubuntuforums.org/showthread.php?t=89960))

Thanks

---

### Post by utnubudnai on 2008-02-27
solutions for "cannot  access  tty"
[http://openware.5d6d.com/viewthread.php?tid=41&extra=page%3D1&frombbs=1](http://openware.5d6d.com/viewthread.php?tid=41&extra=page%3D1&frombbs=1)

---

### Post by stream303 on 2008-02-28
Very cool tip!

This is one of the reasons why the ppc-folk usually recommend the "alternate" image installation though.

Which version of Xubuntu are you installing?  I'd probably recommend Feisty 7.04 in case what you have now continues to give you trouble:

[http://cdimage.ubuntu.com/xubuntu/ports/releases/feisty/release/](http://cdimage.ubuntu.com/xubuntu/ports/releases/feisty/release/)

---

