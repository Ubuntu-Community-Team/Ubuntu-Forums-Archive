---
title: "Airport problems (ICV errors) with a G4 powerbook"
date: 2007-05-16
forum: Apple PPC Users
---

### Post by also-rr on 2007-05-16
I upgraded from Edgy to Fiesty recently. Wireless seemed to work fine after the upgrade but it now disconnects when it feels like it when using WPA.

Sometimes it disconnects every 30 seconds, occasionally it does a few hours.

When it's being troublesome dmesg gets spammed with:

TKIP: ICV error detected: STA=00:11:95:9a:a1:b4

I tried replacing the driver with several different versions (from the OS X partition and a recent wl_apsta.o version as well as the previously working version).

I have also upgraded to iee80211-1.2.17 as this error was a known problem with the .13 version that shipped with Feisty, but the problem hasn't done away. dmesg confirms that the new version is being loaded.

Any ideas?

Thanks,

Richard

---

