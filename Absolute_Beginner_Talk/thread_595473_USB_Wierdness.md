---
title: "USB Wierdness"
date: 2007-10-28
forum: Absolute Beginner Talk
---

### Post by carusoswi on 2007-10-28
I purchased a Maxtor 500 GB USB external drive this weekend.  Ubuntu did not recognize this drive until I had booted into XP and allowed the drive to be detected by that OS.

When I booted back into Ubuntu (7.04) all was well.

Now, I notice that it seems like every other boot, the drive goes undetected.  Also, my wireless adapter (Belkin N1) will sometimes goes undetected.  Just now, I had to unplug the USB cable for the wireless, then, plug it into another port.  When I did that, the wireless was detected, and, following that detection, I was able to reboot and get Ubuntu to recognize my USB external drive.

What is going on, and is there some command line instruction I can use to wake up that external drive when it goes undetected?

I often have to do an "iwconfig" to re associated my router.  Don't know why that should be necessary so often, but, the iwconfig command works, so I'm not complaining.

If I could find something similar for this drive, that would be fine with me.

Advice welcome.

Caruso

---

### Post by Delvien on 2007-10-29
> **carusoswi said:**
> I purchased a Maxtor 500 GB USB external drive this weekend.  Ubuntu did not recognize this drive until I had booted into XP and allowed the drive to be detected by that OS.

When I booted back into Ubuntu (7.04) all was well.

Now, I notice that it seems like every other boot, the drive goes undetected.  Also, my wireless adapter (Belkin N1) will sometimes goes undetected.  Just now, I had to unplug the USB cable for the wireless, then, plug it into another port.  When I did that, the wireless was detected, and, following that detection, I was able to reboot and get Ubuntu to recognize my USB external drive.

What is going on, and is there some command line instruction I can use to wake up that external drive when it goes undetected?

I often have to do an "iwconfig" to re associated my router.  Don't know why that should be necessary so often, but, the iwconfig command works, so I'm not complaining.

If I could find something similar for this drive, that would be fine with me.

Advice welcome.

Caruso

When your computer isnt recognizing and or mounting the external HDD, please the following in terminal:

```
mount
```

And paste the output.

---

