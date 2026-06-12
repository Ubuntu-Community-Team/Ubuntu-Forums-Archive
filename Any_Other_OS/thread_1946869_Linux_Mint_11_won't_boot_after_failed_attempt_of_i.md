---
title: "Linux Mint 11 won't boot after failed attempt of installing Nvidia drivers"
date: 2012-03-25
forum: Any Other OS
---

### Post by akzouu on 2012-03-25
Hey,

I have Linux mint 11 with kernel 3.0.0-12. Yesterday my Mint didn't boot to desktop after login screen. Everything worked well earlier, in spite crashes that I get from some another reason after pc has been on for hours.

So, here is something that i did on recovery command prompt:

```
sudo apt-get update && sudo apt-get upgrade
```

That gives me:

```
The following packages have been kept back:
linux-generic linux-headers-generic linux-image-generic
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
1 not fully installed or removed.
After this operation, 0 B additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up nvidia-current (295.33-0ubuntu1~natty~xup1) ...
update-alternatives: error: alternative link /usr/share/man/man1/nvidia-xconfig.1.gz is already managed by x86_64-linux-gnu_gl_conf.
dpkg: error processing Installed post-installation script returned error exit status 2
Errors were encountered while processing:
nvidia-current
E: Sub-process /usr/bin/dpkg returned an error code (1)
sudo apt-get install nvidia-settings nvidia-common
```

This command gives almost the same. The driver that it tries to install is version 295.33

Earlier already I had put this ppa:

```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
```

The thing I still want to say, the resolution on login screen dropped rapidly from 1920x1080 from resolution like 800x600. Not any application starts on login, just can hear login sound.

---

### Post by sffvba[e0rt on 2012-03-25
*Thread moved to **Other OS/Distro Talk**.*


404

---

### Post by akzouu on 2012-03-27
Problem solved. I found out that the reason, why i was having this problem was modified kernel. I installed drivers by hand.

---

