---
title: "touchpad not working on MacBook after power out"
date: 2013-03-14
forum: Apple Hardware Users
---

### Post by ZICODIAN on 2013-03-14
[COLOR=#000000]The touchpad on my MacBook Pro (7, 1) running Ubuntu 12.04 64 bit has stopped working. It worked fine on the initial install of the operating system but after an instance of the laptop running out of power, the touchpad stopped working. I ended up reinstalling the operating system. The touchpad began working again. Unhappily, when the laptop again ran out of power, the touchpad again stopped working! Do you have any idea why this may be happening? I don't want to reinstall the operating system every time I run out of power! Thanks for any suggestions.[/COLOR]

---

### Post by tgalati4 on 2013-03-14
Multitouch touchpads have a small processor that runs to compute the presses and send events to the operating system.  This requires firmware to run.  My guess is that the touchpad firmware gets messed up during a sudden shutdown.  If you let the machine rundown under Win7 or Suse, do you get the same behavior?   Do you have a USB mouse as a backup?  Why did you need to reinstall the operating system?  Did it not boot up properly (besides the mouse issue)?

---

### Post by ZICODIAN on 2013-03-14
Thank you for your comment. It certainly looks as though you're right about the firmware getting messed up somehow with a sudden shutdown. I do not use Windows or SUSE, but I can say that previous versions of Ubuntu have not shown this difficulty for me. I have a USB mouse which works fine and I reinstalled the operating system in order to see if the problem is likely to be a hardware or a software one. Given that the reinstallation made the touchpad work again (before the subsequent power out), I think it's likely that it is a software problem. Everything shown appears as normal when booting up.

On running xinput list, two devices of interest are as follows:

bcm5974                                   id=12   [slave  pointer  (2)]
Apple Inc. Apple Internal Keyboard / Trackpad     id=11   [slave  keyboard (3)]

When I disable bcm5974 (xinput set-prop 12 "Device Enabled" 0), the clicking button of the touchpad stops working. When I enable bcm5974 (xinput set-prop 12 "Device Enabled" 1), the clicking button works again but the touchpad remains unresponsive. I have tried disabling and enabling device 11 too to no helpful effect.

Would you have any suggestions on what I may do?

---

### Post by tgalati4 on 2013-03-14
bcm implies a Broadcom chipset, which also implies a proprietary driver and binary blob.  So the behavior that you are seeing is probably tied to how the bcm5974 driver gets initiated.  When you turn it off and turn it back on, it doesn't completely reset without a complete power cycle.  This could be a simple driver code change, so send an email to Broadcom and see what kind of response you get.

The comment about Win7 or Suse, was directed at another post, so I apologize for the confusion.  You might want to set the shutdown threshold to 15% so you don't get the emergency shutdown.  Or get a new battery.

---

