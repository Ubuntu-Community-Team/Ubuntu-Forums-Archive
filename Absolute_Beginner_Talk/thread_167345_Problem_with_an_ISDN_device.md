---
title: "Problem with an ISDN device"
date: 2006-04-28
forum: Absolute Beginner Talk
---

### Post by Asix on 2006-04-28
Hello everyone, 
I've searched these forums for a while in order to find a solution for my problem, and some of them really were helpful a bit, but I've still having problems with setting up all of the ISDN stuff (on Ubuntu version 5.10).
First, I've followed all steps from [https://wiki.ubuntu.org/IsdnHowTo](https://wiki.ubuntu.org/IsdnHowTo) page, and when I type ```
pon isdn-provider
``` I get an error message saying: ```

Plugin userpass.so loaded.
userpass: $Revision: 1.5 $
Plugin capiplugin.so loaded.
capiplugin: $Revision: 1.36 $
capiconn: 1.13
capiplugin: CAPI_REGISTER failed - CAPI not installed (0x1009) [No such device or address (6)]

```
When I type ```
sudo modprobe hisax type=20
``` I get an error message saying:
```
FATAL: Error inserting hisax (lib/modules/2.6.12.9.386/kernel/drivers/isdn/hisax/hisax.ko): no such device
```
When I type ```
sudo /etc/init.d/isdnutils restart
``` I get the following output:
```
Restarting ISDN services: error:
Neither /dev/isdninfo nor /dev/isdn/isdninfo exist!
Before you can use any ISDN facilities, ensure you have the
proper kernel modules loaded. These will probably be 'isdn' and
'hisax'. Read /usr/share/doc/isdnutils-base/README.HiSax.gz for
more information (e.g. with 'zless
/usr/share/doc/isdnutils-base/README.HiSax.gz').
```
What's missing here and what do I do? I'm totally confused, I've been trying to set this up for about a week, and I don't have a clue what to do anymore.

---

### Post by Asix on 2006-05-01
Anybody?

---

