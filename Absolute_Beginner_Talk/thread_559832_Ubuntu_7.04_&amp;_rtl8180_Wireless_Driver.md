---
title: "Ubuntu 7.04 &amp; rtl8180 Wireless Driver"
date: 2007-09-25
forum: Absolute Beginner Talk
---

### Post by Fraterdqni on 2007-09-25
Hi all,

New here to the boards and the Ubuntu System. Previously i was using Kanotix Linux which is in the process of moving over to Ubuntu from the way it looks.

Have been wanting to get a head start using Ubuntu and from what i have seen so far i have to say I Love It! :KS

Love the look, layout and feel but the only problem i am having is that i can not get my wireless card to work correctly. I have tried using the same wireless drivers that cam with my card and ndiswrapper as i did with the previous Kanotix version i was using. They worked perfectly with Kanotix but in Ubuntu it will work for approx 5 minutes and then freeze up my whole system.

I even tried removing the driver and using a different one. Same thing happens, after about 5 minutes on the internet, system freezes. :confused:

When i perform ndiswrapper -l it list that the driver is installed and hardware detected and then it will also show...

(alternate: r818x) Have no idea what this is. :confused:

I don't have net access in linux at this time so i have to use Windows to access net and post here. I have downloaded the deb files for the update ndiswrapper version from the site here and going to see if that works. 

Can anyone shed so light on this or give some advise? I am deserate to g:confused: :confused:rid of Windows once and for all and i got to have Ubuntu. Best onei have see in a long while.

Thanks for your assistance in advance :)

---

### Post by mr_boo1711 on 2007-09-25
Hey Fraterdqni,

I had the same sort of problems with the RTL8187 onboard wireless on my MB.  It was widely known problem at the time, and even NDISwrapper never really worked.  In the end I ran a pretty long Cat5e LAN cable to my router and had to use that.  Then one day after it had done some updates for Ubuntu (and I hadn't reconnected the cable by mistake), I noticed that my wifi was working fine!

Suppose that doesnt really help you much though - what I would say is make sure ubuntu is upto date and dont get frustrated - there will be a fix I promise!  I may not be the one to give you it, but I got great help from a lot of people on this site.

Once you get it working, you'll never look back - I promise :)

---

### Post by mr_boo1711 on 2007-09-25
Sorry - I forgot to ask - The wifi adaptor is scanning ok and connecting?  Is it just the fact it crashes after 5mins that's causing the problems? :confused:

---

### Post by Fraterdqni on 2007-09-25
Seems to be scanning fine. When it connects it runs great but only runs for about 5 minutes and then whole system hangs. :confused:

:confused::confused::confused:

---

### Post by mr_boo1711 on 2007-09-25
I might not be related to the wifi adaptor - hmm, are you doing something particular with your internet access?  A certain application or maybe a particular webpage even?

---

### Post by Fraterdqni on 2007-09-26
Got it figured out! Since Feisty has the rtl8180 built in to the kernel i went and removed the driver from the blacklist, then rebooted by system. Went into the network manager and where i place the SSID i added one extra letter to it and then rebooted one more time. Results....

I am posting this from **Ubuntu!!!!!!!** :guitar:

Wooooo Hoooooo!!!!! I am Windows Free!!!!! :lolflag:

Thanks to all!!!!!

---

### Post by marsmissionaries on 2007-09-26
> **Fraterdqni said:**
> Got it figured out! Since Feisty has the rtl8180 built in to the kernel i went and removed the driver from the blacklist, then rebooted by system. Went into the network manager and where i place the SSID i added one extra letter to it and then rebooted one more time. Results....

I am posting this from **Ubuntu!!!!!!!** :guitar:

Wooooo Hoooooo!!!!! I am Windows Free!!!!! :lolflag:

Thanks to all!!!!!
Don't give up on ndiswrapper.

Ndiswrapper works much better than the r818x module.

---

### Post by Fraterdqni on 2007-09-26
> **marsmissionaries said:**
> Don't give up on ndiswrapper.

Ndiswrapper works much better than the r818x module.

Ohh i won't. Things are going great so far so once i get my feet wet a little more with Ubuntu i will work on the ndiswrapper again.

Thanks again to all! :guitar:

---

### Post by mr_boo1711 on 2007-09-26
> **Fraterdqni said:**
> Got it figured out! Since Feisty has the rtl8180 built in to the kernel i went and removed the driver from the blacklist, then rebooted by system. Went into the network manager and where i place the SSID i added one extra letter to it and then rebooted one more time. Results....

I am posting this from **Ubuntu!!!!!!!** :guitar:

Wooooo Hoooooo!!!!! I am Windows Free!!!!! :lolflag:

Thanks to all!!!!!

Good Job!

Sometimes solutions just appear when you're at you're lowest ebb... :)

Windows free - it's the future that is......! ;)

---

### Post by punong_bisyonaryo on 2007-10-02
> **Fraterdqni said:**
> Got it figured out! Since Feisty has the rtl8180 built in to the kernel i went and removed the driver from the blacklist, then rebooted by system. Went into the network manager and where i place the SSID i added one extra letter to it and then rebooted one more time. Results....

I am posting this from **Ubuntu!!!!!!!** :guitar:

Wooooo Hoooooo!!!!! I am Windows Free!!!!! :lolflag:

Thanks to all!!!!!

Can you teach me how to do this exactly? I have a really old [post]("http://ubuntuforums.org/showthread.php?t=449246") here about the rtl8180 here as well but it never got answered.

Thanks in advance!

---

