---
title: "wireless notebook cards"
date: 2007-03-22
forum: Absolute Beginner Talk
---

### Post by imacbo on 2007-03-22
Ok I give up on trying to get my built-in broadcom card to work with Unbuntu. So does any one know which is the best wireless notebook cards for 6.10 Unbuntu. One that comes with the drivers for Unbuntu.

---

### Post by HereInOz on 2007-03-22
Have you checked this out?

[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBroadcom](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBroadcom)

Or for a full list:

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

It could help you on your quest.

---

### Post by HereInOz on 2007-03-22
Also this may be of use to you.

[https://help.ubuntu.com/community/WifiDocs](https://help.ubuntu.com/community/WifiDocs)

Although you have possibly been there already.

---

### Post by imacbo on 2007-03-22
i saw  few on the list that i can buy where I am. Is there any wireless card that come with the driver on the disk or do i have to download it from somewhere. now remember that the wireless is the only way i have to get online and i have to get online with windows. so if there ris a card out there that comes with thelinux driver on the disk would be the best way for me to go. thanks

---

### Post by aeiah on 2007-03-22
get a card that already has the driver on ubuntu. i believe atheros cards work out of the box but their may be anomalies. search around for wireless cards that work out of the box rather than ones that have drivers available. it is possible to install wifi drivers without an internet connection but it can be a pain in the *** because of dependency problems and take quite a while

---

### Post by imacbo on 2007-03-22
i would really like to find an out of the box answer. the pain i have went through so far sucks. So someone plese what is the best out of the box wireless?????

---

### Post by them4504 on 2007-03-22
Before you give up on your wireless card. Go to [https://help.ubuntu.com](https://help.ubuntu.com) and download Ubuntu Desktop Guide.  before you start the proceedure for wireless connecting go to networking  make sure that eth? is set to the one for wireless, usually eth1 or eth2. Then right click on the screen symbol on the right and do the same thing.  It will say disconected when set right. Now go to Desktop and follow the procedure which includes Sudo pppeoconfig.  Put in sign on name, password, and select the positive answer for all the questions. To select you have to sort of wipe them and then hit enter.  After that turn your computer off and then back on.  If it does not work with those ethn's try a new set. Good luck.

---

### Post by Falados on 2007-03-22
Use ndiswrapper and your bcmXXX.ini / .sys file. If you can't get native support, ndiswrapper is your next best option.

---

### Post by gameman12 on 2007-03-22
DO NOT GET A CARD WITH A BROADCOM CHIPSET!!!

i have one on this laptop and it was a pain in the freakin' ***. do not bother with one, they're not even remotely worth it.

---

