---
title: "need help connecting to wireless network"
date: 2007-03-28
forum: Absolute Beginner Talk
---

### Post by Sigitas on 2007-03-28
Hello, I'm a complete Linux and Ubuntu newbie.  I'd like some help in connecting my Ubuntu Edgy box to my home's wireless network.  I have a Linksys WMP55AG wireless card (not even sure if it is set up properly...) and a Linksys WRT54G router.  The router has WPA encryption (tkip algorithm).  If at all possible, I would appreciate it if someone could provide a step-by-step guide (for the noob that I am:) )  for setting up my wireless card, and then connecting my computer to the internet.  I think it's also worth mentioning that I do NOT have wired internet access from where my Ubuntu box is, but I have a wireless enabled laptop if I need to download anything in particular.  I would like to thank anyone who helps me out in advance, as I greatly appreciate any help that you are able to provide.

---

### Post by undertherift on 2007-03-29
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Windows_Wireless_Drivers_.28Ndiswrapper.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Windows_Wireless_Drivers_.28Ndiswrapper.29)

There's alot of information there.  I think you fall into the bcm43xx category - but don't worry, it works just fine.  Follow those steps in a terminal.  (Applications -> Accessories -> Terminal)

You're going to have to get your hands a little messy with the LInksys cards, but post on here and I (we) can help.

Enjoy!

---

### Post by Sigitas on 2007-03-29
Does ndiswrapper work for an Atheros 5001X+ chipset, or is there something else that I have to use?

---

### Post by undertherift on 2007-03-29
Ndiswrapper is a wrapper for windows drivers.  If your card was supproted by a windows driver, it should work.

Check the Ndiswrapper wiki for cards/chipsets that are supported.  I don't know off hand - if you google it, you'll find it pretty easily.  

Good Luck

---

### Post by Sigitas on 2007-03-29
I google searched for my wireless card's compatibility, and found [http://users.linpro.no/janl/hardware/wifi.html](http://users.linpro.no/janl/hardware/wifi.html).  According to them, my wireless card's linux driver is Madwifi...what should I do for that?

---

### Post by undertherift on 2007-03-29
Google some more :)   Sorry, mate, never used that.
But at a first glance...
[http://www.ubuntuforums.org/showthread.php?t=75451](http://www.ubuntuforums.org/showthread.php?t=75451)

Supposedly it should work already... are you sure its not enabled? 

Check lspci to see if it shows up. or type iwconfig.  I think that forum post will send you in the right direction.

Having never used madwifi, i don't think i'll be much help, but let me know if you run into problems.

---

