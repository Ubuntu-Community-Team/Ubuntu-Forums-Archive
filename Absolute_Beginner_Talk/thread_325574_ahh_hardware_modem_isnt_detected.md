---
title: "ahh hardware modem isnt detected"
date: 2006-12-26
forum: Absolute Beginner Talk
---

### Post by nite owl on 2006-12-26
Ok I've gone out of my way after I found out my old modem was a winmodem to buy a hardware modem(USR 56k courier...which says 3com????) which is for my dial-up connection. I also previously didnt have a serial port(only USB's) connection for my computer so I went out and bought a pci dual serial card and just put it into one of my PCI ports on my motherboard. Anyway long story short when i go to administration>networking>modem>auto-detect....It cant detect any modem?????Same goes when I installed gnome-ppp and used the auto-detect option on that to. Is there anything I could possibly do to make this work???(upgrade to edgy?, install another program?, a problem with my installation of my pci card becuase all I have done is put it in and I'm assuming it will automatically pick up the card without doing anything else????) Thanks....:(

---

### Post by nite owl on 2006-12-26
Anyone at all??...lol this has been such a problem for me I really want Linux to work for me because I really agree with everything it stands for....but its becoming very hard

---

### Post by Sef on 2006-12-26
For your modem, have you checked [linmodems]("http://linmodems.org") to see if you can get it to work under Linux?

---

### Post by nite owl on 2006-12-26
It's a hardware serial modem!!! could upgrading to edgy possibly fix this ???

---

### Post by Duck2006 on 2006-12-26
Did you look in your BOIS to see if you have your serial ports "onboard" turned on? Just because you don't have ports on the back of your system, does not mean they are turned off in your BOIS.
All motherboards have serial ports. If your onboard ports are turned on then your card will not work.

---

### Post by ieee488 on 2006-12-26
Are you dual-booting with Windows on this PC? Because if you were, then you could see if the serial PCI board was working.

Anyway, I agree that it could be the serial card that is not working with Ubuntu.

My favorite way of detecting modems is to run the command **sudo wvdialconf** in a Terminal box. I've had hit-or-miss luck with the auto detect stuff, but wvdialconf always works and that's with 2 laptops and 1 desktop.

---

### Post by nite owl on 2006-12-26
Im not dual booting......and there was an option i found in the BIOS that said 'on board port 1' so i disabled it..still no luck but then again I might not have diabled what i needed to??

---

### Post by _duncan_ on 2006-12-26
the past 3 versions of Ubuntu (breezy 5.10, dapper 6.06 and now edgy 6.10) all can't autodetect my US Robotics 56k faxmodem, but I can still use it to dial-up as long as I point the dialer program (wvdial, gnome-ppp, etc) to the correct serial port. In my case it was /dev/ttyS0.

I don't know what port your modem is connected to since I'm unfamiliar with pci dual serial cards, but if you can find out what it is, you stand a good chance of dialing out even if the modem is not autodetected.

I can sense your frustration trying to get on-line with linux. Just hang in there nite owl. It took me 3 months to finally get dial-up connectivity when I first started with linux.

---

### Post by Bartender on 2006-12-26
> **Duck2006 said:**
> All motherboards have serial ports. If your onboard ports are turned on then your card will not work.
 
Modern laptops have pretty much abandoned serial and desktop PC's are rapidly dumping serial too.  It's almost like evolution, as unused parts wither and fade away.  

My ASUS P5GDC-V motherboard, about 3 years old now, included a bank of serial pins on the motherboard and a serial connector on a little plate with a ribbon cable that could be placed in an unused PCI card opening.  But there were no serial connectors on the main motherboard backplane, where the mouse/keyboard/ etc. ports are located.

Hey, wait a minute, this might work for the OP - can you find a manual for your motherboard?  Is there a set of pins on the board for serial?  If so, all you'd have to do is round up one of those little plates that have a ribbon cable and a serial receptacle to get a serial plug on the back of the PC.  That way you'd be running serial natively instead of thru a PCI adapter.

I'd guess that it's either the PCI adapter that's stopping you (Ubuntu doesn't know what it is) or the external modem you scrounged up is broken.  Can you take the external to another PC (probably easier on a Windows PC) and try to get it working?  I'd want to make sure the modem wasn't broken before spending any more time/money on this project.  Can you post the exact model number off the back?  Mine is a 5686-03, model 0701.  If I remember correctly W2K recognized the modem without having to download drivers.

Another reason to try and get it working on a Windows PC - if you can connect to the internet with a Windows PC, go to the USR website, find the support page for your modem, then download the "Stand-alone Flasher" utility and flash the modem to the latest firmware.  It's a very straightforward operation.

They even have a Linux Stand Alone Flasher utility, but I haven't tried that.

EDIT: USR & 3COM merged a few years back

---

### Post by tagginannie on 2006-12-26
> **nite owl said:**
> Ok I've gone out of my way after I found out my old modem was a winmodem to buy a hardware modem(USR 56k courier...which says 3com????) which is for my dial-up connection. I also previously didnt have a serial port(only USB's) connection for my computer so I went out and bought a pci dual serial card and just put it into one of my PCI ports on my motherboard. Anyway long story short when i go to administration>networking>modem>auto-detect....It cant detect any modem?????Same goes when I installed gnome-ppp and used the auto-detect option on that to. Is there anything I could possibly do to make this work???(upgrade to edgy?, install another program?, a problem with my installation of my pci card becuase all I have done is put it in and I'm assuming it will automatically pick up the card without doing anything else????) Thanks....:(


Ubuntu thinks that every one has dsl and us dial up users have to work at getting our modem set up. It took me about 3 hours to get my modem setup with this distro as opposed to others distros witch only took me 10-15 minutes.  

Take a look at these post witch helped me 

[URL="http://ubuntuforums.org/showthread.php?t=323138"]
http://ubuntuforums.org/showthread.php?t=323138[/URL]



Hope this helps

Suzy

---

### Post by ieee488 on 2006-12-26
I have to disagree that it is more difficult with Ubuntu for dial-up.
My experience is with OpenSUSE 10.1 and RedHat8 and Ubuntu 5.10 and Ubuntu 6.06.
The RedHat8 is on my Thinkpad so it really doesn't count.

But as for OpenSUSE 10.1 and Ubuntu, the surest way to get dial-up is with the wvdialconf command. Once you know the steps to take, it literally takes 5 minutes. 

I installed Ubuntu 5.10 first then OpenSUSE 10.1, and the procedure is the same.

I'm lucky in that my internal PCI modem is one that Linux-compatible.

---

### Post by randiroo76073 on 2006-12-26
This is how I got my external modem recognized.

I had to edit:  /etc/ppp/peers/provider:
[COLOR="Red"]line 10 added username[login for ISP]
line 15 added phone#
line 18 entered modem[my case: ttys0][/COLOR]

Then edit:  /etc/ppp/ip-down
[COLOR="Red"] line 13  #    $2   The tty                      ttyS0[/COLOR]
for my correct serial port

And do the same for:  /etc/ppp/ip-up

Then went to:  /usr/share/ppp/ provider-peer and edited that the same as my:  /etc/ppp/peer/provider

After doing all that then everything recognized my modem.  Thats alot of trouble to go to just to get an external modem working

---

### Post by Duck2006 on 2006-12-26
I think it will be a good day when the serial ports are removed from the motherboards.
Most people these days use USB and Wi-Fi connections.

---

### Post by nite owl on 2006-12-26
My model number on my USR 56K courier is 3453 and when its on the only light thats on is the 'CTS'...Is this normal? 

OH: and my motherboard is an, 'ABIT Fatal1ty AA8XE'

---

### Post by Bartender on 2006-12-26
> **Duck2006 said:**
> I think it will be a good day when the serial ports are removed from the motherboards.

Jeepers, Duck, have a heart!  

Yeah, niteowl, my 5686-03 Sportster has only one light on when it's energized but not doing anything.  I just disassembled my Linux setup an hour ago, otherwise I'd check for ya, but I think it's the CS (Clear to Send) or the TR (Terminal Ready) light.  When it's doing something at least three of the other lights are flickering.

---

### Post by nite owl on 2006-12-26
Hmm has anyone else added a PCI card to Ubuntu 6.06 LTS and it not worked??? Am I right in saying that it should just work after I put it on my motherboard and restart??? Or should I have edited the BIOS when I put it in. Also does the USR 56K...need a driver??

---

### Post by tagginannie on 2006-12-27
> **ieee488 said:**
> I have to disagree that it is more difficult with Ubuntu for dial-up.
My experience is with OpenSUSE 10.1 and RedHat8 and Ubuntu 5.10 and Ubuntu 6.06.
The RedHat8 is on my Thinkpad so it really doesn't count.

But as for OpenSUSE 10.1 and Ubuntu, the surest way to get dial-up is with the wvdialconf command. Once you know the steps to take, it literally takes 5 minutes. 

I installed Ubuntu 5.10 first then OpenSUSE 10.1, and the procedure is the same.

I'm lucky in that my internal PCI modem is one that Linux-compatible.


Shoot!! Never thought of wvdial. The distros that I use are RH9 (upgraded) Slackware  and Suse all of the has kde and I had no trouble setting up a dialup connection with KPPP. The first time that I had trouble is with Kubuntu. If Canonical wants to get the first time Linux user than they should make setting up a dialup connection as easy as it is in Red Hat and some other distros and Windows. 


Suzy

---

### Post by randiroo76073 on 2006-12-27
It definitely needs to be easier to get a dial-up connection working since a great number of us are still dependant on one, and the apps need more standardization between distros, or at least the installing of them.

Uh Duck, where did you take your survey at?  New York City!  I'd be glad to update Mate when you buy me all new equiptment :D

---

### Post by Bartender on 2006-12-27
> **nite owl said:**
> Hmm has anyone else added a PCI card to Ubuntu 6.06 LTS and it not worked??? Am I right in saying that it should just work after I put it on my motherboard and restart??? Or should I have edited the BIOS when I put it in. Also does the USR 56K...need a driver??

Hi, nite -
I've dropped several PCI cards into Ubuntu installs.  Sound cards, NIC cards, and video cards.  All of these *after* Ubuntu had already been installed.  Worked every time, so it's not that you've done something wrong.  It's probly more like Ubuntu just doesn't recognize the card, doesn't have drivers for it, so doesn't know what to do.

If I were more competent with Ubuntu I'd give you some commands to try out that probe the system for recognized devices, but can't remember any right now.  If you go into Device Manager, do you see anything labeled as PCI that's "unknown"?

I still think you oughta look inside for a serial pin-out on the motherboard...

---

### Post by _duncan_ on 2006-12-27
> If I were more competent with Ubuntu I'd give you some commands to try out that probe the system for recognized devices, but can't remember any right now. If you go into Device Manager, do you see anything labeled as PCI that's "unknown"?

Maybe "lspci" will do the trick?

---

