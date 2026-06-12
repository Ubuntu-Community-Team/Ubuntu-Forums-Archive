---
title: "USBSerial - Command Not Found"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by sjakma on 2007-04-29
Help!  I just installed Ubuntu 7.04 and I am trying to run the command usbserial to configure a wireless verizon card on a dell 1210.  Each time I run usbserial I get Command Not Found.

Thanks,
Scott

---

### Post by wirelessmonkey on 2007-05-01
To my knowledge, and a quick Google search,  "usbserial" isn't a command, it's a descriptor in lsmod.  Do you have some instructions you're working from?

---

### Post by sjakma on 2007-05-01
Thank You for replying!!  Below are the instructions.   After looking at the issue, it seems that when I run modprobe nothing happens.  When I check /var/log/messages, nothing is appearing.


$lsusb
$sudo modprobe usbserial vendor=0×413c product=0×8114
$ sudo sh -c "usbserial vendor=0×413c product=0×8114 >> /etc/modules"
$ grep tty /var/log/messages

---

