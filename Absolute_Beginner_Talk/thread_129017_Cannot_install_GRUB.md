---
title: "Cannot install GRUB?"
date: 2006-02-12
forum: Absolute Beginner Talk
---

### Post by Michael M on 2006-02-12
I've tried to install Edubuntu (and Ubuntu) numerous times now and I almost get all the way through the installation process until it comes time to install GRUB. The install just won't go past this step and I have to abort. I'm trying to install on an IBM i series Thinkpad with just 3 gb of hard disk space and 160 MB of RAM. I tried to install over MEPIS, and also on a completely re-partioned disk. MEPIS installed well but is too slow to be really useful (and I can't get the wireless working). Any ideas on how to get through this, or are my resources just to pathetic? I'm able to use Damnsmalllinus off a CD image--maybe that's the route to go, but it's a bit too thin?

---

### Post by davmac on 2006-02-14
Michael,

I think it might be your lack of disk space that is causing the problem, and the RAM is on the low side too. If you've found Mepis to be unusably slow, then there's a fair chance the full Ubuntu will be similar.

What I'd recommend is first off to do a bare server install (type "server" at the boot prompt) and then add on just what you need. I'd recommend using XFCE rather than Gnome. If you find this too heavy, then try Fluxbox.

Have a read of [https://wiki.ubuntu.com/Installation/LowMemorySystems](https://wiki.ubuntu.com/Installation/LowMemorySystems) and [http://www.ubuntuforums.org/showthread.php?t=125055](http://www.ubuntuforums.org/showthread.php?t=125055)

Hope this helps,

Dave Mac

---

