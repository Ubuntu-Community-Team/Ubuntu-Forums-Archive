---
title: "Please help install Nvidia drivers..."
date: 2006-06-03
forum: Absolute Beginner Talk
---

### Post by madu on 2006-06-03
Hi guys..

I'm trying to install the Nvidia drivers but seem to having problems.
I am using this post:
[http://www.ubuntuforums.org/showthread.php?t=75074&highlight=nvidia+latest](http://www.ubuntuforums.org/showthread.php?t=75074&highlight=nvidia+latest)

But I get this error:
[B]madu@madu-desktop:~$ sudo apt-get install nvidia-glx nvidia-settings linux-restricted-modules-`uname -r`
Reading package lists... Done
Building dependency tree... Done
linux-restricted-modules-2.6.15-23-386 is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  nvidia-glx: Conflicts: nvidia-settings but 1.0-3ubuntu7 is to be installed
E: Broken packages
madu@madu-desktop:~$[/B]

What is wrong am I doing? Have I not enabled repositories? I think I did, but I tried to find a thread that illustrates how to, but couldnt find one.

Please help me guys..

Thanks a lot..

Madu

---

### Post by jasay on 2006-06-04
nvidia-settings is now integrated into nvidia-glx, so there is no reason to install nvidia-settings anymore.  The two packages now conflict with each other so you can't install both.  Try this instead and then carry on with the howto. ```
sudo apt-get install nvidia-glx linux-restricted-modules-`uname -r`
```

---

### Post by madu on 2006-06-04
Got it Jasay.. It worked.. thanks a lot..!

---

### Post by tseliot on 2006-06-04
[QUOTE=madu]Hi guys..

I'm trying to install the Nvidia drivers but seem to having problems.
I am using this post:
[http://www.ubuntuforums.org/showthread.php?t=75074&highlight=nvidia+latest](http://www.ubuntuforums.org/showthread.php?t=75074&highlight=nvidia+latest)

But I get this error:
[B]madu@madu-desktop:~$ sudo apt-get install nvidia-glx nvidia-settings linux-restricted-modules-`uname -r`
Reading package lists... Done
Building dependency tree... Done
linux-restricted-modules-2.6.15-23-386 is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  nvidia-glx: Conflicts: nvidia-settings but 1.0-3ubuntu7 is to be installed
E: Broken packages
madu@madu-desktop:~$[/B]

What is wrong am I doing? Have I not enabled repositories? I think I did, but I tried to find a thread that illustrates how to, but couldnt find one.

Please help me guys..

Thanks a lot..

Madu[/QUOTE]
That guide is for Breezy. I'll try to make it even clearer at the beginning of that guide.

---

