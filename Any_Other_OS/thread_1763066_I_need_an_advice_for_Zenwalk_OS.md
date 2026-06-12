---
title: "I need an advice for Zenwalk OS"
date: 2011-05-19
forum: Any Other OS
---

### Post by silex89 on 2011-05-19
I have a Virtual machine running with Zenwalk 7.0 (Slackware based), I'm thinking to migrate to that distro (if I can't solve the issues, I'll go to Sabayon), but I want to be EXTREMELY SURE that is a reliable OS (at least it was in the past), so I've been studying it and I almost got convinced to format my laptop and begin using it, but there are some issues that I don't know how to resolve (all of them in the Virtualbox context).


[LIST=1]
[*]I don't have any sound coming from the system (ICH 97 controller for the VB)
[*]I have a mobile broadband device (Huawei E1756C USB Stick with HSPA connectivity). I have the USB controls configured properly to use my USBs with the Virtualbox (which I tested on another VB with WinXP and works fine). But Zenwalk doesn't show me the device anywhere. Maybe I have to work with the kernel source, but I'm not sure.
[*]I have a Broadcom BCM series... and I have the same problem than the point I just mentioned.
[/LIST]
I really want to use this distro (I've been trying it since it's third version and worked really nice with my old Desktop Computer) but these issues really turn me off....

I've already tried to search for answers but this distro is not popular....

What can I do? :(

---

### Post by wolfen69 on 2011-05-20
You don't need to configure internet in the guest OS. You simply need to be online in the host OS, and the guest will automatically connect. At least that was the case with the 60 or so distros I've tried in Vbox.

---

### Post by boydrice on 2011-05-20
> **silex89 said:**
> I have a Virtual machine running with Zenwalk 7.0 (Slackware based), I'm thinking to migrate to that distro (if I can't solve the issues, I'll go to Sabayon), but I want to be EXTREMELY SURE that is a reliable OS (at least it was in the past), so I've been studying it and I almost got convinced to format my laptop and begin using it, but there are some issues that I don't know how to resolve (all of them in the Virtualbox context).


[LIST=1]
[*]I don't have any sound coming from the system (ICH 97 controller for the VB)
[*]I have a mobile broadband device (Huawei E1756C USB Stick with HSPA connectivity). I have the USB controls configured properly to use my USBs with the Virtualbox (which I tested on another VB with WinXP and works fine). But Zenwalk doesn't show me the device anywhere. Maybe I have to work with the kernel source, but I'm not sure.
[*]I have a Broadcom BCM series... and I have the same problem than the point I just mentioned.
[/LIST]
I really want to use this distro (I've been trying it since it's third version and worked really nice with my old Desktop Computer) but these issues really turn me off....

I've already tried to search for answers but this distro is not popular....

What can I do? :(

I can't speak to the particulars of your hardware but as far as Zenwalk is concerned it is a no go for me.  I think the package manager netpkg is terrible.  I would recommend SalixOS or Vector Linux over Zenwalk but in my opinion you are much better just installing Slackware itself.

---

### Post by k357k9 on 2011-05-20
[http://www.linuxbsdos.com/2011/04/13/zenwalk-7-review/]("http://www.linuxbsdos.com/2011/04/13/zenwalk-7-review/")
Did you see this review?

---

### Post by jeffathehutt on 2011-05-20
> **silex89 said:**
> 
[LIST=1]
[*]I don't have any sound coming from the system (ICH 97 controller for the VB)
[/LIST]


I'm not sure if that is from the VM or Zenwalk itself, but I remember in Slackware a long time ago you had to manually add your user to the audio group.  That was 10 years ago and was with slackware, so I have no idea if it is still relevant.

---

### Post by andrew.46 on 2011-05-22
> **jeffathehutt said:**
> [...] I remember in Slackware a long time ago you had to manually add your user to the audio group.  That was 10 years ago and was with slackware, so I have no idea if it is still relevant.

With Slackware you can now add yourself to a small list of groups with a simple 'arrow down' when creating a new account with adduser. Or is that 'arrow up'.....

---

