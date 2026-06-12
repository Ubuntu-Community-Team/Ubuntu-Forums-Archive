---
title: "[SOLVED] Problems getting Netgear WG511 wireless working"
date: 2008-04-14
forum: Absolute Beginner Talk
---

### Post by Berean on 2008-04-14
Hello,

I've got a Netgear WG511 wireless pcmcia care but am having problems getting it working.  I've installed the driver, using the command line and ndiswrapper, but I can't seem to recognise my wireless network.  I have a Netgear DG834Gv3.  Below is a copy/paste of terminal readout.  All help gratefully recieved!

02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)
root@ian-laptop:/home/ian# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

vmnet1    no wireless extensions.

vmnet8    no wireless extensions.

---

### Post by GCoffee on 2008-04-14
what encryption have you got?

---

### Post by Berean on 2008-04-14
> **GCoffee said:**
> what encryption have you got?

Hi, and thanks.  I think (but am not sure!) that I have WPA-PSK?  Does that make sense?  Or at least that was what the printout reads from when I used it in XP.

---

### Post by prshah on 2008-04-14
> **Berean said:**
> 

02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)


```
ndiswrapper -l
``` Please?

---

### Post by Berean on 2008-04-14
> **prshah said:**
> ```
ndiswrapper -l
``` Please?

ian@ian-laptop:~$ ndiswrapper -l
2802w : driver installed
wg511v2 : driver installed
        device (11AB:1FAA) present
ian@ian-laptop:~$

---

### Post by Berean on 2008-04-14
> **Berean said:**
> ian@ian-laptop:~$ ndiswrapper -l
2802w : driver installed
wg511v2 : driver installed
        device (11AB:1FAA) present
ian@ian-laptop:~$


Sorry, one of the drivers wasn't recognised!  This is the updated output.

ian@ian-laptop:~$ ndiswrapper -l
wg511v2 : driver installed
        device (11AB:1FAA) present
ian@ian-laptop:~$

---

### Post by GCoffee on 2008-04-14
I have wpa-2 encryption on my netgear. Try changing to wep and see if that helps.

From what i can make out on your readings the adapter is working fine. It's the router. Are you using a laptop with inbuilt wireless or a network card / netgear adapter?

---

### Post by Berean on 2008-04-14
> **GCoffee said:**
> I have wpa-2 encryption on my netgear. Try changing to wep and see if that helps

I thought I knew more than I do!  How do I change the encryption?

---

### Post by GCoffee on 2008-04-14
Have you got a windows machine? or can you boot into windows? it will probably be easier that way

---

### Post by Berean on 2008-04-14
> **GCoffee said:**
> Have you got a windows machine? or can you boot into windows? it will probably be easier that way

No!  I did away with it about a month ago.  Then my wife was given an ipod which we couldn't get to run in Ubuntu and I tried to reinstall XP.  I've had all sorts of problems since - no XP - and difficulty getting Gutsy back to what it was after Windows failed to load.  I've had wireless before, but with a Netgear USB, but when I tried to reinstall I ran into difficulties with wireless.  I've posted previously and somebody suggested this pcmcia card (WG511) which apparently works straight out the box: it doesn't!  So I'm stumped.  I haven't changed any settings in my router, but I could reset it to factory settings?

---

### Post by GCoffee on 2008-04-14
have you still got your netgear usb?

---

### Post by Berean on 2008-04-14
> **GCoffee said:**
> have you still got your netgear usb?

Yes!

---

### Post by GCoffee on 2008-04-14
Hate to state the obvious but you might of realised what im coming on to here... Try plugging in the netgear usb and taking out your current one.

---

### Post by GCoffee on 2008-04-14
quick question,

how are you posting on the forum with no internet?

---

### Post by Berean on 2008-04-14
> **GCoffee said:**
> Hate to state the obvious but you might of realised what im coming on to here... Try plugging in the netgear usb and taking out your current one.


ian@ian-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ian@ian-laptop:~$ lsusb
Bus 003 Device 002: ID 0846:6a00 NetGear, Inc. WG111 WiFi (v2)
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
ian@ian-laptop:~$ 

I still have no wireless (or so it would seem) and my WG111v2 is insitu now.  However, I don't have the driver installed.  The HDD was wiped when I tried reinstalling XP.

---

### Post by Berean on 2008-04-14
> **GCoffee said:**
> quick question,

how are you posting on the forum with no internet?

With a LAN cable into the back of the DG834Gv3

---

### Post by GCoffee on 2008-04-14
I have a WG111V2 adapter and it works fine with ubuntu. Try connecting to your wireless using the tool in the menu bar

---

### Post by GCoffee on 2008-04-14
By the way, im doing all this from memory as my ubuntu machine is elsewhere shall we say.

---

### Post by Berean on 2008-04-14
I've had it running fine in the past, but not now!  All I have at the top of the screen is two computer terminal images, but there is no wireless to connect to.  I've attached a screenshot of what I open when I click on the image.

---

### Post by GCoffee on 2008-04-14
Make sure you wg111v2 adapter is plugged in and then single click the circled icon. see if your network is listed. if so try to connect to it, take the lan cable out if you need to. Its not the best soloution but if it gets desperate couldn't you just leave the lan cable in? I attached a screenshot for you (or a edit of yours cause im using a windows laptop god forbid me)

---

### Post by Berean on 2008-04-14
> **GCoffee said:**
> Make sure you wg111v2 adapter is plugged in and then single click the circled icon. see if your network is listed. if so try to connect to it, take the lan cable out if you need to. Its not the best soloution but if it gets desperate couldn't you just leave the lan cable in? I attached a screenshot for you (or a edit of yours cause im using a windows laptop god forbid me)

Actually, I did know what to do!  Thank you.  There is no wireless network to connect to.  I have installed Network Selector, and it says "Wireless disabled".  How do I enable it?  I take your point about the LAN cable, but as this is my only PC I want the continued portability of a laptop.

---

### Post by GCoffee on 2008-04-14
you can enable it by going to system>administration>network. If it isnt in administration look in system>preferences

---

### Post by GCoffee on 2008-04-14
amazing how simple soloutions evade detection for such a long time...

---

### Post by GCoffee on 2008-04-14
i will check this thread later to see if it has fixed your problem. i have to go.

---

### Post by Berean on 2008-04-14
> **GCoffee said:**
> amazing how simple soloutions evade detection for such a long time...

GCoffee,

Thanks so much for all your help.  However, it's not there, and so I'm thinking of reinstalling my 7.10 or perhaps upgrading to 8.04.  I'm running this in the Live CD at present, as my installed Ubuntu keeps hanging, crashing, or switching off completely.  Once again, thank you, and I'll let you know how I get on!  Kind regards, berean.:)

---

### Post by Berean on 2008-04-16
Hi,

An update: One of my RAM modules was defective hence the reason the system keeps hanging, crashing, or generally working intermittently.  Also, unbelievably, my Netgear DG834G router was broken, so - now with a new one - everything is working fine!  Therefore, this thread is now solved!  Yippee!

---

