---
title: "PPC - is AGPmode still working for ati/r128/radeon?"
date: 2008-11-13
forum: Apple Hardware Users
---

### Post by stream303 on 2008-11-13
Although I have an nvidia-driven ppc mac, I wonder if the "AGPmode" option still works in xorg.conf for ati/r128/radeon users?

I'm wondering if many are running at 1X AGP because it isn't specified in the device section of /etc/X11/xorg.conf typically something like this:

```
Section "Device"
	Identifier	"Configured Video Device"
	Driver	"r128"
	Option  "AGPmode" "4"
EndSection
```

This would be for a 4X agp card.  I guess you could verify it by going to everymac.com and taking a peek.

I know that when I try it for my nvidia card in /var/log/Xorg.0.log  it is rejected, but maybe ok for ati users?  Either that, or that option is no longer needed in Intrepid's X server..

If it works, I guess every little bit helps, even at 2X if you can get it....

---

