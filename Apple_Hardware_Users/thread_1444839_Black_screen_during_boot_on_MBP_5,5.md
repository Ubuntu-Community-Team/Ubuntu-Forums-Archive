---
title: "Black screen during boot on MBP 5,5"
date: 2010-04-01
forum: Apple Hardware Users
---

### Post by dlenmn on 2010-04-01
Sometime last week I tried starting up ubuntu and I'd end up with a black screen -- I haven't had time to deal with it until now. I tried starting in recovery mode, and it'd go along for a while, but then stop and the screen would go blank. The computer is still on (I can hear the fan), but nothing seems to happen, even after waiting for some time.

The recovery mode output right before the screen goes blank is shown in this [linked image]("https://mywebspace.wisc.edu/lnmaurer/web/DSCF0332.JPG"). Then, it pauses (for some time) before going blank. I think there's some new output right before it goes dark, but it's too fast for me to read or capture.

The machine is running Kubuntu 9.10. The same thing happens with either the -19 or -20 kernels.

I don't recall doing anything unusual before this happened.

The machine works just fine in OS X or Windows 7.

Thoughts?

---

### Post by linuxopjemac on 2010-04-02
I think I heard something similar lately. It was solved by upgrading the nvidia-backlight driver, see here:
[http://ubuntuforums.org/showthread.php?t=1442790&page=2](http://ubuntuforums.org/showthread.php?t=1442790&page=2)

The trick was to replace nvidia-bl-dkms by mbp-nvidia-bl-dkms. You can only do that from the liveCD (chroot into your system).

Add the Mactel PPA to your repository and update your repository. Then install the newer mbp-nvidia-bl-dkms.
[https://wiki.ubuntu.com/MactelSupportTeam/PPA](https://wiki.ubuntu.com/MactelSupportTeam/PPA)
```
sudo apt-get update
sudo apt-get remove nvidia-bl-dkms
sudo apt-get install mbp-nvidia-bl-dkms
```

here you see the packages in the Mactel PPA:
[https://launchpad.net/~mactel-support/+archive/ppa](https://launchpad.net/~mactel-support/+archive/ppa)

---

### Post by dlenmn on 2010-04-02
Thanks for the tip -- I'll look in to it.

---

