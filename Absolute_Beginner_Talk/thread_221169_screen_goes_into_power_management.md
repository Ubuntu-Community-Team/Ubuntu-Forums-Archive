---
title: "screen goes into power management"
date: 2006-07-22
forum: Absolute Beginner Talk
---

### Post by wpshooter on 2006-07-22
Why does my display go into power saving mode (blank) after a prolong period during a long download ?

This occurs when I am downloading the Ubuntu ISO images, which usually takes 1 1/2 to 2 hours.

I have never timed it, but it seems to occur between 30 minutes to maybe an hour.  

And yes, I have the power management set to **NEVER** and the screen saver is **UNCHECKED**.

Also, it is disabled in BIOS.

During other functioning, I normally keep the Ubuntu controlled power management set to 3 minutes.

Thanks.

---

### Post by MellonCollie on 2006-07-22
I had this problem (every 10 minutes) and it annoyed the s#*t out of me. I solved it by editing xorg.conf and changing the DPMS option in the monitor section to "false".

---

### Post by wpshooter on 2006-07-23
> **MellonCollie said:**
> I had this problem (every 10 minutes) and it annoyed the s#*t out of me. I solved it by editing xorg.conf and changing the DPMS option in the monitor section to "false".

If you/I had the monitor power saving function turned off in the BIOS, why would it be necessary to edit/change this ?

Should this have not been turned off during the initial installation of the Ubuntu O/S ?

Is this a flaw in the installation process ?

Thanks.

---

