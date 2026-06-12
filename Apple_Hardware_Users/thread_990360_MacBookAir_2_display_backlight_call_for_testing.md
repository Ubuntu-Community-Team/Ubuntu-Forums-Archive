---
title: "MacBookAir 2 display backlight call for testing"
date: 2008-11-22
forum: Apple Hardware Users
---

### Post by _mario_ on 2008-11-22
Hi,

due to linuxbest figuring out how to change the display backlight of 5th generation MacBooks, we might also be able to support the 2nd generation MacBookAir, which incorporates the same graphics adapter. Can anyone please confirm that it actually works?

Instructions:
1. Install the mbp_nvidia_bl package from the mactel repository:
```
sudo apt-get install mbp-nvidia-bl-dkms
sudo rmmod mbp_nvidia_bl
sudo modprobe mbp_nvidia_bl
```

2. Set display brightness to some low value, e.g.:
```
echo 1 | sudo tee /sys/class/backlight/mbp_backlight/brightness
``` and report whether it works. (Function keys might not work.) Be aware: On a MacBook 5, it was reported to not work using Nvidia's proprietary driver. Switching to a text console first allowed to change the backlight.

3. If it didn't work, remove the package:
```
sudo apt-get remove --purge mbp-nvidia-bl-dkms
```

The initial thread dealing with MacBook/MacBook Pro is [here]("http://ubuntuforums.org/showthread.php?t=977558").

thanks & ciao,
Mario

---

