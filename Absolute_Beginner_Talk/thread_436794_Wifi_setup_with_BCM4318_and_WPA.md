---
title: "Wifi setup with BCM4318 and WPA"
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by leefischer on 2007-05-08
I have just installed Ubuntu on a one year old laptop.  This is my first experience with anything other than OSX and Windows, I am not supersmart or anything.     I am trying to connect to the internet using network manager with the wirless card.  the computer seems to see the card but where it says "password type", under "wireless settings" in the network manager, the only option I can select in the menu is WEP.  The network I want to connect to uses WPA.   

06:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
        Subsystem: Hewlett-Packard Company MX6125
        Flags: bus master, fast devsel, latency 64, IRQ 21
        Memory at c0204000 (32-bit, non-prefetchable) [size=8K]

I have had a fish around on the wiki and stuff but I am having trouble figuring it all out.  Can anyone guide me please.  

This is the first time I have ever posted anything on a forum or used this stuff so please be paitent with me as I figure it out!

Cheers 
Lee from Australia

---

### Post by Kobalt on 2007-05-08
Hello,

You might want to follow this good guide for setting up your card : [http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102)
As for WPA, if you use the default Network-Manager then you don't need to install anything else, it will simply ask for your WPA key and get you connected right away...

---

### Post by leefischer on 2007-05-08
Cheers mate, I will check out the guide now.     I would like to ask you a question about this network manager though.     I just down loaded an installed this ubuntu today and have done nothing other than try to set up the internet connection.    When you say "network-manager".... well I think this is what I am trying to use but I am not sure.    Bear wih me..

On the top right hand ccorner of the screen I there is an icon that looks like two terminals, one behind the other, it is right next to the volume icon.   I click on this icon then select "manual configuration" from the drop-down menu.  From there I get to a new window called "Network Settings" and this is where I can see my wireless connection and check it's properties.  Is this "Network Settings" place I am going to infact the "network-manager"?    If it is then I cannot find an option to use WPA as the password type.   

Am I making sense??

Cheers 
Lee

---

### Post by Capitao Caverna on 2007-05-08
I have the same card (BCM 4318) and I was unable to get it working with WPA under Feisty using the ndiswrapper method.  If you don't use WPA it works following this [http://www.stylesen.org/configuring_wireless_bcm4310_uart_card_in_debian_etch_amd64_using_ndiswrapper](http://www.stylesen.org/configuring_wireless_bcm4310_uart_card_in_debian_etch_amd64_using_ndiswrapper).
By now I gave up of Ubuntu in my laptop and I'm using another distro called Kurumin as it was the only one that was able to get my WPA working.  Now I'm waiting for some solution to come back... :-)

---

### Post by Kobalt on 2007-05-08
What you need to do is to click on this icon of yours (yes, it is Network-Manager) and select your network in the list below, then give your wpa key (which type it will have guessed by itself) that it will store and remember. 
If you can't see a list of available networks then you didn't install your wifi card properly I guess.
If you don't want to use Network-Manager (because in some cases it's buggy with WPA networks) then you can follow this good guide : [http://ubuntuforums.org/showthread.php?t=202834](http://ubuntuforums.org/showthread.php?t=202834)

PS: Capitao Caverna, isn't changing your whole Linux distribution just because of an independent problem a little extreme solution ? You would have found a solution or some help if you'd have posted here I guess...

---

### Post by Carlos Santiago on 2007-05-08
There are two different network managers.
One for all kind of networks, and other (installed by default on Ubuntu 7.04 "Feisty") specific for wireless networks. For the icon description, it seems that you are using the general one.

I would give a try to the wireless network manager (the icon is a small antenna)
It should work out of the Ubuntu 7.04 liveCD.

---

### Post by ericesque on 2007-05-08
lee,

I have the same card and have gotten it to work in feisty no problem.  The standard way to get it working (for guys in the know) is here:  [http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102)

The first post is really all you need.  There are a few ways it will walk you through the setup.  Since you already know you have the 4318, skip down to the bolded Feisty section and you'll be well on your way.

---

### Post by Kobalt on 2007-05-08
> **Carlos Santiago said:**
> There are two different network managers.
One for all kind of networks, and other (installed by default on Ubuntu 7.04 "Feisty") specific for wireless networks. For the icon description, it seems that you are using the general one.
No.
There is Network-Manager, a new Gnome application that is aimed at managing networks of all kinds (not only wireless) in a graphical way. And there is the old method, used until Feisty, of configuring the /etc/network/interface file either manually (through a text editor) or with the network-monitor applet. 
Feisty ships with Network-Manager installed and enabled by default but you can still use the old method, though you need to disable the first one. 
Both methods can handle wired and wireless networks, but they work differently. 
In some cases (there are plenty of them over the forum) Network-Manager isn't working properly, either with WEP or WPA encrypted networks... I don't use it myself for an example.

---

### Post by leefischer on 2007-05-08
Kobalt, I didn't do any installing other than the default of the cd.  Yes I can enter a password, but where it asks me for the "password type" I can only select WEP, there appears to be no option for WPA.   I will check out the links you gave me and see how I get on.   I am going to try and paste a screen shot of the net-manager but I am not sure how to post it.  He we go. 
 [IMG]http://Screenshot.png[/IMG]

---

### Post by Capitao Caverna on 2007-05-08
"PS: Capitao Caverna, isn't changing your whole Linux distribution just because of an independent problem a little extreme solution ? You would have found a solution or some help if you'd have posted here I guess..."

Actually I posted here before and tried all the alternatives that I found to get my card working with some decent speed under WPA... but none of them worked for me.  
I would not say that the move to kurumin is an extreme solution as it is debian derived as well...  I don't think there are so many differences besides the default language. The only problem is that it uses the Etch repositories and then you don't have the most recent (and unstable) packages.

---

### Post by Kobalt on 2007-05-08
> **leefischer said:**
> Kobalt, I didn't do any installing other than the default of the cd.  Yes I can enter a password, but where it asks me for the "password type" I can only select WEP, there appears to be no option for WPA.   I will check out the links you gave me and see how I get on.   I am going to try and paste a screen shot of the net-manager but I am not sure how to post it.  He we go. 
 [IMG]http://Screenshot.png[/IMG]
If you click on your network ESSID in the list and if Network-Manager asks you for a wep key then either you're facing a new bug, or your network is actually wep encrypted...

---

