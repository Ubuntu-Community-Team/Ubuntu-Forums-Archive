---
title: "screen goes black after loading kernel in yaboot"
date: 2007-03-09
forum: Apple PPC Users
---

### Post by sam22 on 2007-03-09
I just installed ubuntu on a partition of my mac mini hard drive. When i boot up linux, the screen goes black, and i get a screen saying VGA mode not supported. How can i fix? I can run the live CD when i boot that up running live-nosplash-powerpc, but how can i fix whats installed on my hard drive if i cant see it?

---

### Post by grazie on 2007-03-10
It looks like the splash parameter is giving you problems. Booting the HD installation, at the boot: prompt enter 'linux single' and see if you can boot with that. To shutdown the machine use 
```
$ shutdown -h now
```

If you can boot successfully I suggest removing the splash parameter (and suggest quiet too) from /etc/yaboot.conf. You'll then need to re-install yaboot as detailed below
```
$ sudo  ybin -v
```
 If you need a little more assistance post your /etc/yaboo.conf.

---

