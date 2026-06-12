---
title: "Installing ADSL modem -- PPoE?"
date: 2006-03-21
forum: Absolute Beginner Talk
---

### Post by SteveHoffmanUK on 2006-03-21
I have been trying to install the eciadsl modem driver for the BT Voyager105 modem. I got this far and then got these messages:

> dpkg: dependency problems prevent configuration of eciadsl-usermode:
eciadsl-usermode depends on pppoe; however: Package ppoe is not installed.
dpkg: error processing eciadsl-usermode (--install): dependency problems - leaving unconfigured
Errors were encountered while processing: eciadsl-usermode

This is my first try at installing anything, and I'm not sure what to do.
I went to Synaptic Package Manager, and it shows that pppoeconf (Version 1.8ubuntu2) is installed. I guess there is a difference between ppoe and ppoeconf? How do I get ppoe and instal it?

---

### Post by Shampyon on 2006-03-21
Sorry, I have no answers, only commiserations.

I had this problem when I first started trying out Xandros a coupld of years back. Tried for ages with my D-Link USB modem, couldn't get it to work. Eventually I upgraded my DSL account, and decided to get an ethernet router with it so I could share the connection with my housemates. Every flavour of linux I've tried istantly recognized the connection, no configuration necessary.

Ethernet's the easiest way to get your DSL running through Linux.

Still, that's no help to you right now, is it? i hope someone's able to get you up and running. Good luck :KS

---

### Post by Online Gamer on 2006-03-21
Hey Steve,
I'm just a noob myself mate but if you go to synaptic manager and click on search then just type ppoe then search it gives ppoeconf and further up ppoe which is the driver. the conf is installed so just click inside the box before ppoe and then it will give you a pop up with mark for installation. Click this and it will mark the ppoe driver. Next on the toolbar is apply then click apply on the pop up. this will then install the ppoe driver.
Hope this helps you mate
Online Gamer

---

### Post by SteveHoffmanUK on 2006-03-21
Online Gamer

Thanks for the suggestion. Unfortunately, when I do a search of the Synaptic Manager on "ppoe", the only package I find is ppoeconf, which is already installed. Just plain ol' ppoe isn't there above it in the search results.

Shampyon

I know that the Voyager is a bit of a beast to try to install, and it might be easier to ditch it and try an ethernet router. The idea of a piece of equipment that Linux instantly recognises has much appeal. What kind did you get?

---

### Post by Online Gamer on 2006-03-22
Steve
It may be just that you havent enabled all the repositories for software package downloads. Please follow this how to guide on the wiki for adding all the extra standard repositories like the universe and multiverse, thats all I use and ppoe appears in my search mate. Try this link

[https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)

just copy and paste it into your browser. It's done using synaptic graphically not the command line interface.

Any more probs let us know.

Good luck

---

### Post by Online Gamer on 2006-03-22
Steve
Also on my travels I found this link to an eci adsl modem setup site forum that deals with linux installs and also has some links and how to threads for ubuntu and the bt voyager 105 modem and also some installs specific for the GS7470 chipset which I believe that modem is.

[http://eciadsl.sourceforge.net/scripts/forum/index.php](http://eciadsl.sourceforge.net/scripts/forum/index.php)

---

### Post by Online Gamer on 2006-03-22
Even better mate Welsh Spud has done a walk through on ubuntu forums for the voyager I managed to pick it up by searching for the chipset id, it's a complete walk through including installing the ppoe package and making it non hotpluggable so it's there on start up with its own drivers not trying to start with usb.

Once again good luck mate
Online gamer

Oh before I forget      here's the link

[http://www.ubuntuforums.org/showthread.php?t=140010&highlight=gs7470](http://www.ubuntuforums.org/showthread.php?t=140010&highlight=gs7470)

---

### Post by SteveHoffmanUK on 2006-03-22
Gamer

Fantastic. Thanks so much for all the leads. 

I will pursue them once I get my laptop sorted out. For various reasons, I did a re-install of Breezy on it and it's hanging during the install. :( Ah, well, all part of the Linux learning curve!

I really appreciate your help -- another demonstration of the value of this forum.\\:D/

---

### Post by Shampyon on 2006-03-29
[QUOTE=SteveHoffmanUK]
I know that the Voyager is a bit of a beast to try to install, and it might be easier to ditch it and try an ethernet router. The idea of a piece of equipment that Linux instantly recognises has much appeal. What kind did you get?[/QUOTE]

Shoot, I haven't been keeping good track of the threads I post in, have I? I've let this one slip by for a whole week! Sorry for being so rude, Steve.

I use a D-Link DSL 504T. 

Oddly enough, while it still works perfectly on Ubuntu, when I tried out Xandros again no network connection was recognised - I put this down to my new motherboard, which seems to be made up entirely of parts no computer hardware salesman has ever heard of. Stupid thing took me a week to track down a tiny adapter cable just so I could hook it up to my ATX power supply.

---

