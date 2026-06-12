---
title: "How can I get my wireless card to work"
date: 2008-01-01
forum: Absolute Beginner Talk
---

### Post by winterfire on 2008-01-01
Happy New Year everyone. 
          Ok, here we go, I bought  a wireless usb adaptor an Airlink AWLL3026 becouse I read that it works right of the box. When I hooked it up to my Dell laptop (Ubuntu 7.10Gutsy), It reconises the card, I see my network (Actiontec), and a signal strength of 89% or better. According to the information I,m seeing, I should be posting this on my laptop.( well, not this post, but another question thats been answered a thousand times.) Anyway, I want it to connect to any available network. What am I missing on this.
                                                                           Thanks for the help

---

### Post by kestrel1 on 2008-01-01
You should only need to select your network, enter the encryption key (if any) & away you go.

---

### Post by CJ56 on 2008-01-01
Have you tried installing wi-fi radar? It's in the repositories. Once installed, it comes up in the Applications menu under Internet - shows you all the available networks. Pick the one you want then Edit (I think) & get a list of drop-down menus. Pick Auto for everything you can & it should think for a bit then start working...

Hope this helps.... ;)

---

### Post by winterfire on 2008-01-03
Ok, I solved my problem and it had nothing to do with the wireless card. After searching all of the obvous solutions, I tested against a known good. The coffee shop down the street has internet access, so i went down, had a vanilla chi latte and tried to log on. sure enough i connected on the first try. I then recalled that my last linux install had problems connecting to the web at home becouse my router and modem has a problem with firefox when it has a stock configeration.So,I went to [http://www.howto.helpero.com/howto/Speed-Up-Firefox_31.html](http://www.howto.helpero.com/howto/Speed-Up-Firefox_31.html) ,
followed the instructions and now I can log-on anywhere.
   Thankyou for all the help you all have given me. This is a great forum!

---

### Post by hyper_ch on 2008-01-03
so that usb adaptor works right out of the box?

---

### Post by winterfire on 2008-01-03
Oh,yes. It was listed on another forum. It also mentions that the next model up (AWLL3028)  had a few problems, so I got the AWLL3026. For a $25.00 U.S., it works better than I thought.

---

### Post by hyper_ch on 2008-01-03
well, good to know... I just noticed tons and tons of wifi-usb adapters which provded tons and tons or problems ;)

---

### Post by winterfire on 2008-01-03
Yeah I know what you mean. I've got a bunch of old laptops I want to fix up and sell, but finding wireless pc and usb cards that will work without a song and dance with Linux is a pain.

---

### Post by adam.skinner on 2008-01-03
fwiw, I'm using a zd1211rw based USB 802.11g adapter, and it worked out of the box with 7.10.  The stupid Edimax rt61 would consistently kill (to the point of needing to reboot the computer) the network connection.  This comes, I gather, from an old driver version incompatible with the present kernel 7.10 uses.  I happened to have this extra USB, so I was good to go once I finally resigned myself to defeat (it took a while, let me tell you!)

---

