---
title: "Amarok upgrade problem with libgpod"
date: 2008-03-22
forum: Absolute Beginner Talk
---

### Post by Twizzle on 2008-03-22
I had Amarok up and running and using a number of guides on this forum managed to use my Ipod Nano with it just fine.

About a week ago, my computer told me that there were some upgrades available so I just let it crack on but then I had a broken pipe (I think thats what it said) so I followed the guide to remove it and it turned out to be something to do with Amarok and libgpod.

I totally removed Amarok and then re installed it, but as soon as I do, I am told there are updates and when I run them, I get the following message:

```
E: /var/cache/apt/archives/libgpod2_0.5.2-2_amd64.deb: trying to overwrite `/usr/lib/libgpod.so.2.0.0', which is also in package libgpod1

```

I have no idea what it really means, but can I fix it?

---

### Post by rubenverweij on 2008-03-30
Does it work if you remove the libgpod1 version via Synaptic Package manager and install the new version of libgpod manually? I had the same problem with another package, it worked for me. ;)

---

