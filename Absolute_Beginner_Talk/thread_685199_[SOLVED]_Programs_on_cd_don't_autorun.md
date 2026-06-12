---
title: "[SOLVED] Programs on cd don't autorun"
date: 2008-02-01
forum: Absolute Beginner Talk
---

### Post by ThePinkWitch on 2008-02-01
I have installed Ubuntu a couple of days ago and I need to install netgear drivers coz i'm trying to get my network between 2 computers up and going. For some reason when I put cd's in with install programs the cd won't autorun in Ubuntu. I don't know how to enable it. The cd is one I got from my ISP when i first got Broadband. I need the drivers for the USB wireless adapter.

---

### Post by jaytek13 on 2008-02-01
You won't be able to install those drivers from the cd. Even if you could they wouldn't be useful, as those drivers are designed for Windows, not Linux. 

Post your hardware model and then someone can probably get you started with getting the correct drivers.

---

### Post by ThePinkWitch on 2008-02-01
oh DUH! Thanks I'm such a noob with this new OS thing. It would be so easier if the computer with Ubuntu were on the internet. I have Netgear WG111v2 USB wireless adapter.  I still haven't got a handle on how to install stuff yet *sigh* Thankyou for your reply.

---

### Post by bluewraith on 2008-02-01
You're going to need what is known as "ndiswrapper". From what I understand, it pretty much takes your driver for windows (the .inf) and makes it work for linux.

Give me a couple more minutes and I'll see what I can do for you. In the mean time, 
[http://ubuntuforums.org/showthread.php?t=56346]("http://ubuntuforums.org/showthread.php?t=56346")
seems to be exactly what you need. Let me see if I can trim the fat of of it for you. :)

Actually, right below my post will work great for you. :)

---

### Post by jaytek13 on 2008-02-01
There is also more up-to-date "guide" here in this post

[http://ubuntuforums.org/showthread.php?t=590942](http://ubuntuforums.org/showthread.php?t=590942)

Which specifically references using it with gutsy.


And since it would seem you're not currently on the Internet with the Ubuntu machine, you'll probably have to download all this stuff and burn it to a cd.

---

### Post by ThePinkWitch on 2008-02-02
[QUOTE=bluewraith;4252854]You're going to need what is known as "ndiswrapper". From what I understand, it pretty much takes your driver for windows (the .inf) and makes it work for linux.

Hey thanks. I have downloaded ndiswrapper but haven't installed it . I still haven't worked out how to do that yet.

---

### Post by ThePinkWitch on 2008-02-02
> **jaytek13 said:**
> There is also more up-to-date "guide" here in this post

[http://ubuntuforums.org/showthread.php?t=590942](http://ubuntuforums.org/showthread.php?t=590942)

Which specifically references using it with gutsy.


And since it would seem you're not currently on the Internet with the Ubuntu machine, you'll probably have to download all this stuff and burn it to a cd.

Hey thankyou, I checked that post out and it does seem like it will be useful. I'm not sure If it's exactly what I need to do because my main machine running WinXP was set up for networking a year ago but the original second machine died so I haven't had a network till now. This second machine now has Ubuntu on it. Thats the only one needs configuring. only I paid someone to set it up last ime. THIS time I'm trying to do it lol. And let me tell you that IS funny. I'm a Noob with Ubuntu and with networking. ](*,)

---

### Post by Shazaam on 2008-02-02
> **ThePinkWitch said:**
> Hey thanks. I have downloaded ndiswrapper but haven't installed it . I still haven't worked out how to do that yet.

This a good page that helps with installing software......

[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

The page says it was written for Ubuntu Dapper but it should work fine with whatever version of Ubuntu you have.

---

### Post by ThePinkWitch on 2008-02-02
I have to download stuff and burn it to CD. I CAN'T find how to istall stuff from a cd. I have Nvidia drivers , wine and Netgear zip file on a cd and can't get thm from cd to computer AHHHHHHHHHh ](*,)

---

### Post by sennep on 2008-02-02
no need to download ndiswrapper to install it, you don't need an internet connection to install it! Just open Synaptic Package Manager (it's in System --> Administration --> Synaptic Package Manager). Use the search function, just search for the word "ndiswrapper". Some search results should appear, choose the two called "ndiswrapper-common" and "ndiswrapper-utils-1.9".  (Click the box next to them and choose Mark for installation). Then, find the button called "Apply", click it! Synaptic Package Manager will ask you to insert your Ubuntu CD, so just give it the CD and continue. When Synaptic is done, ndiswrapper has been installed on your system!


As for the CD you have burned, when you insert it into the computer, does it not show on your desktop? See if you can find it in the /media/ folder.

---

### Post by ThePinkWitch on 2008-02-03
As for the CD you have burned, when you insert it into the computer, does it not show on your desktop? See if you can find it in the /media/ folder.[/QUOTE]

Thanks for that I have managed to install it now. Ido get the contents of the CD to show up But how do you install from the Cd? I have NVidia drivers on the Cd and Net gear drivers. I have tried all the ways I've seen on these websites to install but I must be doing something wrong.
i got WINEe to extract to desktop and have this on the desktop...
wine-0.9.54
setup.zip (for Netgear drivers)
NVIDIA-Linux-x86-169.09-pkg1.run
Please tell me what I do to install/use these. Thanks I'm about to chuck the computer thru the window. :confused:

ooh just found out how to do that thankyou thing..at least I learned something today :lolflag:

---

### Post by sennep on 2008-02-03
I would recommend you to get the internet connection first! 

The reason for that is that it's probably easier to use Restricted Drivers Manager (System--> Administration--> Restricted Drivers Manager) to install the Nvidia drivers for you. (it even downloads them for you). And with an internet connection, you can use Applications--> Add/Remove to install Wine with the click of a button. (you just have to search for it, mark it, and click apply and it will be downloaded and installed automatically)

So we need an internet connection first. I also have a WG111v2, and it took me some time to figure out how to do it, but now it works perfectly. The drivers you have on the CD is a zipped setup.exe. It would probably be easier to download drivers that are not in a setup.exe. I have some links to drivers like that, but first I need to know what kind of Wg111v2 you have (there are a couple different ones).

In the terminal (Applications--> Accessories --> Terminal), type ```
lsusb
``` and hit enter (that's a small L not a capital I by the way)

You should see some strange numbers like 0846:4240 or 0846:6a00 or something like that. Post those numbers, and hopefully I have a link to a driver that will work for you.

---

### Post by ThePinkWitch on 2008-02-03
Thanks so much for your help. I did as you asked it came up with
ID 0846:6a00 Netgear, Inc. WG111 WiFi (v2).
I have no chance of getting the internet up for a while. I've been trying to get my network going for three solid days. I'm about to burn my computer lol. My main was set up to network with a different computer to the one I have with Ubuntu on now, so it should be just the second one I need to set up. Unfortunately it wasn't me who set it up. I know it would be Soooo much easier if I have the net.
Why is it so hard to install and run files?
I'm really confused and exasperated trying to unzip and run stuff to install.

---

### Post by sennep on 2008-02-03
It's actually really easy to install things on ubuntu, but it gets tricky when it comes to installing stuff originally made for windows on ubuntu, like the driver we are about to install.

Let's see, you should download [this driver]("http://www.majorgeeks.com/Realtek_RTL8187_USB_Wireless_LAN_ME2000XP_d5165.html") (you must choose a location and the download will start). And [this]("http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Funiverse%2Fn%2Fndisgtk%2Fndisgtk_0.7.2-1ubuntu1_i386.deb&md5sum=96eb9dd9093622daecf21fcfa1ef275e&arch=i386&type=main") is also handy (choose a location on that one to).

The first download you should unzip while in windows, and then burn the unzipped files to a cd along with the ndisgtk download (the other link I gave you).

Then put the CD in the ubuntu computer and copy the contents to your home folder (or somewhere else if you want)

Then you should doubleclick the .deb file and install it (by clicking the install button on that thing that pops up).

Let me know when your done with it:)

---

### Post by ThePinkWitch on 2008-02-03
> **sennep said:**
> It's actually really easy to install things on ubuntu, but it gets tricky when it comes to installing stuff originally made for windows on ubuntu, like the driver we are about to install.

Let's see, you should download [this driver]("http://www.majorgeeks.com/Realtek_RTL8187_USB_Wireless_LAN_ME2000XP_d5165.html") (you must choose a location and the download will start). And [this]("http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Funiverse%2Fn%2Fndisgtk%2Fndisgtk_0.7.2-1ubuntu1_i386.deb&md5sum=96eb9dd9093622daecf21fcfa1ef275e&arch=i386&type=main") is also handy (choose a location on that one to).

The first download you should unzip while in windows, and then burn the unzipped files to a cd along with the ndisgtk download (the other link I gave you).

Then put the CD in the ubuntu computer and copy the contents to your home folder (or somewhere else if you want)

Then you should doubleclick the .deb file and install it (by clicking the install button on that thing that pops up).

Let me know when your done with it:)

I downloaded the drivers from that site the other day so i have that already. I read your post about the netgear yesterday and had it saved in bookmarks lol. I couldn't find the ndisgtk file I even googled it so THANKYOU!!! Let you know how it goes :)

---

### Post by sennep on 2008-02-03
lol:) What I explained above was actually step 2 and 3 in my guide so you only have to do 1, 4 and 5 now. Ndisgtk isn't actually necessary, but it makes things a lot easier, it greatly reduces the amount of typing in the terminal:)

---

### Post by ThePinkWitch on 2008-02-03
Well I couldn't figure out how to use nndisgtk whatever program so I used your instructions to install with the ndiswrapper. I think it worked lol. but No network. I think I have messed with it so much I have "stuffed" the settings completely. As well as that I don't know the Domain. DNS, Password stuff. Someone else set the network up on this machine and a second one not me. I now have to pay the guy to come back and do it again. That should be fun, he knows nothing about Linux either lol.
The only way wireless as an option comes up is if I tick enable roaming. If I untick it's not there. When I first started Ubuntu and looked at networks there was options there and I could see about 4. (Must have been the neighbours hehe) Nothing now. DOH!!! lol Is the Domain your ISP? Thanks so much for your help and patience.:biggrin:

---

### Post by sennep on 2008-02-04
> **ThePinkWitch said:**
> I think I have messed with it so much I have "stuffed" the settings completely

lol:) I did that too at first, and I had no idea how to fix it, so I just reinstalled Ubuntu:lolflag:


> **ThePinkWitch said:**
>  As well as that I don't know the Domain. DNS, Password stuff.

If you don't know the password then you won't be able to set it up. Does this computer guy know the password?

Yes the wireless option might disappear if you disable roaming, but you should be able to either choose or type in the name of the network you wish to connect to in manual configuration, just find the place that says Network Name or ESSID or SSID and type in the name of your network there. Network manager will loose it's ability to show whether or not you are connected when you set up a manual coniguration, this is also one of the reasons I use Wicd instead of Network Manager.

I don't think you need to write anything on the DNS and Domain settings. The only things I ever needed to set in the manual configuration was Network Name, Encryption Type (like WEP or WPA), password, and in the box below password I chose DHCP. I never set any other settings than those. (except turning off roaming of course)

Even though the computer guy knows nothing about linux he might be able to choose the correct settings (like network name and encryption type), but he probably doesn't know how to set up ndiswrapper and how to blacklist rtl8187, so if you choose to reinstall you should probably do this for him. Also, to make sure ndiswrapper is set up correctly, first use the command ```
lsmod
``` to check if ndsiwrapper is loaded. If it's listed then it's loaded.
Second, to see if the driver is installed correctly, use this :```
ndiswrapper -l
``` It should say something about that your driver is installed and that hardware/device is present.

---

### Post by ThePinkWitch on 2008-02-05
> **sennep said:**
> lol:) I did that too at first, and I had no idea how to fix it, so I just reinstalled Ubuntu:lolflag:




If you don't know the password then you won't be able to set it up. Does this computer guy know the password?

I found the password it's cool :)

Yes the wireless option might disappear if you disable roaming, but you should be able to either choose or type in the name of the network you wish to connect to in manual configuration, just find the place that says Network Name or ESSID or SSID and type in the name of your network there. Network manager will loose it's ability to show whether or not you are connected when you set up a manual coniguration, this is also one of the reasons I use Wicd instead of Network Manager.

Where would I get Wicd?

I don't think you need to write anything on the DNS and Domain settings. The only things I ever needed to set in the manual configuration was Network Name, Encryption Type (like WEP or WPA), password, and in the box below password I chose DHCP. I never set any other settings than those. (except turning off roaming of course)

Even though the computer guy knows nothing about linux he might be able to choose the correct settings (like network name and encryption type), but he probably doesn't know how to set up ndiswrapper and how to blacklist rtl8187, so if you choose to reinstall you should probably do this for him. Also, to make sure ndiswrapper is set up correctly, first use the command ```
lsmod
``` to check if ndsiwrapper is loaded. If it's listed then it's loaded.
Second, to see if the driver is installed correctly, use this :```
ndiswrapper -l
``` It should say something about that your driver is installed and that hardware/device is present.

usage: ndiswrapper OPTION
-i inffile       install driver described by 'inffile'
-a devid driver  use installed 'driver' for 'devid' (dangerous)
-r driver        remove 'driver'
-l               list installed drivers
-m               write configuration for modprobe
-ma              write module alias configuration for all devices
-mi              write module install configuration for all devices
-v               report version information

where 'devid' is either PCIID or USBID of the form XXXX:XXXX,
as reported by 'lspci -n' or 'lsusb' for the card

This is what it says.

I actually reloaded Ubuntu for the THIRD time cos I keep stuffing up the settings. Last time I let the Network manager do it all automatically and it WORKED!!! ..for five minutes lol
I don't want to install network manager again so I'm going to see if I can find out how to reset everything to the beginning. I've stuffed the settings again trying to get it to work again. I'm getting tired of this :confused: Thanks so much for being so helpful =D>

---

### Post by ThePinkWitch on 2008-02-05
I actually reloaded Ubuntu for the THIRD time cos I keep stuffing up the settings. Last time I let the Network manager do it all automatically and it WORKED!!! ..for five minutes lol
I don't want to install network manager again so I'm going to see if I can find out how to reset everything to the beginning. I've stuffed the settings again trying to get it to work again. I'm getting tired of this :confused: Thanks so much for being so helpful =D>[/QUOTE]

I meant install Ubuntu again lol.

---

### Post by sennep on 2008-02-05
> **ThePinkWitch said:**
> usage: ndiswrapper OPTION
-i inffile       install driver described by 'inffile'
-a devid driver  use installed 'driver' for 'devid' (dangerous)
-r driver        remove 'driver'
**-l               list installed drivers**
-m               write configuration for modprobe
-ma              write module alias configuration for all devices
-mi              write module install configuration for all devices
-v               report version information

try that one, the "ndiswrapper -l". It should list installed drivers, in other words, it says if your driver is installed or not. Also, what is the output of ```
lsmod
```? Does it contain the word "ndiswrapper"? Also, does it contain the word "rtl8187"?



> **ThePinkWitch said:**
> 
I actually reloaded Ubuntu for the THIRD time cos I keep stuffing up the settings. Last time I let the Network manager do it all automatically and it WORKED!!! ..for five minutes lol
I don't want to install network manager again so I'm going to see if I can find out how to reset everything to the beginning. I've stuffed the settings again trying to get it to work again. I'm getting tired of this :confused: Thanks so much for being so helpful =D>

It worked for five minutes? that's interesting actually. This other guy called Shaggydavid managed to get his Wg111v2 running without ndiswrapper, he said it took a minute to connect and it would drop out occasionally, but all he had to do was to disconnect and reconnect, and it was fine again. Maybe you don't need ndiswrapper at all? I know his settings on the router were WEP 128bit, did you try to disconnect and reconnect when this happened? 

As for resetting your network settings, I'm not really sure how to do it, but I guess one could reset the config file manually. Hopefully someone else will see this thread and help us with that. What settings have you messed with?

---

### Post by ThePinkWitch on 2008-02-05
Hey it's working! For some reason I had to leave it on Network manager Auto with roaming enabled and it automatically did the settings and connected me. HOW COOL!!!! I'm on the net with Ubuntu afer 3 days messing with it lol. THANKYOU for all your help cos you helped me get the settings and stuff right :mrgreen:

---

### Post by sennep on 2008-02-05
:lolflag: I was just sitting here thinking, "we're never gonna figure this one out" and then you just figured it out all the sudden:) :lolflag:

May I be the first to say, WELCOME to Ubuntu with internet!:) It's so much better than Ubuntu without internet!

The first thing you should do is probably to go to Applications-->Add/Remove

Click the button called Preferences, and a box with lot's of settings should pop up, and somewhere inside that box you should enable Main and Universe, and restricted drivers, and regular updates and security updates.

---

### Post by ThePinkWitch on 2008-02-05
> **sennep said:**
> :lolflag: I was just sitting here thinking, "we're never gonna figure this one out" and then you just figured it out all the sudden:) :lolflag:

May I be the first to say, WELCOME to Ubuntu with internet!:) It's so much better than Ubuntu without internet!

Thanks It sure is :) 

The first thing you should do is probably to go to Applications-->Add/Remove

Click the button called Preferences, and a box with lot's of settings should pop up, and somewhere inside that box you should enable Main and Universe, and restricted drivers, and regular updates and security updates.

  K I'll do that
My Internet keeps dropping out but at least I have it. Thanks again for all your help.

---

