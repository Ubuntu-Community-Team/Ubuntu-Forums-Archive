---
title: "Trust Bluetooth v2.0 EDR &amp; Ubuntu v6.10 - Help!!!"
date: 2006-11-22
forum: Absolute Beginner Talk
---

### Post by dvarsam on 2006-11-22
Hello all!

Today I bought a Bluetooth Device.

The _Model_ is: **Trust BT-2210Tp Bluetooth 2.0 EDR USB Adapter**

I am trying to make it work in my Ubuntu v6.10.

I followed the instructions on the following link:

[https://help.ubuntu.com/community/BluetoothSetup](https://help.ubuntu.com/community/BluetoothSetup)

And got the following results:

**1.** I verified that the package "**bluez-utils**" is installed on my Ubuntu.

**2.** I restarted the Bluetooth services by doing:

> root@dimitris-desktop:/# **sudo /etc/init.d/bluetooth restart**
 * Restarting Bluetooth services                                     [ ok ] 


**3.** Verified whether my bluetooth device has been detected & the appropriate modules loaded by viewing the "**lsusb**" output (in case of usb device) output:

> root@dimitris-desktop:/# **lsusb**
Bus 003 Device 004: ID 0a5c:2121 Broadcom Corp. 
Bus 003 Device 003: ID 0df7:0620 Mobile Action Technology, Inc. MA-620 Infrared Adapter
Bus 003 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 051d:0002 American Power Conversion Back-UPS Pro 500/1000/1500
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 005: ID 0a48:3240 I/O Interconnect 
Bus 002 Device 001: ID 0000:0000

It _must_ be the line that goes "Bus 002 Device 005: ID 0a48:3240 I/O Interconnect".

Unfortunately, I am not getting straightforward info, or something like this:
"Device 005: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)"

**4.** I viewed the output of the command "**hcitool dev**" which gave me a listing of bluetooth devices on my computer:

> root@dimitris-desktop:/# **hcitool dev**
Devices:
        hci0    00:0B:0D:4C:3A:16

_Note_:
Since I am not getting "all zeros", I do NOT need to restart the "bluez-utils" service & try again.

**5.** Now I need to connect to my Bluetooth device & I need to find the address of my device.
> Make the device discoverable (look for a "Connect" button on many keyboards and mice or look in the device's manual)...

_Note_:
Unfortunately there is no Keyboard button labeled "Connect", NOR is there a such a button on my Mouse...

...And then I performed a search for the device, with this command:

> root@dimitris-desktop:/# **sudo hidd --search**
Searching ...
root@dimitris-desktop:/#

_Note_:
The Bluetooth's blue light is ON at all times.
While the process was under "Searching...", I noticed that my Trust's Bluetooth USB, blue light started blinking for about 20 times!
And then it got back to previous state (stopped blinking & turned ON again) & I got NO output!

Is there some other output, I should have got here?

**6.** Then, I tried to temporarily connect to my device, and used the following command:

> **sudo hidd --connect 00:0B:0D:4C:3A:16**
Can't get device information: No route to host
root@dimitris-desktop:/#

_Note_:
The "00:0B:0D:4C:3A:16", is the address of the device, I am trying to connect to (An address I got from the output of Step4 above).

In this step, my Bluetooth device should have connected for the current session...

If I had got a "Can't create HID control channel: Connection refused" error message, most likely the discovery period for the device would have timed out.
And I would have made the device discoverable & enter the above command again, but more quickly!

But I am getting a different message:

> **Can't get device information: No route to host**

What does the above mean?

What am I doing wrong?

Please help?

Thanks.

---

### Post by Zalbor on 2006-11-23
Following that guide, I have the same problem with hidd --search. Nothing is found (I'm looking for my mobile, which is easily found by other mobiles and in windows). As for the next, the reason it doesn't work is that you should try to connect to the device, whose number you're supposed to get by searching...

---

### Post by dvarsam on 2006-11-23
> **Zalbor said:**
> Following that guide, I have the same problem with hidd --search. Nothing is found (I'm looking for my mobile, which is easily found by other mobiles and in windows).

> As for the next, the reason it doesn't work is that you should try to connect to the device, whose number you're supposed to get by searching...

So, where does the problem lie?

_Question_:

a. Is my Bluetooth USB device, I purchased not compatible with linux?
(...& I need to purchase a different model from different manufacturer...)

OR

b. Somebody provided "faulty" directions on how to make our Bluetooth devices work with our Ubuntu Linux PCs?

Thanks.

P.S.> If case "a" is the right answer, what Bluetooth USB device have you managed to make work with Ubuntu? (Please provide your model & manufacturer - in this case, I need to know what models to look for, in my local Computer Stores...)

---

### Post by Zalbor on 2006-11-23
I think it's just a bug on how bluetooth is configured to work on edgy. I'm not sure though.

---

### Post by dvarsam on 2006-11-23
> **Zalbor said:**
> I think it's just a bug on how bluetooth is configured to work on edgy. I'm not sure though.

So, what do I do?

I visited the Ubuntu wiki:

[https://wiki.ubuntu.com/HardwareSupport](https://wiki.ubuntu.com/HardwareSupport)

And saw that there is NO Bluetooth device listed in there.

So, I created one listing in there.

You can take a look here:

[https://wiki.ubuntu.com/Trust_Bluetooth_2%2e0_EDR_USB_Adapter](https://wiki.ubuntu.com/Trust_Bluetooth_2%2e0_EDR_USB_Adapter)

Can anybody provide help, so I can then update the info in the Hardware Support page with the results?

Thanks.

P.S.> I bet that there must be other Ubuntu users with Bluetooth USB Sticks. So, no matter if your Bluetooth USB Sticks are functional or not, please go & add your Hardware products in the page above, so that we can all have a good hardware database, please... We all need to know what Hardware will be functional in our Ubuntu OS!

---

### Post by Zalbor on 2006-11-25
The method might not work, but at least you can still transfer files (at least you can with my mobile). Edit the /etc/bluetooth/hcid.conf file, so that it says "security auto;" and below change the PIN to one you want to use. Start the pairing process with the other device and enter that same PIN, they should get paired.
Now you can install the gnome-bluetooth package (if you're using gnome) and "Bluetooth file sharing" will appear in accessories. Get it running (I've set it to run at startup). If you send a file from the other device, it will be automatically saved on the desktop.
Now, sending a file to the other device is harder. Find the file on your drive, right-click and "send to". The other device won't be in the list at first, but if you try to use it to connect to your PC a few times (even if it fails) it will appear, so you can send a file from the PC...

---

### Post by dvarsam on 2006-11-28
Dear "Zalbor",

Thanks for your reply!

> **Zalbor said:**
> The method might not work, but at least you can still transfer files (at least you can with my mobile).

Edit the /etc/bluetooth/hcid.conf file, so that it says "security auto;" & below change the PIN to one you want to use.
Start the pairing process with the other device & enter that same PIN, they should get paired.

I did this but it did not work...

It only worked under Windows, where I was asked to define a PIN in the Windows PC & before each connection I had to type the same PIN in the Mobile Phone.

From the Mobile Phone I asked it to Search for Bluetooth Devices & it did NOT find any!

> Now you can install the gnome-bluetooth package (if you're using gnome) & "Bluetooth file sharing" will appear in accessories.
Get it running (I've set it to run at startup).

OK, I installed it as you suggested & from Menu, I selected "Applications\Accessories\Bluetooth File Sharing".

> If you send a file from the other device, it will be automatically saved on the desktop.

Again:

From the Mobile Phone I asked it to Search for Bluetooth Devices & it did NOT find any!

> Now, sending a file to the other device is harder.
Find the file on your drive, right-click & "send to".
The other device won't be in the list at first, but if you try to use it to connect to your PC a few times (even if it fails) it will appear, so you can send a file from the PC...

This step does not worth it if my Mobile Phone can NOT detect any Bluetooth Devices...

Any other ideas?

Thanks.

---

### Post by Bazzaah on 2006-12-01
I had the exact same problem as you.

I went to synaptic and got all files relating to Bluetooth and Gnome that I could find.

I've just sent a couple of files from my phone to my PC. 

Excellent, yet another reason not to go back to Windows.

As Bluetooth is now so common, I don't know why Bluetooth files aren't included in the install CD. Now I have the right files installed, Bluetooth works just fine, but I didn't know that I didn't have the right files installed.

Maybe those clever people at Automatix could add it to the list of what that package can install.

---

### Post by dvarsam on 2006-12-01
Dear "Bazzaah",

thanks for your reply!

[QUOTE=Bazzaah]I had the exact same problem as you.

I went to synaptic and got all files relating to Bluetooth and Gnome that I could find.

I've just sent a couple of files from my phone to my PC.[/QUOTE]

Can you confirm that the files you sent from your Mobile Phone to the PC, were sent by using _this_ mentioned Hardware:

> Trust Bluetooth BT-2210Tp v2.0 EDR

OR:

Are you talking about a different Bluetooth Adapter Model?

Because I need to update the wiki.ubuntu.com Hardware info page, if _you_ & _me_ are talking about the _same_ Bluetooth Adapter Model!

Thanks.

P.S.> Also, the response from the "Trust Company was the following:

From: 	Support HQ EXP <Support2.exp@trust.com>
Sent : 	Thursday, November 23, 2006 10:48 AM

Message:
Dear Customer,
Sorry to hear that the Bluetooth 2.0 EDR USB Adapter not works,
But we don't have drivers for Linux.

Kind regards,
Trust customer care

---

### Post by dvarsam on 2006-12-01
Hello again!

One more thing to add here:

After the following response I got from the "Trust Company":

[QUOTE=dvarsam]Dear Customer,
Sorry to hear that the Bluetooth 2.0 EDR USB Adapter not works,
But we don't have drivers for Linux.

Kind regards,
Trust customer care[/QUOTE]

I returned the product to the computer store & purchased instead the following Bluetooth Adaptor which works great with my Ubuntu v6.10:

_Model_: **D-Link DBT-122 Usb Bluetooth Adapter**

_Purchase Date_: **2006-11-28**

To find out HOW TO make it work with your Ubuntu v6.10, visit the wiki.ubuntu.com at the following link:

[https://wiki.ubuntu.com/D-Link_DBT-122_USB_Bluetooth_Adapter](https://wiki.ubuntu.com/D-Link_DBT-122_USB_Bluetooth_Adapter)

Thanks.

---

### Post by Bazzaah on 2006-12-01
I use a Belkin adapter, which is working fine now at least for phone to PC. I've yet to get the PC to phone working but think that should be solveable given that it works the other way around.

I received the same set of messages until that you mention in your OP until I installed the apps I did this morning.

So it's not much use for your Wiki update.

---

### Post by Loranga on 2006-12-15
FYI, I have a CNet cbd-021 (Class II) USB Bluetooth adapter, which I can send files from PC to Phone, but not the other way. This seems to be the opposite compared with your other cases.

To be honest I haven't really got this device working 100% properly in Windows either.

I am very jealous on my Mac friends which seems to have Bluetooth working automagically in OS X.

---

### Post by cracker on 2006-12-15
I have a similar problem...I posted [here](http://ubuntuforums.org/showthread.php?t=318814), but haven't gotten any response. I have a Soliel USB Bluetooth adapter and a Motorola Razr V3, and I'm trying to get connected so I can get the pictures off my phone. I followed the instructions here, though most of this was already set up out of the box: [https://help.ubuntu.com/community/BluetoothSetup](https://help.ubuntu.com/community/BluetoothSetup)

Here is the adapter in lsusb:
```
Bus 001 Device 004: ID 1131:1001 Integrated System Solution Corp. KY-BT100 Bluetooth Adapter
```

The problem I'm having is that the phone won't show up. This is what happens when I have the 'Find Me' on my phone running:
```
ryan@ryana64:~$ sudo hidd --search
Searching ...
ryan@ryana64:~$ 
```

After the time has passed and it is no longer discoverable, here is what happens:
```
ryan@ryana64:~$ sudo hidd --search
Searching ...
        No devices in range or visible
ryan@ryana64:~$ 
```

Here's a little more information:

```
ryan@ryana64:~$ sudo hciconfig
hci0:   Type: USB
        BD Address: 00:11:67:0B:D9:91 ACL MTU: 678:8 SCO MTU: 64:10
        UP RUNNING PSCAN ISCAN 
        RX bytes:995 acl:0 sco:0 events:61 errors:0
        TX bytes:709 acl:0 sco:0 commands:41 errors:0

ryan@ryana64:~$ dmesg | grep Bluetooth
[17179597.216000] Bluetooth: Core ver 2.8
[17179597.216000] Bluetooth: HCI device and connection manager initialized
[17179597.216000] Bluetooth: HCI socket layer initialized
[17179597.256000] Bluetooth: L2CAP ver 2.8
[17179597.256000] Bluetooth: L2CAP socket layer initialized
[17179597.256000] Bluetooth: RFCOMM socket layer initialized
[17179597.256000] Bluetooth: RFCOMM TTY layer initialized
[17179597.256000] Bluetooth: RFCOMM ver 1.7
[17440327.916000] Bluetooth: HCI USB driver ver 2.9
[17440650.372000] Bluetooth: HIDP (Human Interface Emulation) ver 1.1-mh1


```

The device is clearly being detected, and works as far as I can tell. It's obviously finding my phone, but not handling it correctly, because when the phone is not there to detect, it shows a different result. Everything appears in working order, except that I can't get connected, because it won't show up when I search.

---

### Post by dvarsam on 2006-12-19
Hello!

Sorry I can't help you guys, since I don't have so much knowledge for this...
But, as I mentioned before, I returned the "Trust Bluetooth Adapter" & replaced it with a "D-Link Bluetooth Adapter".
However, if you noticed, I have provided a "HowTo" here:

[https://wiki.ubuntu.com/D-Link_DBT-122_USB_Bluetooth_Adapter](https://wiki.ubuntu.com/D-Link_DBT-122_USB_Bluetooth_Adapter)

Has anybody tried out the above?
Did this help/worked for you?

Good Luck!

---

