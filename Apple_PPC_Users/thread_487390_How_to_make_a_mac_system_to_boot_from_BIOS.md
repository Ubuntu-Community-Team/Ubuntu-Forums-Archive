---
title: "How to make a mac system to boot from BIOS"
date: 2007-06-29
forum: Apple PPC Users
---

### Post by Franscisco on 2007-06-29
Does anyone how what keys or how to get to the mac BIOS. I have an old mac system, and I want to install Ubuntu. So, I would like to know how to set the BIOS to boot from the CD.

---

### Post by kano on 2007-06-29
Holding down the "c" key while booting will make it boot from a cd.

---

### Post by Franscisco on 2007-06-29
I did hold the c key, but nothing happened.

---

### Post by kano on 2007-06-29
How old is this mac? OldWorld/Newworld, model?

---

### Post by pxwpxw on 2007-06-29
Command Option o f

Will get you into Open Firmware which is roughtly the mac equivalent of bios.

---

### Post by Franscisco on 2007-06-29
It is a mac OS 9

---

### Post by pxwpxw on 2007-06-29
But what mac model is it?

---

### Post by Franscisco on 2007-06-29
looks like this picture
[http://a4.vox.com/6a00c22524533a8e1d00d09e4b9194be2b-200pi](http://a4.vox.com/6a00c22524533a8e1d00d09e4b9194be2b-200pi)

---

### Post by pxwpxw on 2007-06-29
woops, no thats wrong is that the side view, Its a powerpc
Looks like a blue and white new world power mac 1999.



Can you open the cd from macos and see what files are in it?

---

### Post by Franscisco on 2007-06-29
I don't have the CD from Mac unless there a different way to see what model my mac system is. 
I am too newbee to the mac world, so I don't know anything. The reason I have this mac system is because my friend didn't want it, so he gave it to me before he moved to a different state. So, I decided to have Ubuntu on this mac box instead of a mac system. This means I don't know anything, but I would like at least know what things I can try to boot a Ubuntu live cd on this mac system. 
Thanks for your help I really appreciate it. I will see any other post tomorrow I go to sleep now.

---

### Post by pxwpxw on 2007-06-29
ok, no problem, will look for you after a good sleep.

I looked at some old apple mac docs, it looks like a "blue and white" G3 powermac 1999, which is a New World mac. The documents say you  should only need to hold the "c" key down while it restarts to boot a  cd, provided the cd is bootable, or an alternative is hold 4 keys:
```

 Command(Apple) Option Shift Delete 

```
which sould search for bootable partitions/drives.  I do not have a G3 to try that, so i cant be sure if that works. You dont have to change booting order like in intel pc.

You can check  for the G3 version - see this doc:
Determining the version of Open Firmware on your Mac (1999)
[http://developer.apple.com/qa/hw/hw60.html]("http://developer.apple.com/qa/hw/hw60.html")

> 
Start your Macintosh holding down the Command-Option-O-F keys and wait until the Open Firmware message is displayed. Here is the header for a 1999 Power Macintosh G3 Macintosh (a.k.a., the blue & white or 1999 Power Mac G3):

Apple PowerMac1,1 1.0f3 BootROM built on 12/08/98 at 17:37:02
Copyright 1994-1998 Apple Computer, Inc.
All Rights Reserved.
OpenFirmware 3.1.0


What ubuntu CD have you got and where did it come from? 
It could be  problem with the CD preventing it from booting.
Is macos9 working ok?

.

---

### Post by Franscisco on 2007-06-29
Does it matter if I use any other keyboard, or I have to use a mac keyboard in order to make my commands work.

---

### Post by pxwpxw on 2007-06-29
You do not have to use a mac keyboard, but there might be some differences, I have used a mac keyboard on a Windows pc and it works.
A non-macintosh  usb keyboard will probably work for that mac - try it.
To start in Open Firmware you only need the 4 keys, Command and Alt( or Option) and o and f .
Is macos working for you - have you been using the macintosh desktop and applications?

---

### Post by Franscisco on 2007-06-30
Thank you for helping me out, and sorry for being to ignorant, but what is the command key. Is it the Ctrl key?
I have never been working with macs, so I just want to go to Ubuntu.

---

### Post by pxwpxw on 2007-06-30
On a windows keyboard its probably the  windows key, on my windows keyboard that is the 2nd key from the left in the front row.

from the left side, front row

For the Mac keyboard:
Control Option(Alt)  Command

For the Windows keyboard:
Control Command Alt

---

### Post by pxwpxw on 2007-06-30
PPC G3 B&W

Mac keyboard

[http://img340.imageshack.us/img340/991/kbdlp5.png]("http://img340.imageshack.us/img340/991/kbdlp5.png"):

Front: 

[http://img521.imageshack.us/img521/7072/frontpj2.png]("http://img521.imageshack.us/img521/7072/frontpj2.png")

Back:

[http://img340.imageshack.us/img340/6504/backph2.png]("http://img340.imageshack.us/img340/6504/backph2.png")

---

### Post by Franscisco on 2007-07-01
Believe it or not, I can't boot from the live cd. I already tried using those keys, but there is no good news. 
Please tell me different things that I can try.

---

### Post by pxwpxw on 2007-07-01
Cant help you unless you give some clearer information -
Does the mac work?
What cd are you tryig to boot?
Have you got anything working on the mac?

---

### Post by Franscisco on 2007-07-01
Yeah, the mac works, the system loads, I play music, and I am using a Live cd that has been used before to install Ubuntu.

---

### Post by hacker128 on 2007-07-01
it's a powerpc g3 oldworld mac. i know that much from the picture. looked on wikipedia.

---

### Post by kano on 2007-07-01
If it is indeed an OldWorld, that would explain why you can't boot the cd...
[https://help.ubuntu.com/community/OldWorld](https://help.ubuntu.com/community/OldWorld)

---

### Post by pxwpxw on 2007-07-02
> **Franscisco said:**
> Yeah, the mac works, the system loads, I play music, and I am using a Live cd that has been used before to install Ubuntu.

Well, what do you see when you open the CD using Macos9, and exactly which Live cd is it.

---

### Post by Franscisco on 2007-07-02
When I open the live cd, I see the files in it. This live cd is not a copy. It is a original. I think this mac is an old mac which means I need what? A gabage can, maybe!

---

### Post by pxwpxw on 2007-07-02
No garbage, collectors item.
What color is the G3?
Does it look like this?
[IMG]http://img521.imageshack.us/img521/7072/frontpj2.png[/IMG]

---

### Post by 3rdalbum on 2007-07-02
Just to check: You're using the PowerPC version of Ubuntu?

---

### Post by Franscisco on 2007-07-03
Yeah, my system looks exactly like the picture above. The color would be like gray.

---

### Post by pxwpxw on 2007-07-03
Could it be called "blue and white" ?

Open Firmware 0 
The NewWorld software architecture implemented on the Power Macintosh G3 
computer follows some of the standards defined by the Open Firmware IEEE

Its NewWorld.

Anyway, what is that ubuntu install CD Alternate, Desktop, Server feisty edgy which?- full name of the cd - have you used it to install on other Applemacs  G3, G4,G5 - which ones  (not intel macs).

The B&W G3 can run the Desktop CD according to this post:
[http://ubuntuforums.org/showpost.php?p=2507510&postcount=1]("http://ubuntuforums.org/showpost.php?p=2507510&postcount=1")

---

### Post by pxwpxw on 2007-07-03
Suggest you get a new feisty (704) mac ppc Desktop CD and a Mac keyboard.

There is a sticky link at the top of this Apple Forum for dpwnloading CDs:
>   	
Sticky Thread Sticky: Where to download Ubuntu for PowerPC and other frequently asked questions (Multi-page thread 1 2)
ssam 


Download the iso, if necessary on another Applemac, and and burn to CD  with MacosX Disk Utility, and test it boots and runs on another mac.

If necessary get an Apple USB keyboard  from Apple or Ebay.

Then try the CD on the B&WG3.

---

### Post by Franscisco on 2007-07-06
I have dapper, Feisty, and Edgy cd's (originals) and I have used those CD on PC, but no macs. I would say my mac is blue color. I think I am going to buy a mac keyboard to try to boot.

---

### Post by pxwpxw on 2007-07-06
if you have used the CD's on PC's, then you have the wrong cd's - you need the ppc powerpc mac version - then should boot with luck.

---

### Post by Franscisco on 2007-07-07
So I need to burn a Ubuntu lived CD in order to boot in a mac. But there is one thing, I can't connect to the Internet becuase the mac system doesn't want to work with my internet. I have not idea. I think the system I have is too old because I have tried many times. On my system there is no **System Preferences**
I can only see a apple icon, there, I find a down list which has **control panels** where I see the is a TCP/IP option, but I can't figure anything out.

---

### Post by kano on 2007-07-07
You need a PPC install cd, the x86 ones just won't work. DL it on your PC and burn it, it's just a standard ISO.

---

### Post by joninkrakow on 2007-07-07
> I can only see a apple icon, there, I find a down list which has control panels where I see the is a TCP/IP option, but I can't figure anything out.

That Control Panels folder _is_ your System preferences. Instead of all being in one window, they were separate programs in a folder, and show up as a list in the Apple menu. The one you need is the TCP/IP control panel.

Once it's open, the first thing you need to do is to go to the littls popup menu at top, and choose your connection which, I'm assuming, is Ethernet, so you should choose "Connect via: Ethernet Built-in".

Secondly, below that, choose "Configure:" and the option you need, which is probably DHCP, or maybe Manually. If manually, fill in your IP address, subnet mask, router, and maybe your dns, if you need it. Once that's done, you should be good to go!

If you need PPP or something else, you will need to open the PPP control panel, which should be obvious enough after the TCP/IP one. 

BTW, for some reason, my one OX 9 box always wants me to turn on Appletalk, which is another control panel in the menu, at the top. Open it, confirming to turn on Appletalk when you close if it asks, and then, choose the same "Connect via:" option as you did for your TCP/IP settings.

Once that's done, you should be good to go.

Of course, I say all that only to remember that you should be able to burn a CD on any system that will work. Just make sure you download the PPC iso from the stickied post at the top of this form. Once burnt, it should boot.

-Jon

---

### Post by pxwpxw on 2007-07-07
> **Franscisco said:**
> So I need to burn a Ubuntu lived CD in order to boot in a mac. But there is one thing, I can't connect to the Internet becuase the mac system doesn't want to work with my internet. I have not idea. I think the system I have is too old because I have tried many times. On my system there is no **System Preferences**
I can only see a apple icon, there, I find a down list which has **control panels** where I see the is a TCP/IP option, but I can't figure anything out.

You have a Macos9 operating system. In the drop down menu the System Profiler gives system details. **joninkrakow** has explained about ControlPanel above,

Specs for the B&W Power MacG3 say it has only a CD rom drive, not a CD burner. Hard disk ranging from 6 to 12GB I think.

From what you have posted your CD drive is working, and should boot from an install CD but I cant be sure of that.

Unless you can get comfortable with the macos9 network setup and have a good network connection and a workable internet browser, I would suggest you try to obtain a ubuntu install CD (from ubuntu or  from other linux sellers).

If that gets you a ubuntu installation, it has network setup automatically as part of the install, so you would not need macos9 if you don't want to use it. 

But that all depends on being able to get the install CD and a successful  ubuntu (or xubuntu) installation. Your hard disk size may be a limitation. You will need a network connection to get additional packages and updates.

---

### Post by Franscisco on 2007-07-09
I did tried to connect to the Ethernet. I went to Control Panels, TPC/IP, choosing DHCP to get my ip address automatically, but that did not work. Do I need anything else?

---

### Post by joninkrakow on 2007-07-09
Back in the TCP/IP control panel, at the very top, there is the text "Connect via:" and a popup menu next to it. Do you have the network card selected? It should be "Ethernet Built-in" unless you happen to have a couple card installed (our Powermac has the bult-in slow 10mbt card and a faster 10/100 card) If you do, and it doesn't work, or if it doesn't show up, we will need to look elsewhere, but first, if you do have the proper network card chosen, have you also opened the Appletalk control panel, and turned on Appletalk via the same card? Sometimes, OS 9 wants the two to match before it will work properly.

Lastly, if you have done all these steps, and it still isn't working, it's possible that somebody has turned off the extensions you need to get networking to work. You will need to open another control panel, called "Extensions Manager".

Once it's open, go to the View menu, and choose "Show by folders". Next, the first item is probably named "Control Panels" You can click on the triangle next to it and close that folder up so it's not in your way.

Now, in the Extensions folder, you need to look for the following items, making sure they are all checked and on. If anything is not checked, click in the check box to check it. When you've checked everything, you will need to restart the computer to have the changes take effect. 

Items you need on:
1. Apple Enet
2. CarbonLib (not Enet, but it ought to be on, as not having it on can cause problems)
3. DNSPlugin
4. EnetShimLib (if you are using USB to connect to the internet--otherwise, if it's off, don't bother)
5. Internet Access (probably on if you are getting TCP/IP to open, but just in case)
6. Network Setup Extension
7. Open Transport
8. Open Transport ASLM Modules
9. Shared Library Manager and Shared Library Manager PPC (two separate items)

There may be other items with Opentpt or Open Transport in their names. Make sure they are all on, just in case, but the above, at least, are essential. 

Hopefully this will get you online, but without a CD burner on this thing, will it help? 

I don't recommend an OS 9 machine for internet. None of the browsers available handle modern web pages well. It may be useful for getting essential information when another computer is down (what I use mine for when mucking with Linux that isn't working ;-)  ) 

I just hope you can get a good CD burnt and get Ubuntu working on this box. I think you will be much happier than OS 9! (not that 9 is bad, but it's far toooo old!)

-Jon

---

### Post by pxwpxw on 2007-07-10
> **Franscisco said:**
> I did tried to connect to the Ethernet. I went to Control Panels, TPC/IP, choosing DHCP to get my ip address automatically, but that did not work. Do I need anything else?


What do you use for the internet comnnection, and are you using that connection for other computers. Is it via dialup telephone, dsl modem, dsl router, cable modem?
All of these have different configuration in Macos9.

What is the web browser you are using in Macos9 to test the connection?

You can see all the Application and Extensions from the System Profiler. ( sysprof1.png )

You can also check the Network connection using the System Profiler.
( sysnetwork2.png).

the tcp/ip control panel setup for dhcp ethernet connection is like these last 3 attachments. That was all I needed to get connected via ethernet to a dsl router.
( tcpip1.png tcpip2.png tcpip3.png)

---

### Post by Franscisco on 2007-07-12
I am using a DLS from Verizon. I am using a router and a switch. Thank s for all this help. It really helps. I will be trying all this very soon because of my work.

---

