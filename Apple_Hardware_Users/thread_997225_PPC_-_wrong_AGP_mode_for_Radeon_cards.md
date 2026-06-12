---
title: "PPC - wrong AGP mode for Radeon cards?"
date: 2008-11-29
forum: Apple Hardware Users
---

### Post by stream303 on 2008-11-29
I'm wondering if anyone having any problems with their ppc setups have had to change their AGP mode speed to get the screen to work properly, especially with Hardy / Intrepid?  (ie Radeon 7500, 9200's etc)

Assuming you get past a totally black screen, and are able to get to /etc/X11/xorg.conf, does adding the following to the device section of xorg.conf help?

```
Section "Device"
	Identifier	"Configured Video Device"
	Option		"AGPMode" "4"
EndSection
```

This is just an example.  Depending on the card, you might have to change it to "2" or "8" - your device section may also contain more options.

I think one way to check if your xorg.conf seems to be correct, but are still having problems is to make sure that your agp speed is properly detected (not just the size)

```
dmesg | grep AGP
and
dmesg | grep agp
```

I got interested in this by reading this bug report earlier in the year, and wonder if ppc users are still facing this issue:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/48053](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/48053)

Disclaimer: I don't have a radeon-equipped ppc mac, so it is hard for me to tell.

Maybe some radeon owner can run dmesg and see if there is still a problem with the autodetection...

Also, those of you trying to use
```
Linux video=ofonly nosplash
```

at the second-stage yaboot boot: prompt, may want to try the more specific

```
Linux video=radeonfb nosplash
```

instead...

---

