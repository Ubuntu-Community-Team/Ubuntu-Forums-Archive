---
title: "gnome-mag memory leak corrected"
date: 2006-09-26
forum: Assistive Technology &amp; Accessibility
---

### Post by cerdiogenes on 2006-09-26
Hi,

Recently I make a patch that correct a memory leak in gnome-mag: [http://bugzilla.gnome.org/show_bug.cgi?id=355583](http://bugzilla.gnome.org/show_bug.cgi?id=355583)

I really appreciate if someone could update the gnome-mag package in the repos or say how I can do this (if I must do it at all :-).

Best regards,
Carlos.

---

### Post by Henrik on 2006-09-27
Hi Carlos!

Great news on the fix!

I've added the upstream information to our BTS: [https://launchpad.net/distros/ubuntu/+source/gnome-mag/+bug/57054](https://launchpad.net/distros/ubuntu/+source/gnome-mag/+bug/57054) so we should hopefully absorb the patch soon. Please add any comments you think are relevant to the launchpad bug report.

---

### Post by cerdiogenes on 2006-09-28
Hi Henrik,

> **Henrik said:**
> Hi Carlos!

Great news on the fix!

I've added the upstream information to our BTS: [https://launchpad.net/distros/ubuntu/+source/gnome-mag/+bug/57054](https://launchpad.net/distros/ubuntu/+source/gnome-mag/+bug/57054) so we should hopefully absorb the patch soon. Please add any comments you think are relevant to the launchpad bug report.

I looked at the launchpad site to try to discover what is BTS, but doesn't find any thing usefull. Can you expand this :-)?

Thanks,
Carlosl

---

### Post by Henrik on 2006-09-28
Hi Carlos,

Sorry BTS = Bug Tracking System (ours happens to be called Malone). 

It looks like Daniel is accepting the patch and will apply it after the beta release (which is going on just now).

---

### Post by Henrik on 2006-10-03
The fix should be in the latest edgy updates now. Can you test?

---

