---
title: "[SOLVED] trying to extract DriverDetective.exe but"
date: 2008-04-17
forum: Absolute Beginner Talk
---

### Post by bmann11 on 2008-04-17
when I right click and go to extract it gives me an error message.  This file holds my wireless driver, so I really need to get in there. thanks

---

### Post by tamoneya on 2008-04-17
what is the error message.  How did you attempt to extract it?

---

### Post by wormser on 2008-04-17
.exe files are Windows executable files and cannot be extracted.  What type of wireless card do you have?  Post the results of the following command.  Applications> Accessories> Terminal.

```
lspci
```

---

### Post by bmann11 on 2008-04-17
I attempt to unpack it by right clicking the icon on the desktop and then clicking "extract here"

error message reads "an error occurred while extracting files"  when i hit the command line output button it reads the following:

End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
unzip:  cannot find zipfile directory in one of /home/bradley/Desktop/DriverDetective.exe or
        /home/bradley/Desktop/DriverDetective.exe.zip, and cannot find /home/bradley/Desktop/DriverDetective.exe.ZIP, period.


Thanks.

---

### Post by spiderbatdad on 2008-04-17
```
sudo apt-get install cabextract
```

```
cd Desktop
``` assuming desktop is the location of the .exe.

```
cabextract filename.exe
```

---

### Post by bmann11 on 2008-04-17
lspci 

00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV250 [Mobility FireGL 9000] (rev 01)
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5702X Gigabit Ethernet (rev 02)
02:01.0 CardBus bridge: O2 Micro, Inc. OZ711EC1 SmartCardBus Controller (rev 20)
02:01.1 CardBus bridge: O2 Micro, Inc. OZ711EC1 SmartCardBus Controller (rev 20)
02:03.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)

---

### Post by wormser on 2008-04-18
> Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)I have a BCM4309 and used Restricted Drivers Manager.  Go to System> Administration> Restricted Drivers Manager and just follow the wizard.

---

### Post by Tatty on 2008-04-18
A windows driver will not work in linux, even if you manage to unzip the file.

Follow the above post to try the restricted drivers manager.

---

### Post by tango_ninja on 2008-04-18
hehe never fails. every week or so you get someone asking about .exe files :)

no offence bmann11, i thought the same thing when i switched over to linux. welcome to the forum, hope you find it helpful.

---

### Post by spiderbatdad on 2008-04-18
> **Tatty said:**
> A windows driver will not work in linux, even if you manage to unzip the file.

Follow the above post to try the restricted drivers manager.

You are quite wrong, and apparently unfamiliar with ndiswrapper. the .inf file wrapped in the .exe is used.

---

### Post by bmann11 on 2008-04-18
When I follow the wizard a box pops up asking me where the firmware can be found.  Do I choose the internet location or a local location?  Thanks

---

### Post by Tatty on 2008-04-18
> **spiderbatdad said:**
> You are quite wrong, and apparently unfamiliar with ndiswrapper. the .inf file wrapped in the .exe is used.

Very true, i was neglecting ndiswrapper.  Apologies.

---

### Post by bmann11 on 2008-04-18
allow me to clarify, when I'm in the midst of this process, as window pops up saying" Specify firmware location"

It then gives me a choice of a file on my system (cdrom, windows partition,etc.

or I can download from the internet.

any guidance?  I've been working on this for days and I'm starting to feel like I might be close!!!!

---

### Post by spiderbatdad on 2008-04-18
> **Tatty said:**
> Very true, i was neglecting ndiswrapper.  Apologies.

No worries. I generally try to make statements like: I think you can...or I don't think you can.
So when I see a blanket statement like: You can not...and I know it's possible, it makes my hair stand up...lol. A character flaw.

---

### Post by wormser on 2008-04-18
> **bmann11 said:**
> allow me to clarify, when I'm in the midst of this process, as window pops up saying" Specify firmware location"

It then gives me a choice of a file on my system (cdrom, windows partition,etc.

or I can download from the internet.

any guidance?  I've been working on this for days and I'm starting to feel like I might be close!!!!

The internet.

---

### Post by bmann11 on 2008-04-18
forgive my linux ignorance, super-newb here.  I downloaded from the internet and was told everything is working,Got that far, but

I unhooked my ethernet cable and hooked it up to my router, and I still couln't pick up the signal.  Any more help from this point.  Thanks.

---

### Post by wormser on 2008-04-18
> **bmann11 said:**
> forgive my linux ignorance, super-newb here.  I downloaded from the internet and was told everything is working,Got that far, but

I unhooked my ethernet cable and hooked it up to my router, and I still couln't pick up the signal.  Any more help from this point.  Thanks.

Did you reboot?

---

### Post by bmann11 on 2008-04-18
Rebooted and hooked up the router.

Now, instead of firefox giving me an immediate load error as it did before I rebooted, it gets stuck searching for the page forever.

---

### Post by wormser on 2008-04-18
Click on the network icon near the clock.  Is you wireless network there?  Can it connect?  Which version of Ubuntu is this?  It is easier to help you with more details.  Other wise we are just guessing.

---

### Post by bmann11 on 2008-04-18
When I click on the network icon my network didn't show up.  This is 7.10. and I'm using a dell laptop with pentium/

---

### Post by joshrobinson on 2008-04-18
> **bmann11 said:**
> When I click on the network icon my network didn't show up.  This is 7.10. and I'm using a dell laptop with pentium/

if you click "connect to other wireless network" under the network icon, and you put your network info in, does it come up listed? but show 0 signal? or does it show signal

---

### Post by bmann11 on 2008-04-18
the option of "connect to other wireless network" no longer comes up as an option, although it used to before tonight.

the only options are wired connection or manual.  thanks

---

### Post by joshrobinson on 2008-04-18
have you tried ndisrwapper at all? thats what i use for my broadcom

```
sudo apt-get install ndisgtk
```

in your system menu, there should be a windows driver manager, im not sure exactally what its called, since i compiled from source not using ndisgtk

in there, you will want to browse for and add your .inf file you cabextracted from the .exe
then in a terminal run these commands

```
sudo rmmod bcm43xx
```
then
```
sudo modprobe ndiswrapper
```

anything happen with your wireless card?

---

### Post by bmann11 on 2008-04-18
It's working!!!!!!  It's working!!!!!!!!  Hallehuah, it's working!!!!!!!

Thank you everyone for your help.  These forums are fantastic.  I probably shouldn't tell anyone this, but I was typing my login password instead of my network password.  Sorry about that.

---

### Post by wormser on 2008-04-18
Edit: looks like we posted at the same time.  I am glad it is working.  Mark your thread as Solved and give thanks with the little star from the post that helped.

---

### Post by bmann11 on 2008-04-18
It's working!!!!!!  It's working!!!!!  Hallehuah, it's working!!!!!!

Thanks for your help,  These forums are great.  I apologize wormser, but I was entering my login password instead of my network password.  My bad.  Thanks again for the help.  If it wasn't for me, this wouldn't be as difficult as I'm making it out to be.  Peace, Bman

---

