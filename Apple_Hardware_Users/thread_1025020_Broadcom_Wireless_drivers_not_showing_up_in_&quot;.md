---
title: "Broadcom Wireless drivers not showing up in &quot;Hardware Drivers&quot; ? (MBP 4,1)"
date: 2008-12-29
forum: Apple Hardware Users
---

### Post by Chrisj303 on 2008-12-29
What a night I'm having! 

After solved my last major headache - I encounter another!

Normally, when I install ubuntu on my MBP 4,1 - the Broadcom Wireless drivers appear in the "hardware Drivers" menu.

This time they have not.

I have enabled every possible software source -including Install_CD, but to no avail.

Anyone have any ideas?

---

### Post by cyberdork33 on 2008-12-30
just add 'wl' to /etc/modules and make sure to blacklist b43

---

