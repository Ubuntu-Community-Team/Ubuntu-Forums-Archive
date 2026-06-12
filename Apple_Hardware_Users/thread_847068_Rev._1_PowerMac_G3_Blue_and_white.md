---
title: "Rev. 1 PowerMac G3 Blue and white"
date: 2008-07-02
forum: Apple Hardware Users
---

### Post by UniverseA7X on 2008-07-02
I can't find any thread on this particular machine.

Will any linux distro go on this!?!?

Xubuntu has performance and video problems. Debian just has video problems, won't even load x, though i can log in to a terminal. 

Is there any distro or ubuntu edition that will work on this dying mac? The ram is even maxed out at 1 GB.

Any help is appreciated.

---

### Post by stream303 on 2008-07-02
> **UniverseA7X said:**
> I can't find any thread on this particular machine.

You might want to start with this one in the archives:

[http://ubuntuforums.org/showthread.php?t=616068](http://ubuntuforums.org/showthread.php?t=616068)

> Will any linux distro go on this!?!?

Yes, but please provide more info as to which model it is, how much ram, which video card, etc.  Is the hard drive a replacement or oem - some models have a 125gb partitioning limitation for the root partition, of which there are work arounds.

> Xubuntu has performance and video problems. Debian just has video problems, won't even load x, though i can log in to a terminal.

Debian is also a good choice since it is the parent of Ubuntu, but we all share the same weird apple quirks - so what works for ubuntu generally works well for Debian.

You may want to try some of the solutions in this faq - even though they have titles for other releases - the fixes still work, especially the special need for hand-coding your monitor frequencies in /etc/X11/xorg.conf and the disabling of dri/glx:

[https://wiki.ubuntu.com/PowerPCKnownIssues](https://wiki.ubuntu.com/PowerPCKnownIssues) 

> The ram is even maxed out at 1 GB.

That should make for a nice G3 Ubuntu / Debian install.  If you have Debian, that's fine.  If you want ubuntu, I'd recommend the "alternate" install image to make things easier, although you will have to modify those files mentioned earlier after install:

[https://wiki.ubuntu.com/PowerPCDownloads](https://wiki.ubuntu.com/PowerPCDownloads)

---

