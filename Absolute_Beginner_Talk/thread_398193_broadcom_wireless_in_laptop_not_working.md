---
title: "broadcom wireless in laptop not working"
date: 2007-03-31
forum: Absolute Beginner Talk
---

### Post by djwini on 2007-03-31
first day with ubuntu so be easy on me. i am running a compaq laptop with a built-in broadcom wireless bcm4306 802.11 b/g wlan. using the lshw command, the wireless shows up in the list of components. it would seem to need a driver, but i have no idea how to get one. help with that please?

---

### Post by overdrank on 2007-03-31
> **djwini said:**
> first day with ubuntu so be easy on me. i am running a compaq laptop with a built-in broadcom wireless bcm4306 802.11 b/g wlan. using the lshw command, the wireless shows up in the list of components. it would seem to need a driver, but i have no idea how to get one. help with that please?

Hi and welcome, I did a search and there is a lot of post on that card,
[http://ubuntuforums.org/search.php?searchid=17227458](http://ubuntuforums.org/search.php?searchid=17227458)
I am sure you will find what you need to help, Good luck!

---

### Post by SOULRiDER on 2007-03-31
[This]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx?highlight=%28WifiDocs%29%7C%28ManufacturerModel%29%7C%28AND%29") can probably help you. I suggest you take a look at it and if you have any issues just as here or join IRC and we can clear them up for you :)

Good Luck!

---

### Post by djwini on 2007-04-01
i can't get fwcutter to install. i downloaded the file and moved it from a flash drive to my desktop, extracted the files. and then nothing. i don't know how to install programs yet. trying from the graphic style, i get a message about it not being a found package. using the sudo apt i also get an error message. do i need to be hardwired to the internet for this to work?

---

### Post by Maestro23 on 2007-04-01
> **djwini said:**
> i can't get fwcutter to install. i downloaded the file and moved it from a flash drive to my desktop, extracted the files. and then nothing. i don't know how to install programs yet. trying from the graphic style, i get a message about it not being a found package. using the sudo apt i also get an error message. do i need to be hardwired to the internet for this to work?

Probably going to have to install from source.  Might run into a lot of dependency issues.  Check this section 4 on Installing from source at this link: [http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

Should be a README or INSTALL file in the extracted directory as well.  Do you have a link to where you d/l the driver from?

---

### Post by racin on 2007-04-01
I just set this up on my Gateway laptop same wireless card. You don't need fw cutter! Here is all you need to do! This is from a Howto for broadcom from compwiz18

Feisty

Download [http://ubuntu.cafuego.net/pool/feist...buntu2_all.deb](http://ubuntu.cafuego.net/pool/feist...buntu2_all.deb) 
and double click it to install. Reboot. Enjoy wireless.

Good Luck!

---

### Post by djwini on 2007-04-03
ok, i got it all to work by hard wiring the laptop to my internet connection and doing the universal thing.

---

