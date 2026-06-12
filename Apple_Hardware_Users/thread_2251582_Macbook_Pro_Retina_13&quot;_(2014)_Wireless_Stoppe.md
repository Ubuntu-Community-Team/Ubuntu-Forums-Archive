---
title: "Macbook Pro Retina 13&quot; (2014) Wireless Stopped Working"
date: 2014-11-05
forum: Apple Hardware Users
---

### Post by snowy16 on 2014-11-05
Hey,

I installed 14.04 from the regular ISO on my MBP Retina 2014 with no issues.  I had to download the bcmwl-kernel-source and its dependancies dkms libc6-dev and linux-libc-dev and install them via USB drive.  This got my wireless working and I've had no issues for 3 weeks.

I turned on my MBP today and got slammed with a bunch of error reports after logging in and couldn't get wlan0 to show up.  I thought it might be that the driver or its dependancies were out of date.  I do have a USB ethernet adapter which I was able to use when booted from a LIVE USB drive.  I updated all the dependencies and tried purging and reinstalling bcmwl-kernel-source but the issue persists.  I'm currently on kernel 3.13.0.39.  I've tried booting to 3.13.0.37 but wireless doesn't work with that kernel either.  I booted to OS X to make sure there was no issues with the broadcom and it works so the problem is isolated to Ubuntu.

Any help would be greatly appreciated.

Thanks

---

