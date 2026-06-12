---
title: "iMac 10,1 brightness control"
date: 2011-09-10
forum: Apple Hardware Users
---

### Post by temporalburst on 2011-09-10
Okay, so I managed to install Ubuntu 11.04 on my iMac 10,1 fine, but now I'm having brightness control problems.

Right now, it's at full brightness and nothing will turn it down, I've tried multiple methods to get it to work, including the [bl1.c]("http://www.felipe-alfaro.org/blog/2006/09/11/basic-backlight-support-for-macbook-pro/") program (which I also found in a couple other places) which returns that it changed my brightness when it really didn't, it sets back to 15 every time. I've also tried pommed for the brightness keys, but they don't work with or without it. The brightness applet doesn't work either, of course.

Just wondering if I can possibly fix this without wearing sunglasses when using Ubuntu.

This is what the brightness program did:
```
temporal@temporal-iMac:~$ sudo ./backlight
Current value : 15
temporal@temporal-iMac:~$ sudo ./backlight 10
new value: 10
temporal@temporal-iMac:~$ sudo ./backlight
Current value : 15
temporal@temporal-iMac:~$ sudo ./backlight 1
new value: 1
temporal@temporal-iMac:~$ sudo ./backlight
Current value : 15

```

---

### Post by kapouer on 2011-09-10
Hello, i've had similar issues with imac 12,2.
However you don't provide enough information here, e.g.
did you boot in EFI or BIOS mode, and what
/sys/class/backlight
contains ?

---

### Post by temporalburst on 2011-09-10
Ahh, sorry, I knew my post was missing something.

/sys/class/backlight is just an empty directory for me.

And I booted from rEFIt into GRUB, if that's what you mean. I don't really know what that would make the boot mode. :?

EDIT: I'm running kernel version 2.6.38-11-generic, graphics card is GeForce 9400, if either of those matter.

---

### Post by mateo14 on 2011-09-13
> **temporalburst said:**
> Ahh, sorry, I knew my post was missing something.

/sys/class/backlight is just an empty directory for me.

And I booted from rEFIt into GRUB, if that's what you mean. I don't really know what that would make the boot mode. :?

EDIT: I'm running kernel version 2.6.38-11-generic, graphics card is GeForce 9400, if either of those matter.

1. First you have to install 2.6.39 Linux Kernel

[http://ubuntuguide.net/ubuntu-11-04-...el-to-2-6-39-0](http://ubuntuguide.net/ubuntu-11-04-...el-to-2-6-39-0)

2. sudo gedit /etc/X11/xorg.conf

3. "To enable brightness control in X, append 'Option "RegistryDwords" "EnableBrightnessControl=1"' to the Device-Section of xorg.conf, orginal source"

[http://www.thinkwiki.org/wiki/Category:W510](http://www.thinkwiki.org/wiki/Category:W510)

4. Reboot Your Computer

---

### Post by temporalburst on 2011-09-13
Wow, thank you so much! So happy for the fix for the brightness, it works well.

When it was installing the updated kernel, for some reason, it said "hid [fail]" during the process, but my computer seems to be running just fine anyway.

---

### Post by Stratosmacker on 2011-09-22
> **mateo14 said:**
> 1. First you have to install 2.6.39 Linux Kernel

[http://ubuntuguide.net/ubuntu-11-04-...el-to-2-6-39-0](http://ubuntuguide.net/ubuntu-11-04-...el-to-2-6-39-0)

2. sudo gedit /etc/X11/xorg.conf

3. "To enable brightness control in X, append 'Option "RegistryDwords" "EnableBrightnessControl=1"' to the Device-Section of xorg.conf, orginal source"

[http://www.thinkwiki.org/wiki/Category:W510](http://www.thinkwiki.org/wiki/Category:W510)

4. Reboot Your Computer

That link to the new kernel is broken. I tried to figure it out myself but I couldnt get the nvidia modules to compile.... Blah. Any suggestions dudes?

---

