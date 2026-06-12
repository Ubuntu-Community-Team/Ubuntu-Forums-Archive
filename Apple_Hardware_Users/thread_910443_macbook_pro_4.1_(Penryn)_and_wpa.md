---
title: "macbook pro 4.1 (Penryn) and wpa"
date: 2008-09-04
forum: Apple Hardware Users
---

### Post by oricordeau on 2008-09-04
Hi all,

Does anyone managed to get a wpa encrypted connection working on the Macbook Pro 4.1 (Penryn)????

I managed to get WEP working using the instructions available [HERE]("https://wiki.ubuntu.com/MacBookPro/Penryn"), but I never managed to get it working with WPA. I can see the networks, but it won't connect me. So I was wondering if someone had a trick to share.

FYI (if it changes anything...), I'm running Hardy 32 bits, and I made my install using the alternate desktop iso.

Cheers,
Olivier

---

### Post by hajk on 2008-09-04
If it's any solace, I haven't been successful in getting WPA to work either, and not for want of trying. Just like you, I can connect to an open networks and to WEP protected ones. I'm pretty sure it's an Ndiswrapper problem, since the problem occurs with any connection method I've tried, network-manager, wicd, iwconfig, wpasupplicant... I'm now using a Linksys WUSB54GC adapter, which uses the rt73usb module (use a recent kernel, like 2.6.26), works fine.

---

### Post by hajk on 2008-09-09
Somebody told me about the Broadcom *wl* driver, see my other post [http://ubuntuforums.org/showthread.php?t=914697](http://ubuntuforums.org/showthread.php?t=914697). It works!

---

