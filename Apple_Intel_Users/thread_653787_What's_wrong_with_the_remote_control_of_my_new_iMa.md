---
title: "What's wrong with the remote control of my new iMac?"
date: 2007-12-30
forum: Apple Intel Users
---

### Post by yxvaan on 2007-12-30
My new aluminium iMac 24" doesn't seem to recognize its small white remote controll at all. When I tried to switch on Totem's remote control plug-in, I got an error message: *"Unable to activate plugin. Couldn't initialize lirc."*

I also checked out what the 
[INDENT]"sudo cat /dev/input/event<n>"   (n running from 0 to 9) [/INDENT]
commands give but not one of them reacted to the remote's buttons. 


On the other hand, Ubuntu seems to find the relevant devices:

```
mw@xiMac:~$ dmesg | grep -i "ir rec"
[   38.362399] input: Apple Computer, Inc. IR Receiver as /class/input/input3
[   38.362403] input: USB HID v1.11 Device [Apple Computer, Inc. IR Receiver] on usb-0000:00:1d.2-1
```

So, where's the problem? Does the remote control have to be activated somehow? Or is there a bug in the Xubuntu amd64 version of Gutsy? I'd be very thankful for any suggestions for solving this problem, as I'm planning to turn this machine into a proper "HTPC" with MythTV and all...

-------------------------------------
Edit 3rd January 2008:

Since sending the original post I have installed Lirc (compiled it pretending that the remote was "macmini") and even managed to install the appleir.ko module (see  [e-tip's text]("http://ubuntuforums.org/showthread.php?t=607797&highlight=solved+apple+remote"), but do backup your /lib/modules/ if you decide to give it a try, too - there's a considerable risk of losing some other modules) but the remote control is still totally lifeless. I'd really like to have it working. Wouldn't anyone have any suggestions?

---

