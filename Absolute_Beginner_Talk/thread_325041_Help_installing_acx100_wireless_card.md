---
title: "Help installing acx100 wireless card"
date: 2006-12-24
forum: Absolute Beginner Talk
---

### Post by nyxynyx on 2006-12-24
Hello, i have problems installing the acx100 wireless card(Dlink dwl520+) on Edgy. I followed the instructions at [http://acx100.sourceforge.net/wiki/ACX](http://acx100.sourceforge.net/wiki/ACX) and dmesg shows 

```
acx v0.3.21: net device wlan0, driver compiled against wireless extensions 20 and Linux 2.6.17-10-386
wlan0 (WE): Driver using old /prov/net/wireless support, please fix driver!
wlan0: changing radio power level to 18 dBm (23)
ADDRCONF(NETDEV_UP): wlan0: link is not ready
``` 

Thanks for any help!

---

### Post by nyxynyx on 2006-12-25
anyone?

---

### Post by MkfIbK7a on 2006-12-25
try looking up the driver for your card download it on another computer transfer it with a usb drive and start from there

---

### Post by nyxynyx on 2006-12-25
i have hard-wired internet access on the system with wireless card trouble. I tried ndiswrapper with the winxp drivers but it doesnt work :( Any suggestions?

---

### Post by nyxynyx on 2006-12-25
The card works fine in Windows. So probably not a hardware problem. Anyone?](*,) ](*,)

---

### Post by SpaceTrapper on 2007-01-13
I have the same card and it has worked fine with ubuntu since i think 4.10. The ACX100 drivers are included, so all I ever had to do is put in the card and reboot if it wasnt in the machine (and working correctly) right at install....It didn't work with most betas though, so make sure youre running a stable release.

I dont know exactly what that error means, if you cant get it to work i can only recommend you try with a 6.10 live-cd or if youve screwed up the drivers reinstall it....

---

