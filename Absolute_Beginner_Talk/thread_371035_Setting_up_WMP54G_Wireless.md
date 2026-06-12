---
title: "Setting up WMP54G Wireless"
date: 2007-02-26
forum: Absolute Beginner Talk
---

### Post by Torahteen on 2007-02-26
Ok, this should be my last problem. The last time I installed Ubuntu, I had it hard-wired with my network router, which is a WRT45GS Wireless Router from linksys. Now, I've got a wireless WMP54G PCI Adapter rom linksys that I want to connect to the same router.

Ubuntu recognizes the card as a wireless card, and lets me configure it. I have the right SSID, and I'm pretty sure I have the right pass to access the router (my WEP). I don't know how to set up a static IP, and hadn't had to do it before so I assumed it was DCHP that I needed to use. So... I click activate, and after a while it says it's activated. I click ok, and then try opening Firefox. However, I'm apparently not connected to the router. I tried going to 192.168.1.1, with no luck.

So... how do I set this up? I tried using ndiswrapper, and installed the driver for it, and it says I have it installed and that the hardware is present when I type in sudo ndiswrapper -l. I don't care which direction I take from here, but would somebody please help!

---

### Post by netkid91 on 2007-02-26
I have the exact same setup as you, same router and card (minus mine has the speedboster stuff).  What drivers are you using, the ones off the CD?
Can you type:
iwconfig [interface of your wireless card]
into a console and post the output?

---

### Post by houstonbofh on 2007-02-26
Every WiFi problem thread I have been in lately has been this card.  Take it back and get a supported one if you value your sanity! :)  Keep in mind that Linksys changes version without any notice on the box.  You may **not** have the same card others have made work.  You may have the card no one can get to work!  Search just on my handle and wmp54g for an idea of why I hate this card.

---

### Post by Torahteen on 2007-02-26
I got the driver online somewhere. There's one on the CD? Where is the one on the CD? Maybe that would work better. After typing in iwconfig eth0, I get this:

```
iwconfig eth0
eth0    IEEE 802.11b/g    ESSID:off/any    Nickname:"Barcom 4306"
           Mode: managed    Access Point: Invalid    Bit Rate = 1Mb/s
           RTS thr: off    Fragment thr: off
           Link Quality: 0    Signal Level:0    Noise Level:0
           Rx invalid nwid: 0    Rx invalid crypt: 0    Rx invalid frag: 0
           Tx excessive retries: 0    Invalid misc: 0    Missed Beacon: 0
```

---

### Post by netkid91 on 2007-02-26
You did get a CD with the card didn't you?  Put it in, cd to /media/cdrom/, look for a driver directoy, find the XP directory in there.  Make sure to remove the old one from NDISWrapper with the -r flag, then install the one off the CD and see if it works better.

---

### Post by Torahteen on 2007-02-26
Ok, I've installed the driver on the CD, but now what do I do?

---

### Post by netkid91 on 2007-02-26
Post the output of iwconfig again after a reboot (did you check ndiswrapper -l to make sure the driver is compatible as well?)

---

### Post by Torahteen on 2007-02-26
```
iwconfig eth0
eth0    IEEE 802.11b/g    ESSID:off/any    Nickname:"Broadcom 4306"
           Mode: managed    Access Point: Invalid    Bit Rate = 1Mb/s
           RTS thr: off    Fragment thr: off
           Encryption Key: off
           Link Quality: 0    Signal Level:0    Noise Level:0
           Rx invalid nwid: 0    Rx invalid crypt: 0    Rx invalid frag: 0
           Tx excessive retries: 0    Invalid misc: 0    Missed Beacon: 0
```

Looking at the list of installed drivers, it said that the driver is present and that the hardware is present.

---

### Post by netkid91 on 2007-02-26
K, run:
iwconfig eth0 essid [your network name]
And post the output again (iwconfig without any arguments)

---

### Post by netkid91 on 2007-02-26
Run:
iwconfig eth0 essid [your network name]
then post the output of
iwconfig

---

### Post by Torahteen on 2007-02-26
Where'd you go? You logged out, and now eth0 isn't showing up in Networking.

---

### Post by netkid91 on 2007-02-26
**SOLVED:**
After NDISWRAPPER was setup, the following line was added to /etc/modprobe.d/blacklist
blacklist bcm43xx
After that, everything worked like a charm.

---

### Post by Torahteen on 2007-02-26
I thank netkid once again for his help... saved me a lot of money XD

---

### Post by tjtansey on 2007-02-26
Buddy do yourself a favor, start over from scratch and remove the drivers and ndiswrapper, then follow this walkthrough.  If you have any questions PM me.  Make sure you replace the url for your driver in the wget line, everything else should work like a charm.




Installation of Linksys WPC54G v2 wireless card cut and paste commands to make your life easy
remove card
in terminal:
sudo aptitude install ndiswrapper-common ndiswrapper-utils-1.8

mkdir linksys
cd linksys
wget [ftp://ftp.linksys.com/pub/network/wp...ility_v2.0.zip](ftp://ftp.linksys.com/pub/network/wp...ility_v2.0.zip)
unzip wpc54g_v2_driver_utility_v2.0.zip

At this point you have the software you need to install your driver

Now a little housekeeping to ensure you don't any future problems, we are going to convert the following filename to all CAPS this ensures your driver recognizes the file
mv tnet1130.sys TNET1130.sys

Now we are going to install the drivers
sudo ndiswrapper -i lsbcmnds.inf
sudo ndiswrapper -i LSTINDS.INF
sudo modprobe ndiswrapper

Now we are going to set up your system to initialize on boot-up
sudo nano /etc/modules

add the following line at the end of the file
ndiswrapper
then ctrl-x
y
enter
Now insert your card and enter
ndiswrapper -l

the screen should read:
Installed drivers:
lsbcmnds driver installed
lstinds driver installed, hardware present
Disable your wired network connectio
Now run dmesg and look for the following lines:
ndiswrapper: driver lstinds (Linksys,03/10/2004,6.0.0.1 loaded
ndiswrapper: using irq <irq#>
wlan0: vendor: 'TNET1130'
wlan0: ethernet device 00:0f:66:d8:a7:88 using NDIS driver lstinds, 104C:9066:1737:0033.5.conf

Now restart networking with the following command:
sudo /etc/init.d/networking restart

Now you are ready to set up your Wlan in the networking tab under System>Admnistration>Networking

Good luck
Forward Message

---

### Post by Torahteen on 2007-02-27
TJ, I probably would've done that, except that this is working just fine, and I don't want to touch it.

One more problem though. Every reboot, I need to type in sudo modprobe ndiswrapper. Is there a way to get Ubuntu to execute this command on startup?

---

### Post by Mizled on 2007-02-27
```
modprobe ndiswrapper
```

That should work for you..

---

### Post by Torahteen on 2007-02-27
Ok, but how do I make it so that the command is executed every time I start up Ubuntu?

---

### Post by Torahteen on 2007-02-27
Bump... need help with this, and don't wanna have to start a new thread.

---

### Post by Mizled on 2007-02-27
Did you try doing...
```
sudo depmod -a
sudo modprobe ndiswrapper

```


After that do 
```
sudo ndiswrapper -m
```

it should output something like....(this is mine)
```
adding "alias wlan0 ndiswrapper" to /etc/modprobe.d/ndiswrapper ...
```


Should be permanent then...

---

### Post by Mizled on 2007-02-27
You may also want to do 

```
gksudo gedit /etc/network/interfaces
```

and add

```

iface wlan0 inet dhcp
wireless-essid Your_ESSID
wireless-key XXXXXXXYour WEP Enc KeyXXXXXXXXXXXX
auto wlan0

```


and comment out anything else that has wlan0 (if thats your wireless) and it will auto connect to your wireless...

---

### Post by compmodder26 on 2007-02-27
> **Torahteen said:**
> Ok, but how do I make it so that the command is executed every time I start up Ubuntu?

Put "ndiswrapper" in the file /etc/modules

---

