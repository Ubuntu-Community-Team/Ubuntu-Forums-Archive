---
title: "Acer wireless not working"
date: 2007-11-05
forum: Absolute Beginner Talk
---

### Post by mindstormmaster1 on 2007-11-05
My acer wireless doesnt seem to work with Ubuntu but it does with DSL( Damn Small Linux)  Can any one tell me how to get it to work I can a complete newbe and have no idea what I am doing.

O the model of the internal wifi chip is   Atheros AR5007EG Wireless Network Adapter

And it a Acer Aspire 5050-3785

I dont know if this matters but im using a live cd of Ubuntu 7.20

Thanks

Ethan Steckmann(a future Ubuntu user)

---

### Post by pedja_portugalac on 2007-11-05
I am on Acer Aspire 9410Z also with Atheros WiFi and it work fine for me. Try to do like this: go to System, Administration and Restricted Drivers Manager. If in that window you can see Atheros Hardware Access Layer (HAL), than check the box to enable it. You should see ( In use). In my case it was automatic just after installing Ubuntu but you can try this in case you jump that step. If everything goes well you can see what wireless networks are in your range by clicking on the network icon in right above angle of your desktop.

---

### Post by mindstormmaster1 on 2007-11-05
I will try that will it work with a live cd

---

### Post by pedja_portugalac on 2007-11-05
yes

---

### Post by mindstormmaster1 on 2007-11-05
It didnt work any other ideas

 thanks

e

---

### Post by hotweiss on 2007-11-05
You have to use the ndiswrapper:
[http://ubuntuforums.org/showthread.php?t=512828&highlight=5007eg](http://ubuntuforums.org/showthread.php?t=512828&highlight=5007eg)

---

### Post by pedja_portugalac on 2007-11-06
> **mindstormmaster1 said:**
> It didnt work any other ideas

 thanks

e

During the installation of Ubuntu Gutsy, there is option "something like" install with drivers. Within this option you will be prompt to put inside original manufacturers CD with drivers. I have never tried this option but it should import your driver from Original computers Drivers CD.

---

### Post by Odisej on 2007-11-06
I also have Acer and it works fine. But if I were in your shoes I would try to install the latest madwifi drivers. You should find it here: [http://madwifi.org/](http://madwifi.org/)

Regards,

Odisej

UPDATE: I just read your original post again and noticed you are using a Live CD version. I don't think much can be done in "live CD" mode. But should you decide to install, my idea might work. :P

---

### Post by mindstormmaster1 on 2007-11-06
So i need to install it first ok I will think about it.

Also im seeing a lot about madwifi but have no idea how it work or how to install it or anything  could someone please for a tutorial for me or point me to one thanks.

Also why would DSL work with my wifi and not ubuntu which i suppose to have great driver support.

I am running a AMd Turion 64 processor with a 32 bit version on windoes vista home premium if that matters.


And the fist idea did work.  I think madwifi is my best bet if i knew how to use it.

ethan

---

### Post by mindstormmaster1 on 2007-11-06
[http://www.stchman.com/ath_drv.html](http://www.stchman.com/ath_drv.html)

I found this site does it look like it will work.

e

---

### Post by hotweiss on 2007-11-06
The Madwifi driver does not support the 5007 card. You need to use the wrapper!!! And you should also install the Acer ACPI module to:

[http://code.google.com/p/acer-acpi-deb/](http://code.google.com/p/acer-acpi-deb/)

---

### Post by tuskenraider on 2008-01-30
i have a 9410z and a broadcom wireless card....:( i hate it!!! my wireless was soooo horrible that i actually went and bought a pcmcia card. edimax has one on new egg for like 23bucks tax and all...  now that card is fantastic... currently i dont even have the restricted broadcom drivers enabled. im now much happier.

tuskenraider

---

### Post by oedha on 2008-01-30
may i ?
here is what i did to atheros 5007EG
-download the AR5007EG windriver
-install ndiswrapper manually
-open terminal; type sudo rmmod ath_pci ( remove the pci module )
-type sudo vi /etc/modprobe.d/blacklist-common
-insert : blacklist ath_pci ( to put ath_pci in blaklist mode )
-save it and restart the computer
-extract the windriver into one folder ( ex: documents )
-go to System &#8211; Administration &#8211; Windows Wireless Drivers
-install net521.inf
-click configure button and set it up
-open terminal; type sudo ndiswrapper -m ( to load ndis on restart )
-reboot the computer


it works fine for me
~E~

---

