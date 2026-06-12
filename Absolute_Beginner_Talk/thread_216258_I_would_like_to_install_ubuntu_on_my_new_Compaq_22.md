---
title: "I would like to install ubuntu on my new Compaq 2210US laptop..."
date: 2006-07-15
forum: Absolute Beginner Talk
---

### Post by UberIcarus on 2006-07-15
How do I go about this, and will I run into driver trouble? Is there like a guide somewhere to trying to install linux on otherwise propietary windows machines?

---

### Post by bikeboy on 2006-07-15
Just beginning section here:
[http://psychocats.net/ubuntu/index.php](http://psychocats.net/ubuntu/index.php)

Some good guides here too:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

Best bet is to download the Desktop cd, it has an easy to use installer. There is no guarentee that everything in your system will work 100%, but for most things it will be fine. If you're not sure, list your pc specs.

---

### Post by UberIcarus on 2006-07-15
Cool! I actually want to replace windows on this laptop. I'll just reinstall if I find it all too difficult. I have 3 other computers. The main things I'm worried about is sound, USB support, ethernet support, intel Extreme 2 graphics support, DVD ROM support, the integrated wireless card, the power management system (will it recognize the battery and tell me when its getting low, etc.), and finally will it recognize the touchpad as a mouse?

---

### Post by bikeboy on 2006-07-15
General linux experience from me.
Sound: good support, probably 100%
USB: no problems
Ethernet: no probs
Intel graphics: not sure on that model, but usually good.
DVD-ROM: no probs
Wireless: depends on who makes it, if it's Centrino then should be all good
Power man: Basics such as what you said 100%, sometimes things don't go perfectly though, like on my acer laptop it doesn't show the remaining battery life properly without a bit of fiddling. But it will recognise when it's plugged in etc.
Touchpad: Mine works perfectly, dad's works perfectly, older toshiba joystick thingy worked fine too. So I'm guessing no probs.

---

### Post by UberIcarus on 2006-07-15
Errr....now I have a problem. I burned the ISO but the laptop does not recognize it as a bootable disk. More interesting is that I get a boot priority that includes an ATAPI (or some similar acronym) CD Rom...while this has a DVD Rom drive...


Did I burn the ISO wrong? I used nero and burned it as an ISO.

Hrmm...going to try a new disk.


HAHAHAHA...Nevermind, I put the wrong disk in.

---

### Post by UberIcarus on 2006-07-15
Okay...got unbuntu installed, and I like the GUI. I really like the GUI. I also like the functionality.

I have one problem: My wifi is not working, at all. It's the kind you have to push a button to turn on. I push the button and nothing happens. This is not a problem I can live with on the laptop...any suggestions?

---

### Post by crispy_420 on 2006-07-15
You have to set it up for it to work.

System -> Administration -> Networking

There you'll find your setup gui. Hopefully you'll see your card listed as a network interface. And just hope you don't have ra0 listed, I have that card in mine and it will not work with network manager yet(ended up buying and external card to solve that, atleast until RaLink support is added). You'll want to activate it and then go into properties to setup other features like security.

You'll probally want to make your network card the default interface too.

---

### Post by UberIcarus on 2006-07-15
It appears that I have a broadcomm wireless network card in this, and searching through the forums I've found that there are evidentally problems getting broadcoms to work.


=\ trying a help guide I found somewhere here. Will probably have to wait awhile because I don't have a wired network at the moment.

---

### Post by bikeboy on 2006-07-15
Depending on the particular broadcom chipset it works fine, that's what I have at the moment. But I've bought a new Ralink rt2500 based card because they work out of the box :)

To identify your exact chipset try this. Applications > Accessories > Terminal. Then copy this into the terminal and press enter.```
lspci | grep -i broadcom
``` Then I might be able to help with finding the right guide for getting it going.

---

### Post by UberIcarus on 2006-07-16
It seems that the lspci | grep -i broadcom (or broadcomm, tried that too) doesn't do anything for me. =\

My wireless card under device manager is BCM4306 802.11b/g wireless.

---

### Post by bikeboy on 2006-07-16
Hmmm strange that it didn't come up. You're in luck however as I use a program called ndiswrapper with my bcm4306 card, it uses the windows drivers to make your wireless work. Have a read of these instructions:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

