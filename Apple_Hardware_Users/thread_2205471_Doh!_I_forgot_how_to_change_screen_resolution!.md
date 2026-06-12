---
title: "Doh! I forgot how to change screen resolution!"
date: 2014-02-14
forum: Apple Hardware Users
---

### Post by Quackers on 2014-02-14
I have Ubuntu 13-10 running on my MacBook Pro retina 10,1. 
It's running in EFI mode.
I've edited /etc/default/grub by adding the entry
i915.lvds_channel_mode=2 i915.modeset=0 i915.lvds_use_ssc=0
after "quiet splash". I *think* this turns off the Intel graphics chip.

I then installed nvidia-current (304.88, which is a bit old but nvm) and ran nvidia-xconfig. I then added the line
Option         "UseDPLib" "off"
to the devices section of /etc/X11/xorg.conf

I rebooted and all is well  :D  Nvidia driver fires up and screen resolution is 2880 x 1800.
Things are very small  :shock:

Therein lies the problem. Neither Nvidia's settings nor Ubuntu's normal screen resolution settings show any other available resolution than 2880 x 1800.
I went all through this about a year ago and I found a way to change screen resolution..................but now I can't remember what I did  :(

Any suggestions please?
Thanks.

---

### Post by Quackers on 2014-02-14
Lol, nevermind, I found my own post about it  :D
Post 22 here
[http://ubuntuforums.org/showthread.php?t=2157775&page=3&highlight=screen+resolution]("http://ubuntuforums.org/showthread.php?t=2157775&page=3&highlight=screen+resolution")

---

