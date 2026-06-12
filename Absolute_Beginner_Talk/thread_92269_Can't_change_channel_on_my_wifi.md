---
title: "Can't change channel on my wifi"
date: 2005-11-19
forum: Absolute Beginner Talk
---

### Post by fhqwhgad on 2005-11-19
Hi.
I'm having this problem with my wifi card in my laptop.
Ubuntu detects the card fine but it keeps running it on channel:0.
I've tried doing a 'iwconfig eth0 channel 11' to change it to run on 11 but it remains on 0.

It calls the card eth0 but it does register it as a wifi card.

The card i'm using is a 3com officeconnect Wireless 11g (3RCWE154G72) and it uses the prism GT chipset.

Would be nice to actually be able to get it online so i hope someone here can help me out.

---

### Post by fhqwhgad on 2005-11-19
bump.

Furthermore when i do a iwconfig to list the device it says "NOT READY!" on the field right before the essid.

Really noone who has any idea what's wrong or how i can fix it?

I was wondering if maybe i should download some new drivers or firmware but prism54.org doesn't seem like much help at the moment and i'm pretty sure i read somewhere that ubuntu already had prism gt support.

---

### Post by Lambert on 2005-11-19
Go to terminal and type

sudo lshw -businfo

Find your device, notice what class it is then

sudo lshw -C <class>

Post out put here.

Include out put of 

lspci

If it's v2 notice the prism 54 driver doesn't work for the card.
[http://linux-wless.passys.nl/query_part.php?brandname=3Com&zoek=brandname](http://linux-wless.passys.nl/query_part.php?brandname=3Com&zoek=brandname)

---

### Post by fhqwhgad on 2005-11-19
[QUOTE=Lambert]Go to terminal and type

sudo lshw -businfo

Find your device, notice what class it is then

sudo lshw -C <class>

Post out put here.

Include out put of 

lspci

If it's v2 notice the prism 54 driver doesn't work for the card.
[http://linux-wless.passys.nl/query_part.php?brandname=3Com&zoek=brandname](http://linux-wless.passys.nl/query_part.php?brandname=3Com&zoek=brandname)[/QUOTE]

Oh rotten luck. I know it says Version 2 on the card.
What do i do then?

---

### Post by Lambert on 2005-11-19
this shows ndiswrapper supporting this card

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#0-9](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#0-9)

You can search the forums as there are many posts how to use this.

You'll have to install ndiswrapper first which it's on the install cd. 

If you have somekind of internet access while logged into ubuntu you can install ndisgtk which is a graphical front end for ndiswrapper.

Maybe limit your search in the tips and tricks section or networking section 

Here's a link also.

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Ubuntu](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Ubuntu)

---

### Post by fhqwhgad on 2005-11-19
[QUOTE=Lambert]this shows ndiswrapper supporting this card

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#0-9](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#0-9)

You can search the forums as there are many posts how to use this.

You'll have to install ndiswrapper first which it's on the install cd. 

If you have somekind of internet access while logged into ubuntu you can install ndisgtk which is a graphical front end for ndiswrapper.

Maybe limit your search in the tips and tricks section or networking section 

Here's a link also.

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Ubuntu](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Ubuntu)[/QUOTE]

Yea i do have a wired ethernet card i can plug in while i get this setup.
Thank you very much for your help. Hopefully this will work.

---

