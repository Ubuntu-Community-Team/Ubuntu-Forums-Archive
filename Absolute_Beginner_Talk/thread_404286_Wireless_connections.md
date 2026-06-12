---
title: "Wireless connections"
date: 2007-04-08
forum: Absolute Beginner Talk
---

### Post by chown on 2007-04-08
Im a beginner to ubuntu and linux in general, im having some serious problems getting connected to the internet on my dual boot ubuntu/winxp machine.
i have the latest ubuntu version installed.

when i try to use firefox i get a server not found error, i have tried many websites including google.com. I have tried going into the menu's to find some sort of a wireless utility to connect to my wireless network but i cant find any.

any help is much appreciated. :)

---

### Post by metol on 2007-04-08
Is your wireless card recognized by Ubuntu?  Try going to System-->Administration-->Networking.  If there is a wireless connection in the list, you will need to activate it and set the properties and network password to connect to your wireless router.

---

### Post by Austin_KW on 2007-04-08
What kind of wireless adapter do you have
[INDENT]For a pci/pcmcia adapter post the output of "sudo lspci"
For a usb adapter "sudo lsusb"[/INDENT]

Is the interface created "ifconfig -a" and to see the wireless properties of the interface "iwconfig"
If the above dont show your wireless interface, are the driver modules installed/loaded "lsmod"

---

### Post by chown on 2007-04-08
Yes i have a wireless connection in the network settings list, it says below 'the interface ra0 is not configured.'
when i click properties the cursor changes and it just keeps on spining but nothing is happening. its like the system is hanging.

its also a pci card, the first output from 'sudo lspci' is:

me@my-ubuntu:~$ sudo lspci
0000:00:00.0 Host bridge: Intel Corporation 945G/P Memory Controller Hub (rev 02)
0000:00:01.0 PCI bridge: Intel Corporation 945G/P PCI Express Graphics Port (rev 02)
0000:00:1b.0 0403: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
0000:00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
0000:00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01)
0000:00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01)
0000:00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01)
0000:00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01)
0000:00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
0000:00:1f.0 ISA bridge: Intel Corporation 82801GH (ICH7DH) LPC Interface Bridge (rev 01)
0000:00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
0000:00:1f.2 0106: Intel Corporation 82801GR/GH (ICH7 Family) Serial ATA Storage Controllers cc=AHCI (rev 01)
0000:00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc: Unknown device 7146
0000:01:00.1 Display controller: ATI Technologies Inc: Unknown device 7166
0000:02:00.0 Ethernet controller: Intel Corporation 82573E Gigabit Ethernet Controller (Copper)
0000:03:02.0 Network controller: RaLink: Unknown device 0301
0000:03:03.0 Multimedia video controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
0000:03:03.1 Multimedia controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [Audio Port] (rev 05)
0000:03:03.2 Multimedia controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)
0000:03:04.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev c0)


thanks for the fast reply guys :)

---

### Post by Austin_KW on 2007-04-08
Ok so it is a ralink device, and if it is creating ra0 then some driver is being loaded. I think this is the rt2500 driver which should work.

What is the output from the following commands
```
lsmod | grep rt
ifconfig ra0
iwconfig ra0
iwlist ra0 scan
cat /etc/network/interfaces
```

---

### Post by chown on 2007-04-08
ok here is the output for the commands, i hope this is ok


Commands Run:

lsmod | grep rt
ifconfig ra0
iwconfig ra0
iwlist ra0 scan
cat /etc/network/interfaces

Commands output:

chown@chown-ubuntu:~$ lsmod |grep rt
rt61                  238720  0
parport_pc             40816  1
parport                44172  3 ppdev,lp,parport_pc
chown@chown-ubuntu:~$ ifconfig ra0
ra0       Link encap:Ethernet  HWaddr 00:00:00:00:00:00
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:209

chown@chown-ubuntu:~$ iwconfig ra0
ra0       RT61 Wireless  ESSID:""
          Mode:Auto  Channel:0
          RTS thr=0 B   Fragment thr=0 B
          Link Quality:0  Signal level:0  Noise level:113
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

chown@chown-ubuntu:~$ iwlist ra0 scan
ra0       No scan results
chown@chown-ubuntu:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

chown@chown-ubuntu:~$


sorry for the late reply...
thanks again :)

---

### Post by chown on 2007-04-09
Can someone please help me with this?

---

### Post by RomeReactor on 2007-04-09
Hi. Your card isn't listed in the interafces file; try adding it

```
gksudo gedit /etc/network/interfaces
```

Now insert this in the file

```
auto ra0
iface ra0 inet dhcp
```

I recommend you delete all other entries as well (except for **lo** so the file looks like this

```
auto lo
iface lo inet loopback

auto ra0
iface ra0 inet dhcp
```

Now reboot and see if it works. Also, please post the output of 
```
sudo lshw
```

---

### Post by Austin_KW on 2007-04-09
This is the ralink rt61 chipset. Except for the 2500, any of the ralink drivers that I have tried in edgy dont seem to work. 
Your ifconfig is not showing a valid MAC address and scanning is not seeing your wireless network so I think you need a new driver.

Downloading and building the drivers from  the maintainers at serialmonkey.com is as follows in a terminal.
```
sudo apt-get install build-essential linux-headers-$(uname -r) 
wget http://rt2x00.serialmonkey.com/rt61-cvs-daily.tar.gz
tar -xvzf rt61-cvs-daily.tar.gz
cd rt61-cvs-*/Module/
make
```

Then to remove the old driver and install the new
```
sudo modprobe -r rt61
sudo make install
```

you will then want to modify your /etc/network/interfaces as suggested above for either connecting to a WEP or WPA protected network, substitute your essid & key
eg for WEP
```

auto ra0
iface ra0 inet dhcp
wireless-essid MyESSID
wireless-key 12345678

```


OR example for WPA-PSK
```

auto ra0
iface ra0 inet dhcp
    pre-up ifconfig ra0 up
    pre-up iwpriv ra0 set AuthMode=WPAPSK
    pre-up iwpriv ra0 set EncrypType=TKIP
    pre-up iwconfig ra0 essid MyESSID
    pre-up iwpriv ra0 set WPAPSK="TJNXdnaCgot5thOdN4YBVNBHCm48OcScq2Yb"

```

---

### Post by Austin_KW on 2007-04-09
you can leave the lo, eth0 & eth1 config in the interfaces file but you can remove the ath0 and wlan0 lines as you dont have an atheros wireless card

---

### Post by chown on 2007-04-11
ok i followed RomeReactors instructions first and now i get the error:
(gksudo:5301): Gtk-WARNING **: cannot open display:

when i boot ubuntu now i get past the login screen and i get a dark red screen (default ubuntu bg colour) and the system hangs, but i can still go into terminal using ctrl+alt+f1/f2/f3...

also i get a constant stream of:
[ 252.523421] usb 5-8: reset high speed USB device using ehci_hcd and address 5, 
messages.

this doesnt look good... lol

---

### Post by Austin_KW on 2007-04-11
I dont think your errors have anything to do with your wireless, Did your system crash?
The 'cannot open display' is usually a xserver access error. gksudo did not have access to the DISPLAY. Were you using a different user shell? I see it a lot because I am too lazy to re-type sudo and ofter "sudo -i" But this should be a temporary error condition.

You get past the login screen so it seems like some setting in your own account (one of the hidden gnome config files), create another user & login to verify.
 
What is usb device 5 check with "lsusb".

---

### Post by chown on 2007-04-12
oh ok, well every time i try to type in a command the usb message pops up so i can type in about 5 characters and then it will pop up again and again. 

its very confusing...

---

### Post by Austin_KW on 2007-04-12
> **chown said:**
> oh ok, well every time i try to type in a command the usb message pops up so i can type in about 5 characters and then it will pop up again and again. 

its very confusing...
Start unpluging you usb devices

---

### Post by chown on 2007-04-27
> **Austin_KW said:**
> This is the ralink rt61 chipset. Except for the 2500, any of the ralink drivers that I have tried in edgy dont seem to work. 
Your ifconfig is not showing a valid MAC address and scanning is not seeing your wireless network so I think you need a new driver.

Downloading and building the drivers from  the maintainers at serialmonkey.com is as follows in a terminal.
```
sudo apt-get install build-essential linux-headers-$(uname -r) 
wget http://rt2x00.serialmonkey.com/rt61-cvs-daily.tar.gz
tar -xvzf rt61-cvs-daily.tar.gz
cd rt61-cvs-*/Module/
make
```

Then to remove the old driver and install the new
```
sudo modprobe -r rt61
sudo make install
```

you will then want to modify your /etc/network/interfaces as suggested above for either connecting to a WEP or WPA protected network, substitute your essid & key
eg for WEP
```

auto ra0
iface ra0 inet dhcp
wireless-essid MyESSID
wireless-key 12345678

```


OR example for WPA-PSK
```

auto ra0
iface ra0 inet dhcp
    pre-up ifconfig ra0 up
    pre-up iwpriv ra0 set AuthMode=WPAPSK
    pre-up iwpriv ra0 set EncrypType=TKIP
    pre-up iwconfig ra0 essid MyESSID
    pre-up iwpriv ra0 set WPAPSK="TJNXdnaCgot5thOdN4YBVNBHCm48OcScq2Yb"

```


I started doing the above, i couldnt use the wget command on the computer with the problem lol, i downloaded the tarbal in windows and put it on a memory stick, then put the files on the ubuntu desktop followed the commands and i get message 'bash: make: command not found' i tried using variations of the make command but i get the same message.
im a complete newbie to this.

ps: sorry for re-opening this old thread :/ i just need this help

---

### Post by Austin_KW on 2007-04-27
Sounds like you dont have the development tools (build-essential)
sudo apt-get install build-essential linux-headers-`(uname -r)`

---

