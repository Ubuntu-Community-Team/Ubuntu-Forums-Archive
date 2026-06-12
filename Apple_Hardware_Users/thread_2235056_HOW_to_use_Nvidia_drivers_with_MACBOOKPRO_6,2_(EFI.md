---
title: "HOW to use Nvidia drivers with MACBOOKPRO 6,2 (EFI)"
date: 2014-07-18
forum: Apple Hardware Users
---

### Post by zeating on 2014-07-18
been searching how to properly install nvidia propriatary drivers under macbookpro, I've read that some people are able to do it, but whenever I try it's a black screen when I boot, every single time. Is there any support for this at all anymore?

---

### Post by jeehyun on 2014-07-20
You can just use "additional drivers" on system settings. It can not change brightness though.

---

### Post by Linux4ever on 2014-07-26
I have the Macbook Pro 7,2. Using pre-installed ubuntu nvidia drivers works in EFI boot. But once I use the nvidia set of drivers I will get a black screen. I don't even see login screen. Is there a way to fix this, so that it works for EFI boot?

---

### Post by tienneOz on 2014-07-31
I got the same issue, see my thread [here]("http://ubuntuforums.org/showthread.php?t=2237163"). Do you have sleep mode troubles too ? Did you try to proper reinstall drivers with the [Ubuntu-drivers]("http://askubuntu.com/questions/22118/can-i-install-extra-drivers-via-the-command-prompt") command ? Or to [reset]("http://askubuntu.com/questions/354582/how-to-reset-reinstall-default-drivers") /etc/X11/xorg.conf ?
It didn't work for me but maybe you will be more lucky.

---

### Post by tienneOz on 2014-08-02
I finally solved my issue. If anyone need, I did a clean install of mac  os then Ubuntu using these  [instructions](http://ubuntuforums.org/showthread.php?t=2157775).  I finally had a working system using only the Intel video card. But I  still didn't have my external screen working so I tried to boot from ATI  allowed grub and all was surprisingly working fine !
I hope this will help.

---

