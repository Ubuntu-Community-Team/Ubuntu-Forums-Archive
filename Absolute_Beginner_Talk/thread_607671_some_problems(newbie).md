---
title: "some problems(newbie)"
date: 2007-11-09
forum: Absolute Beginner Talk
---

### Post by Erotokritos on 2007-11-09
well first of all hello to everybody here. i finally made the big step to install ubuntu on my pc(version 7.10)(i also have windows xp). I knew that ubuntu is not the easiest OS for someone like me(not any programming experience at all) but i though i should give it a try and test my self.

and then all the problems came in :P

1) i face a problem when trying to connect to the internet. i actually can't install my modem(usb sagem fast 800-840)
2) i get a problem when i try to apply the full visual effects(it says that effects couldn't be enabled :S)
3)i don't have the new drivers for my graphics card( ATi x1600 series) and i don't know how to install them
4)well 3 are enough i think :P


so if anyone has enough time and patience to give me an answer, i would be really gratefull

oh and please write all the steps, cuz as i state at the beggining and at the title, i am a newbie and i don't know how to do stuff, so don't think that i know the commands of the terminal for example

---

### Post by Shinbu-Otaku on 2007-11-09
hello, and welcome!

the only 1 i might be able to help with is your graphics card (Although i have an Nvidia G-Force card i think it can apply to ATI aswell)

Basically, go to Administration > Restricted Driver Manager (Administration is found in one of the menus at the top of the screen, but i cant remember wat the menu is called...). Here it should show what drivers are 'restricted' on your installed hardware. *Hopefully* your graphics card will be on there. If you just click 'install drivers' it should download and install it for you. Once down press Ctrl+Alt+Backspace to restart your desktop and it should all work. If not, then maybe your card is not supported.

Hope that helps one of your problems :) (Although, this will only help once your modem is installed....sorry i cant help with tht though)

---

### Post by Trebaruna on 2007-11-09
And if you're lucky there will also be a restricted driver for your modem.

To elaborate on the visual effects: only with a 3d driver can Compiz (the software that does the effects) actually work. ATi requires restricted drivers for that. Since you say your card doesn't have those drivers, Compiz can't work, either. Solve the one, and the other should work.

---

### Post by Pumalite on 2007-11-09
[http://ubuntuforums.org/showthread.php?t=590272&highlight=ATI+x1600](http://ubuntuforums.org/showthread.php?t=590272&highlight=ATI+x1600)

---

### Post by Erotokritos on 2007-11-09
since i don't have internet in ubuntu how is it suposed to d/l and install the restricted drivers?

---

### Post by Erotokritos on 2007-11-09
any idea on how to installing my modem??? pleaseee

---

### Post by hyper_ch on 2007-11-09
if you download the dvd image then it will fetch the drivers from there.

You just need enough space to put the dvd image onto your harddisk. Download it in windows, then copy it (in ubuntu from the windows drive to your linux partition), then mount the dvd image and set the sources in apt to also use it).

---

### Post by yellowbread on 2007-11-09
For the modem problem, look here. [http://ubuntuforums.org/search.php?searchid=30921820]("http://ubuntuforums.org/search.php?searchid=30921820")

I found this by doing a search on "sagem".

---

### Post by FreewheelinFrank on 2007-11-09
> **Erotokritos said:**
> since i don't have internet in ubuntu how is it suposed to d/l and install the restricted drivers?

Good point. I had the same problem with a USB ADSL modem. In the end I found a utility which allowed me to connect, but your modem is different.

There seem to be similar utilities for your modem:

[http://atm.eagle-usb.org/wakka.php](http://atm.eagle-usb.org/wakka.php)

[http://freshmeat.net/projects/ueagle-atm/](http://freshmeat.net/projects/ueagle-atm/)

[http://sourceforge.net/projects/eagle-usb/](http://sourceforge.net/projects/eagle-usb/)

Somebody with the same problem as you here:

[http://ubuntuforums.org/showthread.php?t=55677](http://ubuntuforums.org/showthread.php?t=55677)

In the end I got fed up with the USB ADSL modem and bought a router: an ethernet connection is hassle free. I wish Ubuntu would address this issue: not many users are going to try Ubuntu, find their modem doesn't work and go out and buy a new modem or router just to use Ubuntu.

When you do get a connection, install the restricted driver, then if you want desktop effects, go to synaptics and install xserver-xgl. (Your screen mayl go black for a short time when Ubuntu boots, but desktop effects work- I'm guessing this black screen is why it's not used by default.)

I have the ATi x1600 series myself- I've heard new and improved drivers are on the way, so maybe desktop effects will be enabled by default soon anyway.

---

### Post by Erotokritos on 2007-11-09
there isn't any other way to obtain the restricted drivers,  without connecting to the internet?

---

### Post by hyper_ch on 2007-11-09
did you read my post?

---

### Post by FreewheelinFrank on 2007-11-09
This may help:

[https://help.ubuntu.com/community/UsbAdslModem/ueagle-atm#head-b0787f02ebeee3fc70ff8abfaae2ddc8183f0faf](https://help.ubuntu.com/community/UsbAdslModem/ueagle-atm#head-b0787f02ebeee3fc70ff8abfaae2ddc8183f0faf)

Not sure how it will work in 7.10: 7.10 broke my USB ADSL connection.

An alternative would be to get hold of an ethernet ADSL modem: a lot of people have them lying round unused after they buy a wireless router. Ask around or look on eBay: I saw some going for £1.50 when I had my connection problems. In the end I got a wireless router, as I have a laptop with wireless anyway.

---

### Post by Erotokritos on 2007-11-09
> **hyper_ch said:**
> did you read my post?
yes but i didn't quite understand it :P

---

### Post by rubicon on 2007-11-09
You could DL packages (frankly say, almost all things you need for your ubuntu is packages ;) ) here: [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

Just select your distributive and enter package name to search.

---

### Post by Erotokritos on 2007-11-09
using wine is an option?

---

### Post by Pumalite on 2007-11-09
[https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows](https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows)

---

### Post by rubicon on 2007-11-09
> **Erotokritos said:**
> using wine is an option?
Erm... Option for what? 

If you want to use Wine to access your modem (ADSL, right?), then you probably will be dissapointed, because Wine can't use WinXP drivers (no Windows drivers at all, except some for printers... fix me if I forgot something). 

But it is a good thing to just use Windows programs inside of your Ubuntu!

---

### Post by Erotokritos on 2007-11-09
> **rubicon said:**
> Erm... Option for what? 

If you want to use Wine to access your modem (ADSL, right?), then you probably will be dissapointed, because Wine can't use WinXP drivers (no Windows drivers at all, except some for printers... fix me if I forgot something). 

But it is a good thing to just use Windows programs inside of your Ubuntu!
damn :@ 

so the only thing i can do with my knowledge is actually go buy a router ?

---

### Post by FreewheelinFrank on 2007-11-09
> so the only thing i can do with my knowledge is actually go buy a router ?

Did you try this from the link I posted above?

> Setting up the modem

   1.  First of all you need to download the modem firmware from [WWW] here (use another computer which has Internet access and transfer the file on Ubuntu with a cd/dvd/usb pen/whatever).
   2. Start Ubuntu and plug your modem.
   3.  Let's say you saved the file, mentioned above, on your "home" folder (/home/username). Open a Terminal(console) and enter this:

      $ tar -xvzf ueagle-data-1.1.tar.gz 
      $ sudo mkdir /lib/firmware/ueagle-atm
      $ cd  ueagle-data-1.1/
      $ sudo cp -a * /lib/firmware/ueagle-atm

      This extracts the firmware files and copies them to the appropriate location.

[Step 4 is not for Ubuntu 7.10]

   5.  Now UNPLUG your modem, wait a few seconds and PLUG it again. After a few seconds(maybe 20-30seconds) the lights on the modem should start to flash and then stay on after a while. If this doesn't happen then you should restart your computer.
   6. To configure your connection scroll down to the title "Configuring The Connection" or click [WWW] here.

I can't tell you if it will work because I didn't have the same modem, however, it's not a difficult procedure to follow, although I appreciate it could be off-putting when you're new to Ubuntu, and could appear to be more difficult than it is if you don't have a lot of experience. 

You should at least try it and see if it works.

I share your frustration with the attitude of Ubuntu to USB ADSL modem users: my CD of Ubuntu 6.06 sat on my shelf unused for a year because it wouldn't work with my modem.

The only reason I started to use Ubuntu was that somebody wrote a simple utility to get my modem working:

[http://ubuntuforums.org/showthread.php?t=585647](http://ubuntuforums.org/showthread.php?t=585647)

I imagine there are many more Ubuntu CD's sitting on shelves because modems don't work. Telling people they should really get a new modem if they want to use Ubuntu is not going to inspire converts.

---

### Post by Erotokritos on 2007-11-10
> **FreewheelinFrank said:**
> Did you try this from the link I posted above?



I can't tell you if it will work because I didn't have the same modem, however, it's not a difficult procedure to follow, although I appreciate it could be off-putting when you're new to Ubuntu, and could appear to be more difficult than it is if you don't have a lot of experience. 

You should at least try it and see if it works.

I share your frustration with the attitude of Ubuntu to USB ADSL modem users: my CD of Ubuntu 6.06 sat on my shelf unused for a year because it wouldn't work with my modem.

The only reason I started to use Ubuntu was that somebody wrote a simple utility to get my modem working:

[http://ubuntuforums.org/showthread.php?t=585647](http://ubuntuforums.org/showthread.php?t=585647)

I imagine there are many more Ubuntu CD's sitting on shelves because modems don't work. Telling people they should really get a new modem if they want to use Ubuntu is not going to inspire converts.
did nothing. oh nvm i will buy a router :/

---

### Post by FreewheelinFrank on 2007-11-10
Make sure it has a built in ADSL modem.

I don't know where you live, but here in the UK you can find an ethernet ADSL modem from £0.99 on eBay. OK, so postage is £5.00, but if you lived near the seller you could just pick it up. 

[http://cgi.ebay.co.uk/ADSL-Ethernet-Modem-Aztech_W0QQitemZ220168202292QQihZ012QQcategoryZ62025QQssPageNameZWDVWQQrdZ1QQcmdZViewItem](http://cgi.ebay.co.uk/ADSL-Ethernet-Modem-Aztech_W0QQitemZ220168202292QQihZ012QQcategoryZ62025QQssPageNameZWDVWQQrdZ1QQcmdZViewItem)

[http://cgi.ebay.co.uk/TALK-TALK-SmartAX-MT882-ADSL-broadband-modem-BNIB_W0QQitemZ160176623394QQihZ006QQcategoryZ62025QQssPageNameZWDVWQQrdZ1QQcmdZViewItem](http://cgi.ebay.co.uk/TALK-TALK-SmartAX-MT882-ADSL-broadband-modem-BNIB_W0QQitemZ160176623394QQihZ006QQcategoryZ62025QQssPageNameZWDVWQQrdZ1QQcmdZViewItem)

These modems are supplied free by broadband ISP's, then people get a wireless router and have then lying around. Check on eBay or ask around.

ADSL routers seem to go for about £30 wired/£50 wireless here in the UK- they have the advantage of a built in firewall as well, although not everybody wants to spend that sort of money just to use Ubuntu.

---

### Post by Erotokritos on 2007-11-10
> **FreewheelinFrank said:**
> Make sure it has a built in ADSL modem.

I don't know where you live, but here in the UK you can find an ethernet ADSL modem from £0.99 on eBay. OK, so postage is £5.00, but if you lived near the seller you could just pick it up. 

[http://cgi.ebay.co.uk/ADSL-Ethernet-Modem-Aztech_W0QQitemZ220168202292QQihZ012QQcategoryZ62025QQssPageNameZWDVWQQrdZ1QQcmdZViewItem](http://cgi.ebay.co.uk/ADSL-Ethernet-Modem-Aztech_W0QQitemZ220168202292QQihZ012QQcategoryZ62025QQssPageNameZWDVWQQrdZ1QQcmdZViewItem)

[http://cgi.ebay.co.uk/TALK-TALK-SmartAX-MT882-ADSL-broadband-modem-BNIB_W0QQitemZ160176623394QQihZ006QQcategoryZ62025QQssPageNameZWDVWQQrdZ1QQcmdZViewItem](http://cgi.ebay.co.uk/TALK-TALK-SmartAX-MT882-ADSL-broadband-modem-BNIB_W0QQitemZ160176623394QQihZ006QQcategoryZ62025QQssPageNameZWDVWQQrdZ1QQcmdZViewItem)

These modems are supplied free by broadband ISP's, then people get a wireless router and have then lying around. Check on eBay or ask around.

ADSL routers seem to go for about £30 wired/£50 wireless here in the UK- they have the advantage of a built in firewall as well, although not everybody wants to spend that sort of money just to use Ubuntu.
i live in greece. i found this :[http://www.e-shop.gr/show_per.phtml?id=PER.612319](http://www.e-shop.gr/show_per.phtml?id=PER.612319)

check out it's characteristics(the bold letters)

the page might be in greek but the char. are in english(ofc)

---

### Post by FreewheelinFrank on 2007-11-10
I don't see any mention of an ADSL modem.

Here are some TP-Link products which* do* include a modem.

[http://www.tp-link.com/products/adsl.asp](http://www.tp-link.com/products/adsl.asp)

I picked up a router without a modem and had to take it back to the shop. :oops:

CABLE/DSL is *not* what you want.

I found this on the site you linked to:

[http://www.e-shop.gr/show_per.phtml?id=PER.613542](http://www.e-shop.gr/show_per.phtml?id=PER.613542)

EDIT: on second look, this seems to be just a modem. OK if you're just connecting one computer, but I don't think it is a router, nor does it have a built in firewall. I reckon a modem/router with built-in firewall would be a better investment.

Unfortunately, routers with an ADSL modem are more expensive.

---

### Post by Pumalite on 2007-11-10
DSL should give you a modem. You get a router ant put it between that modem and your computer.

---

### Post by Erotokritos on 2007-11-10
> **FreewheelinFrank said:**
> I don't see any mention of an ADSL modem.

Here are some TP-Link products which* do* include a modem.

[http://www.tp-link.com/products/adsl.asp](http://www.tp-link.com/products/adsl.asp)

I picked up a router without a modem and had to take it back to the shop. :oops:

CABLE/DSL is *not* what you want.

I found this on the site you linked to:

[http://www.e-shop.gr/show_per.phtml?id=PER.613542](http://www.e-shop.gr/show_per.phtml?id=PER.613542)

EDIT: on second look, this seems to be just a modem. OK if you're just connecting one computer, but I don't think it is a router, nor does it have a built in firewall. I reckon a modem/router with built-in firewall would be a better investment.

Unfortunately, routers with an ADSL modem are more expensive.
thanks m8. i hope it will do the trick. once i get it i will inform you :D

---

### Post by FreewheelinFrank on 2007-11-10
Please shop around and ask questions before you buy. I can't tell you from here what's on offer in Greece or appropriate to your ISP. 

I just linked to the first thing I found on the website you linked to which seemed vaguely suitable. Bear in mind I don't understand Greek or have any idea about good-value computer hardware stores in Greece.

A modem is about £25, a router £30, a router plus modem £40,  wireless router plus modem £60.

You will find special offers available in different shops: I saw a router plus modem for £30, and picked up a wireless router with modem for £50. No point buying a modem for £25 and a router for £30 when you could've got a wireless router with modem for less.

---

### Post by rubicon on 2007-11-14
Hey, Erotokritos, have you managed to get connected to internet in ubutnu yet?

Well, I had same problem - USB ADSL winmodem. But I found a way to get this working :) Though, not so easy. :)

What have I done so far:
1. Installed VirtualBox (not OSE version from archive.ubuntu.org, i downloaded package directoly from innotek site)
2. Set Windows XP in VirtualBox
3. Enabled usbfs ([http://michael-prokop.at/blog/2007/07/11/virtualbox-usb/](http://michael-prokop.at/blog/2007/07/11/virtualbox-usb/))
4. Allowed my usb modem to be "visible in guest operation system" in VirtualBox
5. Boot up Windows XP, installed my drivers for Acorp Sprinter@ADSL
6. Got connected from Windows :)

I don't know (too lazy to look it up) how to make Ubuntu use this connection in Windows. Maybe, if you decide to try my method, someone will instruct us what to do :lolflag:

---

### Post by rubicon on 2007-11-21
Managed to do it!

- To use internet connection established in VirtualBox (Windows XP) in Ubuntu, set up a NAT network interface from VirtualBox machine settings. 
- Then install some proxy-server in VirtualBox.
- Look into help for 'port-forwarding', it may look hard to understand at first, but that is not actually so :)
- Port-forward from 8080 to 8080 (that was default ports in proxy-server, so you may notice it is differs for your proxy-server).

Okay. Now you can use proxy server by setting it in programs. 
For instance, Synaptic. Just type 127.0.0.1:8080 in 'Proxy-server' (or something like that - I have localized version, but I hope you'll understand what all that mean :) ).

Hope somebody will read this thread and find it useful :D

---

