---
title: "Can't adjust backlight on Natty 11.04 running on 8,2 Macbook Pro MBP"
date: 2011-07-08
forum: Apple Hardware Users
---

### Post by nyargh on 2011-07-08
Hi,

I can't seem to adjust the backlight on my Natty 11.04 install on a 8,2 Macbook Pro (MBP).  It seems a few people have had this working, and many have not.  I have tried everything, and I'm hoping that someone out there has a fix.  Otherwise, I think the Wiki should be updated to indicate that the Backlight is not working on the 8,2 MBP.   Keyboard Backlight works just fine, and this has an ATI chipset, not Nvidia so the Mactel PPA nvidia backlight module doesn't apply.

I've tried a 2.6.39 kernel with the stock apple_bl module, along with a variety of ACPI kernel boot options and the xorg.conf fix that was mentioned.  Still no joy.  

What drives me nuts is that this was working on my first install, then it stopped after reboot. I've reinstalled Natty twice and haven't gotten it to work since.  In all cases the indicator shows that the backlight is being adjusted, and manually setting it in /sys/devices/virtual/backlight doesn't return any errors and reflects the setting - but the backlight doesn't change. :(

Any ideas?

---

