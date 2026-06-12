---
title: "Quick question"
date: 2007-02-19
forum: Absolute Beginner Talk
---

### Post by Muppeteer on 2007-02-19
I just upgraded my kernel to 2.6.19.1 and was wondering if i have to do anything in synaptic to get updates for the new build? I've ran "apt-get update" and upgrade with nothing installing. I noticed in synaptic a day or so ago i had to manually update Easytag as the typical update didn't detect this. And i also used conky which showed there were 88 updates available...

I have "multiverse, universe, restricted & main sources"...

Seems something isn't right. I've been trying to search for answers but as imagined, it only comes back with kernel updates :(

---

### Post by lhtown on 2007-02-19
Try "apt-get dist-upgrade" after you "apt-get update". "apt-get update" just syncs your machine with the repository and finds the latest updates. It does not install anything, and yes it is recommended to run it before upgrading.

Synaptic works well also if you are running a desktop.

---

### Post by Muppeteer on 2007-02-19
Here's all that came back
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade...Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

I'm assuming it's ok then?

---

### Post by lhtown on 2007-02-20
That looks fine to me.

The timing varies, but updates seem to come out maybe once a week or so.

---

