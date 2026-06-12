---
title: "[SOLVED] Configuring Bluetooth communication between phone &amp;amp; laptop"
date: 2008-04-15
forum: Absolute Beginner Talk
---

### Post by KMuchane on 2008-04-15
Hi, 

I would like for  my laptop to communicate with my phone via bluetooth. If possible, I would like to do away with the USB cable I currently use, so that I can free one USB port. Right now,  I am  using  the cellphone as a modem to connect to the internet... 
Where do I start?
Thanks!

---

### Post by Inxsible on 2008-04-15
enable bluetooth on your phone and then run```
sudo hcitool scan
```It should recognize your phone and give you the mac address.

You can also search for bluetooth devices from the phone and once it sees your computer, you need to pair it by providing the passkey. The default passkey is 1234, but you can change it if you like by editing the hcid.conf file
```
gksudo gedit /etc/bluetooth/hcid.conf
``` You can't miss the passkey key and value pair :)

---

### Post by Inxsible on 2008-04-15
Another option is to install [Blueman bluetooth manager]("https://launchpad.net/blueman")

---

### Post by KMuchane on 2008-04-15
Hi,  

After I run sudo hcitool scan I get  'Device is not available. No such device'. I am suspecting the cell is acting up. Or...

---

### Post by KMuchane on 2008-04-15
Hi,  

After I run sudo hcitool scan I get  'Device is not available. No such device'. I am suspecting the cell is acting up. Or...

---

### Post by Inxsible on 2008-04-15
are you sure you have a built  bluetooth in your machine and if not, have you attached a dongle of some kind ?

---

### Post by scorp123 on 2008-04-15
> **KMuchane said:**
>  I would like for  my laptop to communicate with my phone via bluetooth. If possible, I would like to do away with the USB cable I currently use, so that I can free one USB port. Right now,  I am  using  the cellphone as a modem  Try this:
[http://ubuntuforums.org/showthread.php?t=639362](http://ubuntuforums.org/showthread.php?t=639362)

I use my Samsung SGH-G800 as modem (HSDPA) via Bluetooth ... so maybe my setup works for your phone as well?

---

### Post by pseudo-random on 2008-04-15
hcitool requires an adapter as an argument eg:
> sudo hcitool -i hci0 scan
Thats why you got no device.

---

### Post by scorp123 on 2008-04-15
> **pseudo-random said:**
> hcitool requires an adapter as an argument ... Thats why you got no device. Not necessarily ... if you give no device it should default to the first one present in the system. The "official" Ubuntu Bluetooth-DialUp guide also uses the command "hcitool scan" without giving an interface:
[https://help.ubuntu.com/community/BluetoothDialup](https://help.ubuntu.com/community/BluetoothDialup)

Having followed that guide to get my own mobile phone working with Bluetooth dial-up I am confident that the commands in the guide work tip top.

Maybe his Bluetooth adapter is switched off? I have one stupid Fujitsu-Siemens laptop where a button on the side controls whether Bluetooth is on or off .. Whenever I put the laptop into its bag or take it out from there again I can be sure that the button's setting has changed. Could be something like that in his case too. :confused:

---

### Post by KMuchane on 2008-04-16
Hi! 

The laptop  has bluetooth alright, and infrared too. It is a HP 510, the phone is a motorola L6i.
Apart from the power button, the wireless one and the other one which switches the lid off when you close it, I cannot see any other that might switch anything on.  
And adding an argument to hcitool makes no difference. 

So I think it is a question of switch on bluetooth on the laptop. Surely, it cannot be on all the time...hmmm   

Thanks!

---

### Post by scorp123 on 2008-04-16
> **KMuchane said:**
>  The laptop  has bluetooth alright, and infrared too. It is a HP 510, the phone is a motorola L6i. Apart from the power button, the wireless one and the other one which switches the lid off when you close it, I cannot see any other that might switch anything on.   Do you have a bluetooth icon on your desktop? e.g. something like this:  

[IMG]http://arstechnica.com/journals/linux.media/bt_gnome_sync_notification.png[/IMG]

 ... I don't mean the pop-up window. What I mean is that white runic "B" on a blue background that should be sitting on your panel .... That would indicate the presence of an activated bluetooth adapter (in the sense: the system sees that it's there). Lacking that it most likely means your bluetooth adapter is either not activated ... or maybe even not supported, at least not out of the box?

Can you try the following please: Open a terminal and then type these commands:
```
sudo lspci
sudo lsusb 
``` (when it asks for a password you have to type in your own password blindly as nothing will be echoed back ... just type it in and hit the enter key).

If I do the same commands here on my HP Pavilion dv2108ea laptop I get these results:
```
> sudo lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
05:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
08:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 02)
08:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
08:09.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
08:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 01)
08:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
08:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
``` ... As you can see there is no bluetooth device here!

But if I do "lsusb" I get this:
```
> sudo lsusb
Bus 005 Device 008: ID 046d:c504 Logitech, Inc. Cordless Mouse+Keyboard Receiver
Bus 005 Device 007: ID 0c45:62c0 Microdia 
Bus 005 Device 006: ID 0424:2504 Standard Microsystems Corp. 
Bus 005 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
[B][COLOR="Red"]Bus 001 Device 004: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
[/COLOR][/B]Bus 001 Device 001: ID 0000:0000
``` (color and emphasis added by me)

As you can see here my bluetooth adapter is a USB device ... it's indeed a dongle that I had to connect to one of my USB ports because my laptop otherwise doesn't have any bluetooth adapter. But it could be on some laptops that even though a device is internal and built into the laptop that it is seen as USB device ... Take my webcam for example: The device being listed as "Microdia" (in the output above) is a webcam built into the lid of my laptop screen, and yet to the system it's a USB device.

So that's why I suggest you check both "lsusb" and "lspci" ... If both outputs don't list any bluetooth adapter then you probably don't have any in your system or it's not yet automagically recognised and supported yet by the current Ubuntu release?

Sorry for the long posting ... ;)

---

### Post by Inxsible on 2008-04-16
On my laptop, the wireless and the bluetooth switch are the same. Strange -- but that's how it is.

---

### Post by KMuchane on 2008-04-16
Alas... it seems I do not have Bluetooth.  Both lsusb and lspci do not output anything with bluetooth. I grep 'ed  them just to be certain. 

Dommage...

---

### Post by scorp123 on 2008-04-16
> **KMuchane said:**
> Alas... it seems I do not have Bluetooth. There are really really small bluetooth adapters for the USB port which you could consider. I have one of these:

[IMG]http://www.heise.de/bilder/102939/1/1[/IMG]

The USB dongle is so small that I don't bother ever removing it from the USB port. And I still have enough other free USB ports left so that using one port exclusively for Bluetooth doesn't matter.

---

### Post by KMuchane on 2008-04-17
Thanks for the answers. Is there a specific one I need to get ? Or I just buy any  slot it and I am ready to go ?

---

### Post by scorp123 on 2008-04-17
> **KMuchane said:**
> Thanks for the answers. Is there a specific one I need to get ? Or I just buy any  slot it and I am ready to go ? In my experience you could buy any USB Bluetooth dongle and it should work. If it doesn't ... oh well, return it to the shop because it "doesn't work" (which would not be a lie anyway :)  ) and try another one :)  Most of those dongles are not really expensive anyway so the risk of buying a device that turns out not to be working shouldn't be too big IMHO.

---

### Post by KMuchane on 2008-04-17
Thanks guys , the response is overwhelming as always!

---

### Post by coolfusion on 2008-04-18
hi on doing 
sudo hcitool -i hci0 scan
it shows me physical address of my device 
but nothing afterwards 
can u plz tell me how shuld i procced

---

### Post by KMuchane on 2008-04-18
coolfusion, 
 
I suggest you start another thread. This one is already marked solved so nobody will probably see your question.

---

### Post by scorp123 on 2008-04-18
> **coolfusion said:**
>  can u plz tell me how shuld i procced See posting #9 in this thread. There is a guide which should be easy to follow. After everything is configured it's just "point and click".

---

### Post by scorp123 on 2008-04-18
> **KMuchane said:**
>  so nobody will probably see your question. I did :)

---

### Post by KMuchane on 2008-04-18
hmmm... scorp123 saw it ,you are in good hands, bro!

---

