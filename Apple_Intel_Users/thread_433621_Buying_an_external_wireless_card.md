---
title: "Buying an external wireless card"
date: 2007-05-05
forum: Apple Intel Users
---

### Post by The_Giver on 2007-05-05
Is there any external card out there that will gurantee me wireless in ubuntu? I'm kind of getting fed up with this wireless card issue.... it should just work =(


Edit: This is for the macboook pro! C2D

---

### Post by jakev383 on 2007-05-05
I agree that it should just work. But it doesn't.
I've had extremely good experiences with anything by Oorinco or Proxim (same card). And if you look at them don't worry about the Silver/Gold stuff. You won't be using those functions anyway. Those are Atheros based, so if you can find a card that uses that chipset you should be pretty good.
I've also gotten older Linksys cards to work - I haven't tried an external wireless card in 2 years, so I can't speak for anything off the shelf.
I got an internal Intel 2100 (and 2200) to work, but I had to use ndiswrapper to get it to work. For the 2100 I also got driverloader to work extremely well.
Umm... Last one I can think of is an older Linksys USB adapter that I got to work rather well.
I know that's all dated, but hopefully it will help some.

---

### Post by The_Giver on 2007-05-05
This is for the macbook pro btw


Thanks!

---

### Post by jakev383 on 2007-05-05
Sorry! I was just trolling the New Posts tab looking for unanswered posts that I could help with. Teach me to post before coffee!
:confused:

---

### Post by The_Giver on 2007-05-05
It's okay...

Anyway... here is some more info... hopefullly someone can help some:


On OsX I can pull the following info (for a brand new C2D):


  Wireless Card Type:    AirPort Extreme  (0x168C, 0x87)
  Wireless Card Locale:    USA
  Wireless Card Firmware Version:    1.0.47


Anyone with the same specs get the wireless to work (mine doesnt even show under ifconfig ... and there is no encryption on the network).

---

### Post by Chrisj303 on 2007-05-05
I asked about this a while back, but didn't receive an answer. I see no reason why if an external device works with a PC running Linux, why it wouldn't with a Mac.

Look at this list : [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

If a soloution to the Airport issue isn't found soon, then i will definitley try one of these, after all they only cost a few quid - and if it gets me encrypted wireless, thats all i care about!

chrisj303

---

### Post by Chrisj303 on 2007-05-05
Bump,

Sorry but i *really* want a response to this - i know it sounds like giving up, but i would rather just get a USB wireless adapter until there is a better soloution with the Airport cards.

---

### Post by ronocdh on 2007-05-05
> **Chrisj303 said:**
> Bump,

Sorry but i *really* want a response to this - i know it sounds like giving up, but i would rather just get a USB wireless adapter until there is a better soloution with the Airport cards.
Hm, you might be right about this. I've actually considered just flipping back to Edgy, though, because under Edgy it was a totally trivial ndiswrapper procedure with the NET5416 drivers to get wireless working. I sure as heck had WEP everywhere I went, too (never tested WPA).

*mimes weighing action with both hands*

---

### Post by Chrisj303 on 2007-05-05
I couldn't even get wi-fi under edgy with the NET5614 drivers!

Can you see any reason why a USB adapter, that is known to work with a PC wouldn't work with a Mac. I mean, thats really all the intel models are after all?

---

### Post by ronocdh on 2007-05-05
> **Chrisj303 said:**
> I couldn't even get wi-fi under edgy with the NET5614 drivers!

Can you see any reason why a USB adapter, that is known to work with a PC wouldn't work with a Mac. I mean, thats really all the intel models are after all?
I can't, actually; it should largely bypass the hardware with which we are having trouble. What's your specific hardware info, e.g. wireless chipset and stuff?

---

### Post by Chrisj303 on 2007-05-05
Macbook c2d - i assumed that there was only model/chipset for the airport cards fitted. But if i were to use an external USB adapter, it wouldn't matter, surely.

The way i see it, is that if i take away OSX froim this machine then it is basically just a PC. If i were to pick up a known PC compatible adapter it *should* work (shouldn't it?!)

---

### Post by ronocdh on 2007-05-05
> **Chrisj303 said:**
> Macbook c2d - i assumed that there was only model/chipset for the airport cards fitted. But if i were to use an external USB adapter, it wouldn't matter, surely.

The way i see it, is that if i take away OSX froim this machine then it is basically just a PC. If i were to pick up a known PC compatible adapter it *should* work (shouldn't it?!)
Yeah, should. Hypothetically. Either way we're talking a [$15 investment]("http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&DEPA=0&Description=usb+wireless+adapter&x=0&y=0") to test, you know? I'm saving up for a sick new camera from Newegg, maybe place an order in a week or three. If you beat me to it, let us know how it goes.

I have a busy weekend but by the weeknights I should have a chance to wipe Ubuntu and try yet again for wireless. I mean, there's *got* to be a reliable method!

---

### Post by The_Giver on 2007-05-05
Damn I even have Beryl working now =/ 

If I could only find either a guide.... or someone who has gotten this to work already with my specific model.... and a  USB card... I would order it right now !!!!!  


Again I can only get this info from OS X


  Wireless Card Type:    AirPort Extreme  (0x168C, 0x87)
  Wireless Card Locale:    USA
  Wireless Card Firmware Version:    1.0.47


While others get:


Wireless Card Firmware Version: Broadcom BCM43xx 1.0 (4.80.79.1)

Could someone explain what that is and what this might mean???


For the people still having problems would you mind looking under system profiler in osx for this info (its under Network/Airport)

THANKS

---

### Post by Chrisj303 on 2007-05-05
> **The_Giver said:**
> Damn I even have Beryl working now =/ 

If I could only find either a guide.... or someone who has gotten this to work already with my specific model.... and a  USB card... I would order it right now !!!!!  


Again I can only get this info from OS X


  Wireless Card Type:    AirPort Extreme  (0x168C, 0x87)
  Wireless Card Locale:    USA
  Wireless Card Firmware Version:    1.0.47


While others get:


Wireless Card Firmware Version: Broadcom BCM43xx 1.0 (4.80.79.1)

Could someone explain what that is and what this might mean???


For the people still having problems would you mind looking under system profiler in osx for this info (its under Network/Airport)

THANKS

Mine :  
  Wireless Card Type:	AirPort Extreme
  Wireless Card Locale:	Worldwide
  Wireless Card Firmware Version:	1.0.27p3


But this isn't telling us the chipset - the vital clue, and no i don't know how to find that out.!

I'm in the UK - that might make a difference (?)...

I'm going to buy a card - whatever one i can get my hands on locally, that fits the guide that i linked earlier best.
Whenever i buy stuff from there ("PC World") i let them know prior to purchase that i need it for OSX/Linux, and if dosen't work i'm getting an exchange or money back:mad: . - so i'm not going to lose anything!

I'll post back the results, good or bad.

---

### Post by The_Giver on 2007-05-05
Hey try to follow this guide by Tyrdium (if you have tried this before it will ask you to remove the old install.. trype in "r" to accept this: 


sudo aptitude install build-essential
sudo aptitude install subversion
svn co [http://svn.madwifi.org/branches/madwifi-hal-0.9.30.10](http://svn.madwifi.org/branches/madwifi-hal-0.9.30.10)
cd madwifi-hal-0.9.30.10
make
sudo make install
sudo modprobe ath_pci
sudo modprobe wlan_scan_sta
sudo wlanconfig ath0 list scan (scan for APs) 


//optional

sudo iwconfig ath0 essid "foo" (connect to open AP "foo") //  I personally, the giver... tried this up to this command and it worked.. i cheked ifconfig and it was all there!!!
sudo dhclient ath0 (get IP address from DHCP)
Etc., according to guide: [http://madwifi.org/wiki/UserDocs/FirstTimeHowTo](http://madwifi.org/wiki/UserDocs/FirstTimeHowTo)



Now it works (but I haven't really tried WPA)....

---

### Post by Chrisj303 on 2007-05-05
> **The_Giver said:**
> Hey try to follow this guide by Tyrdium (if you have tried this before it will ask you to remove the old install.. trype in "r" to accept this: 


sudo aptitude install build-essential
sudo aptitude install subversion
svn co [http://svn.madwifi.org/branches/madwifi-hal-0.9.30.10](http://svn.madwifi.org/branches/madwifi-hal-0.9.30.10)
cd madwifi-hal-0.9.30.10
make
sudo make install
sudo modprobe ath_pci
sudo modprobe wlan_scan_sta
sudo wlanconfig ath0 list scan (scan for APs) 


//optional

sudo iwconfig ath0 essid "foo" (connect to open AP "foo") //  I personally, the giver... tried this up to this command and it worked.. i cheked ifconfig and it was all there!!!
sudo dhclient ath0 (get IP address from DHCP)
Etc., according to guide: [http://madwifi.org/wiki/UserDocs/FirstTimeHowTo](http://madwifi.org/wiki/UserDocs/FirstTimeHowTo)



Now it works (but I haven't really tried WPA)....

The WPA is what i'm having issues with - i can connect to an unencrypted network no problem - if you can test it with WPA, please do and let us know how it goes!

---

### Post by ronocdh on 2007-05-05
> **Chrisj303 said:**
> Mine :  
  Wireless Card Type:	AirPort Extreme
  Wireless Card Locale:	Worldwide
  Wireless Card Firmware Version:	1.0.27p3


But this isn't telling us the chipset - the vital clue, and no i don't know how to find that out.!
Chipset, you mean **sudo update-pciids** and **lspci**? That should give you what you need to know.

---

### Post by The_Giver on 2007-05-05
Unfortunately, I do not have access to one at the moment (at University.. and they use some other method for security)...

---

### Post by ronocdh on 2007-05-05
> **The_Giver said:**
> Unfortunately, I do not have access to one at the moment (at University.. and they use some other method for security)...
My university actually still uses WEP with a shared key, although they do force authentication by MAC. Most other universities with a competent IT department use a VPN or something, which would allow me to connect from a friend's laptop, but I suppose that's just what my school is trying to avoid, as we're in an urban environment. Oh well. 

Sorry to post off-topic! I was interested in all the setups you guys have, as I have been seeing a lot of gripes about lack of WPA. I triple boot, and WinXP sucks with WPA, so my WAP in my apartment actually is set to 128 WEP. =/ I live in a very nice residential neighborhood though, so I'm not worried about some little script kiddie hacking me and stealing my Pure Pwnage episodes. ;)

---

