---
title: "Ubuntu freezes constantly"
date: 2008-03-13
forum: Absolute Beginner Talk
---

### Post by Strates on 2008-03-13
I'm using Ubuntu 7.04 Live CD, on an HP machine. After about 20 seconds to a few minutes of running it will freeze with no response from anything other than a hard reboot. Occasionally it will freeze while booting. I'm running an x86 AMD processor, with onboard HD.

Can anyone help with this problem by any chance?


                                          Nathan

---

### Post by ajmorris on 2008-03-13
hey there, 
could you please paste the outputs of the following commands? (from a terminal):
 
```
sudo dmesg
```
```
sudo less /var/log/syslog
```
 
Also, change your kernel line in /boot/grub/menu.lst for you current kernel with the following at the end of the line, this is the usual fix for this problem:
nosplash noapic nolapic

---

