---
title: "Ubuntu on Powerbook G4 - Ca'nt use WPA"
date: 2006-07-07
forum: Apple PPC Users
---

### Post by marklid on 2006-07-07
Hi,

I have just installed Ubuntu 6.06 on  a Powerbook G4 and despite hours of trying this and that, I just can't get the option to use WPA to connect to my wireless network.](*,) 

I has the 'regular' Airport card i.e. I don't think it's the 'Extreme' version.

I have tried these instructions:
- sudo apt-get install wpasupplicant (might already be installed)
- (You might have to do a sudo apt-get update in order to fetch the newest metadata for apt-get)
- sudo apt-get install network-manager-gnome
- sudo gedit /etc/network/interfaces — Comment out everything but “lo” entries in that file
- Create a file called /etc/default/wpasupplicant, add entry ENABLED=0
- Reboot your system
- Left-click the network manager icon in Gnome and select your wireless network
- Follow the prompts for password, type, etc.

This gives me the network manager, in which I can see the SSID of my wireless network, but when i try and connect to my wireless network, it only gives my 3 options under the "Wireless Security" section:
WEP 128-bit Passphrase
WEP 64/128-bit Hex
WEP 64/128-bit ASCII

Can anyone PLEASE help, or point me in the right direction ?
I'm new to Linux and would really appreciate how to get this up and running.

Thanks.:D

---

### Post by robino on 2006-07-08
Hi, If you would have the original Airport (not extreme) you can stop all efforts since the original AIRPORT (not express) does [not support WPA.]("http://www.hpl.hp.com/personal/Jean_Tourrilhes/Linux/Linux.Wireless.drivers.802.11b.html#Airport")

But if you have a G4, there should be an airport extreme inside. In that case, I am not sure if WPA does or doensn't work already with Networkmanager.

According to [this extensive HowTo]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper"), WPA is supported.

This guide however says nothing about networkmanager with WPA and airport extreme. But you [should be able]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper#head-494fd4e0aada56fc459f20fa1ac6df1afcc73b12") to use wpasupplicant in the terminal.

---

### Post by marklid on 2006-07-08
Hi,

Thanks for your reply, although it isn't good news, as if I can't get WPA running under Linux I will unfortunately have to go back to OSX :( 

Is there any way of telling for sure if the card is a regular Airport or Airport Extreme ?
(I have wiped OSX from the machine so can't tell)

Thanks.

---

### Post by robino on 2006-07-08
It is very likely you have a extreme, since it is a G4. You can check this simple by seeing which drivers has been loaded. Type the following code in a terminal & check its output (this command is to check which kernel modules currently are loaded).

```
lsmod
```

Do you see:
[I]
bcm43xx               
ieee80211softmac       
ieee80211              
ieee80211_crypt [/I]        

Then you have Airport Extreme. If you see airport in that list, the module for the older Airport (b) has been loaded, pointing that you have the old Airport- which is very unlikely.

---

### Post by marklid on 2006-07-08
Damn - looks like it is the standard Airport card, as within the lsmod output is :

airport                 7808  0
orinoco                47348  1 airport
hermes                  9024  2 airport,orinoco


...so there's no way to get WPA working under Linux for this card ? :(

---

### Post by robino on 2006-07-08
The bad news is you cannot get WAP working indeed with the old Airport card under Linux. The good news is, that OSX doesnt support WPA neither since it is the card that doesn't support WPA.

You can always buy an USB or PCI-card that does support WPA and which does work with Linux. A good buy therefore would be cards that use [the ZD1211 chip]("http://zd1211.ath.cx/") since the module supports as well PowerPc.

Hope this helps.

---

### Post by marklid on 2006-07-08
The anoying this is that I *could* use WPA to connect to my network in OSX !

I wonder is there are any Windows drivers for the Airport that I could maybe use with ndiswrapper ?

I will have a look at the hardware in the list and see if I can pick somethign up fairly cheap...


Cheers for your help.

---

### Post by lorris on 2006-07-08
yeah, maybe you could provide the model number of your powerbook g4. I know that ibook G4 models all had extreme, but since this is a powerbook g4's they go back to the original TiBook in 2001. if you are using a later g4 powerbook model and you can get wpa working on mac osx, then it is definitely a linux related driver issue. check for airport extreme, the chipset that is using and digg until you come up with other users with the same problem. i'm sure you are not the only person that has run into this problem. you may also check for support under other os's like freebsd, netbsd and other linux distro's.

check out this site:

[http://www.apple-history.com/]("http://www.apple-history.com/")

and this specific link:

[http://www.apple-history.com/?page=gallery&model=pg4&performa=off&sort=date&order=ASC]("http://www.apple-history.com/?page=gallery&model=pg4&performa=off&sort=date&order=ASC")

you can also sort apple released products by date and model tabs on the right (Date,Family,Processor)

a little more info about the wireless card might help in tracking down the issue.

Ciao!

Lorris

---

### Post by lorris on 2006-07-08
you could also do a search for "NetworkManager and Airport Extreme: SUCCESS." . it seems someone has had success by not having wpasuppliciant installed. seems to conflict with the broadcom driver.

Ciao!

Lorris

---

### Post by marklid on 2006-07-08
Hi Lorris, thanks for your input.

Looking at the links, it seems to be this model
[http://www.apple-history.com/body.php?page=gallery&model=pg4_dvi&performa=off&sort=date&order=ASC](http://www.apple-history.com/body.php?page=gallery&model=pg4_dvi&performa=off&sort=date&order=ASC)

It is definitely a standard Airport card - I have just dismantled the machine to look !
As I mentioned above it definitely supports WPA as I was using it in OSX to connect to my network.

I will have a look around some alternative distros forums to see if I can find anything else...

---

### Post by jah on 2006-07-12
> **marklid said:**
> 

This gives me the network manager, in which I can see the SSID of my wireless network, but when i try and connect to my wireless network, it only gives my 3 options under the "Wireless Security" section:
WEP 128-bit Passphrase
WEP 64/128-bit Hex
WEP 64/128-bit ASCII



Hi there,

I have EXACTLY the same problem. I just installed Dapper on my G3 iBook, which has an original Airport card. WPA works just fine in OSX however i am having a lot of trouble getting it working on Linux.

I can see my base station just fine, however when i go to connect, it doesn't give me an option to use WPA - only WEP!

I have searched and searched however all the help seems to be specific to Airport EXTREME, rather than the ORIGINAL Airport.

I believe i am using the Orinoco driver, however i am a complete newb, and thus ANY help at all would be greatly appreciated.:)

---

### Post by marklid on 2006-07-12
Frustrating isn't it !
I'm afraid I'm no nearer to resolving this. 

I have moved over to using Kubuntu (much nicer appearance than the strange brown of Ubuntu). Using the KDE network manager gives my the option to choose WPA but this doesn't work as the driver doesn't support it for the normal Airport cards. 

I have searched all over the net but am no nearer to getting this working...

---

### Post by king_arthur on 2006-07-13
Yup, I can confirm that standard Airport supports WPA (and WPA2) encryption, no problem on OSX, that's what I am using right now.

I wonder where **robino** found this wrong and misleading information.

WPA however, is still a bit of dog with Ubuntu.
I have been trying for quite a while on several PC's as well but have surrendered to WEP once I realized it was simply becoming a matter of principle.

WEP is still better than nothing, and I have better things to do than spending countless hours in just getting WAP to work... :)

---

### Post by mikeym on 2008-04-05
Just thought I'd mention that I have the same issue. I also definitely have a G4. Also switched to WEP.

---

### Post by akaSG on 2008-04-05
I was having problems with WPA on my 12' Powerbook running 7.04.

Guidop told me about Wicd. I downloaded it from sourceforge. And within minutes I was wireless on Linux for the first time in 3 years.

Give it a try.

---

