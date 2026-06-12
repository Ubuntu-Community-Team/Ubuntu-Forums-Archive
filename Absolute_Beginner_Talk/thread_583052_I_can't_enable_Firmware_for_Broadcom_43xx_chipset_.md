---
title: "I can't enable Firmware for Broadcom 43xx chipset family"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by Dr.Suave on 2007-10-20
Hiya

Just installed Ubuntu - completely new to Linux

I'm trying to enable the Firmware for Broadcom 43xx chipset family - but everytime I click the box to enable it I get this message:

"The software source for the package bcm43xx-fwcutter is not enabled"

There dosen't seem to be anything I can do about it.

What should I do? get the driver off the net? install ndiswrapper?

Please help!

Wilf

---

### Post by derred on 2007-10-20
You have to enable the restricted repositories. Go to System/Administration/ Software sources and check Proprietary drivers and devices. Do an update. try to enable the drivers again. You will be asked where to get them from (local or internet). Select internet and go with the default address. This worked for me on a Dell Latitude D400 laptop with a bcm43xx WiFi card.
Good luck!

---

### Post by kamaboko on 2007-10-20
i did that, but each time i restart my computer the restricted drivers don't load and my wifi doesn't work.  it does show them as loaded under system > admin > restricted driver manager.  so...i have to unload and reload them every time i restart the computer: vostro 1400 laptop.

---

### Post by Dr.Suave on 2007-10-20
Dont really have any alternate means of connecting to the internet on that computer - could I download the driver elsewhere, burn it to disc and then install it?

thanks for the help

---

### Post by kamaboko on 2007-10-20
pm me your email address and i'll send it as an attachment

---

### Post by Dr.Suave on 2007-10-20
cheers

just sent my email address

once I've got the file on disk what do I do with it? :)

---

### Post by kamaboko on 2007-10-20
ygm with instructions

---

### Post by Dr.Suave on 2007-10-20
Thanks for emailing me the file - but I cant find an option to browse my hard drive for the update anywhere...

---

### Post by VON_CAPO on 2007-10-20
> **Dr.Suave said:**
> Hiya

Just installed Ubuntu - completely new to Linux

I'm trying to enable the Firmware for Broadcom 43xx chipset family - but everytime I click the box to enable it I get this message:

"The software source for the package bcm43xx-fwcutter is not enabled"

Wilf
I have a Broadcom 4318 PCI, I made it work in 3 minutes:

1- Download and install " bcm43xx-fwcutter_006-3_i386.deb "

1b- If you see the following:
[[IMG]http://img165.imageshack.us/img165/937/screenshot2oh5.th.png[/IMG]](http://img165.imageshack.us/my.php?image=screenshot2oh5.png)

 (it tries to download something from Internet and it fails, go to Synaptic and uninstall bcm43xx-fwcutter.

Then, install again " bcm43xx-fwcutter_006-3_i386.deb ", if everything is OK you will see the following:
[[IMG]http://img165.imageshack.us/img165/9900/screenshot1copyjt7.th.png[/IMG]](http://img165.imageshack.us/my.php?image=screenshot1copyjt7.png)


2- Extract the firmware.
Then go to the Restricted Manager y select Firmware for Broadcom
[[IMG]http://img98.imageshack.us/img98/7232/screenshot3kn9.th.png[/IMG]](http://img98.imageshack.us/my.php?image=screenshot3kn9.png)


3- You will see the following
[[IMG]http://img50.imageshack.us/img50/2493/screenshot4ww0.th.png[/IMG]](http://img50.imageshack.us/my.php?image=screenshot4ww0.png)
Click "Enable Firmware"


4- A dialogue to browse will appear
[[IMG]http://img514.imageshack.us/img514/4180/screenshot5sy1.th.png[/IMG]](http://img514.imageshack.us/my.php?image=screenshot5sy1.png)


5- Select " wl_apsta.o " (For my 4318  card, it works perfect)

[[IMG]http://img144.imageshack.us/img144/2518/screenshot7ar1.th.png[/IMG]](http://img144.imageshack.us/my.php?image=screenshot7ar1.png)

[[IMG]http://img265.imageshack.us/img265/206/screenshot8ld1.th.png[/IMG]](http://img265.imageshack.us/my.php?image=screenshot8ld1.png)


You're done.
Internet at once, and it is not necessary to reboot. :)

---

### Post by Dr.Suave on 2007-10-20
Swish! THanks for the simple tutorial - I managed to get through it no problem

My computer can now see my wireless network

but it cant seem to connect!!

I'm using a wireless Belkin 54g card - is this compatible?

Thanks a lot

wilf

---

### Post by Dr.Suave on 2007-10-20
ok dokes - done some research - my card IS a broadcom card

After some creative clicking I've managed to get it to connect to my wireless network.

But despite the strong signal strength - firefox STILL cant access the web! :confused:

Any ideas at all?

---

### Post by VON_CAPO on 2007-10-20
> **Dr.Suave said:**
> Swish! THanks for the simple tutorial - I managed to get through it no problem

My computer can now see my wireless network

but it cant seem to connect!!

I'm using a wireless Belkin 54g card - is this compatible?

Thanks a lot

wilf

Actually, you do not look at the manufacturer model but the chipset installed.

So, first you should find out about the chipset, and after that, you should try to find the right tutorial into the forum.

Also you can read a overview about the subject here ---> [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

---

### Post by VON_CAPO on 2007-10-20
> **Dr.Suave said:**
> ok dokes - done some research - my card IS a broadcom card

After some creative clicking I've managed to get it to connect to my wireless network.

But despite the strong signal strength - firefox STILL cant access the web! :confused:

Any ideas at all?

I had experimented the same problem for almost 2 (TWO) years.

Try with a open network, and then with a secured one. If it that's not work, reboot and try again.

Do not trust too much in the signal level :roll:

Experience had teach me that I must try over and over again, seldom I could not connect for 3 hours (perhaps interference????)

I have to mention that using NDiswrapper to make work the card, has no difference at all ---> same problems.

---

### Post by runemaste644 on 2007-10-20
Heres a magic script for bcm43xx [http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990)
it really works!

---

### Post by huntermaclean on 2007-10-20
Runemaste644: I tried that application with no luck. I'm running:
ubuntu 7.10
Dell Inspiron 8500
Broadcom 4306

---

### Post by VON_CAPO on 2007-10-20
> **Dr.Suave said:**
> 

But despite the strong signal strength - firefox STILL cant access the web! :confused:

Any ideas at all?

If you have an IP address and a DNS address, YOU ARE CONNECTED to the router and to the Internet.

Right click on the wireless icon and select "Connection Information"
[[IMG]http://img218.imageshack.us/img218/4497/39286527wi3.th.jpg[/IMG]](http://img218.imageshack.us/my.php?image=39286527wi3.jpg)

The problem (I believe) is in the data transmission between the card and the router (but it is beyond my scope if the right answer is the driver itself or interference).

---

### Post by Dr.Suave on 2007-10-20
Ok - Runemaster's script didnt work because my kernel isnt supported - maybe I should just downgrade to Feisty Fawn?

VON_CAPO - I did have a connection for a bit, but then restarted the computer. Now it's gone - and when I had it I couldn't seem to browse the web.

Is Ubuntu actually this hard to connect to Wifi with? Should I give up on the idea?

I might see if I can find a cable connection somewhere and try the online installer of Runemaster's script...

thanks for all the help - hope I manage this!

---

### Post by VON_CAPO on 2007-10-20
> **Dr.Suave said:**
> 
VON_CAPO - I did have a connection for a bit, but then restarted the computer. Now it's gone - and when I had it I couldn't seem to browse the web.

A few months ago, I bought a external antenna with a 2 meters long cable (I placed it on the window) and my connection improved a lot. 

Take in count that the longer the cable... the weaker the signal.

---

### Post by Dr.Suave on 2007-10-20
OK - found a wired connection and did an online install of Runemaster's program - and now I can't even find a wifi section in the Network Manager!! when I take my Belkin card in and out of the laptop nothing happens - I think I might have screwed this up by trying so many different things...

Does anyone know how to fix this one? :)

Thanks a lot

Wilf

---

### Post by Dr.Suave on 2007-10-20
Huzzah! I reinstalled Ubuntu entirely, then used the program Runemaste644 recommended - and it worked straight away! I'm posting this over a wireless connection!! Brilliant!

All I have to do now is disable my trackpoint and install Compiz Fusion and I'll have the perfect laptop!

But *that* is another post for another day.

Thank you so much everyone who helped me get to this point!

Wilf

:):):)

---

### Post by alex69 on 2007-12-13
thanks Von_Capo, could you send me the bcm43xx-fwcutter package? it seems to be hard to find for me...

thanks in advance

---

### Post by VON_CAPO on 2007-12-13
> **alex69 said:**
> thanks Von_Capo, could you send me the bcm43xx-fwcutter package? it seems to be hard to find for me...

thanks in advance

Go here: ---> [http://packages.ubuntu.com/gutsy/utils/bcm43xx-fwcutter](http://packages.ubuntu.com/gutsy/utils/bcm43xx-fwcutter)  

Click on your architecture, I mean i386 or AMD64. 

In the next page you will see a lot of links from where to download the package, right click on anyone of them and select "save as".

If you need the firmware (it is file called " wl_apsta.o "), you can download it from:
---> [http://joona.kuori.org/ubuntu-powerbook/wl_apsta.o](http://joona.kuori.org/ubuntu-powerbook/wl_apsta.o)

**EDIT:**
Another link from where to download the firmware:
---> [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware)

---

### Post by tippyknit on 2008-02-14
> **kamaboko said:**
> pm me your email address and i'll send it as an attachment

I'm new to Ubuntu and have the same problem.

I have a 2007 iMac with a built in AirPort Extreme wireless card (firmware Broadcom 43xx chipset family). Every time I load Ubuntu, it tells me that 'bcm43xxchipset' could not be loaded - a 'microcode error'. I have tried the suggestions on this page, all but the one of updating - I have to connect wirelessly. Can anyone send me the file that's supposed to help with the firmware update?

---

### Post by Spectre Nexus on 2008-04-14
Greetings, I am a newb when it comes to Ubuntu and Linux in general. 
I have a Presario V5000 with a Broadcom 43xx wi-fi chip

After reading numerous posts about how horrible this card is I took
it in stride and after some trial and error I have the wi-fi working.

However the error I am getting is every time I reboot the system wi-fi is 
gone and in the restricted drivers manager is still says it enabled, However 
the only way to get wi-fi working again is to disable it and reboot
then go through the whole re-enable process then it works fine until the next reboot.
 Due to restrictions I am forced to shut down and restart the system numerous times a day, therefor leaving it on isn't an option.

My question is Is there something I am doing wrong or something else I need
to do to make this a easier process, so I can actually use this laptop like a laptop
and not a desktop. 

Ubuntu 7.10 - Gutsy Gibbon
fully updated

Thank You in advance

---

