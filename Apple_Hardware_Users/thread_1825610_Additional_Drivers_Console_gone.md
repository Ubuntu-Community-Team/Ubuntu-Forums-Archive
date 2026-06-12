---
title: "Additional Drivers Console gone"
date: 2011-08-15
forum: Apple Hardware Users
---

### Post by Doeydude on 2011-08-15
Hi There

I have installed Ubuntu 10.10 on to my iMac G5. I know that there are many other distros, but I have chosen this one for a number of reasons.

Anyway, I am have a few problems with a number of drivers. One in particular is the Airport wireless connection. There are tons of very complex suggestions out there for me to try when I search for a solution and I have tried a few without any success.

I think my solution is easier then a lot of the forums are suggesting. When I click on the network icon at the top of the screen I can see my LAN connection and greyed out under wireless I can see "device not ready (firmware missing)".

After a few searches I have come across a number of repeated solutions. The easiest being to click on "System - Administration - Additional Drivers" and after it checks for updates a Control Panel should appear and I should select to install the necessary drivers.

However what actually happens is that after I click on Additional Drivers, it checks for updates, but never displays any control panel for me to make any further selections.

Is there a way to view the control through a Terminal command?
Is there any other location that has a switch to allow/disallow the display of the Additional Drivers control panel?

This is driving me crazy. Any help would be appreciated.

Doey

PS.  I have just tried to boot from the Live disk and the console is accessible. This is with the 10.04 disk that I did the original install from before immediately upgrading it to 10.10.

---

### Post by Hizaresgon on 2011-08-16
NO its not possible to connect Drives to  Console Game........

---

### Post by Doeydude on 2011-08-16
Aaahhhh, OK Then

Sorry about that. When I said Console I actually meant Control Panel Console and not Gaming Console.

If you read the rest outside of the header you will see that what I am talking about has nothing to do with gaming and all to do with wireless networking.

Sorry for any confusion.

---

### Post by rsavage on 2011-08-16
From my lubuntu thread (see last page of powerpc sticky):

"*If you have an airport extreme card then you need to download the  firmware. Maverick and Natty users should open lxterminal and type "sudo  apt-get install firmware-b43-installer". You should now see your  wireless networks. Lucid users should type "sudo apt-get install  b43-fwcutter" in lxterminal and then go to Preferences > Additional  drivers and select the Broadcom b43 driver. *"

Substitute lxterminal with whatever terminal/console program you have.

Airport classic is  different, again there are instructions on the lubuntu thread.

---

### Post by Doeydude on 2011-08-16
Hi there rsavage

I ran *"sudo  apt-get install firmware-b43-installer" *in terminal as suggested and everything extracted without any errors. I checked the network connections before and after a restart and there is still nothing showing. 

It is definitely showing up in the Device Manager. There is no question mark next to it in the list and it is giving me back the correct details - BCM4306 802.11b/g Wireless LAN Controller. In fact I have attached a screen grab of the Device Manager.

It actually allows me to make changes to the Device Properties. Is there a way to activate it from here?

A lot of the other forums that I am reading suggest that I go to System - Administration - Additional Drivers, and once it has run its scan i should be seeing a Control Panel for the Driver. In here I should activate the Broadcom device and the Bob's your uncle. However the Control Panel never appears. Is there a way of getting it to appear through Terminal?

I was reading your post on Lubuntu. It sounds very interesting. Faster is always better. One of the biggest things that made me decide on Ubuntu 10.10 for my G5 was the Elegant GNOME theme. It just makes it look real sharp.

I read that this theme can be applied to Lubuntu too. [http://www.ananiev.org/2011/02/lubuntu-after-fresh-install.html](http://www.ananiev.org/2011/02/lubuntu-after-fresh-install.html) . If this was the case and Docky could be added to it, then I would seriously consider moving across if it would sort out the drivers issue (nVidia FX5200 Ultra mostly).

Doey


[IMG]http://www.jinnyjoe.com/DM.png[/IMG]

---

### Post by rsavage on 2011-08-16
I think you are making things too complicated.  The solution will probably be simple.  Have you read this thread that is linked on the lubuntu one [http://ubuntuforums.org/showthread.php?t=1705143](http://ubuntuforums.org/showthread.php?t=1705143) .  You probably just need to tick the 'enable wireless' option on network manager.  Also the power pc faq has some info regarding routers [https://wiki.ubuntu.com/PowerPCFAQ#Will_my_wireless_work.3F](https://wiki.ubuntu.com/PowerPCFAQ#Will_my_wireless_work.3F) .

I don't have access to a mac at the moment so I can't be sure, but I don't think I had anything appear in the Additional Drivers section under lubuntu natty.  So that could be normal.

---

### Post by Doeydude on 2011-08-16
rsavage

I have followed you instructions and I am now using WICD but it makes no different. I agree with you in that I too think that there is something simple amiss here. 

I ran "sudo lshw -c network" in terminal as suggested in [http://ubuntuforums.org/showpost.php?p=9241613&postcount=12](http://ubuntuforums.org/showpost.php?p=9241613&postcount=12) and I have included the relevant part of the results below. If you notice it says "network UNCLAIMED".

I looked this up and came across this thread [http://ubuntuforums.org/showthread.php?t=1530270](http://ubuntuforums.org/showthread.php?t=1530270). Again, as in many other threads, the solution was to "check in System/Administration/Hardware Drivers and see if a driver is listed there for your wireless - if so, enable it".

The problem with me the whole time has been that I cannot. Firstly, there is no "Hardware Drivers" to be found. Other threads say that once "Additional Drivers" runs it then gives you the chance to enable the Airport. But again this does not display so I cannot enable anything.

I am convinced that if I can get this Control Panel (Console) to appear I will be able to get it work properly.

Would you have any suggestions?

```

  *-network UNCLAIMED
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0001:01:01.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=16
       resources: memory:80084000-80085fff

```

---

### Post by rsavage on 2011-08-16
The problem is things change slightly with different versions of ubuntu (lucid, maverick, natty, lubuntu, ubuntu, xubuntu) and so it is hard for me to give you exact instructions.  Also, I have never used an imac G5.  Plus, my ibook is in bits ready to be sold on ebay so I have no way of checking what I write!  

I am not very familiar with wicd so can't give you any help with that at all.

Firmware:  There are two different commands to download it.  For lucid (and I think maverick) I have always used "sudo apt-get install  b43-fwcutter".  For natty that didn't work so I had to use "sudo apt-get install firmware-b43-installer". You could try removing the one you have been using "sudo apt-get remove ****whatever***" and try installing the other one.

Also, try with your 10.04 live cd.  You should be able to download the firmware using "sudo apt-get install  b43-fwcutter".  That should definitely work.  It will show up on the "Additional drivers" like you want.  You should see your networks on the network applet.

---

