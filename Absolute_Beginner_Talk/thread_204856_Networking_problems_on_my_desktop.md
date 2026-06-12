---
title: "Networking problems on my desktop"
date: 2006-06-27
forum: Absolute Beginner Talk
---

### Post by WADemosthenes on 2006-06-27
I'm trying to configure my wireless card in my desktop.  The computer reconizes it, so I configured it to "automatic" and dhcp, then apply.  Then I try to enable it, it enables for a second, but then goes back to "deactivated."  How can I activate it?  Could this mean that kubuntu doesn't have the right drivers?

---

### Post by stevanbt on 2006-06-27
What's the make and model of you wireless card?

[SIZE="1"]Is something Doing Your Head In? ](*,)  [http://blog.doingmyheadin.com](http://blog.doingmyheadin.com)[/SIZE]

---

### Post by WADemosthenes on 2006-06-27
It's not on the ndiswrapper list, proabably because it's a desktop wireless card, the most common are laptop cards.  It's a Lynksys "Wireless-G PCI Adapter" Model No.:WMP54G.

---

### Post by Apple 101 on 2006-06-27
It doesn't need to be on the list.  My card isn't and it works perfectly with ndiswrapper.

---

### Post by WADemosthenes on 2006-06-27
[QUOTE=Apple 101]It doesn't need to be on the list.  My card isn't and it works perfectly with ndiswrapper.[/QUOTE]

Using the drivers on the cd, of course.  That worked, as you suggested ("driver installed, hardware present"), but before that my computer already reconized a card, and when I used "iwconfig" it said the same thing, and when I tried to connect it did the same thing.  I'm going to put on xubuntu, I know how to deal with it better, it's what I've been using on my laptop.  I'll get back to you with those results tomorrow.  Thanks for the help.

---

### Post by WADemosthenes on 2006-06-28
Okay, I installed xubuntu.  I am much releived to be back in Xfce.  But when I went to configure the card (system > networking > properties) it didn't detect my network, but activated.  Now I know my network is running, because my xubuntu laptop's card see's it (and the one next door :P), so I know there's a problem.  I'm not sure what to do, I would install it with ndiswrapper, but I don't know how that would work.  Would I have to uninstall it before I install the drivers using ndiswrapper?  If I didn't would it show up an a different card, write over the other, or just not work?  Could there be some hardware problem, would my situation point to an antena problem or something like that?  Thanks.

---

### Post by WADemosthenes on 2006-06-28
Tried ndiswrapper, didn't work.  I'm going to try to re-install xubuntu without the card in so it doesn't get installed, maybe ndiswrapper will work that way.  I haven't had much direction for a while, so I'm just trying stuff :P

---

### Post by Apple 101 on 2006-06-29
Install *ndisgtk* (package in Universe) and find your wireless card's .INF and .SYS files.  It will configure ndiswrapper for you, as long as ndiswrapper is installed.

---

### Post by WADemosthenes on 2006-06-29
[QUOTE=Apple 101]Install *ndisgtk* (package in Universe) and find your wireless card's .INF and .SYS files.  It will configure ndiswrapper for you, as long as ndiswrapper is installed.[/QUOTE]

I've used ndiswrapper before, I'm know what to do.  I didn't have the .sys file in there, that was the first problem, and the card was already detected.  Both can be fixed with the re-install of xubuntu.  I'll try later today after class, and I'll report back how it worked out.  Thanks.

---

