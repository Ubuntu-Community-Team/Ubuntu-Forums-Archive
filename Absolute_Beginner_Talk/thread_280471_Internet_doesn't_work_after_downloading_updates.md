---
title: "Internet doesn't work after downloading updates"
date: 2006-10-19
forum: Absolute Beginner Talk
---

### Post by Evergrey on 2006-10-19
Hello, this is second time I installed Ubuntu as Dual boot with xp... I had many problems first time so I decided to try all over again.
After new format and install I was very happy to see that my internet connection works, new updates ready for downloading (I wasn't that lucky first time). My first installation had no problems with internet but I could not download any updates.
Now I downloaded all updates, around 200MB. I restarted comp after all updates completed and then shut down my comp.
Later when I boot ubuntu I cannot open any page in firefox, or start gaim. After install -> first boot, internet worked just fine.
What could be wrong now?
I tried booting xp and it works fine.
Some details.

I'm using thomson speedtouch 530 adsl modem to connect to interet. It is connected in D-Link 5 port switch. I use switch cause I have 2 computers and want internet access on both.
Switch should be no issue because it worked after new fresh install... :(


edit:
I forgot to mention that I have 2 kernels for some reason in Grub boot menu. It looks like this:

Kernel 2.6.15-27-386
Kernel 2.6.15-27-386 (recovery mode)
Kernel 2.6.15-23-386
Kernel 2.6.15-23-386 (recovery mode)

---

### Post by macdo on 2006-10-19
The reason you've got two kernels is because that was one of the updates. No worries.

As for the internet problem, could you type at the command line ```
ifconfig -a
```
and post the result, please?

---

### Post by rakhi on 2008-02-27
Hi, I'm having a similar issue - my network went down after installing some updates, and now GNOME desktop doesn't start any more.  I booted into recovery mode and turned on my internet using 

/etc/init.d/udev restart
/etc/init.d/module-init-tools restart
/etc/init.d/networking start

but when I run 'apt-get update' it can't resolve any of the servers, so I guess it's still not working.

when I run ifconfig -a I get:

> eth 1  

---

### Post by rakhi on 2008-02-27
Sorry, pressed <tab> <enter> by mistake.

> eth 1       Link endcap:Ethernet    HWaddr 00:1C:BF:2C:C8:74
                              BROADCAST MULTICAST MTU:1500  Metric:1
                              RX packets:0 errors:0 dropped:51982 overruns:0 frame:0
                              TX packets:0  errors:0 dropped:0         overruns:0 carrier:0
                              collisions:0 txqueuelen:1000
                              RX bytes:0 (0.0 b)   TX bytes:0 (0.0 b)
                              Interrupt: 19 Base address: 0x8000 Memory:dfcff000-dfcfffff

I turned my wireless radio off to better debug the ethernet.

Any help would be MUCH appreciated!!!

---

