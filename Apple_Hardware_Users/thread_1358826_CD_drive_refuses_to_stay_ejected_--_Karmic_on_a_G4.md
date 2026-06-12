---
title: "CD drive refuses to stay ejected -- Karmic on a G4 eMac"
date: 2009-12-18
forum: Apple Hardware Users
---

### Post by Dernhelm on 2009-12-18
I have a problem with my CD drive--if anyone has any idea what is going on or how to fix it, I'd be most grateful. 

I've recently installed Ubuntu 9.10 on a G4 eMac. It's working wonderfully, for the most part. Flash is a small problem, but the Firefox plugin 'Greasemonkey' can run a script which embeds an external media player in the page to play the flash file. VLC or whatever. The other problem is Mac-on-Linux, which I find only works on *old* versions of Ubuntu. That's something else to work around (but ny ideas would be VERY welcome. Here's my main problem though--

When I hit the eject button on the Apple keyboard, the CD drive ejects, and then pulls back in instantly. If you manage to toss a CD onto it quickly enough to get it into the computer, Ubuntu doesn't recognise it's existence. :(

Help?

I've tried typing 'eject' into the terminal--works exactly the same as pressing the eject button. Aside from that, I've no idea where to look for the problem.

Let me know if there's more info I could provide that would be helpful in figuring this out!

Thanks in advance. :)

---

### Post by zts-it on 2009-12-19
> **Dernhelm said:**
> ...

When I hit the eject button on the Apple keyboard, the CD drive ejects, and then pulls back in instantly. If you manage to toss a CD onto it quickly enough to get it into the computer, Ubuntu doesn't recognise it's existence. :(  ....I had similar problems on MacMini G4 (2005) with Ubuntu 9.10. I've noticed problems with a newer slim (metal) Apple keyboard right away but didn't dwell much on it since I had a Logitech backlit keyboard that I connected and the eject keys work very well ( Fn+F8 ). However, I've never solved the second problem -- the CD/DVD recognition/mounting once the media is inserted remained a huge problem for me -- pretty much it never worked. That prompted me to downgrade to Ubuntu 9.04 in which I don't have any problems. Something in the development process from 9.04 to 9.10 went wrong in the PPC version. But it could be fixed I guess as soon as more users confirm that there is a media mounting/recognition problem in 9.10 PPC.

---

### Post by phillw on 2009-12-19
Having had this problem when running a MacOS (gud ol' 10.1.5) on an aged G3 I've always considered it a glitch within the Mac. I've always found that 'File Eject' worked fine. So, possibly, 9.04 was employing a workaround to counter a problem with the Mac ?  Just a thought.

Phill.

---

### Post by yamanqui on 2010-02-11
I just installed Ubuntu - Karmic on my eMac G4 and have exactly the same problem with the CD (everything else seems to works fine). Is there any way to fix this?

---

### Post by teachop on 2011-03-12
This problem still exists in Ubuntu 10.10 on eMac G4.

---

### Post by linuxopjemac on 2011-03-13
bug in Ubuntu for quite some time as well:
[http://ubuntuforums.org/showthread.php?p=9263201](http://ubuntuforums.org/showthread.php?p=9263201)

This was (is?) problematic too:
[http://ubuntuforums.org/showthread.php?t=1479453](http://ubuntuforums.org/showthread.php?t=1479453)

---

### Post by teachop on 2011-03-14
The drive will stay open if you add this to /etc/sysctl.conf but it creates other problems.
```
dev.cdrom.autoclose = 0

```
By hook and crook I can get disks to operate on my eMac when needed.  Fortunately the drive is rarely used.  This works somewhat:
1) Add the above line to sysctl.conf and reboot.
2) Leave a disk in the drive when rebooting, then Ubuntu gets it mounted.  The drive will continue to work for this session.
3) Close the drive by pushing it, and not with the keyboard button.

If I understood all about how device mount points work, I suppose that point 2 above indicates this is a solvable issue.

I said it creates other problems.  After using the drive, at times it will fly open when empty.  For example, I unplugged the Ethernet, and when it was reconnected, the drive flew open.

---

