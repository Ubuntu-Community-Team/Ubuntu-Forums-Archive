---
title: "Choosing which Ubuntu version for trouble free wireless connection"
date: 2007-06-25
forum: Absolute Beginner Talk
---

### Post by a.v.l on 2007-06-25
Which version of Ubuntu is most likely to get my wireless laptop card to work. 

I need to re-install Ubuntu again and would like to choose a version which will give me the best chance of getting my Belkin wireless card to communicate with my Belkin ADSL modem with wireless G router ..... model no. F5D7632-4.

My modem router is set with WPS-PSK security and connected to my desktop machine via an ethernet cable. I have also been able to get the lasptop card to communicate with the modem/router when using XP but not with 6.06 Ubuntu.

If I go to System>administratin>networking I can see the wireless card which tells me it is configured, but try as much as I can it will not work. Now I have to reinstall Ubuntu for other reasons and thought I would take this opportunity of asking my best option regarding version to install.

---

### Post by Golyadkin on 2007-06-25
For hardware support there is no difference between the different Ubuntu distributions. The difference is in the windowmanager used.

---

### Post by Seisen on 2007-06-25
What model is your wireless card?

---

### Post by lazyart on 2007-06-25
You might want to try a Feisty LiveCD and see if you have more success.

---

### Post by ts51 on 2007-06-25
You'll need to get the correct drivers/firmware for your card. For a trouble free wireless install, you'll need to buy a fully supported card that "just works".

---

### Post by kevdog on 2007-06-25
There is no such thing as a wireless trouble free installation in any Ubuntu version.  Even in many of the cards that supposedly work -- they dont without a little tweaking.  Setting up ndiswrapper, madwifi, etc. although a little bit of a pain initially, really isnt a big deal.  If you are a beginner I actually find it as a good exercise so that you actually get to learn a little bit about basic command syntax, and how to actually install a program by hand.  This skill will come in handy in the future!:p

---

### Post by a.v.l on 2007-06-25
> **Seisen said:**
> What model is your wireless card?

The wireless card is a Belkin wireless G notebook network card Part number F5D7010

---

### Post by kevdog on 2007-06-25
I saw a lot of listings for that site on the ndiswrapper website.  It really depends on the chipset of the card.  To discover the chipset, post the results of the following:

lspci -n

---

### Post by a.v.l on 2007-06-25
> **kevdog said:**
> I saw a lot of listings for that site on the ndiswrapper website.  It really depends on the chipset of the card.  To discover the chipset, post the results of the following:

lspci -n

This is the results.


0000:00:00.0 0600: 8086:2560 (rev 03)
0000:00:02.0 0300: 8086:2562 (rev 03)
0000:00:1d.0 0c03: 8086:24c2 (rev 02)
0000:00:1d.1 0c03: 8086:24c4 (rev 02)
0000:00:1d.2 0c03: 8086:24c7 (rev 02)
0000:00:1d.7 0c03: 8086:24cd (rev 02)
0000:00:1e.0 0604: 8086:244e (rev 82)
0000:00:1f.0 0601: 8086:24c0 (rev 02)
0000:00:1f.1 0101: 8086:24cb (rev 02)
0000:00:1f.3 0c05: 8086:24c3 (rev 02)
0000:00:1f.5 0401: 8086:24c5 (rev 02)
0000:00:1f.6 0703: 8086:24c6 (rev 02)
0000:02:03.0 0607: 1180:0475 (rev 80)
0000:02:08.0 0200: 8086:1039 (rev 82)
0000:02:0d.0 0c00: 104c:8023
0000:03:00.0 0280: 1814:0201 (rev 01)

---

### Post by xSNTx on 2007-06-25
> **kevdog said:**
> There is no such thing as a wireless trouble free installation in any Ubuntu version.  Even in many of the cards that supposedly work -- they dont without a little tweaking.  Setting up ndiswrapper, madwifi, etc. although a little bit of a pain initially, really isnt a big deal.  If you are a beginner I actually find it as a good exercise so that you actually get to learn a little bit about basic command syntax, and how to actually install a program by hand.  This skill will come in handy in the future!:p

This is not true. I have a Toshiba laptop with an Atheros wireless nic. I installed Fiesty and the nic worked out of the box. I did not have to do anything.

-SNT

---

### Post by mlentink on 2007-06-25
> **xSNTx said:**
> This is not true. I have a Toshiba laptop with an Atheros wireless nic. I installed Fiesty and the nic worked out of the box. I did not have to do anything.

Same for my desktop with a 11$ Sweex (=Atheros) card, and my laptop with a Intel 3945ABG card.
Just worked...

---

### Post by a.v.l on 2007-06-25
Anyway, back to my problem.  In network settings I can see my wireless card marked as "Rao" which is set as "active" now, how do I get the laptop card to communicate with the modem router please.

---

