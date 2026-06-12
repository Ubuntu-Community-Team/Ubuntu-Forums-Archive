---
title: "Nvdia an X relation"
date: 2007-10-06
forum: Absolute Beginner Talk
---

### Post by babacan on 2007-10-06
Hello
How exactly I should install Nvidia close source drivers (aka official ones) so I dont need to reinstall drivers at each kernel update ? I used envy earlier and ended up with x.org error and had to reinsall ubuntu from the begining.

Please explain to me the exactly way by steps instead of saying  "do this" as I am a newbie.

Regards

---

### Post by Pumalite on 2007-10-06
Sorry, but with each kernel upgrade, you have to re-install your drivers

---

### Post by RomeReactor on 2007-10-06
Hi. The easiest way to get the proprietary Nvidia drivers is through the **Restricted Drivers Manager** (System->Administration->Restricted Drivers Manager). Ubuntu will figure out everything for you that way.

Envy is very useful if have a GeForce 8800 that only works correctly with the newest drivers downloaded from Nvidia's website. Otherwise, just use the Restricted Drivers Manager.

---

### Post by mgmiller on 2007-10-06
> Sorry, but with each kernel upgrade, you have to re-install your drivers

No, you don't. 

If, as the OP suggested, he stays with the stock Ubuntu repos for his drivers, kernel upgrades are painless.

I suggest, he runs the restricted drivers manager found in System>Administration>Restricted Drivers Manager.  If he has a card that is supported, it will walk him through everything.

Edit:
You beat me to it.

---

### Post by ZipoTe on 2007-10-06
i always use the latest one, downloaded via official website so, have a try :wink:

---

### Post by Pumalite on 2007-10-06
My mistake. I interpreted this:'close source drivers (aka official ones)'
as proprietary drivers.

---

### Post by babacan on 2007-10-06
Thanks for the answers.


Actually the easy way (Restricted Drivers Manager (System->Administration->Restricted Drivers Manager)  doesnt work for me as I have a 6600 gt and for any accelerated graphic I get weird red dots around the screen (like in beryl 3d desktop effects , dots while watching a movie amd similar) however things were working correctly with auto Envy installation. Assuming (hoping :) ) Envy will work for 7.10 , after kernel update and the usual crush of Ubuntu and sends you to the black screen with black line , what exactly I should be doing to fix it by somehow getting the latest drivers with Envy?

Apart from that , does Envy installs always the latest Nvidia driver ? I am asking this because after dling Envy theres no update for the programs itself to recognize if theres a new version of Nvidia driver or not to download.


Regards

---

### Post by Pumalite on 2007-10-06
I'm with ZipoTe; I like proprietary drivers.

---

