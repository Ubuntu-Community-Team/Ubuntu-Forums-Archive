---
title: "Sleep on iBook G4: Work in Progress that works for me"
date: 2004-11-22
forum: Apple PPC Users
---

### Post by paulproteus on 2004-11-22
I'm a long-time Debian user, and I'm running Ubuntu Warty on my iBook G4
laptop.

If you use an iBook G4 and want sleep (suspend to RAM) support, and are a relatively advanced user, read on!  If you're not interested, go buy some plum juice (I just had some and it's good stuff).  If you're not advanced, then rest assured that testers will work out most of the bugs for 2.6.11, at which point someone (me?) will make this nice and easy.

Benjamin Herrenschmidt has made sleep work in the iBook G4, along with a few other recent Apple laptops.  I'm using an iBook G4, so I patched the 2.6.9 kernel source with his patch and made a package.

For some reason, my laptop doesn't wake up with the Ubuntu XF86Config-4, so I'm also giving out someone else's from the debian-powerpc mailing list's.  You can download my kernel image and XF86Config-4 here:

* [http://www.asheesh.org/downloads/isnooze/kernel-image-2.6.9-isnooze-asheesh_10.00.Custom_powerpc.deb](http://www.asheesh.org/downloads/isnooze/kernel-image-2.6.9-isnooze-asheesh_10.00.Custom_powerpc.deb)
* [http://www.asheesh.org/downloads/isnooze/XF86Config-4.that_guy](http://www.asheesh.org/downloads/isnooze/XF86Config-4.that_guy)

Bonus:

* I use a prism2_usb wifi card, too, so here's my linux-wlan-ng directory from /lib/modules/2.6.9-isnooze-asheesh/ - [http://www.asheesh.org/downloads/isnoooze/wlan.tar.gz](http://www.asheesh.org/downloads/isnoooze/wlan.tar.gz) 

(It's slow, I know.  Sorry.)  Put the XF86Config-4 in /etc/X11/ , and
"dpkg -i" the kernel image.

Reboot as necessary.  Everything should act mostly the same, except that
when you close your laptop's lid, it will go to sleep.  One problem I've
had already is that if you change USB state (e.g., insert or remove a
device) while the laptop is asleep, it won't wake up quite right.  So
remove everything first.

Reply with comments or questions!

-- Asheesh.

P.S. This is a crosspost of mine from ubuntu-users.  Also, the source link is at lists.debian.org, but I can't seem to access it right now.

---

### Post by ele on 2004-12-03
Could you give me your .config file alone? I tried with 2.6.9 but got some error on dm-linear.
Anyway krnel booted and Benh's patch n.6 works for me pretty well:
[http://gate.crashing.org/~benh/albook-ibookg4-sleep-6.diff](http://gate.crashing.org/~benh/albook-ibookg4-sleep-6.diff)

Some notes: while going sleeping there is a sharp noise coming from speakers.
Is it the same for you?

Thanks,

e.

---

