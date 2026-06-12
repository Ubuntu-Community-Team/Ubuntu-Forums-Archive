---
title: "Kubuntu + Proxim card = No Wireless?"
date: 2007-03-30
forum: Absolute Beginner Talk
---

### Post by joethenoob on 2007-03-30
I've been using Ubuntu on a Dell C400 for a few months now and everything seemed to work pretty well. When I installed Ubuntu, I made sure to have my Proxim 8470-FC wireless card was in hoping that it would be detected and drivers would install automatically. I don't know if this had a factor in whether or not it worked (notice my name), but I had no problem at all connecting to my wireless network. Ran like a champ.

I was told that KDE was a more feature-rich desktop, so I reloaded with Kubuntu the other day. Again, I had my card in during the install, but this time I can't get it to work. I've been looking thru the forums and found bits and pieces about wlassistant, but the posts were usually very specific. Like "for your broadcom card, you need to do this..." and so on. Can't tell what applies to me and what doesn't.

The only obvious issue i see when I try to connect is that only WEP is a security option, no WPA. Can someone please tell me once and for all (1) whether or not wlassistant supports WPA and (2) what is necessary to configure a Proxim 8470-FC card to run from Kubuntu?

Thanks in advance.

---

### Post by x64Jimbo on 2007-03-30
You really should be looking at KNetworkManager. The NetworkManager package is going to be standard in Feisty, and it's for a good reason. Compared to NM, all other interface managers are crap.

---

### Post by joethenoob on 2007-03-30
Knetworkmanager did the trick. Thanks!

---

