---
title: "two finger scrolling"
date: 2008-04-13
forum: Apple Intel Users
---

### Post by pierrelux on 2008-04-13
I can't get two finger scrolling to work following the insctructions provided on the wiki. I have a Macbook Pro 4.1 under Hardy 64 bit with the kernel provided with the distro (not the mactel kernel).

The touchpad works for basic scrolling though... I noticed that synclient -l will output "Can't access shared memory area. SHMConfig disabled?". Same kind of message with gsynaptics.

---

### Post by tannewt on 2008-04-14
pierrelux,

The MacBook Pro 4,1s have significantly different hardware than previous mbps.  I have one myself and have written a userspace daemon to handle the advanced mouse features.

Check out [touchd.sourceforge.net]("http://touchd.sf.net").  The first alpha is out but since then I've rewritten the click detection and it works much better.  I'll be releasing that code as alpha 2 soon or you can always get the latest from subversion.

Cheers,
Scott

---

### Post by pierrelux on 2008-04-14
Great useful work, thanks. The DBUS feature is interesting. 

I'm definitely testing it as soon as I can crash my system a bit.

---

