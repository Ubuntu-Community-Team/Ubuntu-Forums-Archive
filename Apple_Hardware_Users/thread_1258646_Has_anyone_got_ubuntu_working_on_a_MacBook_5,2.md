---
title: "Has anyone got ubuntu working on a MacBook 5,2?"
date: 2009-09-05
forum: Apple Hardware Users
---

### Post by davideotape on 2009-09-05
I'm asking this question because I myself have a MacBook 5,2 and I can't get ubuntu to install at all.

First I tried Jaunty, but grub legacy didn't work ([https://bugs.edge.launchpad.net/ubuntu/+source/grub/+bug/417337](https://bugs.edge.launchpad.net/ubuntu/+source/grub/+bug/417337))

Then, I tried Karmic, but xorg doesn't support NV9400gm ([https://bugs.edge.launchpad.net/ubuntu/+source/xorg/+bug/422463](https://bugs.edge.launchpad.net/ubuntu/+source/xorg/+bug/422463))

Please could someone tell me how they have managed to get Ubuntu working on a 5,2 macbook :D

Regards,
David

---

### Post by hansdown on 2009-09-05
Hi davideotape.

It has been accomplished.

[http://www.youtube.com/watch?v=gsCO2yIfBPw](http://www.youtube.com/watch?v=gsCO2yIfBPw)

More info.

[http://www.google.ca/search?q=install+ubuntu+on+MacBook+5%2C2&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.ca/search?q=install+ubuntu+on+MacBook+5%2C2&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

---

### Post by dennis123123 on 2009-09-05
> **davideotape said:**
> 
Then, I tried Karmic, but xorg doesn't support NV9400gm ([https://bugs.edge.launchpad.net/ubuntu/+source/xorg/+bug/422463](https://bugs.edge.launchpad.net/ubuntu/+source/xorg/+bug/422463))


That seems incredibly strange, even so, vesa driver should work still, giving you access to get the nvidia binary driver.

EDIT: or maybe not; read from #153 [http://ubuntuforums.org/showthread.php?t=1188849&page=16](http://ubuntuforums.org/showthread.php?t=1188849&page=16)

---

### Post by davideotape on 2009-09-06
Thanks for the replies guys :)

Hansdown: I said before that grub legacy won't work with my MacBook, so that video (on the face of it) seems to be useless to me. I've also searched using those terms, but to no avail.

Dennis: I don't know why it isn't falling back on vesa myself. Oh well, I guess I'll just have to wait and see what happens.

---

### Post by dennis123123 on 2009-09-06
Like I said, there seems to be a regression in Xorg or something related. It should be fixed soon.

You have a few choices I see:


[LIST]
[*]Install Jaunty and pull in grub2 from Karmic / compile yourself
[*]Install Karmic and attempt to fix the problem with the latest nvidia beta driver (190.xxxx) - its rumored to work on other forums for some people
[*]Install Karmic and pull in Xorg from Jaunty (xserver-xorg v1.6.0)
[*]Wait until its fixed and live with MacOS / Windows / Linux in a VM in the mean time
[/LIST]
Let us know how it goes, whatever you choose!

---

### Post by davideotape on 2009-09-06
The trouble is I can't even install anything apart from jaunty and before. I've tried chrooting into jaunty and installing grub2, but I must be doing something wrong. I don't suppose there's a guide out there that could tell me how to chroot and install grub 2 is there?

Edit: If there's also a guide that tells me how to get the 190 drivers working on the livecd from the command line then I'd also be interested in that.

---

### Post by dennis123123 on 2009-09-06
I had completely forgotten that ubuntu makes you install through a live cd ><

If you can handle it, there is an alternative installer that uses good old text mode.
[http://www.ubuntu.com/getubuntu/downloadmirrors#alternate](http://www.ubuntu.com/getubuntu/downloadmirrors#alternate)
EDIT: oh, wait, there isnt an alternate Karmic listed, try this instead:
[http://cdimage.ubuntu.com/releases/karmic/alpha-5/karmic-alternate-i386.iso](http://cdimage.ubuntu.com/releases/karmic/alpha-5/karmic-alternate-i386.iso)

As for the nvidia drivers, download the beta from nvidia.com and run it; I think thats as simple as it gets really.

```
sh ./NVIDIA-Linux-x86-190.18-pkg1.run
```EDIT: just seen you said "on the live cd" - I doubt you can... go for a real installation

---

