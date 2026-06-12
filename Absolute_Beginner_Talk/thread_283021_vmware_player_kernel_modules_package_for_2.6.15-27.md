---
title: "vmware player kernel modules package for 2.6.15-27 kernel"
date: 2006-10-23
forum: Absolute Beginner Talk
---

### Post by wande on 2006-10-23
Where I can find "vmware-player-kernel-modules-2.6.15-27" package? My apt only finds modules for 2.6.15-23 and installation of vmware-player fails because of that.

---

### Post by bobosity on 2006-10-23
I'm just seconding your request. I have the exact same problem. I had player working once but after reinstalling ubuntu I can't get it back. 

I think that vmplayer is one of those killer apps that will help people migrate from windoze. Maybe someone can put together a serious how-to for ubuntu.

---

### Post by wande on 2006-10-24
I ended up downloading vmware's installation package from [http://www.vmware.com/download/player/]("http://www.vmware.com/download/player/"), it compiles the required kernel modules if you have the kernel-headers installed.

---

### Post by bobosity on 2006-10-24
Ok.... I think I got it.

kernel headers from:

[http://security.ubuntu.com/ubuntu/pool/multiverse/v/vmware-player-kernel-2.6.15/vmware-player-kernel-modules-2.6.15-27_2.6.15.10-10_i386.deb](http://security.ubuntu.com/ubuntu/pool/multiverse/v/vmware-player-kernel-2.6.15/vmware-player-kernel-modules-2.6.15-27_2.6.15.10-10_i386.deb)

get player from:

[http://www.vmware.com/download/player/](http://www.vmware.com/download/player/)

This was ridiculously hard and I'm going to have to go through this again when I update the kernel. I think a tutorial would be helpful.

---

### Post by funkyade on 2006-10-24
> **bobosity said:**
> Ok.... I think I got it.

kernel headers from:

[http://security.ubuntu.com/ubuntu/pool/multiverse/v/vmware-player-kernel-2.6.15/vmware-player-kernel-modules-2.6.15-27_2.6.15.10-10_i386.deb](http://security.ubuntu.com/ubuntu/pool/multiverse/v/vmware-player-kernel-2.6.15/vmware-player-kernel-modules-2.6.15-27_2.6.15.10-10_i386.deb)

get player from:

[http://www.vmware.com/download/player/](http://www.vmware.com/download/player/)

This was ridiculously hard and I'm going to have to go through this again when I update the kernel. I think a tutorial would be helpful.

I agree, the idea of having them in the repositories is that they are upgraded whenver you upgrade your kernel, this doesn't seem to work. I think someone needs to create a dependency.

The easiest way is to lock you linux-image package at the version you have vmware modules for. That way you won't have to keep recompiling the modules...

---

