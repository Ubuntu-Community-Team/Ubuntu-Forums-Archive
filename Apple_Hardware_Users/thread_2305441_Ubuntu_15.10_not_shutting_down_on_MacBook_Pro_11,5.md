---
title: "Ubuntu 15.10 not shutting down on MacBook Pro 11,5"
date: 2015-12-06
forum: Apple Hardware Users
---

### Post by Simon_Zhu on 2015-12-06
Hi guys.
I have a MacBook 15 inch (Mid 2015), and I recently tried to install Ubuntu 15.10. Almost everything seemed to be working fine, except that it won't shut down properly. When I try to shut down, it just hangs forever on the splash screen with the ubuntu logo. I've installed it both with and without rEFIt, and I've even tried installing Mint instead but i get the same issue. The funny thing is, I can restart completely fine and the problem only shows up when I try to shut down. Also, I do not see grub when I start up the computer (although there seem to be posts online mentioning that i have to comment out a few lines in the configuration file).

Has anyone gotten Ubuntu to work on MacBook 11,5? Do you think it is a driver issue? I am new to Ubuntu so I'd appreciate if you guys would let me know what i can do to find out more about the problem. Thanks.

---

### Post by coldraven on 2015-12-06
I don't know about Macs but with the 4.2.0-19-generic kernel in 15.10 my laptop would not switch off. I've edited grub to use the 4.2.0-18-generic kernel and it now works fine. See my post in this sticky:
[http://ubuntuforums.org/showthread.php?t=2300290](http://ubuntuforums.org/showthread.php?t=2300290)

If that's too complicated maybe you should try with 14.04 instead.

---

### Post by Simon_Zhu on 2015-12-06
I turned off "quiet splash" in the grub settings to see what was causing the problem, but all I see it reaches "Will now halt. reboot: Power off", and then it hangs there. I've tried many of the proposed solutions to this problem online (setting "acpi=off", "pci=noacpi", etc) but none of them have worked for me so far.

---

