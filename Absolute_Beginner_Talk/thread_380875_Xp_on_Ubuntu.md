---
title: "Xp on Ubuntu"
date: 2007-03-10
forum: Absolute Beginner Talk
---

### Post by jcrnan on 2007-03-10
How do I get XP installed on Ubuntu? Is there any step for step guides for how to do this? The vmware player/server thing confuses me.

---

### Post by oilchangeguy on 2007-03-10
first do you know how to obtain vm ware? try automatix, and install it from there. sceond what is confusing you? once vm ware is loaded, open it and you install your os there just as you normally would. which for xp it has to be a legal copy, not a copy you've already used on another computer.

---

### Post by Obor on 2007-03-10
If I remember right Automatix can only install vmplayer (I don't use it anymore so I might be wrong).
If you want to install your copy of Win XP in VMware server you can follow [this thread]("http://www.ubuntuforums.org/showthread.php?t=183209")

There is also [Qemu]("https://help.ubuntu.com/community/WindowsXPUnderQemuHowTo") (that howto is for Feisty i.e. next version of Ubuntu) which you can use instead of vmserver.

---

### Post by jcrnan on 2007-03-10
I'm not interested in using Automatix. Also what I was wondering was what is the difference between Server and Player is. And as far as Qemu, it looks interesting but I won't use Feisty for still a little while.

---

### Post by pveith on 2007-03-10
I would suggest downloading the vmware-server or (if you have a pacifica/vanderpool processor) testing feisty with kvm. The vmware-player is in the ubuntu repos, but i lags the install guest features, which will leave you with a very slow 640x480 Windiws, while vmware server provides the drivers for XP to run faster and use higher resolutions.

There is also the virtual-box now open-source. This would be my recommandation for edgy  (see [http://www.virtualbox.org/)](http://www.virtualbox.org/)).

---

### Post by Obor on 2007-03-10
> **jcrnan said:**
> Also what I was wondering was what is the difference between Server and Player is.
VMplayer will let you run, share and evaluate **pre-built **applications, OSs etc. For what you want to do i.e. install your xp you will need the [vmserver]("http://www.vmware.com/products/free_virtualization.html"). 


If you want qemu guide for dapper there is [one here]("http://maconstuff.blogspot.com/2006/06/how-to-run-windows-xp-under-ubuntu.html")

---

