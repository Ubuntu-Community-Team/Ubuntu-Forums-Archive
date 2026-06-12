---
title: "Power Surge on Hub Port"
date: 2013-05-28
forum: Any Other OS
---

### Post by manolomanolo on 2013-05-28
Hi to all.

Despite here I'm asking for support on Ubuntu based distros, in the title I wrote the warning message that I get when running Windows XP Professional 64bit.
In short, it seems there's some problem with one or more of my USB ports. That message appears no matter there is any USB device connected to any of my USB ports. At the moment, the only way to "fix" the problem on Windows is just disabling the USB 2.0 Enhanced controller as [described here]("http://support.microsoft.com/kb/934644"). Unfortunately, the side effect is that I completely lose the possibility to use any of the 4 usb ports on my laptop, despite the side effect reported on the article was just losing the USB 2.0 functionality, but just getting USB 1.1 functionality on each port. In detali, when disabling that controller I'm not even able to make an optical mouse work. However, this is not a "solution" also taking into account that the workasound does not always prevent that message to bother again. I mean, once it stops it never comes up again, but I'm not always able to stop that message that way.

Please see the screenshots.
[ATTACH=CONFIG]243139[/ATTACH][ATTACH=CONFIG]243140[/ATTACH]

**Back to Linux**, the problem is probably related to the fact that often I'm not able to resume from Hybernate or Suspend (since it seem to happen the same on Windows systems). Also, very often I'm not even able to restart the system. The only way I found to restart the system is unplugging any power source (i.e.: unplug both battery and power cable) and press the "power" botton a couple of time. According to my understanding that helps the computer get rid of any "passive" or "excessive" or "whatever" charge may be stucking my computer. In detail, if I just try to restart my system what I get is the system trying to boot a couple of time without even been able to load the BIOS: so, the try just lasts maybe around 7 seconds and then the computer reboots... 7 seconds more and reboot again...
However, I experience a general slow down of the computer maybe due to continuous logging of related warning messages.
Some error/warning messages appear on the console screen when trying to resume from Suspend or when trying to halt the system.
Maybe you want me to attach any log or any dmesg.

**So, what am I asking now? If possible, solving the problem by both chainging some hardware or disabling some port withour losing the complete functionality on all the 4 USB ports.**

Thanks,
regards.

Acer Aspire 5730z
Linux Mint 14

---

### Post by Perfect Storm on 2013-05-29
Moved to Other OS/Distro Support.

---

### Post by tgalati4 on 2013-05-29
If you are running Ubuntu then those over-power messages will normally show up in *dmesg*, or in some log files in /var/log.  It's possible that you have some dirt in the USB ports, or cracked solder joints from flexing of the USB connector, or static electricity damage to the USB controller.  Although difficult to do, I would take the laptop apart and resolder the ports with the correct solder iron and tip (800F, micro tip) and see if that fixes it.  Since there is typically one controller that serves 4 ports, it is unlikely that you can simply turn off the offending port.  It's all or nothing.

This looks like a hardware problem, not a software problem.  You can probably turn off the USB ports in BIOS and that will end the messages, but then you lose the USB ports.

It's also possible that you have a defective mouse or other device that is really drawing more current than it is supposed to.  When that happens, the USB port will shut down to protect itself.

---

