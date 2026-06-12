---
title: "usb modems"
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by Malherbe on 2008-02-12
New to ubuntu

After downloading and installing ubuntu, i found out that i can not do the most basic thing - connect to the internet with a wireless usb modem ! I use a slipstream modem manufactured by thetalogix in South Africa. Can anybody help me out regarding driver etc for usb wirelss modems. Also how to install the drivers if any available for linux. Without the ability to connect to the web, ubuntu means nothing to me.   
Any help would be appreciated !

Thanks       [http://ubuntuforums.org/images/smilies/icon_smile.gif](http://ubuntuforums.org/images/smilies/icon_smile.gif)
:)

Mal

---

### Post by Peryl on 2008-02-12
Can you please post specific information?

A model number would greatly speed up the process

---

### Post by immesys on 2008-02-22
I know I'm bumping this, but I have spent the last three weeks trying to find drivers for the exact modem. Its a Thetalogix Slipstream modem. 

I also found out that the slipstream card is an Option Globetrotter or something like that, just a little modified. So I tried the Vodacom/Vodafone driver project, but it never found the modem even if I booted with it in. If you want to try your luck, here's the URL: 
[https://forge.vodafonebetavine.net/projects/vodafonemobilec/](https://forge.vodafonebetavine.net/projects/vodafonemobilec/)

Its supposed to work with the slipstream card, I suspect it doesn't because the card acts like a usb hub with a flash drive/Cd drive and modem (which probably boggles the driver along the way). Thanks Thetalogix... those gimicky things always make peoples lives SO much more fun...

The thetalogix people say on their website that the slipstream modem is supposed to have linux drivers, but I can't find them on the website or the internet... when I emailed them, they ignored me... thanks Thetalogix.

Anyway, if anyone has had any luck with this card, please post... I'm desperate.

---

### Post by immesys on 2008-02-22
I emailed them again and got a reply!

They sent me the following instructions (For fedora), although I haven't tested them

> 

Linux Installation Guide
SlipStream
T1200
Tested on Fedora Core 5/6
2.6 Kernel only
Copyright © Thetalogix (Pty) Ltd 2007 All Rights Reserved.


The following steps outline SlipStream mini-modem installation on Linux:
1. Open a new terminal and log in as root by using the "su" command if you are running the X server.

2. For a 1.8 Mbps module type:
modprobe usbserial vendor=0xaf0 product=0x6501.
For a 3.6 Mbps module type:
modprobe usbserial vendor=0xaf0 product=0x6901

3. Monitor the messages log to determine whether Linux recognizes the modem by typing:
tail -f /var/log/messages

4. Plug in the modem, and the log should output or something similar:
kernel: usb 3-1: new full speed USB device using uhci_hcd and address 7
kernel: usb 3-1: configuration #1 chosen from 1 choice
kernel: usbserial_generic 4-2.2:1.0: generic converter detected
usb 4-2.2: generic converter now attached to ttyUSB0
kernel: usbserial_generic 4-2.2:1.1: generic converter detected
usb 4-2.2: generic converter now attached to ttyUSB1
kernel: usbserial_generic 4-2.2:1.2: generic converter detected
usb 4-2.2: generic converter now attached to ttyUSB2

5. The "usbserial_generic" describes the driver being used, and take note of the device nodes, in this
case "ttyUSB0", "ttyUSB1", and "ttyUSB2". The next steps assumes the device nodes are "ttyUSB0",
"ttyUSB1", and "ttyUSB2", therefore, replace the "ttyUSB0", "ttyUSB1", or "ttyUSB2" where needed.

6. Press Ctrl-C

7. Ensure that each device node has been created in etc/ by typing:
ls /dev |grep ttyUSB

8. This should return "ttyUSB0", "ttyUSB1", and "ttyUSB2". If this has not been returned, manually create
the nodes by typing:
mknod /dev/ttyUSB0 c 188 0
mknod /dev/ttyUSB0 c 188 1
mknod /dev/ttyUSB0 c 188 2

9. Finally, set the priviledges of the device nodes by typing:
chmod 777 /dev/ttyUSB0
chmod 777 /dev/ttyUSB1
chmod 777 /dev/ttyUSB2

10. The modem should now be useable.


Configuring the modem for within X using system-config-network
1. Open a new terminal and log in as root by using the "su" command.

2. Open system-config-network by typing:
neat

3. Go to the Hardware Tab, and click New.

4. Select Modem from the list, and click Ok.

5. Complete the fields as follows:
Modem device: /dev/ttyUSB0
Baud rate: 115200
Flow control: None
Modem Volume: Off
Use touch tone dialing: checked.

6. Click Ok

7. Go to the Devices Tab, and click New.

8. Select Modem connection from the Device Type List, and click Forward.

9. Complete the fields as follows:
Phone number: *99***1#
Provider Name: SlipStream
Login name: none
Password: none
Note: The Login name and password should reflect your APN login name and password. You must enter
a Login name and Password if you wish to continue.

10. Click on Forward, Forward, Apply.

11. Select SlipStream within the list, and click Edit.

12. Go to the Advanced Tab and complete the Modem initialization string field as follows:
Modem initialization string: at+cgdcont=1,&#8221;ip&#8221;,&#8221;internet&#8221;
Note: Replace "internet" in the Modem initialization string with the required APN if needed. The quotation
marks must not be omitted.

13. Complete all other settings as needed. You may wish tick the Restart if connection dies checkbox,
and enable compression under the Compression Tab.

14. Click Ok.

15. The modem should now be configured to dial. To do this, select SlipStream from the list and click
Activate. See steps 12 and 13 form the "Configuring the modem for dialing outside X" section if you wish
to dial using the console.


---

