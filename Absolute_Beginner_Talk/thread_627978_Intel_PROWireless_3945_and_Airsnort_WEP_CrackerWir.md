---
title: "Intel PRO/Wireless 3945 and Airsnort WEP Cracker/Wireless Sniffer"
date: 2007-11-30
forum: Absolute Beginner Talk
---

### Post by blurryone on 2007-11-30
Hi All,

I have the above mentioned wireless card, just wondering if anybody has had any luck on getting it going with Airsnort i tried on vista also but the latest version of the vista driver for this hardware does not support promiscuous mode so i couldn't use it, i was hoping that now i have moved to ubuntu the card may work...

I am using restricted driver Intel(R) PRO/Wireless 3945 Network Connection driver for Linux

I can get Airsnort running but when i try to start a capture nothing comes up. Have had a look around and i couldn't find any threads on this so here it is!

Does anybody have this going? what version of drivers are you using? am i even using the software correctly?
:confused::confused:

Cheers
Blurry

---

### Post by barney385 on 2007-11-30
Are you sure the airsnort developers weren't busted?

:guitar:

---

### Post by blurryone on 2007-11-30
i have absolutely no idea....

where i live there aren't to many laws on these sorts of things so i should be fairly safe..

---

### Post by barney385 on 2007-11-30
It's only good for 802.11b I think. 

Hmmm...seems there should be better. I checked their website and it doesn't appear to have been updated since 2005?

Maybe I missed something...

:popcorn:

---

### Post by blurryone on 2007-11-30
i have absolutely no idea mate - pretty interesting i thought the project was an ongoing one... i guess we will soon find out.. is there anything out there that you know of that would be a recent app of the same sort?

---

### Post by bobyy on 2007-11-30
Hy
I belive you must check if your card supports the "monitor mode "
i tell you that because i work with Kismet (and in this case when sniiffig kismet put the card in monitor mode) you check the config file? ..maybee it is wrong what i tell you , but check the manual for Airsnort.
Another great tool is Wireshark.and it is in repo.

---

### Post by barney385 on 2007-11-30
Here are a few to check out that are much more complete:

[http://sectools.org/wireless.html](http://sectools.org/wireless.html)

[http://packages.debian.org/airsnort](http://packages.debian.org/airsnort)

Here's a good forum for good info:

[http://www.netstumbler.org/](http://www.netstumbler.org/)

Good Luck Mate!! Hope you find something that will work for you.:)

---

### Post by barney385 on 2007-11-30
> **bobyy said:**
> Hy
I belive you must check if your card supports the "monitor mode "
i tell you that because i work with Kismet (and in this case when sniiffig kismet put the card in monitor mode) you check the config file? ..maybee it is wrong what i tell you , but check the manual for Airsnort.
Another great tool is Wireshark.and it is in repo.


Isn't Kismet 802.11b only?

---

### Post by blurryone on 2007-11-30
Cheers barny will investigate the links you've provided

I assume when you are asking if something is 802.11b you mean that it is outdated because routers use 802.11g? i dont really know much about wireless standards.

bobyy

i already have and use wireshark.. i was looking for a Wi-Fi capturer/monitor... 

Promiscuous mode and monitor mode are same-same i said i was pretty sure my card did not support it and so was asking if somebody has it working in that mode with a different set of drivers or such that i had potentially not tried.

Thanks for the reply :) greatly appreciated though - Wireshark is very awesome.

---

