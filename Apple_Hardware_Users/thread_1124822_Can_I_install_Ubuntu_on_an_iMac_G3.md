---
title: "Can I install Ubuntu on an iMac G3?"
date: 2009-04-13
forum: Apple Hardware Users
---

### Post by ke6rj on 2009-04-13
I got a $10 "yard sale" 4 Gig HD iMac. I don't expect much out of it. Just some basic computing, nothing fancy. Would be kick if it'l work and I can show it tomorrow evening during my Ubuntu demo on my 10 yr. old Dell 4000 laptop. Been only using Ubuntu for a week. No-one in our (Big Bear) computer club is using it. 
Harry
[email]rjqi@netzero.com[/email]

---

### Post by Joeb454 on 2009-04-13
Thread moved to  Apple Users :)

---

### Post by cyberdork33 on 2009-04-13
Check the PowerPC Sticky here in the forum. I believe there are several iMac G3 users.

---

### Post by stream303 on 2009-04-13
Yes, it can be done.

However, G3 iMacs and Linux are probably the worst combination I can think of if one is new to Linux considering all the gotcha's along the way.

Know that what you'll end up with for comparison is roughly an equivalent to a 600mhz single-cpu Intel box that can't do flash or 3D, possibly running with only 128mb of memory or so.

So if your computer group is going to do it, be sure they are doing it for the challenge and not making any evaluations about Linux or any distro's installer upon it.

Ubuntu is ok, but I'd stick to either 8.04.1 or perhaps the upcoming Jaunty - 8.10 Intrepid was very problematic.  Or go Debian Lenny.

Here are some of the common challenges that will need to be addressed:

1) Any drives larger than 8gb will need custom partitioning to keep the root partition under it, typically at 7gb or so to be safe.

2) You'll need to manually modify /etc/X11/xorg.conf with values that will allow the graphics card to work.  These cards were designed to communicate with only OSX, so installers don't pick the right values - you'll have to do it yourself.

3) In many cases you start out with a black screen, and you'll have to pass kernel parameters to avoid this at the second-stage yaboot boot: prompt

```
Linux video=ofonly
```

If that works, you'll have to modify your /etc/yaboot.conf and make the system aware of those changes with sudo ybin -v.

As you can see, running Linux on a ppc mac, especially an older low-spec G3 iMac means you'll have to get your hands very dirty. :)

It could be a great learning project, but be prepared to search the wikis, forums, and other posts about how to do it.  Each installation is an adventure in itself - especially if you received the unit second-hand and don't know what has already been done to it.

It is amazing what you get when you consider what Jobs was doing just a few years earlier with the NeXT line of hardware.

---

