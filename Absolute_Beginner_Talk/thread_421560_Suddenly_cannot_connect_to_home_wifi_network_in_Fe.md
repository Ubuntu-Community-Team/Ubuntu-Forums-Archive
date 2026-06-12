---
title: "Suddenly cannot connect to home wifi network in Feisty"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by PartisanEntity on 2007-04-24
For some reason, today I cannot connect to my home wifi network in Feisty. Right now I am posting from XP from the same machine, so it works in Windows.

My home wifi network is wpa encrypted. And I usually use network manager to connect. It was working yesterday and I did not install or un-install anything, neither did I play with any settings.

I tried restarting the machine a couple times, I also tried restarting the router (as well as checking the settings).

I am not sure how to proceed from  here.

---

### Post by wscheer on 2007-04-25
PartisanEntity,
Do you know what type of wifi card you have in your computer? You might be able to find some more information by searching the forums here for that specific card. More than likely someone else has run into a similar situation.

I have stayed at 6.06 because my broadcom 4306 wasn't working on new versions of ubuntu.

---

### Post by PartisanEntity on 2007-04-25
I have the same card as you and it worked in Dapper, Edgy and now Feisty.

An update to my case:

I have figured out that I can connect, but it takes ages, I must try about 4-5 times in order to get Network Manager to connect. It tries to connect, then gives up and I have to repeat the process.

There definitely seems to be a performance degradation as far as my broadcom wifi card and Feisty are concerned.

---

### Post by wscheer on 2007-04-26
Hmmm...
I have "/" installed on its own partition. I might make the leap to Fiesty. If it does not work, I'll probably just go back to 6.06

When I originally upgraded to 6.10, my machine would hang as it was loading gnome. I would get a blank white box in the upper left hand corner which would eventually give me some gnome error about loading daemons. After about a 4-5 min. hang, it would operate just fine with the wireless working as well.

I'll probably do the upgrade this weekend and i'll post an update here to let you know how it goes.
Sometimes my ubuntu addiction gets in the way of my halo 2 addiction and visa versa. :razz:

---

### Post by wscheer on 2007-04-28
PartisanEntity,
Made the jump to 7.04 and got the wireless working.
I followed this guide for Broadcom 4306 ndiswrapper [http://ubuntuforums.org/showthread.php?t=201902](http://ubuntuforums.org/showthread.php?t=201902).

make sure you comment out all the wireless settings in 
```
sudo gedit /etc/network/interfaces
```

Its listed as the first problem at the bottom of that guide.

Let me know how it goes.

---

### Post by PartisanEntity on 2007-04-28
Thanks for the info, but I replaced the broadcom card with an intel wireless card and don't have to fiddle around anymore. Out of the box support and no more issues :)

---

