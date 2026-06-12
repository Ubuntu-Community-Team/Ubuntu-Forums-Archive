---
title: "Wireless adapter"
date: 2007-04-09
forum: Absolute Beginner Talk
---

### Post by gunthermeyer on 2007-04-09
How do I get Ubuntu to acknowledge that I have a usb wireless adapter connection? I'm using a Belkin F5D6050 external wireless adapte. I'm using Ubuntu 6.10 for a x86 system. I know that it recognizes my intenal wireless card on my other computer. Thanks for any help. If I can get Ubuntu to acknowledge that I have a usb wireless adapter I might consider using Ubuntu on my desktop computer. I'm already using it on one of laptop computers. I'm also a new to Ubuntu and I hope that this isn't a dumb question. Also can I download the patches or something with Windows and plug it into Ubuntu later.

---

### Post by siciliancasanova on 2007-04-09
Here is the hardware support page for the [Belkin card]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBelkin")

There were few other posts for your card but it looks like using [ndiswrapper]("http://ubuntuforums.org/showthread.php?t=9454") to install the latest driver and also using wifi radar should work for you.

---

### Post by quagee on 2007-04-09
Try installing linux-restricted-modules-generic.

sudo apt-get install linux-restricted-modules-generic.

It will prompt you to put the install cd in and install from the cd.

I had issues with this as well when I installed Edgy, but not with Dapper.  Dapper recgnized the wireless right away.  With Edgy, I had tried everything including several versions of ndiswrapper.

Good luck with that.

---

