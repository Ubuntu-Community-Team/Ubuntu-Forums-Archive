---
title: "Dial Up Modem - Dell Inspiron 6400 - How do I connect?"
date: 2007-11-07
forum: Absolute Beginner Talk
---

### Post by MozartlovesUbun2 on 2007-11-07
Please help

how do I connect to a dial up modem using Gutsy with my laptop (specs below)

can someone please post a step by step guide

thanks

---

### Post by oilchangeguy on 2007-11-07
you've got a really nice computer. why would you use dial-up? it's fast becoming out dated. if you live in an area that has high speed, you owe it to yourself, and your computer to upgrade to highspeed.

---

### Post by MozartlovesUbun2 on 2007-11-07
> **oilchangeguy said:**
> you've got a really nice computer. why would you use dial-up? it's fast becoming out dated. if you live in an area that has high speed, you owe it to yourself, and your computer to upgrade to highspeed.

lol

thats a bad excuse for ubuntu, (dial up is too slow we dont support it, go get high speed)

well i am renting a place in montreal for a month

and the old land lady has only a  dial up

would be great if i can just check my mails from home

saves me dragging the lappy out to the library or cafe, though its nice :-)

apart from that i spent bloody 3 hours trying to figure it out

until i found out ubuntu doesnt support dial up, what a mess

---

### Post by Maestro23 on 2007-11-07
> **MozartlovesUbun2 said:**
> lol

thats a bad excuse for ubuntu, (dial up is too slow we dont support it, go get high speed)

well i am renting a place in montreal for a month

and the old land lady has only a  dial up

would be great if i can just check my mails from home

saves me dragging the lappy out to the library or cafe, though its nice :-)

apart from that i spent bloody 3 hours trying to figure it out

until i found out ubuntu doesnt support dial up, what a mess

Did you check: [https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)

---

### Post by oilchangeguy on 2007-11-07
it's not that ubuntu does not support dial-up, linux in general has problems with internal modems. and the reason is most internal modems are known as soft modems, meaning they require software to work (drivers). and most modem makers have not released their code to linux, so drivers can be created. if your computer has a serial port, you can get an external modem. usually these work out of the box. these are known as hard modems. the computer views them as hardware. usb external modems are not much better than internal modems. check ebay for a serial port modem.

---

### Post by MozartlovesUbun2 on 2007-11-07
> **oilchangeguy said:**
> it's not that ubuntu does not support dial-up, linux in general has problems with internal modems. and the reason is most internal modems are known as soft modems, meaning they require software to work (drivers). and most modem makers have not released their code to linux, so drivers can be created. if your computer has a serial port, you can get an external modem. usually these work out of the box. these are known as hard modems. the computer views them as hardware. usb external modems are not much better than internal modems. check ebay for a serial port modem.

hmm, well i'm kinda stuck with my laptop internal built in modem

i dont have any serial ports, etc

has anyone else managed to ge tit running on a dell inspiron 6400?

---

### Post by NathanB on 2007-11-07
> **MozartlovesUbun2 said:**
> 
until i found out ubuntu doesnt support dial up, what a mess

Complete nonsense!  All you need is a {low cost} external modem with an RS-232 serial connection.  Find them here:

[http://www.google.com/search?q=external+dial-up+modem](http://www.google.com/search?q=external+dial-up+modem)

After purchase, unwrap, and plugin of said device, go to System > Administration > Networking and click on the Modem Connection option.  Click the Properties button to set it up with your ISP's phone number and other settings.  Afterwards, just click the Activate button whenever you wish to "dial-in" to the Internet.

---

### Post by MozartlovesUbun2 on 2007-11-07
> **Maestro23 said:**
> Did you check: [https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)

yes i did

i downloaded the package

sorry but i didnt get it all to run properly

still stuck

---

### Post by Maestro23 on 2007-11-07
> **MozartlovesUbun2 said:**
> yes i did

i downloaded the package

sorry but i didnt get it all to run properly

still stuck

What errors were you getting?  Did it install correctly or you couldn't get it to install?

---

### Post by MozartlovesUbun2 on 2007-11-07
> **NathanB said:**
> Complete nonsense!  All you need is a {low cost} external modem with an RS-232 serial connection.  Find them here:

[http://www.google.com/search?q=external+dial-up+modem](http://www.google.com/search?q=external+dial-up+modem)

After purchase, unwrap, and plugin of said device, go to System > Administration > Networking and click on the Modem Connection option.  Click the Properties button to set it up with your ISP's phone number and other settings.  Afterwards, just click the Activate button whenever you wish to "dial-in" to the Internet.

i only have USB ports, whats RS-232?

plus i am only another 3 more weeks in montreal, do i have to go get extra hardware

is there no other way around it? :confused:

---

### Post by MozartlovesUbun2 on 2007-11-07
i first tried what the guy mentioned here

**[SOLVED] Inspiron 6400 56Kb modem **  "but not for me yet"

[http://ubuntuforums.org/showthread.php?t=574233](http://ubuntuforums.org/showthread.php?t=574233)

i took off the "#"s

but still not working, what do i do next?

---

### Post by Maestro23 on 2007-11-07
> **MozartlovesUbun2 said:**
> i first tried what the guy mentioned here

**[SOLVED] Inspiron 6400 56Kb modem **  "but not for me yet"

[http://ubuntuforums.org/showthread.php?t=574233](http://ubuntuforums.org/showthread.php?t=574233)

i took off the "#"s

but still not working, what do i do next?

Did you use the ScanModem tool like suggested in the doc?  If so, what was the output for your modem?
[https://help.ubuntu.com/community/DialupModemHowto/ScanModem](https://help.ubuntu.com/community/DialupModemHowto/ScanModem)

---

### Post by edwardLS on 2007-11-08
I have a Dell Inspiron 9100 with an internal (soft) modem, and I use it regularly.  I have had it working on Dapper Drake, Feisty Fawn, and now Gutsy Gibbon.  With the exception of Gutsy Gibbon I had to use the scanmodem route to determine the type of soft modem I had, and then select and install the correct drivers for that modem.  I had the most difficulty with Feisty Fawn, but I did get it to work.  Gutsy Gibbon permitted me to use the Restricted Drivers and worked almost perfectly.  I say "almost perfectly" because I do not have the sound from the modem as it dials and negotiates with my ISP.  I have grown used to the sound as a troubleshooting/tracking action means.

Just to add to the linux modem discussion.  I also have an external modem working on a desktop and it has worked (US Robotics) out of the box under Dapper Drake, Feisty Fawn, and Gutsy Gibbon.  

Good luck.  BTW my modem is a Broadcom modem.

---

### Post by Bartender on 2007-11-08
Serial device to USB is not a problem.
SBT-USC1M cable.
[http://www.newegg.com/Product/Produc...&Tpk=SBT-USC1M](http://www.newegg.com/Product/Produc...&Tpk=SBT-USC1M)

That cable is automatically recognized by the Linux kernel.  Ubuntu 7.04 and I'm sure 7.10 will use the adapter seamlessly.  

This is beginning to sound like a needless expense/hassle for you if you only need it for a month, but that cable and a used US Robotics full-hardware serial modem should get you going.

---

### Post by MozartlovesUbun2 on 2007-11-08
> **Maestro23 said:**
> Did you use the ScanModem tool like suggested in the doc?  If so, what was the output for your modem?
[https://help.ubuntu.com/community/DialupModemHowto/ScanModem](https://help.ubuntu.com/community/DialupModemHowto/ScanModem)

hi
yes i did as you told me to, and followed the instructions on the link, downloaded it and did a run, didnt work for me, maybe i did something wrong, well to access the internet wifi i'm in the library, so do i have to be connected with the modem cable when i run the scanModem.gz pack?

thats the only thing i can think i guess i did wrong

(so i'll have to go back home and try again)
thx

================
also Nick from ** [SOLVED] Inspiron 6400 56Kb modem **  [http://ubuntuforums.org/showthread.php?t=574233](http://ubuntuforums.org/showthread.php?t=574233)
was kind enough to reply back, i'll wait for his instructions

---

### Post by MozartlovesUbun2 on 2007-11-15
posted here:

[http://ubuntuforums.org/showthread.php?t=598382&page=2](http://ubuntuforums.org/showthread.php?t=598382&page=2)

=================================
 NotTheMessiah  NotTheMessiah is offline
Just Give Me the Beans!
	  	
Join Date: Jun 2007
Beans: 80
Ubuntu 7.10 Gutsy Gibbon User
Re: Dell 6400 ATi X1400 Gutsy Gibbon "Suspend Hibernate" how to make it work? help
Quote:
Originally Posted by MozartlovesUbun2 View Post
ok thanks for the detailed info

well i guess i'll wait a little longer and stick to ubuntu for the time being

spent 3 hours last week trying to get a dial up connection through the laptop

just to find out that its disabled or what ever under ubuntu

still havnt managed to get it running
There is a free driver for internal winmodems(for conexant -and intel HD audio) from dell support website.
[http://support.dell.com/support/down...&fileid=206745](http://support.dell.com/support/down...&fileid=206745)
Then just use wvdial or G-ppp

==================================

did not work for me

---

### Post by jwalling on 2007-11-21
> **Bartender said:**
> Serial device to USB is not a problem.
SBT-USC1M cable.
[http://www.newegg.com/Product/Produc...&Tpk=SBT-USC1M](http://www.newegg.com/Product/Produc...&Tpk=SBT-USC1M)


Fixed URL for SBT-USC1M : [http://www.newegg.com/Product/Product.aspx?Item=N82E16812156008&Tpk=SBT-USC1M](http://www.newegg.com/Product/Product.aspx?Item=N82E16812156008&Tpk=SBT-USC1M)

**_Sabrent has 4 models:_**

_Sabrent SBT-USC1K / CBL-USB-GM_
USB to Serial (9-pin) DB-9 RS-232 Adapter Cable
[http://www.sabrent.com/products/specs/SBT-USC1K.htm](http://www.sabrent.com/products/specs/SBT-USC1K.htm)
Complies with USB Specification v1.1(0) & USB CDC v1.1
NewEgg.com
[http://www.newegg.com/Product/Product.aspx?Item=N82E16812156003](http://www.newegg.com/Product/Product.aspx?Item=N82E16812156003)
Linux reviews
5/16/2006 
 Rating: 5 out of 5
 Perfect under linux
 Pros: Showed up right away when plugged into a linux box, been working flawlessly ever since
 Cons: None
3/28/2006
 Rating: 5 out of 5
 Pros: Uses Prolific PL2303 chipset which is supported in Linux. Plug and play for me in Ubuntu 5.10.
 Cons: Not really a con to me, but what I got is different than pictured. It basically looks like the Sabrent SBT-USC6k cable that Newegg also sells except it only has a 1 foot cable as described. This means that it has thumbscrews and not the screw terminals as pictured.
2/3/2005
 Rating: 5 out of 5
 Comments: Works perfectly under linux using "USB Prolific 2303 Single Port Serial Driver"

_Sabrent SBT-USC6K _
USB to Serial (9-pin) DB-9 RS-232 Adapter Cable 6ft Length
[http://www.sabrent.com/products/specs/SBT-USC6K.htm](http://www.sabrent.com/products/specs/SBT-USC6K.htm)
Complies with USB Specification v1.1(0) & USB CDC v1.1

_Sabrent SBT-USC1M / CBL-USB-CS1B_
USB 2.0 to Serial (9-pin) DB-9 RS-232 Adapter Cable
[http://www.sabrent.com/products/specs/SBT-USC1M.htm](http://www.sabrent.com/products/specs/SBT-USC1M.htm)
Complies with USB Specification v2.0 and 1.1(0) & USB CDC v1.1
NewEgg.com
[http://www.newegg.com/Product/Product.aspx?Item=N82E16812156008&Tpk=SBT-USC1M](http://www.newegg.com/Product/Product.aspx?Item=N82E16812156008&Tpk=SBT-USC1M)
Linux reviews:
11/5/2007
 Rating: 5 out of 5 - Linux compatible (CentOS 5)
 Pros: Works with CentOS 5, no additional drivers need. Green light when plugged into USB. Shows up at /dev/ttyACM0.
 Cons: Cannot control DirecTV set top box.
 Other Thoughts: For my MythTV setup, I needed a serial to USB adapter to control a DirecTV D11 and H20 box. This cable does not do it. However this does provide a serial port, and fits in to my setup as follows: computer <-> (this) <-> null modem cable <-> GWC UC320 USB to serial converter -> DirecTV set top box.
9/22/2007
 Rating: 5 out of 5 - Linux OK
 Pros: Work without drivers in Ubuntu 7.04. Even passes through VMware player just fine (my jump drive doesn't). Device is newer version than pictured (USB 2.0)
 Cons: Once in WinXP on VMware, I needed to install drivers. I don't care though because I only use windows for the wife's software.
 Other Thoughts: Used it to connect an old GPS for Wardriving. Only needed to select /dev/ttyUSB0 and I was off and running.
5/7/2007
 Rating: 4 out of 5 -  Decent adapter
 Pros: Works without a hitch under Linux (pl2303 driver). I use this for an external modem and X10 CM11A.
 Cons: Does not work with my APC Smart UPS.
 Other Thoughts: Haven't tried with any flavor of Windows.

_Sabrent SBT-USC6M_
USB to Serial (9-pin) DB-9 RS-232 Adapter Cable 6ft Length
[http://www.sabrent.com/products/specs/SBT-USC6M.htm](http://www.sabrent.com/products/specs/SBT-USC6M.htm)
Complies with USB Specification v1.1(0) & USB CDC v1.1
NewEgg.com
[http://www.newegg.com/Product/Product.aspx?Item=N82E16812156009](http://www.newegg.com/Product/Product.aspx?Item=N82E16812156009)
No linux reviews

---
Your experience will depend on the chip set which may have changed in the same adapter model  according to some reviewers.  Look for Prolific Technology PL2303 compatible chip set which is allegedly supported by Gutsy.  Redhat/Win/Mac drivers are here: [http://www.prolific.com.tw/eng/downloads.asp?ID=31](http://www.prolific.com.tw/eng/downloads.asp?ID=31)

---
I am still researching USB Serial adapters so I cannot verify what works. My goal (fantasy)  is to have a USB Serial Adapter working with an external RS-232 modem running under Ubuntu 7.10 shortly after my new laptop arrives. 

John Walling
Seattle, WA

---

### Post by markofealing on 2007-12-03
I'm running Kubuntu 7.10 on a Dell Latitude C640. Up until yesterday I could not use the internal modem, as could not find a working soft modem driver. On upgrading yesterday from 7.04 to 7.10, Kubuntu detected the modem and asked if I wanted to use the Restricted driver for it. I said yes and it installed the driver.

My softmodem is:

00:1f.6 Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (rev 02)

I got the above by doing a lspci in Terminal.

I use KPPP and went into configure, selected modem and added a new one, gave it a name and selected Test. By default the device was set to dev/modem. It just worked. 

Well impressed with the latest Kubuntu release and the upgrade was absolutely painless (I've now upgraded 3 systems without any problems).

You may have to enable restricted drivers.

---

### Post by MozartlovesUbun2 on 2007-12-03
> **markofealing said:**
> I'm running Kubuntu 7.10 on a Dell Latitude C640. Up until yesterday I could not use the internal modem, as could not find a working soft modem driver. On upgrading yesterday from 7.04 to 7.10, Kubuntu detected the modem and asked if I wanted to use the Restricted driver for it. I said yes and it installed the driver.

My softmodem is:

00:1f.6 Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (rev 02)

I got the above by doing a lspci in Terminal.

I use KPPP and went into configure, selected modem and added a new one, gave it a name and selected Test. By default the device was set to dev/modem. It just worked. 

Well impressed with the latest Kubuntu release and the upgrade was absolutely painless (I've now upgraded 3 systems without any problems).

You may have to enable restricted drivers.

Lucky you.

---

