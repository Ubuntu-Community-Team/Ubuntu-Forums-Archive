---
title: "Xubuntu, Powerbook G3 Lombard 333MHz, &amp; a  Belkin 54g Wifi PCMCIA install help please"
date: 2007-10-27
forum: Apple PPC Users
---

### Post by Archaeology_Student on 2007-10-27
Hello,

I have a Powerbook G3 Lombard with the following specs:

[LIST]
[*]G3 333MHz PPC
[*]320MB RAM
[*]10.1 GB hard drive
[*]Belkin 54g PCMCIA (this wifi works in OS X!)
[*]OS: xubuntu 6.10 (freshly installed)
[/LIST]

I have the Powerbook running xubuntu and boy am I ever impressed! Quick to load up, quick to access programs when compared to OS X 10.3.9!

I have a Belkin 54g PCMCIA wifi card (Belkin 802.11g wireless PCMCIA card, model # F5D7010, rev.1315) that has drivers for OS X from Belkin. It worked flawlessly thanks to the the Broadcom chipset for the Mac G3/G4 laptops, and this outperforms the original airport card. 

This is a great upgrade card for the Powerbook G3's and OS X, but no one really knows about this little gem.

I have read [this article on installing the same card in Linux using ndiswrapper]("http://www.gidforums.com/t-4390.html") and the original windows driver from the install CD, but how do I go about using the OS X driver? Do I follow the same steps and then just insert the CD-ROM with the Apple OS X driver, or is ndiswrapper only for windows based drivers?

What options are there for wifi on xubuntu for PPC? Would I have better luck with ubuntu 7.10 because it includes a tonne of software?

Thank you for your time and help :)

---

### Post by Archaeology_Student on 2007-10-28
Downloaded Wicb which really helps! I also downloaded pcmcia-cs which is non-existent in xubuntu, and can cause issues. I have installed the belkin pcmcia card which uses the Broadcom 4306 chipset, and still get nothing... I am starting to get a little frustrated with xubuntu :( 

Again the main reason for switching to xubuntu was speed, and the ability to play videos. Without a Wifi connection that works I am frustrated.

When I put the card into the pcmcia slot the lights do not light up, and it does not appear anywhere in xubuntu. Any ideas? I would really appreciate watered down instructions that are simple enough for us dumb users :)

---

### Post by Archaeology_Student on 2007-10-28
From what I have read ubuntu 7.04 and 7.10 easily work with the card, and xubuntu 6.10 has issues. Should I go for 7.04 for PPC over 6.10? I'd love to get flash working with Gnash and wifi for this up and running, and I am set! Just two simple requirements really, and I will be happy!

---

### Post by Auria on 2007-10-28
> **Archaeology_Student said:**
> From what I have read ubuntu 7.04 and 7.10 easily work with the card, and xubuntu 6.10 has issues. Should I go for 7.04 for PPC over 6.10? I'd love to get flash working with Gnash and wifi for this up and running, and I am set! Just two simple requirements really, and I will be happy!

7.04 is usually recommended over 6.10
don't expect too much out of gnash though, most web sites will not work of have glitches

i can't help about wifi but hopefully someone else will know :)

---

### Post by Archaeology_Student on 2007-10-28
Thank you for the reply.

I read a few posts that had promising results with Gnash 0.8 :)

I really would like to figure out why the card does not appear to be powered when I plug it into the pcmcia slot :(

Maybe the hiccups will dissapear with ubuntu 7.10 over Xubuntu 6.10.

Thank you

---

### Post by Archaeology_Student on 2007-11-12
Using Ubuntu, the wifi worked flawlessly! The system is slowwwwwwww, but the wifi works! What is the primary difference with Xubuntu not seeing the card or powering it on?

Any thoughts or ideas?

Thank you :D

---

### Post by pxwpxw on 2007-11-13
Maybe the card is just showing whether the network is enabled by the network manager.
I have xubuntu and ubuntu, and have had to use different wifi network manager setup, but the  broadcom drivers and firmware are the same I think - using apple airport extreme cards.

---

### Post by Archaeology_Student on 2007-11-13
> **pxwpxw said:**
> Maybe the card is just showing whether the network is enabled by the network manager.
I have xubuntu and ubuntu, and have had to use different wifi network manager setup, but the  broadcom drivers and firmware are the same I think - using apple airport extreme cards.

What did you use to setup the card with Xubuntu? I have seen a few different techniques, and I am curious to know how you got yours working, and also, what version of Xubuntu are you using?

---

### Post by pxwpxw on 2007-11-14
> **Archaeology_Student said:**
> What did you use to setup the card with Xubuntu? I have seen a few different techniques, and I am curious to know how you got yours working, and also, what version of Xubuntu are you using?

I don't have a pcmcia card, I just have the Apple Airport Extreme cards as bought with iBookG4 and PowermacG5, with broadcom bcnm4306 chip and driver module plus bcm43xx firmware. So don't know what the led on the card signifies.

I have xubuntu710, ubuntu710 and previously 704.

I use wireless or wired net connections, just set up using the network-admin application (appications:system:network in xubuntu), and enable or disable the wired or wireless connection from there with a network restart to change over. 

I had to remove the ubuntu710 network-manager-gnome package, didn't work.

---

### Post by Archaeology_Student on 2007-12-23
PXWPXW, followed your suggestions and the wifi works! I added ndiswrapper, and got rid of the gnome network manager and it works :)

I did notice that I am having issues in terms of speed. It is super slow and drops the network consistently. To be fair and compare, it is fast when I use the NIC connection :confused:

Any other tips :)

---

### Post by Archaeology_Student on 2007-12-24
Dang network connection :(

I changed a setting (the other day and don't recall what it was) and now I can not connect to my network. I have tried using the correct settings in the network manager for the wireless connection, and using the Wicd connection setting. 

I can see the various networks around me, but I can not connect to them for some reason. I go through Wicd, and have chosen the WEP and added the correct WEP key, but it will not connect. I am also using the broadcom Supplicant driver under the preferences... at a loss here :(

Any ideas? More info? 

Thank you in advance :)

---

