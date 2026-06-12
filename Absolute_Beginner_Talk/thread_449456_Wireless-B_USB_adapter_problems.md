---
title: "Wireless-B USB adapter problems"
date: 2007-05-20
forum: Absolute Beginner Talk
---

### Post by xthund3rh3adx on 2007-05-20
I have Ubuntu Feisty Fawn installed and I have a problem getting my USB Wireless-B (linksys) adapter working.

I am probably missing a driver but i cannot find one ANYWHERE.

Please help...

---

### Post by chamberlain2006 on 2007-05-20
Hello, I'll show you how.  Please open up your terminal (Applications>Accessories>Terminal) and type in "lsusb".  Post the output here, please.

---

### Post by xthund3rh3adx on 2007-05-20
Bus 001 Device 004: ID 077b:2219 Linksys WUSB11 V2.6 802.11b Adapter
Bus 001 Device 002: ID 0409:0058 NEC Corp. HighSpeed Hub
Bus 001 Device 001: ID 0000:0000


ok so common sense says that Ubuntu reconizes it......so yeah whats next?

---

### Post by chamberlain2006 on 2007-05-20
Do you have a wired internet connection?

---

### Post by xthund3rh3adx on 2007-05-20
yes I do for the time being so i can get this adapter working ;)

---

### Post by xthund3rh3adx on 2007-05-20
would that be a problem?

I connect through a Wireless-G router

---

### Post by chamberlain2006 on 2007-05-20
Great.  First, go to [http://www.linksys.com/servlet/Satellite?c=L_Download_C2&childpagename=US%2FLayout&cid=1115417109934&packedargs=sku%3D1115416828445&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=0993428445B03](http://www.linksys.com/servlet/Satellite?c=L_Download_C2&childpagename=US%2FLayout&cid=1115417109934&packedargs=sku%3D1115416828445&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=0993428445B03) to download the driver.  Then, type these commands into the terminal.
```

cd Desktop
unzip WUSB11v4_08272004_dr%2C0.exe
cd WUSB11v4_08272004/Drivers
sudo apt-get install ndiswrapper-utils-1.9 ndiswrapper-common
sudo ndiswrapper -i WUSB11v4.inf
ndiswrapper -l
sudo ndiswrapper -m
sudo modprobe ndiswrapper
iwconfig
If iwconfig shows a wlan0 entry, you're all good.  Go to System>Administration>Networking to configure the device.

```

---

### Post by abhishek456 on 2007-05-20
found these drivers. Maybe these can help you


[http://www.opendrivers.com/driver/214899/linksys-wusb11-instant-wireless-usb-network-adapter-v2.5-driver-linux-free-download.html]("http://www.opendrivers.com/driver/214899/linksys-wusb11-instant-wireless-usb-network-adapter-v2.5-driver-linux-free-download.html")

---

### Post by xthund3rh3adx on 2007-05-20
thank you so much dude! rock on!

---

### Post by Bartikky on 2007-06-10
Erm, I done what you said there, but I still seem to have a problem, this is the ouput i got from entering iwconfig after doing all the other codes in the right order, 

> lo no wireless extensions.

eth0 no wireless extensions.

wlan0 IEEE 802.11b ESSID:off/any Nickname:""
Mode:Managed Frequency:2.457 GHz Access Point: Not-Associated
Bit Rate:11 Mb/s Tx-Power=15 dBm
Retry limit:8 RTS thr=1536 B Fragment thr=1536 B
Power Management:off
Link Quality:0 Signal level:0 Noise level:0
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

Does everything there look correct to you?

And also I can't find System>Administration>Networking, only thing available to me is Network and Network Tools.

---

### Post by tgbrowning on 2007-06-10
Been following along trying to get a Linksys USB network card (WUSB54GC) to work and so far, have gotten stuck on one of the middle points.  I've got ndiswrapper installed okay (finally) and located a driver from the installation cd (rt73.ini) and installed it via ndiswrapper.  

When I check that it's installed, get an invalid driver message:  

browning@browning-laptop:~/Downloads/Drivers/Windows/WUSB54GSC$ sudo ndiswrapper  -i rt73.inf
Installing rt73
browning@browning-laptop:~/Downloads/Drivers/Windows/WUSB54GSC$ ndiswrapper -l
Installed ndis drivers:
rt73    invalid driver!

Suggestions.  

Browning>>>

[ this is actually starting to get interesting. I'm about at the point where I'm getting dangerous to my computer ...]

---

### Post by xthund3rh3adx on 2007-06-14
problems!!

well, I installed the drivers, everything and anything says thats its connected, i see my wireless connection, wlan0 is working, its connected to my network, but yet, NOTHING coNNECTS TO THE INTERNET!! :S help??

---

### Post by xthund3rh3adx on 2007-06-14
anyone?
:(

---

### Post by tgbrowning on 2007-06-18
Sorry I didn't reply sooner, but have been fighting a newer problem with the mounting of USB drives to my computer. Kind of took my full attention.

Anyway, I still haven't gotten the WiFi to work and I'm still struggling to get that darn network dialog to show it as a wireless connection rather than a ethernet one. The device is there, seen by the system because it shows up in both the network manger dialog and the device manager one.  Not entirely sure where to go with this, since I'm still trying to get to the bottom of the USB mount problem.  

(which is was fixed, btw, with the simple expedient of starting from scratch. unfortunely, I still have no idea what caused the problem and haven't been able to duplicate it, though from the mail response I've gotten, quite a few people are having that same problem themselves.)

Browning>>>

---

### Post by arijarot on 2007-06-23
I followed ```
cd Desktop
unzip WUSB11v4_08272004_dr%2C0.exe
cd WUSB11v4_08272004/Drivers
sudo apt-get install ndiswrapper-utils-1.9 ndiswrapper-common
sudo ndiswrapper -i WUSB11v4.inf
ndiswrapper -l
sudo ndiswrapper -m
sudo modprobe ndiswrapper
iwconfig
```

and here are the errors:
sudo ndiswrapper -i WUSB11v4.inf
```
couldn't find "Sources" in "."; make sure all driver files, including .inf, .sys (and .bin, if any) are in "." - installation may be incomplete
```
sudo ndiswrapper -m
```
couldn't add module alias: at /usr/sbin/ndiswrapper-1.9 line 717.
```
sudo modprobe ndiswrapper
```
FATAL: Module ndiswrapper not found.
```
iwconfig
```
bash: iwconfig: command not found
```

any ideas?

---

### Post by arijarot on 2007-06-23
even a point in the right direction would be greatly appreciated :-k

---

### Post by tgbrowning on 2007-06-24
open a terminal window and type the following line:

browning@browning-laptop:~$ sudo ndiswrapper

The response I get when I'm in my home folder show I have ndiswrapper installed and the system finds it, no problem.

Getting a list of what is actually installed is done with the following line:

ndiswrapper -l

Which yields..>>>


browning@browning-laptop:~$ ndiswrapper -l
Installed ndis drivers:
bcmwl5          driver present, hardware present
browning@browning-laptop:~$

You don't actually have to get the source for ndiswrapper, at least you don't if you've got Dapper or higher. Once you've gotten the package manager up and running and installed all of the updates, you should be able to do a search for all references to ndiswrapper and come up with it that way

Give the manager a shot and see if the manager sees ndiswrapper as installed. If it does, i would reinstall it via the manager.

Let me know how it comes out.

Browning>>>


Password:
Usage: ndiswrapper OPTION

Manage ndis drivers for ndiswrapper.
-i inffile        Install driver described by 'inffile'
-d devid driver   Use installed 'driver' for 'devid'
-e driver         Remove 'driver'
-l                List installed drivers
-m                Write configuration for modprobe


where 'devid' is either PCIID or USBID of the form XXXX:XXXX
browning@browning-laptop:~$

---

### Post by arijarot on 2007-06-24
My network manager doesn't recognize / show the adapter. **only** "lsusb" does.

---

### Post by tgbrowning on 2007-06-24
I don't think you have ndiswrapper installed completely.  Get into the synaptic package manager and do a search of nitles and descriptions for "nsdiswrapper".  Look this list over. You should, I believe, have an entry for it if you've gotten all of the upgrades. You're using Feisty, so I could be wrong.  

If it's marked as installed, mark it for reinstallation and then see if this command works okay:

sudo ndiswrapper -l 

After being installed, you should have an file in /etc/network/interfaces called interfaces. Open that up and look and see what it says. You should have an entry for etho or eth1 that's marked as a wireless network adapter.

Browning>>>

---

### Post by tgbrowning on 2007-06-25
You ever get your wifi connected?

---

### Post by arijarot on 2007-06-25
> **tgbrowning said:**
> You ever get your wifi connected?

No, but it's ok...thanks.

---

### Post by godtvisken on 2007-07-08
> **chamberlain2006 said:**
> Great.  First, go to [http://www.linksys.com/servlet/Satellite?c=L_Download_C2&childpagename=US%2FLayout&cid=1115417109934&packedargs=sku%3D1115416828445&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=0993428445B03](http://www.linksys.com/servlet/Satellite?c=L_Download_C2&childpagename=US%2FLayout&cid=1115417109934&packedargs=sku%3D1115416828445&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=0993428445B03) to download the driver.  Then, type these commands into the terminal.
```

cd Desktop
unzip WUSB11v4_08272004_dr%2C0.exe
cd WUSB11v4_08272004/Drivers
sudo apt-get install ndiswrapper-utils-1.9 ndiswrapper-common
sudo ndiswrapper -i WUSB11v4.inf
ndiswrapper -l
sudo ndiswrapper -m
sudo modprobe ndiswrapper
iwconfig
If iwconfig shows a wlan0 entry, you're all good.  Go to System>Administration>Networking to configure the device.

```

OK. I did all of this and it worked fine, and I go to configure the device. I clicked the wireless device in the network-admin, then clicked Properties. I deselected "enable roaming mode", then filled in my WiFi details. It seemed to go fine, i saved it and clicked close. But then nothing happened. The output of iwconfig was no different than before, just blank. 

What to do?

---

### Post by godtvisken on 2007-07-08
OK, I clicked on the network computer icon in the top toolbar and was able to select my wireless network. I connected, entered the key, and the iwconfig output seemed to be correct. But i opened firefox and no page would load. I also tried to ping the router and it reported "network unreachable". At one point the network computer icon switched to the wireless style icon, but randomly switched back. Now i click to connect to my network again and enter the WEP key, but it repeatedly asks me over and over to enter it (yes, i'm doing it correctly..) What is "open system" vs "shared key"? I have tried enabling both.

---

### Post by godtvisken on 2007-07-08
After rebooting, now instead of the network computer icon or the wireless icon, i get an eternally spinning blue, and the caption reads "Waiting for Network Key for the wireless network '(name)'"

---

### Post by godtvisken on 2007-07-09
My sister was messing around with it, and somehow it is now connected to the network, the icon changed to the wireless network icon. Although pinging the route failed, firefox couldn't load anything, and then it asked again for passphrase. I have tried restarting the router and the computer again.

---

### Post by godtvisken on 2007-07-10
Well, somehow i finally got the output of iwconfig to be correct, so it seems as if it is connected, but then pinging the router yields ```
Network unreachable
``` and of course no webpages load. Any ideas?

---

### Post by arijarot on 2007-07-10
IMHO, it sounds like you have everything recognized hardware wise, but it doesn't seem like you have it configured correctly. Maybe doing a meticulous configuration is in order. This could be on either end, the router or the adapter.

---

### Post by godtvisken on 2007-07-10
Well, latest update: I found an unsecured network of one of my neighbors and was successfully able to connect to that (in fact, I'm posting this message using that network). So something is going wrong with the WEP, I suppose.

---

### Post by godtvisken on 2007-07-10
Attempting to connect to my own encrypted network still..

Here's the information I can have, please just ask if you need more to better understand the problem

1. The iwconfig output has been correct
2. I set the IP manually with `sudo ifconfig wlan0 192.168.1.111 up'
3. Then did `sudo route add default gw 192.168.1.1 dev wlan0'
4. The DNS servers listed in the System -> Administration -> Network were correct
5. Everything seemed fine, but still, unable to ping the router or browse to any website, and a dialog keeps popping up asking for the passphrase.

---

### Post by tgbrowning on 2007-07-12
> **godtvisken said:**
> Attempting to connect to my own encrypted network still..

Here's the information I can have, please just ask if you need more to better understand the problem

1. The iwconfig output has been correct
2. I set the IP manually with `sudo ifconfig wlan0 192.168.1.111 up'
3. Then did `sudo route add default gw 192.168.1.1 dev wlan0'
4. The DNS servers listed in the System -> Administration -> Network were correct
5. Everything seemed fine, but still, unable to ping the router or browse to any website, and a dialog keeps popping up asking for the passphrase.


That means your encryption is not set up exactly the way you might think, if my experience is any guide.

Are you using the Networks, that front end that comes preinstalled usually? If so, my experience also tells me that you may need to try a different route. I have [COLOR="Red"]never[/COLOR] been able to get a wireless connection with that manager to any wireless network that uses any encrpytion.  

I strongly suggest you Wicd a try.  Go to this website ([http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)), nose around and give it a try. Using it, I've been able to get both Dapper and Feisy to work with broadcom wifi cards.

Browning>>>

---

