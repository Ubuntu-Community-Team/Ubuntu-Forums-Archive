---
title: "Network freezes Ubuntu at startup"
date: 2007-04-08
forum: Absolute Beginner Talk
---

### Post by ocho on 2007-04-08
When I boot into Ubuntu, it freezes about halfway through the loading bar. I rebooted and went into the terminal using ctrl-alt-f1 and found that it froze at the initializing network stage. Above this, I found an error message under the initializing drivers section stating something along the lines of
"error loading prism54usb: EEPROM failed."
This, I believe, is a wireless usb driver so I'm thinking this may be the culprit. How can I uninstall this driver? I can boot into Ubuntu if I press ctrl-alt-delete. Thanks in advance.

---

### Post by Jussi01 on 2007-04-08
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/netbase/+bug/102675](https://bugs.launchpad.net/ubuntu/+source/netbase/+bug/102675) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				This is a known bug, I think you will just have to put up with it until it gets fixed, hopefully soon!

---

### Post by ocho on 2007-04-08
Thanks a lot Jussi01, that does seem to be a common problem with the Feisty release. No one else seems to have a problem with "EEPROM read failed" in regards to prism54usb, is this a big problem?

---

### Post by hardyn on 2007-04-08
its not exacltly the same error as the other posers... that eeprom error is something more.

if you can figure out what the module name is... i will assume prism54usb you can remove it though

sudo rmmod prism54usb

good luck.

---

### Post by Jussi01 on 2007-04-08
Its probably a hardware specific version of the same problem for your hardware. Id say wait until the fix for the other thing comes out, if that doesnt fix it then you may have to look closer...

---

### Post by ocho on 2007-04-08
Alright, I screwed something up. I was reading the posts on that bug site and found that a solution some were using was "sudo update-rc.d -f networking remove" 

I used this, and now the network manager does not even detect I have a wireless adapter plugged in. Ndiswrapper still has the driver installed. 

Can I reverse this command somehow? I'm quite illiterate when it comes to linux commands, so I don't really know what this even did.

---

