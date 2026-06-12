---
title: "Open Network Works, WEP Does Not"
date: 2007-05-16
forum: Absolute Beginner Talk
---

### Post by acidbaby on 2007-05-16
I have just installed Ubuntu 7.04 on a PC with a Netgear WG511 wireless card. My wireless router is an Airport Extreme Base Station and my security was originally set to WEP. When I first installed Ubuntu, all of the networks that normally appear appeared in the drop down but when I chose mine I got this error:

Error Connecting To Wireless Network
The requested wireless network requires security capabilities unsupported by your hardware

So I took off the security from my network, refreshed the list and it connected no problem. But now I have an open network which is not good.

If I go to my neighbors secured network from the list it pops up with the dialog box to enter the network key instead of the error message so my guess is with the Airport base station.

This is my first time working with Linux so please bear with me. If anyone has a recommendation it would be greatly appreciated. Thanks.

---

### Post by 3rr0r on 2007-05-16
You should try setting up your card with your home network WEP key before you try to connect.  That worked for me.  Try both the HEX and ASCII, I have 2 routers and one of them only works with the ASCII key, while the other only accepts the Hex value.  Wierd, I know.

---

### Post by acidbaby on 2007-05-16
Thanks. However, I tried setting them up manually with each and I still get the same error message.

---

### Post by ugm6hr on 2007-05-16
Just a thought - does the network card connect to your Airport with WEP from any other OS (from the same location)?  

The reason I ask, is that sometimes this can be caused by wireless interference (i.e. a neighbour is using a similar frequency on their network).  The fact that it allows you to try and connect on a neighbour's network rather than your own (presumably nearer) wireless router is similar to a problem encountered by a friend with an Apple Airport.  So it might be worth trying to reconfigure your Airport on a different frequency and trying to connect again.  The other way to check if this is the problem is to try moving the router right next to your computer, and see if it manages to connect.  

If it doesn't work, sorry to have wasted your time  :(

---

### Post by dannyboy79 on 2007-05-16
> **3rr0r said:**
> You should try setting up your card with your home network WEP key before you try to connect.  That worked for me.  Try both the HEX and ASCII, I have 2 routers and one of them only works with the ASCII key, while the other only accepts the Hex value.  Wierd, I know.

i have a question. I have the WGT624 netgear wireless G router and I have it set to WEP 128bit. I type in a passphrase and it then generates 26 numbers and letters. i take that 26 numbers and letters and enter it into the wep settings for the netgear wg511t on my laptop running xubuntu fiesty and it works fine.

the problem is, I couldn't get my roommates laptop to work using the same wep key? he has the intel wireless pro something or other wireless tool on his laptop and it doesn't show my network originally because I have ssid broadcast off but when I start configuring it and I enter hte ESSID and I hit connect, it finds it and states that it has basic WEP protectiono on and that I need to enter either a 13 character ASCI password or 26 character Hex password, well after I enter all the 26 characters it still will not connect to matter what I do. I have tried using Windows Wireless Zero config or whatever it's called. I believe the Interl Wireless PRo tool was set at Open but I think I could have tried shared but it doesn't say anything about that withint he netgear rouuter wireless settings. 

since I already have 26 characters, how do I make the intel wireless pro thingy work on my network? I hahve tried entering "0x" or "x0" before the 26 characters but as soon as I get to the 13 character when I used the 0x or x0, it brings up an error stating that it has to be either 13 or 26 and that's before I even got to the 26 character. Do you have any suggestions to get other hardware manufactures wireless cards connected to my Netgear WEP network?

---

### Post by pigboy306 on 2007-05-16
As an aside I have an ACER TM2200 it has a wifi card in i have installed Ndiswrapper and got the card recognised, but for the love of god it will not connect to my WIFI network with it's 26charachter Hex security.
 Windows no problems with connecting....

---

### Post by acidbaby on 2007-05-16
When it was running Windows in the same location it would connect to the network with WEP enabled no problem. I did have problems getting it to recognize the key on Windows a while back and found out the solution was that the key had to be 13 characters exactly. With the Airport Extreme, it only gives the option of a 13 character key now.

Also I did read about ndiswrapper, but I didn't think that would apply to this situation since the card is recognized by the system and is functioning. Just not completely.

---

### Post by pigboy306 on 2007-05-16
I am just after some help my wife to be is thinking about the marriage now ..fourth night of trying to get WIFI working

---

### Post by dannyboy79 on 2007-05-16
> **pigboy306 said:**
> I am just after some help my wife to be is thinking about the marriage now ..fourth night of trying to get WIFI working


well I would say that if we want help with our problems we should create our own thread as we are all kind of hijacking this guys thread.

---

### Post by dannyboy79 on 2007-05-16
> **acidbaby said:**
> I have just installed Ubuntu 7.04 on a PC with a Netgear WG511 wireless card. My wireless router is an Airport Extreme Base Station and my security was originally set to WEP. When I first installed Ubuntu, all of the networks that normally appear appeared in the drop down but when I chose mine I got this error:

Error Connecting To Wireless Network
The requested wireless network requires security capabilities unsupported by your hardware

So I took off the security from my network, refreshed the list and it connected no problem. But now I have an open network which is not good.

If I go to my neighbors secured network from the list it pops up with the dialog box to enter the network key instead of the error message so my guess is with the Airport base station.

This is my first time working with Linux so please bear with me. If anyone has a recommendation it would be greatly appreciated. Thanks.

acidbaby, you need to find out what exactly the airport extreme is looking for, the asci text password or the 26 hex password. I have the wg511t and it uses the hex key and all I have to do is add to my /etc/network/interfaces file at the end. when I get home I'll let you know the exact words to put and how it should be added so that it works for ya btu like I said, you'll need to find out what the extreme is requiring from you. whether it's the 13 asci or the 26hex wep key. have you tried out wifi-radar? it may have a little better of a gui for connecting to secured networks. good luck

---

### Post by gt24 on 2007-05-17
This thread may help if you have a WG511 v1 card... but it is more-so for connecting to WPA networks.

[http://ubuntuforums.org/showthread.php?t=421526](http://ubuntuforums.org/showthread.php?t=421526)

In general, this card does not like Gnome Network Manager when it comes to WPA networks.  I was able to get it to connect to a WEP network with no issues with the Gnome Network Manager and without doing anything special, so I'm not sure what your problem is.  The built in drivers are somewhat faulty and need stronger access points to connect reliably.  In that thread, there is a procedure where you replace the drivers with windows drivers to eliminate the stability issues and then there is a procedure to set up a variety of approaches... being wpa_supplicant, Wifi Radar, or WICD... to allow your card to work smoothly.

Yes, there is huge differences between each Netgear WG511 card version, so make sure your card has NO version number on the bottom (the v1 card doesn't state this, the v2 card has "v2" written on the bottom, and so on).  If it is a v1 card, try that link above.

---

