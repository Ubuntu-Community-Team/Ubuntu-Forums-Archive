---
title: "Wireless Internet Help"
date: 2006-10-07
forum: Absolute Beginner Talk
---

### Post by Borlz89 on 2006-10-07
Hi everyone,am Borlz89, Hopefully this is the right place to post this question if not can the Mods move this to the right place please, anyway am new  to this Forums and New to Linux. I'm planing to install Linux on my laptop which is 4 years old and only use for me was internet and school work. Right now am testing Linux using the Ubuntu Live  and I been liking it so far. But so far am having trouble getting on the internet using wireless means. I have an Linksys Wireless-G Broadband Router model No. WRT54GS and a U.S. Robotics USB Adapter to connect to wireless internet. When I try to connect to the internet the computer has the Connection Properties menu on but still not connecting to the internet. Is their any way to fix this problem?

---

### Post by motstudios on 2006-10-07
well, like i said in another post, if the wifi card is detected but u cant connect to the net, it may need configuring and activating. if its not showing up, u may first need to look for an open source driver for the cards chipset. if u cant find one, u can use ndiswrapper.

ndiswrapper tutorial: [http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation)

you could find ndiswrapper already made using the search function in synaptic. if you want to compile from source, u will also need to fetch the linux kernel sources and build-essential from synaptic.

id suggest trying to get the ndiswrapper from synaptic if its not already on ubuntu. to see if it is already included, just open a terminal and type ndiswrapper and if it shows some kinda help thing then u will only need to follow the ndiswrapper tutorial and obtain ur wifi windows driver

---

### Post by Peter41az on 2006-10-08
I loaded automatix, and using the windows wireless drivers wizard within, it is as easy as pie. Download the correct windows drivers, click install driver, find the inf, and bam youre there. easier for those not too familiar yet with command line ndiswrapper. Not to mention all the other goodies automatix provides. [www.getautomatix.com](www.getautomatix.com). Automatix was the line that brought me over to linux fully, never to go back to windoze..



> **motstudios said:**
> well, like i said in another post, if the wifi card is detected but u cant connect to the net, it may need configuring and activating. if its not showing up, u may first need to look for an open source driver for the cards chipset. if u cant find one, u can use ndiswrapper.

ndiswrapper tutorial: [http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation)

you could find ndiswrapper already made using the search function in synaptic. if you want to compile from source, u will also need to fetch the linux kernel sources and build-essential from synaptic.

id suggest trying to get the ndiswrapper from synaptic if its not already on ubuntu. to see if it is already included, just open a terminal and type ndiswrapper and if it shows some kinda help thing then u will only need to follow the ndiswrapper tutorial and obtain ur wifi windows driver

---

### Post by motstudios on 2006-10-08
never tried automatix, might give it a spin and see how it is

---

### Post by Borlz89 on 2006-10-08
Thanks guys I'll try automatix and see if it could get me going.

---

