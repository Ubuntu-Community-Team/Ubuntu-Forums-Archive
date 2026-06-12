---
title: "Just want to replace eth1 with wlan0. Please help!"
date: 2006-04-21
forum: Absolute Beginner Talk
---

### Post by TrojanSkin on 2006-04-21
Just need, in simple terms, how to get rid of my wireless usb connection eth1. It was named wlan0 and worked fine. Now for some reason it's called eth1 and I can't do a damn thing with it! Don't want to reinstall AGAIN!!! Help! Thanks.

---

### Post by gardara on 2006-04-21
When I had a mini-pci card in my laptop the wireless connection got named eth1, but now with a pcmica card the wireless connection is called wlan0

---

### Post by TrojanSkin on 2006-04-21
I've just reinstalled, used ndiswrapper and all's well. For now!. Now to sort my laptop problems! Just boots into boot screen again!](*,)

---

### Post by dave9191 on 2006-04-21
If you open the file /etc/iftab in a text editor as root, change the eth1 lable to wlan0 lable and see if that works :)

--
Dave

---

### Post by TrojanSkin on 2006-04-21
Thanks. I'm doing my laptop too, and I'm quite likely to need it again!

---

### Post by macdo on 2006-04-21
As for the boot screen problem, try alt+F8 - it works for me, but I have no idea why it isn't just going there automatically....

I'm going to try to install from scratch, to see if that doesn't help. I'll keep you informed!

---

### Post by Papa-san on 2006-04-21
I had a tough go with this. I ended up going into network manager, and clicking on eth1  and deactivating it.Then into the properties menu for it. There is a checkbox for  'enable this connection' I unchecked it. clicked OK. then checked at the bottom to see if wlan0 was set to default. OK, then logged off, but checked 'save these settings' before clicking to reboot. 

(All of my stuff is written 'tongue in cheek' I prolly have the actual names wrong, but look for the similar items...)

---

### Post by TrojanSkin on 2006-04-23
Thanks, but no luck. I've gone back to Breezy and everything's fine. My laptop no longer has xp. Yay!

---

