---
title: "Ignore update notification per application"
date: 2006-09-22
forum: Absolute Beginner Talk
---

### Post by Seine on 2006-09-22
G'day 

Does anyone know how I can stop Synaptic advising me that system components need updating when I've decided to leave the component at its old version?

Specifically, I have an older version of wine in which WoW works. If I upgrade wine WoW stops working. As a consequence synaptic keeps trying to tell me that it needs updating and because I ignore it, I won't necessary know when there's important updates (security fixes for example) without explicitly looking. :-({|= 

Any advice?

Thanks
Jem

---

### Post by Qrk on 2006-09-22
Use Package->Force Version

when you have wine highlighted

---

### Post by Seine on 2006-09-22
Thank you! :KS

---

### Post by malco2001 on 2007-04-30
i actually had to use lock version under synaptic

---

### Post by RanulfWolfSage on 2007-06-28
I've forced the version on Wine, as well as locked it under Synaptic, and it's STILL popping up the message wanting me to upgrade it. The funny thing is, it's the same version that it wants to upgrade to. I'm assuming this is because I built Wine from source for my install, and didn't use the included package. My only question is now how do I get it to stop pestering me about upgrading it. As I stated before, it's Forced and Locked in Synaptic. Please advise!

---

### Post by Seisen on 2007-06-28
Its because you compiled Wine instead of installling in through synaptic. When you compiled Wine did you make it into a .deb file to install it?

---

### Post by RanulfWolfSage on 2007-06-28
No, I was following a tutorial on compiling wine for WoW, and it had me install it using 'make install.' How would one create a .deb file? And is there any way other than re-installing Wine to shut off the notification? By the way, thanks for the very quick reply!

---

### Post by Seisen on 2007-06-28
By using checkinstall when you compile the program. The link will explain it better than I can.

[https://help.ubuntu.com/community/CheckInstall]("https://help.ubuntu.com/community/CheckInstall")

---

### Post by RanulfWolfSage on 2007-06-28
Thanks, I really appreciate it! So since I never really modified the install of wine, other than using the winecfg command, can I theoretically use the checkinstall in the installation folder and re-install over top of the current install, without causing issues?

---

### Post by RanulfWolfSage on 2007-06-28
Ok, I need to correct myself here. I was messing with compiling a package yesterday for something else on my  desktop PC at work that I setup with Ubuntu and confused the two. I actually used the following tutorial to install wine, meaning I did install if via a .deb file. So why does it then keep prompting me to update wine? It's as I said before, locked and forced version.

Here's the tutorial I followed:
[https://help.ubuntu.com/community/BuildingWineFromSource]("https://help.ubuntu.com/community/BuildingWineFromSource")

Any tips would be appreciated, thanks! FWIW, the compiled Wine is preforming MUCH better than the deb package that was available in Ubuntu, which is why I kind of want to keep it the way it is.

---

### Post by bodhi.zazen on 2007-06-28
I do not know if it will help, but this is how I put wine on hold :

[http://doc.gwos.org/index.php/HowToWine#How_to_put_wine_on_hold](http://doc.gwos.org/index.php/HowToWine#How_to_put_wine_on_hold)

---

### Post by RanulfWolfSage on 2007-06-28
Thank you, thank you, THANK YOU! I am so relieved to be rid of the update notification! Bookmarked the page for future upgrades. Obviously worked like a charm! :D

---

