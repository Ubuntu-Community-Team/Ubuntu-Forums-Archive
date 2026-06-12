---
title: "wifi help on dell 700m"
date: 2008-01-02
forum: Absolute Beginner Talk
---

### Post by richriv712 on 2008-01-02
recently installed gutsy and am new to linux. everything is running smooth except for wifi on my dell 700m. can anyone help. thanks.

---

### Post by ubutufan on 2008-01-03
Symptoms??

---

### Post by richriv712 on 2008-01-03
led light off, not scanning for signals, basically dead. if you got any ideas i'd appreciate it. thanks.

---

### Post by ubutufan on 2008-01-04
To begin with, go System>Administration>Restricted Drivers Manager and check if your wireless card drivers are installed. If not then tick to enable and apply.

If this is not the case then in terminal (Applications>Accessories>Terminal type lspci (that will list all your pci devices). Post the outcome here.

---

### Post by richriv712 on 2008-01-04
the drivers for my wireless card are not shown(in restricted drivers), is it just a matter of downloading, installing and then enabling? again, i'm a newbie so thanks!

my intel Pro/Wireless 2200bg does show in terminal.

---

### Post by RSLxH on 2008-01-04
> **richriv712 said:**
> the drivers for my wireless card are not shown(in restricted drivers), is it just a matter of downloading, installing and then enabling? again, i'm a newbie so thanks!

my intel Pro/Wireless 2200bg does show in terminal.

Here is a howto guide:
[URL="http://www.debuntu.org/2006/03/27/9-how-to-ipw2200-getting-intel-pro-wireless-2200-bg-to-work-on-debian-ubuntu"]how-to-ipw2200-getting-intel-pro-wireless-2200-bg-to-work-on-debian-ubuntu
[/URL]

---

### Post by ubutufan on 2008-01-04
> **richriv712 said:**
> the drivers for my wireless card are not shown(in restricted drivers), is it just a matter of downloading, installing and then enabling? again, i'm a newbie so thanks!

my intel Pro/Wireless 2200bg does show in terminal.

That is the idea. There are already posts ready for you referred by another person. let us know if you were successful.

---

### Post by richriv712 on 2008-01-04
i looked over the info you guys gave and it made do a little more digging and all is well! thanks guys! i downloaded the driver and went into bios at start up and turned fn+f2 hotkey off and manually tuned it on. after a reboot i got a list of available signals and was able to get on home base. thanks again guys. cheers!

---

