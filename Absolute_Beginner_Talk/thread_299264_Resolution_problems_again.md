---
title: "Resolution problems again"
date: 2006-11-13
forum: Absolute Beginner Talk
---

### Post by mechaichezilla on 2006-11-13
Hi,

I just got my first ubuntu running and have some problems changing resolution/refresh rate.

I already looked at the xorg.conf file and there are a lot of resolutions and I can choose them all when I try to change the resolution. Now the first problem is, that there's only on refresh rate to choose from for each resolution. So, if I lower the resolution, my TFT-display tells me that it's out of range, because the refresh rate goes above 75Hz. Is there a way to override the refresh rate? This problem is rather unimportant, since the native resolution of the display works, but I'd like it to be fixed, since I'm not sure on which monitor the machine will be running in the end, and as long I'm trying it out, I'd like to have a bit more control over the resolutions and refresh rates.

The bigger problem I have is that the resolution goes down to 640x480 once I don't connect a monitor and access the machine over VNC and 640x480 is the only available resolution then (the other ones are still in the xorg.conf). Any ideas how to fix this?

Thanks

---

### Post by SZorg on 2006-11-13
If you want to override the refresh rate for a specific resolution just add to it in xorg.conf.

It should look like:

```
"1280x1024_60" or "1024x768_60"
```

the _60 being the refresh rate of choice.

To be safe, I'd add it to all of the bit depths. (IE, All the instances of the specific resolution.)

---

