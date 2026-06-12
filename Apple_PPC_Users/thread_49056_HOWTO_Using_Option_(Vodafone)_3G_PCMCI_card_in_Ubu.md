---
title: "HOWTO: Using Option (Vodafone) 3G PCMCI card in Ubuntu PowerPC"
date: 2005-07-14
forum: Apple PPC Users
---

### Post by eduardgrebe on 2005-07-14
I have been using a Vodafone-branded Option 3G (UMTS) PCMCIA modem in Mac OS X on my Powerbook G4 and had struggled to use it under Hoary PPC. I found an excellent HOWTO for using the card under linux by Tazz_Tux here: [http://mybroadband.co.za/vb/printthread.php?t=21726](http://mybroadband.co.za/vb/printthread.php?t=21726). However, his instructions didn't work immediately on hoary ppc.

I use it with the Vodacom network in South Africa, but you can just replace network-specific items with the relevant info for your network.

First, ensure that your PCMCIA services are running and that the OS is detecting the card when it's inserted. This should work automatically. 

In order for ubuntu to handle the modem correctly and create appropriate aliases you must load the serial_cs module as follows:
```
sudo modprobe serial_cs
```

Then check your syslog to make sure the card is properly initialised. Type the following:
```
sudo tail -f /var/log/syslog
```
When you insert the card, you should see something like the following:
```

Jul 14 23:53:48 localhost kernel: ohci_hcd 0001:11:00.0: OPTi Inc. 82C861 (#3)
Jul 14 23:53:48 localhost kernel: ohci_hcd 0001:11:00.0: irq 53, pci mem 0xf3000000
Jul 14 23:53:48 localhost kernel: ohci_hcd 0001:11:00.0: new USB bus registered, assigned bus number 5
Jul 14 23:53:48 localhost kernel: ohci_hcd 0001:11:00.0: WARNING: OPTi workarounds unavailable
Jul 14 23:53:48 localhost kernel: hub 5-0:1.0: USB hub found
Jul 14 23:53:48 localhost kernel: hub 5-0:1.0: 2 ports detected
Jul 14 23:53:49 localhost pci.agent[13878]:      ohci-hcd: already loaded
Jul 14 23:53:49 localhost usb.agent[13922]:      usbcore: already loaded
Jul 14 23:53:56 localhost kernel: usb 5-1: new full speed USB device using ohci_hcd and address 2
Jul 14 23:53:56 localhost kernel: usbserial_generic 5-1:1.0: Generic converter detected
Jul 14 23:53:56 localhost kernel: usb 5-1: Generic converter now attached to ttyUSB0
Jul 14 23:53:56 localhost kernel: usbserial_generic 5-1:1.1: Generic converter detected
Jul 14 23:53:56 localhost kernel: usb 5-1: Generic converter now attached to ttyUSB1
Jul 14 23:53:56 localhost kernel: usbserial_generic 5-1:1.2: Generic converter detected
Jul 14 23:53:56 localhost kernel: usb 5-1: Generic converter now attached to ttyUSB2
```

You now have a generic USB modem set up at /dev/ttyUSB0.

Let's use wvdial to handle the ppp connection. Edit/create /etc/wvdial.conf. Mine is as follows:

```

[Dialer Defaults]

Phone = *99***1#
Username = username
Password = password
Stupid Mode = 1
Dial Command = ATDT

[Dialer pin]

Init1 = AT+CPIN=1234

[Dialer option]

Modem = /dev/ttyUSB0
Baud = 460800
Init2 = ATZ
Init3 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ISDN = 0
Modem Type = Analog Modem

[Dialer 2gonly]

Init4 = AT+COPS=0,0,"Vodacom-SA",0

[Dialer 3gonly]

Init4 = AT+COPS=0,0,"Vodacom-SA",2

[Dialer internet]

Init5 = AT+CGDCONT=1,"IP","internet";

[Dialer internetvpn]

Init5 = AT+CGDCONT=1,"IP","internetvpn";

[Dialer myapn]

Init5 = AT+CGDCONT=1,"IP","myapn"

[Dialer 384k]

Init6 = AT+CGEQMIN=1,4,64,384,64,384
Init7 = AT+CGEQREQ=1,4,64,384,64,384

[Dialer 144k]

Init6 = AT+CGEQMIN=1,4,64,144,64,144
Init7 = AT+CGEQREQ=1,4,64,144,64,144

[Dialer 64k]

Init6 = AT+CGEQMIN=1,4,64,64,64,64
Init7 = AT+CGEQREQ=1,4,64,64,64,64


```

You will need to change some of the settings in the file according to your local network. I think the phone number *99***1# is used by all networks for packet switched data, but check with your network. Importantly, you must replace the digits 1234 in the [pin] section with your sim card's PIN. The sections [Dialer internet], [Dialer myapn] and [Dialer myapn] sets up three APNs used by the Vodacom network. Again, check with your network, but "internet" is likely to work.

Once you've configured wvdial, you can use it to establish the ppp connection. You can call sections of wvdial.conf in the command line. 

However, here I experience an irritating problem. The Option card takes about 10 seconds or so after being passed the PIN before it is ready to dial (you can see when it's ready because the green LED will stop flashing, leaving only the blue LED flashing). My wvdial tries to dial before the modem is ready and the ppp connection fails. I therefore run the following, but must press control-C and and run the dialer again before it works.

```

wvdial pin option internet 3gonly 384k
(press ^C after the PIN has been passed to the modem, wait until green LED stops flashing)
wvdial option internet 3gonly 384k

```

Ideally, one should tell wvdial to wait 10 seconds between running the [pin] section and the rest, but I don't know how to do this. Another alternative is to run a terminal app like minicom and manually pass AT+CPIN=1234 to the modem before running wvdial (without the pin flag).

If you want to dial again later without having unplugged the modem, you can use only:

```

wvdial option internet 3gonly 384k

```

It is a good idea to switch off the card before unplugging by typing
```

sudo cardctl eject

```

---

### Post by marlight on 2005-09-09
eduardgrebe, thanks for the great info - it helped me get the UK version of this card working!

I had to tweak a couple of things and thought I would post the info here to help anybody else in the UK who needs to get this working.

Background: I run Ubuntu 5.04 ("Hoary Hedgehog") on an Intel based laptop, an Acer Travelmate 382 tmi.  (I know, this is the PPC forum, but it's also one of the first links Google threw up on my search for knowledge. Apologies for intruding ;-) )

The UK version of this card reports itself as a "Fusion UMTS Quad-GPRS". It is 3G (UMTS), GPRS, and GSM, with no WiFi.

In [his post](http://mybroadband.co.za/vb/printthread.php?t=21726)  that you linked to, Tazz_tux loads usbserial with the vendor and product IDs. Using the information from /proc/bus/usb/devices gave me different vendor and product IDs from the ones Tazz_tux posted, so the modprobe command to load usbserial became:

```
sudo modprobe usbserial vendor=0x0af0 product=0x6300
```

Next I insert the card while running a 'tail -f /var/log/messages', and I can see that the card loads and links serial ports to /dev/ttyUSB[0,1,2,3].  Good old minicom let's me connect to '/dev/ttyUSB0' and '/dev/ttyUSB2'.  (Having the two lines of communication is very useful once the connection is up and running. Once pppd has grabbed ttyUSB0, for example, you can connect to ttyUSB2 to communicate with the card to check things like signal strength.)

I had to tweak the '/etc/wvdial.conf' configuration that you posted, but only the provider name for the "COPS" settings.

The configuration that I ended up with was:
```

[Dialer Defaults]
Phone = *99***1#
Username = username
Password = password
Stupid Mode = 1
Dial Command = ATDT

[Dialer pin]
Init1 = AT+CPIN=1234

[Dialer option]
Modem = /dev/ttyUSB0
Baud = 460800
Init2 = ATZ
Init3 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ISDN = 0
Modem Type = Analog Modem

[Dialer 2gonly]
Init4 = AT+COPS=0,0,"Vodafone",0

[Dialer 3gonly]
Init4 = AT+COPS=0,0,"Vodafone",2

[Dialer internet]
Init5 = AT+CGDCONT=1,"IP","internet";

[Dialer internetvpn]
Init5 = AT+CGDCONT=1,"IP","internetvpn";

[Dialer myapn]
Init5 = AT+CGDCONT=1,"IP","myapn"

[Dialer 384k]
Init6 = AT+CGEQMIN=1,4,64,384,64,384
Init7 = AT+CGEQREQ=1,4,64,384,64,384

[Dialer 144k]
Init6 = AT+CGEQMIN=1,4,64,144,64,144
Init7 = AT+CGEQREQ=1,4,64,144,64,144

[Dialer 64k]
Init6 = AT+CGEQMIN=1,4,64,64,64,64
Init7 = AT+CGEQREQ=1,4,64,64,64,64

```

I also configured '/etc/ppp/peers/wvdial' as:
```

plugin passwordfd.so
noauth
name wvdial
replacedefaultroute
noipdefault
nomagic
usepeerdns
ipcp-accept-local
ipcp-accept-remote
nomp
noccp
nopredictor1
novj
novjccomp
nobsdcomp

```

Some of the settings in there may not be required, but this is working for me now so I'm leaving it as is :-)

Once that is all set up we can dial.

One difference to note when dialling is that the card that I currently have doesn't require the pin number to be set. The card is on loan to me on a trial from a service provider trying to get some business, so this may change if we go ahead and get some actual cards allocated.

So, the dial command becomes:
```

wvdial option internet 3gonly 384k

```

I takes a few seconds to get an IP address allocated, so if you are trying this you may need to wait up to 15 seconds, maybe a little longer, for the Vodafone PPP servers to throw you an IP bone.

Next I need to tweak hotplug to load 'usbserial' correctly for this card when it's plugged in, and link the appropriate ttyUSB? device to /dev/modem. I'll post details when (if!) I get this working.

One problem to be aware of if you have the same hardware combo is that if I run 'cardctl eject' it freezes my laptop deaddeaddead, no keyboard response, nothing at all. YMMV, but be aware of this.

---

### Post by daller on 2006-11-17
I get an error on running the command:

wvdial pin option internet 3gonly 384k

```
--> WvDial: Internet dialer version 1.56
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: AT+CPIN=6829
OK
--> Sending: ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Sending: AT+COPS=0,0,"Vodacom-SA",2
OK
--> Sending: AT+CGDCONT=1,"IP","internet";
OK
--> Sending: AT+CGEQMIN=1,4,64,384,64,384
OK
--> Sending: AT+CGEQREQ=1,4,64,384,64,384
OK
--> Modem initialized.
--> Sending: ATDT*99***1#
--> Waiting for carrier.
--> Timed out while dialing.  Trying again.
--> Sending: ATDT*99***1#
--> Waiting for carrier.
ERROR
--> Invalid dial command.
--> Disconnecting at Fri Nov 17 21:45:01 2006
```

The "username" and "password" is just left "as is"?

The last lines of dmesg:

```
[17179808.312000] usb usb6: configuration #1 chosen from 1 choice
[17179808.312000] hub 6-0:1.0: USB hub found
[17179808.312000] hub 6-0:1.0: 1 port detected
[17179810.684000] ohci_hcd 0000:03:00.1: wakeup
[17179811.068000] usb 6-1: new full speed USB device using ohci_hcd and address 2
[17179811.280000] usb 6-1: configuration #1 chosen from 1 choice
[17179811.648000] usbcore: registered new driver usbserial
[17179811.648000] drivers/usb/serial/usb-serial.c: USB Serial support registered for generic
[17179811.648000] usbcore: registered new driver usbserial_generic
[17179811.648000] drivers/usb/serial/usb-serial.c: USB Serial Driver core
[17179811.668000] drivers/usb/serial/usb-serial.c: USB Serial support registered for Option 3G data card
[17179811.668000] option 6-1:1.0: Option 3G data card converter detected
[17179811.668000] usb 6-1: Option 3G data card converter now attached to ttyUSB0
[17179811.668000] option 6-1:1.1: Option 3G data card converter detected
[17179811.672000] usb 6-1: Option 3G data card converter now attached to ttyUSB1
[17179811.672000] option 6-1:1.2: Option 3G data card converter detected
[17179811.672000] usb 6-1: Option 3G data card converter now attached to ttyUSB2
[17179811.672000] option 6-1:1.3: Option 3G data card converter detected
[17179811.672000] usb 6-1: Option 3G data card converter now attached to ttyUSB3
[17179811.672000] usbcore: registered new driver option
[17179811.672000] drivers/usb/serial/option.c: Option Card (PC-Card to) USB to Serial Driver: v0.4
```

---

### Post by eduardgrebe on 2006-11-25
I now use a much simpler way of dialing up. While I use a Huawei HSDPA card now, this should work just as well on the Option card. 

In order to pass the pin to the card I use a simple utility called gcom. It is available in the universe repository. Gcom allows a range of interactions with the Option card, but if only the device is passed asks for the pin. You can also pass the pin using the command line.

After plugging in the card:
```
gcom -d /dev/ttyUSB0
```
and type in your pin. You should see the card registering on the network and it should tell you signal strength.

Then you can easily dial using pppd. To set up your pppd scripts create the following two files (I call them vodacom since this is the name of my cell network):

/etc/ppp/peers/vodacom
```

noauth
connect "/usr/sbin/chat -v -f /etc/chatscripts/vodacom"
debug
/dev/ttyUSB0
115200
defaultroute
lcp-echo-interval 65535

```

and /etc/chatscripts/vodacom
```

# This chatfile was generated by pppconfig 2.3.10.
# Please do not delete any of the comments.  Pppconfig needs them.
# 
# ispauth chat
# abortstring
TIMEOUT         15
ECHO            ON
HANGUP          ON
'' ATZ
OK AT+CGDCONT=1,"IP","internet"
OK              "ATDT*99*111#"
CONNECT         ''

```

What may need to change for your network is the access point "internet" for Vodacom and many other networks, but your network should tell you what the access point is called as well as the dialup number: *99*111# works on most networks and so does *99# but you should also confirm this with your network.

Once you've defined the scripts,
```
pon vodacom
``` should dial up to the network. Use ```
tail -f /var/log/messages
``` to track what is happening and if you see IP addresses you're most likely on the network.

Remember that you'll have to execute gcom every time you've plugged in the card before you can dial. I use a script to dial up that simply executes the above commands:
```

gcom -d /dev/ttyUSB0
pon vodacom
tail -f /var/log/messages

```

---

### Post by daller on 2006-11-25
Thank you for your reply!

I've tried this some time ago, and it seemed to work!

But now it asks for a PUK code! - Guess I made a mistake in the script I made! (making it connect to the card several times with the wrong pin!)

And I've tried to use the SIM in my phone! (It's rejected since it's not a 3G cellphone!)

---

### Post by gillan on 2006-12-19
Hi There

Thanx for the help, one question though. as soon as the string 

AT+COPS=0,0,"Vodacom-SA",2

is sent, I get an error message in the terminal window  TOO MANY PARAMETERS. I have rechecked, even copied and pasted the text from the forum and I still get this message.  Can you help.

---

### Post by justinlawrence on 2007-04-24
> **gillan said:**
> Hi There

Thanx for the help, one question though. as soon as the string 

AT+COPS=0,0,"Vodacom-SA",2

is sent, I get an error message in the terminal window  TOO MANY PARAMETERS. I have rechecked, even copied and pasted the text from the forum and I still get this message.  Can you help.

I solved this by adjusting the wvdial command,  like so:

wvdial option internet && sleep 5 && 3gonly 384k

hope this helps!

---

### Post by ranpha on 2007-12-26
Hi 

I'm using a Sierra Wireless MC8780 builtin modem.

and i can dial and get a IP

only no internet yet

---

