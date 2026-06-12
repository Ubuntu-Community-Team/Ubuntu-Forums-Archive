---
title: "Lost My Network Adapter !"
date: 2006-08-02
forum: Absolute Beginner Talk
---

### Post by menawollas on 2006-08-02
Hi

I have a wireless network. It works fine amd has done for years. My main PC multiboots Ubuntu/Kubuntu/XP/Vists. No problems.

Last night I set up my wifes PC to mutiboot XP/Kubuntu. Again, no problems, two network adaptors found ath0/eth0. I configure ath0 and download all the updates for Kubuntu.

HOWEVER, this morning, no internet connection? I check in the network settings, and its only showing eth0, ath0 has gone! I reboor to XP, and can connect to the internet, so its not the card.

So,

1. How do I force a redetection of network cards, or add it manually?

2. Any ideas what happened? all i did on starting Kubuntu was reset the screen resolution?

Thanks

---

### Post by ViaD on 2006-08-07
This happend to me too. ](*,) 

It might be related to a kernel upgrade. I rebooted and chose an older kernel from the grub menu, and wipiyayho, it worked again! I allso changed the /boot/grub/menu.lst to boot the wlan-working kernel as default. 

Hope it will work for you too!

Cheers :)

---

