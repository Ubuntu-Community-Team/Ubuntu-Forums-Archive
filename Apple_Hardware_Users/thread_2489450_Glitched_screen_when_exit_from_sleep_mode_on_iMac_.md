---
title: "Glitched screen when exit from sleep mode on iMac 2009"
date: 2023-07-31
forum: Apple Hardware Users
---

### Post by bakaonigiri2 on 2023-07-31
Hello,

I tried to make an old iMac 2009 Intel usable again via the latest Ubuntu (I used the legacy installer for version 23.04).

This works great so far, but I have 1 problem. When I wake the computer from sleep mode, the screen is glitched. It have an ATI Radeon graphic GPU.

What can I do to solve that ?

Thanks.

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=292526&stc=1[/IMG][IMG]https://ubuntuforums.org/attachment.php?attachmentid=292527&stc=1[/IMG][IMG]https://ubuntuforums.org/attachment.php?attachmentid=292528&stc=1[/IMG][IMG]https://ubuntuforums.org/attachment.php?attachmentid=292529&stc=1[/IMG]

---

### Post by 1petter1 on 2023-09-22
Hello there
I have the same issue on both of my intel iMacs (I guess similar age): I had it with manjaro, mint and openSuse as well. I don't believe that is distro based. I fear it is the driver, which is incompatible with suspend and get glitchy. But nice to see not being alone with that Problem!

---

### Post by 1petter1 on 2023-09-22
I ended up killing the suspend feature completely using this command:
sudo systemctl mask suspend.target
this removes this feature from the UI as well. I suppose that the open source readon driver has a problem with suspend. You can try the catalyst(TM) driver 13.1 from AMD website. It is a .run Skript you have to use to install which works with ubuntu afaik. I could not get it installed on my current openSuse iMac. Maybe I&#8217;ll try it on my mint imac later.

---

### Post by stephan1827 on 2024-02-14
I also have this issue with 2008 iMac. Is there any solution for this?

---

