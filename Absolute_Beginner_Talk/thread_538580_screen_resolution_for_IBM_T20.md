---
title: "screen resolution for IBM T20"
date: 2007-08-30
forum: Absolute Beginner Talk
---

### Post by pkj on 2007-08-30
Hi,
Have installed Ubuntu 7.04 on IBM Thinkpad T 20..
However the resolution i am getting are only 600*800, at best...

I have gone through the earlier posts and have done the following...

sudo dpkg-reconfigure xserver-xorg

I noticed that 1024 * 768 resolution is already selected...
Checked /etc/X11/xorg.confg
1024*768 is included in it...
However i am not getting 1024*768 in my selection ie. System > Preferences > Screen Resolution...

any suggestions....

pkj

---

### Post by Tabenx on 2007-08-30
I had the same problem in a similar situation. What i did was i did "sudo dpkg-reconfigure xserver-xorg" again then restarted immediately. The problem was resolved when it booted back up.

---

### Post by thetejon on 2007-08-30
I had the same problem with at Thinkpad T61 and an Nvidia graphics card.  I had to select "nvidia" instead of "nv" from the list in dpkg-reconfigure.  Is yours an Nvidia card, too?

---

### Post by pkj on 2007-09-01
Thanks

After a few tries, i could get the desired resolution.....

pkj

---

