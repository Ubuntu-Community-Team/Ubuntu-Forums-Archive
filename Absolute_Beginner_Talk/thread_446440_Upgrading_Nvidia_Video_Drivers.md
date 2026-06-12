---
title: "Upgrading Nvidia Video Drivers"
date: 2007-05-16
forum: Absolute Beginner Talk
---

### Post by synergy99 on 2007-05-16
I'm a complete noob, But I've dived in the deep end and installed Kubuntu.

I'm trying to upgrade my nvidia drivers. I downloaded the x86 package with a .run extention

I did a "/etc/init.d/kdm stop" to shutdown the X desktop. Then I sh the .run file from Nvidia. It eventually says to me : [B]"No precompiled kernel interface was found to match your kernel; would you like the installer to attempt to download a kernel interface"
[/B]  but when it tries to download it doesnt find whatever its looking for.

Can anyone explain what I'm doing wrong? Whats it mean by kernel interface?

(ps - this is an AMD 64 X2 system with Nvidia Geforce 7800 GTX's)

---

### Post by Hobo Joe on 2007-05-17
Get Envy.

It's in synaptic I believe.

---

### Post by Pollywoggy on 2007-05-17
> **Hobo Joe said:**
> Get Envy.

It's in synaptic I believe.

I know that many people use Envy but all I did to get Nvidia to work was install the nvidia-glx-new package.  The upgrade to Feisty broke Nvidia for me but I got it working again by removing ALL the nvidia* packages (and purging them) and then installing the aforementioned package.  I already had a working nvidia config (xorg.conf).

---

