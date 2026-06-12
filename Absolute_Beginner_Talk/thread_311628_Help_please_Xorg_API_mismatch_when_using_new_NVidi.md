---
title: "Help please Xorg API mismatch when using new NVidia (1.0-9629) driver"
date: 2006-12-03
forum: Absolute Beginner Talk
---

### Post by cogvos on 2006-12-03
Dear all,

Sorry baffled again.
I have just downloaded the Nvidia driver 1.0-9629 from their website and installed it as follows.

1 killed X server.
2 Logged in as root
3 sh nvidia package.
3a it stated that it didn't have a precompiled kernel module and asked if I wanted to download. But I couldn't as I have a win modem in this box which is not supported (checked with scanModem).
3b so I let it build a module - all ok (?)
4 Let it reconfigure Xorg.conf - all ok (?)
5 Started X, Nvidia logo appeared. logged in, all looked ok.

6 rebooted. X failed to start with the following error -
API mismatch Nvidia kernel module has version 1.0-7184. This X module has version 1.0-9629 and then something like please make sure they match.

:confused: Whats gone wrong? Since the install built the module how did it get the wrong version? How do I get them to match? How come it worked initially and now doesn't!

Hope someone can unconfuse me.

John.

---

### Post by steve.horsley on 2006-12-03
I think you need to uninstall the restricted-modules kernel that you got from the repositories, and **then** install the newer driver from nvidia.

I have to say, I'm a little irritated that the Edgy repos don't offer that 9629 driver. It reminds me of what Linux was like years ago, having to spend so long getting things working, sorting out incompatibilities.

---

### Post by cogvos on 2006-12-03
Hi Steve,

Sorry little more confused here. On initial install the Xorg.conf had the default nv driver, least I think it had. Do you know if this uses the restricted driver? I was under the impression that this was a 2d one that came with the majority of distros (certainly came with suse) and was not provided by Nvidia. 

On other distros I just installed the latest from Nvidia and there were no conflicts. I haven't installed the restricted driver from the repository manually, but then have no idea if anything else might have grabbed it without my knowledge. How do I find out?

Any ideas what to do if it turns out (as I suspect) the restricted driver has not been installed from the repository?

Many thanks

John.

---

### Post by steve.horsley on 2006-12-03
It's a two-piece set as far as I can tell. There's the driver that gets loaded in xorg (nvidia, not the 2D nv driver) and a matching kernel module. The restricted-modules kernel in the repos provides the earlier (7184?) module. You have to remove this before you can load the later nvidia modules.

---

### Post by cogvos on 2006-12-03
Hi Steve,

Success! You were right, oddly enough there was a restricted kernel module that was being loaded (how it got there is beyond me). I removed it. Re-installed the latest driver and all is ok. At least with the display anyway. Am having major problems elsewhere though and am beginning to wonder if Umbuntu is for me.

Still many thanks for your assistance.

John.

---

### Post by po0f on 2006-12-03
cogvos,

You will have to fix a lot of symlinks if you ever decide to use the drivers in the repositories again.  The NVIDIA installer messes with a bunch of file under /usr/lib and /usr/lib/xorg, so Apt won't touch them.  I figured this out myself the other night the hard way.  :)

---

### Post by cogvos on 2006-12-03
Hmmm, two steps forward, one step back. I guess it won't matter that much as I tend to stick to ethe Nvidia drivers so the fact the repository is now closed to me should not be an issue (he types hopefully)

Given the aclocal problems I have run into trying to compile one app it's the least of my worries, however thanks for the warning.

John.

---

### Post by Stolen on 2006-12-31
I also ran into this problem, and it was because I didn't follow the complete method 2 in 
[http://doc.gwos.org/index.php/Latest_Nvidia_Edgy](http://doc.gwos.org/index.php/Latest_Nvidia_Edgy)

The part I missed was:
```

sudo nano -w /etc/default/linux-restricted-modules-common

```
and add nv to the DISABLED_MODULES line:
```

DISABLED_MODULES="nv"

```

This prevents the nv module in the restricted modules package from loading and therefore avoids the mismatch.

---

