---
title: "Asus A53U maximum CPU too slow"
date: 2012-09-09
forum: Asus Ubuntu Support (CLOSED)
---

### Post by korgoth28 on 2012-09-09
Howdy, I bought this laptop:
[http://www.amazon.com/gp/product/B005UUSHH8/ref=oh_details_o02_s00_i00](http://www.amazon.com/gp/product/B005UUSHH8/ref=oh_details_o02_s00_i00)
(it was on sale at the time)

which advertises a 1.33 ghz AMD brazos dual c60. the lubuntu cpufreq and cpu monitor applets show the maximum option as 1 ghz. I tried cpufreq-set -f 1300000 but the applets still say it's at 1.0.

any ideas? thanks in advance!

---

### Post by TenPlus1 on 2012-09-09
Try updating to a newer kernel for better support of the hardware, it may solve your problem...

[http://www.ubuntugeek.com/how-to-install-linux-kernel-3-5-rc-in-ubuntu-using-ppa.html](http://www.ubuntugeek.com/how-to-install-linux-kernel-3-5-rc-in-ubuntu-using-ppa.html)

---

### Post by 00b00nt00 on 2012-10-02
> **korgoth28 said:**
> Howdy, I bought this laptop:
[http://www.amazon.com/gp/product/B005UUSHH8/ref=oh_details_o02_s00_i00](http://www.amazon.com/gp/product/B005UUSHH8/ref=oh_details_o02_s00_i00)
(it was on sale at the time)

which advertises a 1.33 ghz AMD brazos dual c60. the lubuntu cpufreq and cpu monitor applets show the maximum option as 1 ghz. I tried cpufreq-set -f 1300000 but the applets still say it's at 1.0.

any ideas? thanks in advance!


I have the same processor. It's actually rated at 1 GHz with a turbo of up to 1.33 GHz. cpufreq is correct.

---

### Post by Baltazar Blake on 2012-10-07
> **korgoth28 said:**
> Howdy, I bought this laptop:
[http://www.amazon.com/gp/product/B005UUSHH8/ref=oh_details_o02_s00_i00](http://www.amazon.com/gp/product/B005UUSHH8/ref=oh_details_o02_s00_i00)
(it was on sale at the time)

which advertises a 1.33 ghz AMD brazos dual c60. the lubuntu cpufreq and cpu monitor applets show the maximum option as 1 ghz. I tried cpufreq-set -f 1300000 but the applets still say it's at 1.0.

any ideas? thanks in advance!
 
Try to change the settings in bios from smart mode to ashe mode because in ashe mode it runs over clock  and it might give u  what u need .Off course will not give u a lot more frequency but at my pc from 1.3 Mhz i took it to 1.5 and i have an asus k50c ,ye is not much but is something .

---

### Post by korgoth28 on 2012-10-12
Thanks for all the suggestions.

How do I enable ASHE? I installed jupiter and the applet shows up, but I don't see any options to enable it. cpufreq still shows 1 ghz in performance mode. 

I also couldn't find any settings in the setup menu that comes up during boot.

---

