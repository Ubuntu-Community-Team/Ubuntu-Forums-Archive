---
title: "Modem connection"
date: 2007-12-02
forum: Absolute Beginner Talk
---

### Post by ser_virtual on 2007-12-02
Hi,

I just installed Ubunutu 7.10 on a Dell Inspirion 1501. I also installed the driver for the Conexant D110 modem provided by Dell and it appears as activated in the Restricted Device Manager. However I don´t know how to proced. When trying to fill in the tabs of the Network Tools, I don´t know which port the modem is connected to. I also don't know why every time I reopen this tool the password seems to have duplicated. Moreover, the wireless connection mode is activated while the modem one deactivates in the mait tab of this configuration tool. I also have doubts on the process of getting connected. In ms windows you click on a dial up buttom and hear the corresponding sound . Is there a similar way under Ubuntu? Sorry, I´m a newbi.

By the way, is there any preference on the DNS numbers you are requeste to fill in the Networ Tools tab DNS.

Thaks in advance

---

### Post by madjr on 2007-12-22
> **ser_virtual said:**
> Hi,

I just installed Ubunutu 7.10 on a Dell Inspirion 1501. I also installed the driver for the Conexant D110 modem provided by Dell and it appears as activated in the Restricted Device Manager. However I don´t know how to proced. When trying to fill in the tabs of the Network Tools, I don´t know which port the modem is connected to. I also don't know why every time I reopen this tool the password seems to have duplicated. Moreover, the wireless connection mode is activated while the modem one deactivates in the mait tab of this configuration tool. I also have doubts on the process of getting connected. In ms windows you click on a dial up buttom and hear the corresponding sound . Is there a similar way under Ubuntu? Sorry, I´m a newbi.

By the way, is there any preference on the DNS numbers you are requeste to fill in the Networ Tools tab DNS.

Thaks in advance

install gnome-ppp patched:
[http://launchpadlibrarian.net/106924....24-1_i386.deb](http://launchpadlibrarian.net/106924....24-1_i386.deb)

bug report for patch found here:
[https://bugs.launchpad.net/ubuntu/+s...pp/+bug/121487](https://bugs.launchpad.net/ubuntu/+s...pp/+bug/121487)

---

