---
title: "Broadband modems"
date: 2007-03-31
forum: Absolute Beginner Talk
---

### Post by stenella on 2007-03-31
Hi,
I'm thinking of installing Ubuntu. Tried Linux a couple of years ago and couldn't get my broadband modem working. I was told at the time that this was the manufacturers fault for not writing one for Linux. That may be true, but wasn't a lot of help. . At the moment I have a d-link 362-t, which I bought here in the Czech Republic, where I live at the moment. Their website doesn't even mention it when I went looking for a driver...typical

So, the question is. What Broadband modems exist that do have drivers available?

I'd really appreciate any advice as I'm not only a Linux noob, but am, by trade a painter and am a lot better with brush and canvas than coding etc.
Cheers.

---

### Post by NikoC on 2007-03-31
At home I have a Belkin wireless router for which I didn't have to install anything... I think the critical point is the wireless card in your machine! E.g. in my laptop is an ipw2200 which worked flawlessly out of the box and from which I can access my router's 'homepage', i.e. 192.168.2.1, from a browser window without any extra installation.

---

### Post by ramjet_1953 on 2007-03-31
With a broadband router, it shouldn't really matter, as long as it is 10Base/100Base T.
However one qualification needs to be made. DO NOT use a USB ADSL Modem. They tend to be locked to Windows, like dial-up WinModems.

If the router is plugged-in and powered-up, your system should see it as a network connection and if need be, just tell Ubuntu that you connect to the Internet via the LAN.

As was previously mentioned, I think the real issue is whether or not Ubuntu is seeing your NIC.

Regards,
Roger :cool:

---

### Post by stenella on 2007-03-31
Cheers,guys

That really simplifies things. i don't have a wireless card in the computer - for now - but the modem has an ethernet cable. Windows keeps losing the ethernet connection... Well, deep breath, I guess it's time to give it a shot.
Thanks again

---

### Post by TheAMan on 2007-05-14
I have successfully configured 7.04 Feisty and access to the Optus 3G wireless broadband using the Fusion GT 3G Quad card.  My setup is a Lenovo T60P (widescreen). I have not worked out how to use the internal Sierra wireless card yet which seems to be locked for Vodaphone... if anyone has any idea how to do this for the T60P please post!

To connect to broadband wireless using the Fusion PC Card:
1) Plug in the card
2) Find out the /dev of the USB port by running
>$ dmesg
This should provide an output like...

[61726.772000] usb usb7: configuration #1 chosen from 1 choice
[61726.772000] hub 7-0:1.0: USB hub found
[61726.772000] hub 7-0:1.0: 1 port detected
[61728.940000] usb 7-1: new full speed USB device using ohci_hcd and address 2
[61729.152000] usb 7-1: configuration #1 chosen from 1 choice
[61729.156000] option 7-1:1.0: GSM modem (1-port) converter detected
[61729.156000] usb 7-1: GSM modem (1-port) converter now attached to ttyUSB3
[61729.160000] option 7-1:1.1: GSM modem (1-port) converter detected
[61729.160000] usb 7-1: GSM modem (1-port) converter now attached to ttyUSB4
[61729.164000] option 7-1:1.2: GSM modem (1-port) converter detected
[61729.164000] usb 7-1: GSM modem (1-port) converter now attached to ttyUSB5
[61729.164000] option 7-1:1.3: GSM modem (1-port) converter detected
[61729.164000] usb 7-1: GSM modem (1-port) converter now attached to ttyUSB6

Now you should be able to use this for configuring the Modem in network connections which I tried but while I it seemed to successfully connect, get the right DNS and IP assigned I could not get through. I found this logged bug with no resolution [https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/94304](https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/94304)

2)... so turned to using GNOME PPP (installed it via Synaptic). This uses wvdial. 
3) Launch Applications->Internet->GNOME PPP
4) Set Username/pw to anything you like (it doesn't matter) and Phone number to *99***1#
4) Go into the Setup and set:
Options ->
Device : /dev/ttyUSB3 (or whatever dmesg says is free)
Type : USB Modem
Speed : 460800
Phone : Tone
Init String : init 1 was simply ATZ
Options -> select stupid mode

Hit connect... that worked for me.

If you are having problems I recommend just going through WvDial and editing the /etc/wvdial.conf.The settings above would look like

[Dialer Defaults]
Phone = *99***1#
Username = aa
Password = aa
New PPPD = yes
Stupid Mode = 1
Modem = /dev/ttyUSB3
Baud = 460800
Init1 = ATZ

You should see the negotiation and connection info to help you with problems.

Apart from the problem with the network manager app I was pleasantly surprised that this worked!

I hope someone finds this helpful
Regards,
Andrew

---

