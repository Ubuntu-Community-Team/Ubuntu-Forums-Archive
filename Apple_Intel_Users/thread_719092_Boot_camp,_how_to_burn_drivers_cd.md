---
title: "Boot camp, how to burn drivers cd?"
date: 2008-03-08
forum: Apple Intel Users
---

### Post by fredscripts on 2008-03-08
Hi!

I'm following this guide [http://ubuntuforums.org/showthread.php?t=187465](http://ubuntuforums.org/showthread.php?t=187465) in order to triple boot and I don't know how to burn the cd that tells on step 4:

```
"Run BootCamp (in the Applications/Utilities directory) and create a Windows XP driver CD. Do NOT repartition your drive yet, cancel and quit BootCamp"
```

Because once I open BootCamp, I have this menu I'm attaching and if I click continue I'm partitioning the HD.

Anyone knows where I can burn that CD?

---

### Post by bcr88 on 2008-03-08
That guide must be old. In Leopard, the drivers are on the Leopard install DVD. Once you install Windows, put in your Leopard disc, and you can install the drivers from that.

EDIT: I just looked at that guide and basically, you can skip step 4 and whenever it tells you to use your driver CD, use your Leopard disc. Also, in Leopard, you can create and resize volumes non-destructively with Disk Utility. So, if you would like, it might be easier to use Disk Utility instead of the command line to make your three partitions. I would suggest making all three Mac OS Extended (Journaled) at first because those are the only kind of volumes you can resize. Once you've gotten your partitions where you want them, you can format them how the guide tells you.

---

