---
title: "Unhappy  dlink DWL-G510 wireless network help ubuntu"
date: 2007-10-26
forum: Absolute Beginner Talk
---

### Post by jsmit487 on 2007-10-26
hey guys

im a newbe to linux and ubuntu and iv got a dlink DWL-G510 wireless network card and i dont now how to get it working on ubuntu plz help

---

### Post by kheaver on 2007-10-26
> **jsmit487 said:**
> hey guys

im a newbe to linux and ubuntu and iv got a dlink DWL-G510 wireless network card and i dont now how to get it working on ubuntu plz help

I've got the same question, my mates got one of these, I'm a newbie and he's computer illiterate.

I feel like tweedle dee and tweedle dum.

Kim

---

### Post by Chuckels550 on 2007-10-26
Check this sticky:

[http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539)

---

### Post by psycosmyth on 2007-10-26
check your restricted driver manager under "system". Your card should use the Atheros driver for HAL. Gutsy is the first version that I had to manually set this for. Previously it just worked.

---

### Post by mdpalow on 2007-10-26
Hi All,

I'm a newb as well, but I'd like to reply with some POSSIBLE help.

Assuming you installed Ubuntu 7.10 with your CAT5 cable plugged into the back of your computer - your computer would be defaulted to using the ethernet cable. Just making sure, BUT did you click on the "Wired Network Connection" icon in the panel (picture of two monitors) and switch it from WIRED to WIRELESS? I know it's pretty simplistic, but I don't know your skill level and perhaps you've just overlooked the simple step.

When you click on the icon, you can select the network that is found (assuming it's yours) and then just enter the 64/128 hex password to the network. I had a 128bit WEP key I created, so that's what I used to connect.

If the network you see is not yours, you have TO CONNECT TO OTHER WIRELESS NETWORK and then select yours.

Sorry if this was obvious to you and you already did it. I only replied with this because my DWL wireless card worked immediately after install, but I had to switch to it from the panel to use it.

BTW - I have a DWL-G520.

---

### Post by duggo03 on 2007-10-31
Hi,

I am also a newb, so be gentle. 

I had the same problem on Ubuntu 7.04. I found that Ubuntu found the network card straight off but I could not get access to the network even when I made sure the wireless card was selected. 

However, after some tweeking, I found that the wireless network properties needs a network password. I do not have a password on my network but do have a password I use to configure my wireless router. I put that password in the properties field for the Dlink DWL 510 and now my network card works fine.

Hope this helps.

---

