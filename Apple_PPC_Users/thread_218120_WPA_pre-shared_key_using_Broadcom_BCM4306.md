---
title: "WPA pre-shared key using Broadcom BCM4306"
date: 2006-07-18
forum: Apple PPC Users
---

### Post by Seamus on 2006-07-18
Guys,

I know there are a lot of threads around getting BCM43xx wifi cards working, but as yet I have succeeded - I am trying to use the new native driver.

What I want to ascertain is if it is possible to use this driver with WPA PreShared Key as opposed to simple WEP.

My Linksys WRT54G is using WPA you see, and I am loathe to drop it down to WEP to get it working.

If anyone can confirm if this works or not it will save me considerable time I am sure since currently I am trying to get it working but on WPA.

Look forward to your help,

Cheers

---

### Post by rasec on 2006-07-18
It works for just fine for me. I got it working using both network manager and wpa_supplicant.conf method. I believe that there is a bug in the current network manager that causes it to mishandle the wpa passphrases, so unless you want to recompile it I would recommend that you go the wpa_supplicant route. Check the wireless forum on how to use wpa_supplicant.conf, they probably have hundreds of threads on the topic.

---

### Post by Seamus on 2006-07-21
> **rasec said:**
> It works for just fine for me. I got it working using both network manager and wpa_supplicant.conf method. I believe that there is a bug in the current network manager that causes it to mishandle the wpa passphrases, so unless you want to recompile it I would recommend that you go the wpa_supplicant route. Check the wireless forum on how to use wpa_supplicant.conf, they probably have hundreds of threads on the topic.

thanks mate - will give that a go.

---

