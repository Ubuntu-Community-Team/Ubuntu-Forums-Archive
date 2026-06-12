---
title: "NVIDIA Driver Install Options"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by Cat.Food on 2007-04-21
Hello!

Been using Dapper Drake for a few weeks now.  I tried out Feisty Fawn, but Dapper just seems more right for me...

Anyways, according to the online desktop guide for Dapper, after installing the NVIDIA driver, you enter this command to enable it:

[Click here for the desktop guide.]("https://help.ubuntu.com/6.06/ubuntu/desktopguide/C/hardware.html")

> sudo nvidia-glx-config enable

However, according to the community-supported documentation, you enter this command to enable it:

[Click here for the community-supported guide.]("https://help.ubuntu.com/community/Latest_Nvidia_Dapper")

> sudo nvidia-xconfig

So, my question is:  What's the difference between these two commands?  What do they each do?

I should note that running both will cause X to fail upon rebooting.  Yep, I found that out the hard way...

Thanks in advance for the help!  :)

---

### Post by overdrank on 2007-04-21
> **Cat.Food said:**
> Hello!

Been using Dapper Drake for a few weeks now.  I tried out Feisty Fawn, but Dapper just seems more right for me...

Anyways, according to the online desktop guide for Dapper, after installing the NVIDIA driver, you enter this command to enable it:

[Click here for the desktop guide.]("https://help.ubuntu.com/6.06/ubuntu/desktopguide/C/hardware.html")



However, according to the community-supported documentation, you enter this command to enable it:

[Click here for the community-supported guide.]("https://help.ubuntu.com/community/Latest_Nvidia_Dapper")



So, my question is:  What's the difference between these two commands?  What do they each do?

I should note that running both will cause X to fail upon rebooting.  Yep, I found that out the hard way...

Thanks in advance for the help!  :)

Hi I am not a expert but I use glx will offer different effects than the other option. Nvidia config lets you configure you system and it is step by step like the default resolution you like.:guitar:

---

### Post by Cat.Food on 2007-04-22
Hi!

I just wanted to follow-up to my original post...

After a bit of troubleshooting, I've found that this command was causing the problems:

> sudo nvidia-glx-config enable

It was actually configuring my xorg.conf file for a Radeon card!!!  WTF?!?

I did a bit of checking around on the intarwebs, and found others have experienced similar problems with that command in Dapper...

If you're setting up the NVIDIA drivers in Dapper, the correct command to enable them is:

> sudo nvidia-xconfig

The official documentation is wrong!

---

