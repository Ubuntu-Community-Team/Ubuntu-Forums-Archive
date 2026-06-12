---
title: "Can't even connect to the Internet..."
date: 2007-05-19
forum: Absolute Beginner Talk
---

### Post by aberadam on 2007-05-19
So I started off with good intentions, now I appreciate XP more and more... I cannot connect to the damn internet.  Without that I can't begin to sort out the other issues and Ubuntu is useless to me.  

I have only one way to connect to the net and that is via a USB wireless dongle on my desktop.  Using roaming in network connections I can get it to show the wireless network but I can't join it when I input the passcode.  

Here's the original thread: [http://ubuntuforums.org/showthread.php?t=448500](http://ubuntuforums.org/showthread.php?t=448500)

Here's the Ubuntu 'HowTo': [https://help.ubuntu.com/community/InternetHowto](https://help.ubuntu.com/community/InternetHowto) - which doesn't tell me how because I don't even know what the term 'USB modem' means.  Do I have a 'USB modem'?  How am I supposed to know?  It's a wireless USB thing I stick in and it just works in XP but not on Ubuntu.  

One question:  Do I need 'ndiswrapper'?  Whatever that is.  

It show the correct network.  It shows it having a signal.  It just won't go any further no matter what I do.  

Please help, this is so disappointing, I want to use Ubuntu because I like the idea of 'open source' and have never been impressed by XP.  Until now that is.

---

### Post by halitech on 2007-05-19
a USB modem would be one that connects from your computer to the modem using a USB cable. It sounds like you are using a Wireless USB network card to connect to a wireless router which is probably connected to a dsl or cable modem.

What is written on the USB stick? it might give us an idea or where to go. It does sound like Ubuntu is seeing it but maybe open a terminal and type 

```
sudo lsusb
```

and copy paste the output here

---

### Post by aberadam on 2007-05-19
OK, I'll be back in a few minutes.

---

### Post by aberadam on 2007-05-19
Here's what I get after running that command - the Logitech thing is my wireless mouse. 

Bus 002 Device 002: ID 046d:c518 Logitech, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 148f:2573 Ralink Technology, Corp. 
Bus 001 Device 001: ID 0000:0000

---

### Post by aberadam on 2007-05-19
Here's what it says on my USB wireless thing stick: 

Cable & Wireless

802.11g Wireless USB Adaptor
FCC ID:NDD9573180519

Model N0: USBA 10CW3XI

MAC:000E2EA1FF9B

---

### Post by halitech on 2007-05-19
ok, so this
```
Bus 001 Device 002: ID 148f:2573 Ralink Technology, Corp.
```
is your wireless USB nic.

try the instructions here:
[http://ubuntuforums.org/showthread.php?t=400236](http://ubuntuforums.org/showthread.php?t=400236)
and
[https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_(Ralink_rt73_driver](https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_(Ralink_rt73_driver)

---

### Post by aberadam on 2007-05-19
Thankyou very much.  

The second says 'page does not exist', but the first link works.  Um, yeah I'll try my best, but lacking a degree in computers...

---

### Post by halitech on 2007-05-19
post back with any questions and we'll do our best to answer them and good luck

---

### Post by aberadam on 2007-05-19
I've had a look through those instructions and I don't have a chance. I found this Ralink site though: [http://www.ralinktech.com/ralink/Home/Support/Linux.html](http://www.ralinktech.com/ralink/Home/Support/Linux.html)

Maybe I could just download one of those and install it?  But which...

---

### Post by jimrz on 2007-05-19
> **aberadam said:**
> Thankyou very much.  

The second says 'page does not exist', but the first link works.  Um, yeah I'll try my best, but lacking a degree in computers...

hang in there ... you don't need a computer degree to use and enjoy ubuntu ... you just need a little time to find your way around, a willingness to work with things new to you and, sometimes, the kind of assistance (so nicely demonstrated by halitech)  these forums provide , for which I doubt you can find a equivilant for xp

welcome to ubuntu

---

### Post by halitech on 2007-05-19
I would say go with this one

[http://www.ralinktech.com.tw/data/RT73_Linux_STA_Drv1.0.4.0.tar.gz](http://www.ralinktech.com.tw/data/RT73_Linux_STA_Drv1.0.4.0.tar.gz)

thanks Jim, I do it cause I know what it was like to start out and feel like tearing your hair out and how nice it was to have someone hold my hand so I would stay with linux. been using Ubuntu now for over a year and hardly look at my windows box anymore :)

---

### Post by aberadam on 2007-05-19
I'm very grateful for his help, and yes I'm sure there's no equivalent XP forum to this with great support, but I can get on the internet with XP so I don't need it... 

I have no chance with those instructions. There are dozens of terms in the opening two paragraphs that I don't understand and the same is repeated all the way down the page.

---

### Post by aberadam on 2007-05-19
Thanks.  How do I run that file?  I'm in XP now and need to get it over to Ubuntu first of all.  

See what I mean :)

---

### Post by halitech on 2007-05-19
save the file and then extract it and probably should be able to instaa it from there

---

### Post by aberadam on 2007-05-19
Using Ubuntu I extracted that file from my phone (I'm using that to transfer the files over) and now it's sat on my Ubuntu desktop.  I don't know what to do with it.  There's no obvious 'extractable' thing to click inside it and if I right click it nothing happens.  Nothing relevant in the help files I can see.  

So, please tell me how I run this thing.:)

---

### Post by chamberlain2006 on 2007-05-19
Shouldn't the Ralink driver be included?  Run the "iwconfig" command in terminal (Applications>Accessories>Terminal) and check for part that says something like rausb1.

---

### Post by aberadam on 2007-05-19
Something like rausb1?  There's probably a thousand things like it in there.

---

### Post by halitech on 2007-05-19
d'oh, never thought of iwconfig. thanks for bringing that up, sometimes I think of the hardest things first :(

---

### Post by chamberlain2006 on 2007-05-19
Just try iwconfig.  There should be sections like lo, eth0, etc.  Look for one like ra0 or rausb1

---

### Post by aberadam on 2007-05-19
OK, I'll try it, if there is all it means is back to square one though! 

GGGAAAHAHHHHHH

I want to throw my computer out of the window.

---

### Post by chamberlain2006 on 2007-05-19
You might as well post the entire output of iwconfig.  Please be patient, though, we'll get it to work.

---

### Post by aberadam on 2007-05-19
Thankyou chamberlain! :)

Ok, I've lost the .doc word file I'd saved with Open Office.  Lost it in my damn phone.  Bear with my while I reboot Ubuntu... it didn't have anything rao1 or similar in it though.

---

### Post by halitech on 2007-05-19
> **aberadam said:**
> OK, I'll try it, if there is all it means is back to square one though! 

GGGAAAHAHHHHHH

I want to throw my computer out of the window.

I understand your frustration, been there myself. Might be an idea to walk away if you are feeling frustrated, go for a walk and then come back refreshed. Don't worry about us, someone will be here to help you out :)

---

### Post by aberadam on 2007-05-19
Ok, here it is, half an hour later: 

o        no wireless extensions. 
 
eth0      no wireless extensions. 
 
wmaster0  IEEE 802.11g  Frequency:2.412 GHz   
          RTS thr:off   Fragment thr=2346 B    
           
wlan0     IEEE 802.11g  ESSID:""   
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated    
          RTS thr:off   Fragment thr=2346 B    
          Link Quality:0  Signal level:0  Noise level:0 
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by chamberlain2006 on 2007-05-19
wlan0 seems to be a good sign, do you have any other devices that might have created that?

---

### Post by aberadam on 2007-05-19
Thanks halitech :) 

I didn't put those smiley faces in the iwconfig thing BTW.  

I can't wait until I get onto the next step - getting my ATI card to work - I gather it's a real joy.  *Writes off tomorrow* :)

---

### Post by chamberlain2006 on 2007-05-19
Yupp, that seems good, I think.  Try going into System>Administration>Networking and configuring wlan0.

---

### Post by aberadam on 2007-05-19
I have a Logitech wireless mouse.  That's the only other USB thing I have connected apart from my phone temporarily to transfer these files around.  Don't think my motherboard has wireless, in fact certain.

---

### Post by aberadam on 2007-05-19
Thanks chamerlain, I think I've already done that though.  Is that the one where I write the name of the network plus the passcode?  If so then it's done.

---

### Post by chamberlain2006 on 2007-05-19
Hmmm.  Try doing
```
sudo /etc/init.d/networking restart
```
and check the result.  (You have to do that in terminal).

---

### Post by aberadam on 2007-05-19
OK, thanks, I'll get back.

---

### Post by aberadam on 2007-05-19
* Reconfiguring network interfaces...                                          RTNETLINK answers: No such process 
There is already a pid file /var/run/dhclient.eth0.pid with pid 5413 
killed old client process, removed PID file 
Internet Systems Consortium DHCP Client V3.0.4 
Copyright 2004-2006 Internet Systems Consortium. 
All rights reserved. 
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/) 
 
wmaster0: unknown hardware address type 801 
wmaster0: unknown hardware address type 801 
Listening on LPF/eth0/00:14:85:2e:85:a3 
Sending on   LPF/eth0/00:14:85:2e:85:a3 
Sending on   Socket/fallback 
There is already a pid file /var/run/dhclient.wmaster0.pid with pid 5392 
killed old client process, removed PID file 
Internet Systems Consortium DHCP Client V3.0.4 
Copyright 2004-2006 Internet Systems Consortium. 
All rights reserved. 
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/) 
 
wmaster0: unknown hardware address type 801 
wmaster0: unknown hardware address type 801 
Listening on LPF/wmaster0/ 
Sending on   LPF/wmaster0/ 
Sending on   Socket/fallback 
Error for wireless request "Set Encode" (8B2A) : 
    SET failed on device wmaster0 ; Operation not supported. 
Error for wireless request "Set ESSID" (8B1A) : 
    SET failed on device wmaster0 ; Operation not supported. 
eth1: ERROR while getting interface flags: No such device 
There is already a pid file /var/run/dhclient.eth1.pid with pid 134993416 
Internet Systems Consortium DHCP Client V3.0.4 
Copyright 2004-2006 Internet Systems Consortium. 
All rights reserved. 
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/) 
 
wmaster0: unknown hardware address type 801 
SIOCSIFADDR: No such device 
eth1: ERROR while getting interface flags: No such device 
eth1: ERROR while getting interface flags: No such device 
wmaster0: unknown hardware address type 801 
Bind socket to interface: No such device 
Failed to bring up eth1. 
eth2: ERROR while getting interface flags: No such device 
There is already a pid file /var/run/dhclient.eth2.pid with pid 134993416 
Internet Systems Consortium DHCP Client V3.0.4 
Copyright 2004-2006 Internet Systems Consortium. 
All rights reserved. 
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/) 
 
wmaster0: unknown hardware address type 801 
SIOCSIFADDR: No such device 
eth2: ERROR while getting interface flags: No such device 
eth2: ERROR while getting interface flags: No such device 
wmaster0: unknown hardware address type 801 
Bind socket to interface: No such device 
Failed to bring up eth2. 
ath0: ERROR while getting interface flags: No such device 
There is already a pid file /var/run/dhclient.ath0.pid with pid 134993416 
Internet Systems Consortium DHCP Client V3.0.4 
Copyright 2004-2006 Internet Systems Consortium. 
All rights reserved. 
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/) 
 
wmaster0: unknown hardware address type 801 
SIOCSIFADDR: No such device 
ath0: ERROR while getting interface flags: No such device 
ath0: ERROR while getting interface flags: No such device 
wmaster0: unknown hardware address type 801 
Bind socket to interface: No such device 
Failed to bring up ath0. 
Error for wireless request "Set Encode" (8B2A) : 
    SET failed on device wmaster0 ; Operation not supported. 
Error for wireless request "Set ESSID" (8B1A) : 
    SET failed on device wmaster0 ; Operation not supported. 
There is already a pid file /var/run/dhclient.wmaster0.pid with pid 134993416 
Internet Systems Consortium DHCP Client V3.0.4 
Copyright 2004-2006 Internet Systems Consortium. 
All rights reserved. 
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/) 
 
wmaster0: unknown hardware address type 801 
wmaster0: unknown hardware address type 801 
Listening on LPF/wmaster0/ 
Sending on   LPF/wmaster0/ 
Sending on   Socket/fallback 
DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 6 
DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 17 
DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 8 
No DHCPOFFERS received. 
No working leases in persistent database - sleeping. 
There is already a pid file /var/run/dhclient.eth0.pid with pid 134993416 
Internet Systems Consortium DHCP Client V3.0.4 
Copyright 2004-2006 Internet Systems Consortium. 
All rights reserved. 
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/) 
 
wmaster0: unknown hardware address type 801 
wmaster0: unknown hardware address type 801 
Listening on LPF/eth0/00:14:85:2e:85:a3 
Sending on   LPF/eth0/00:14:85:2e:85:a3 
Sending on   Socket/fallback 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4 




WOAH, THAT ONE DID SOMETHING!11 :)

---

### Post by chamberlain2006 on 2007-05-19
What did it say about wlan0?

---

### Post by aberadam on 2007-05-19
Um, I don't know, that's all that happened when I typed in what you told me.

---

### Post by chamberlain2006 on 2007-05-19
Ok...will you post the contents of the /etc/network/interfaces file?

---

### Post by aberadam on 2007-05-19
Yeah sure, can you tell me what to type though, like "sudo...

---

### Post by chamberlain2006 on 2007-05-19
sudo cat /etc/network/interfaces should do.

---

### Post by aberadam on 2007-05-19
sudo  /etc/network/interfaces ?

---

### Post by aberadam on 2007-05-19
OK, thanks.

---

### Post by Outrunner on 2007-05-19
Here's some advice for you:

```
sudo cat /etc/network/interfaces > file.txt
```

To have the output of sudo cat /etc/network/interfaces copied to file.txt (in your /home/username)

---

### Post by heimo on 2007-05-19
> **Outrunner said:**
> Here's some advice for you:

```
sudo cat /etc/network/interfaces > file.txt
```To have the output of sudo cat /etc/network/interfaces copied to file.txt (in your /home/username)

Huh. That's one way to do it. Then there's also cp command (copy), which does similar stuff.
```
cp /etc/network/interfaces ~/file.txt
```

---

### Post by aberadam on 2007-05-19
auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

iface wmaster0 inet dhcp
wireless-essid BTHomeHub-183B
wireless-key e2e0136b99











auto wmaster0

auto eth0



There it is.

---

### Post by aberadam on 2007-05-19
Including the secret key!  :)

---

### Post by chamberlain2006 on 2007-05-19
There seems to be a problem with the provided ralink driver.  We'll have to install from source, but I can help you with that.  Is your card a USB, PCI, or what?

---

### Post by chamberlain2006 on 2007-05-19
From [http://ubuntuforums.org/showthread.php?p=1409752#post1409752:](http://ubuntuforums.org/showthread.php?p=1409752#post1409752:)

> 
Quote:
sudo apt-get install build-essential linux-headers-$(uname -r)
This will install necessary packages for the compilation, after typing your password.

and then:

Quote:
wget [http://rt2x00.serialmonkey.com/rt2500-cvs-daily.tar.gz](http://rt2x00.serialmonkey.com/rt2500-cvs-daily.tar.gz)
tar -xzf rt2500-cvs-daily.tar.gz
cd ./rt2500*/Module
make
sudo ifdown ra0
sudo cp ~/rt2500*/Module/rt2500.ko /lib/modules/`uname -r`/kernel/drivers/net/wireless/
sudo cp ~/rt2500*/Module/rt2500.ko /lib/modules/`uname -r`/kernel/drivers/net/wireless/rt2x00-legacy/rt2500/
sudo cp ~/rt2500*/Module/rt2500.ko /lib/modules/`uname -r`/kernel/ubuntu/wireless/rt2x00-legacy/rt2500
echo "alias ra0 rt2500" | sudo tee /etc/modprobe.d/rt2500
sudo depmod
Reboot your computer once installation is complete. If you get an error complaining about "***/kernel/drivers/net/wireless/rt2x00-legacy/rt2500" or so not being found, dont worry about it.

If your wireless is not "up" or enabled, you can enable it via commandline with:

Quote:
sudo ifup ra0

Follow those instructions to install the latest driver.

---

### Post by aberadam on 2007-05-19
Just got back online, OK, will give it a go.  Thanks for all your help!  :)

---

### Post by aberadam on 2007-05-19
My card?  My wireless is USB.  Graphics card PCI Express.

---

### Post by aberadam on 2007-05-19
Hang on, it says to get a driver off the Internet in those instructions... I have no Internet access with Ubuntu.

---

### Post by aberadam on 2007-05-19
I can download the file now and move it over but wher edo I put it in Ubuntu?  Which folder?  Would it still work?

---

### Post by chamberlain2006 on 2007-05-19
Just download the file it says, and put it in your home directory (/home/YOURNAME).

---

### Post by chamberlain2006 on 2007-05-19
Is there no way you can get a wired connection?  Because you need to install a couple packages that will be annoying to install otherwise.

---

### Post by aberadam on 2007-05-20
There's no way I can get it with a wire.  The connection is two floors up.  

I've been through those instructions as best I can, but I'm so ignorant I copy & pasted the whole thing into Terminal and tried that.  It didn't work so I went line by line. 

I *think* I got the download installed but no further.  I tried the last line but it says 'ra0' doesn't exist or similar.

---

