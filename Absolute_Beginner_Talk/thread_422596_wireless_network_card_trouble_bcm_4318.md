---
title: "wireless network card trouble bcm 4318"
date: 2007-04-25
forum: Absolute Beginner Talk
---

### Post by locksmithdan on 2007-04-25
I'm having trouble getting my wireless to work after reading several other posts telling how. I'm using an inspiron b120 with a broadcom bcm 4318 card. Any help would be greatly appreciated.

---

### Post by bdogg64 on 2007-04-25
> **locksmithdan said:**
> I'm having trouble getting my wireless to work after reading several other posts telling how. I'm using an inspiron b120 with a broadcom bcm 4318 card. Any help would be greatly appreciated.

Try this guide

[http://www.ubuntuforums.org/showthread.php?t=346083](http://www.ubuntuforums.org/showthread.php?t=346083)

---

### Post by locksmithdan on 2007-04-26
isn't that a different wireless card though? I don't know if that makes a difference, i'm totally new to ubuntu. It seems like i would need different drivers or something.

---

### Post by Bachstelze on 2007-04-26
Yes, you'll most likely need different drivers. Could you please type this in a terminal and paste the output ? Shoud be of the form xxxx: xxxx where the x are hex digits.

```
lspci -n | grep $(lspci | grep Network | awk '{print $1}') | awk '{print $3}'
```

---

### Post by Seisen on 2007-04-26
Here's a guide that might work, let us know if it doesn't work.

[http://ubuntuforums.org/showthread.php?t=285809]("http://ubuntuforums.org/showthread.php?t=285809")

---

### Post by locksmithdan on 2007-04-27
ok, 14e4:4318 was the output
and to Seisen this is probably a stupid question, but when i'm blacklisting the native drivers am I supposed to replace the xx in 43xx with 18 or am I supposed to just leave it that way? when I leave it with the "x"s I get this: ERROR: Module bcm43xx does not exist in /proc/modules
daniel@daniel-laptop:~$ 
when i put in 18 i get the same error only, obviously, it's bcm4318 doesn't exist

---

### Post by Bachstelze on 2007-04-27
You need to leave it as is (bcm43xx). Also, the *rmmod* is supposed to **r**e**m**ove the **mod**ule so if the module wasn't already there, it's still fine, you can go ahead :)

---

### Post by locksmithdan on 2007-04-27
when I continued and entered the next code this is what happened: daniel@daniel-laptop:~$ sudo ndiswrapper -i /location_of_your_wireless_driver/bcmwl5.inf
installing bcmwl5 ...
couldn't open /location_of_your_wireless_driver/bcmwl5.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 174.
daniel@daniel-laptop:~$ 
daniel@daniel-laptop:~$

---

### Post by Bachstelze on 2007-04-27
That's because you're not supposed to type it literally but enter the path to where the driver is located on *your* hard drive. To dowload and install it, do :

```

cd
mkdir Drivers
cd Drivers
```

then, if you can get online on your Ubuntu machine, do :

```
wget ftp://ftp.compaq.com/pub/softpaq/sp33001-33500/sp33008.exe
```

else, download if from another one, put it on your desktop and do

```
mv ../Desktop/sp33008.exe .
```

then you can go on :

```
cabextract sp33008.exe
sudo ndiswrapper-1.9 -i bcmwl5.inf
sudo ndiswrapper-1.9 -l
```

if that says "driver installed, hardware present", you can go on with

```
sudo depmod -a
sudo modprobe ndiswrapper
sudo iwconfig
```

your wireless interface should appear.

---

### Post by seismicmike on 2007-04-27
Here's some fun! I have a Gateway M320 Notebook (PLEASE NOBODY MOCK ME FOR MY NON COMPATIBLE HARDWARE) that had a built in wireless card that was working fine until I lost the drivers in an OS reinstall (the gateway support website no longer has the right version of the driver) so I bought a card... Belkin Wireless G+, part number F5D7011 in case anyone is interested... I downloaded the correct driver from Belkin's website (b/c I don't know where the CD is right now)....

it's not bcmwl5.inf... it's bcmwl6.inf... don't know if that makes any difference, but....

I follow every single step in this how to and even some other hints from [http://ubuntuforums.org/showthread.php?p=2544889&posted=1#post2544889](http://ubuntuforums.org/showthread.php?p=2544889&posted=1#post2544889)

and get absolutely NOTHING from my card. ndiswrapper -l tells me that the driver is installed and the hardware is present, but the networking gui, ifup and ifdown and iwconfig tell me it isn't there... there are no lights on the card... but the driver is installed and is present...

YES I have done modprobe ndiswrapper. Any suggestions?

In a perfect world I would have a Mac with OSX Tiger and Ubuntu on a dual boot, but I don't have the kind of money necessary to make this happen.

---

### Post by Bachstelze on 2007-04-27
After ndiswrapper -l told you "driver installed, hardware present", did you do those ?

```
sudo depmod -a
sudo modprobe ndiswrapper
```

---

### Post by locksmithdan on 2007-04-27
when I got this far: sudo ndiswrapper-1.9 -l, it didn't say driver installed hardware present, it said daniel@daniel-laptop:~/Drivers$ sudo ndiswrapper-1.9 -l
bcmwl5 : invalid driver!
according to the other guide I have a different card. A different guide told me I could check using this comand: lspci | grep Broadcom\ Corporation
so I did and I got this as the output: 02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
02:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
which seems like it should be the same card unless there's something very counterintuitive. I guess me being an idiot would be another option that seems pretty likely. Thanks a lot for the help thus far. It feels like i'm moving forward even if it still doesn't work.

---

### Post by bedfojo on 2007-04-27
There are actually a number of different drivers for BCM 4318 cards.

I have an Acer Aspire 3613WLMi and if I have to use the one from the Acer website for my laptop. If I use the one posted in some install scripts, I get the same message as you.

So download the latest driver for your specific laptop model from the manufacturers website and use that version of bcmwl5 with ndiswrapper (removing the old one first). See if that helps.

---

### Post by locksmithdan on 2007-04-27
i feel really dumb, but how do I remove the old ones?

---

### Post by Bachstelze on 2007-04-27
sudo ndiswrapper-1.9 -r DRIVER_NAME

---

### Post by saadakhtar on 2007-04-27
you do not have to use NDISWRAPPER necessarily
if i am not mistaken this is a very common broadcom chipset based wireless card. I have one on my laptop and i had to install only 1 package to get it to work.

Please follow these instructions:
make sure that you have access to internet on you machine. most probably a wired connection thru ethernet since your wireless interface is not working yet!
start your package manager (synaptic)

Now search for: "wlan-ng"
this is the linux native driver for broadcom chipset wireless cards
install this package.

Now restart your computer. In terminal you can type "shutdown -r now" or simply follow the GUI way to do the same task. Once you machine is up. start terminal.

Now do the following:

sudo -s
type in your root password

ifdown wlan0

and then type in

ifup wlan0

you should see your wireless card trying to associate to the nearest and strongest network. But its not all done yet. You need to have a connection manager to handle all you SSID's.

Now using you package manager search for "kwlan" (this is what i recommend) install it and now use it to manage your wireless connections.

Hope this works for you

enjoy.

---

### Post by seismicmike on 2007-05-23
> **HymnToLife said:**
> After ndiswrapper -l told you "driver installed, hardware present", did you do those ?

```
sudo depmod -a
sudo modprobe ndiswrapper
```

uuuuuuuuuuumm... yes.... I followed instructions step by step here: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

and nothing........

---

### Post by seismicmike on 2007-05-29
OOOOKAY!!! Here's some interesting times... I tried out MEPIS for a bit which comes pre-installed with ndiswrapper (something ubuntu propper should consider!) and it was nice b/c they have this network assistant that did everything (EVERYTHING) automatically - and it had a bunch of drivers pre-installed.... Well.. I tried to do some upgrades and screwed the distro up (I changed all repositories to feisty and said mark all upgrades... I guess for some reason it decided to install Korean fonts (cause i'm in Korea) and it didn't work right and so all I had were boxes instead of text) and got to a point where I knew I had to re-install so I decided to give ubuntu another try.... so I grabbed the wireless drivers that Mepis came with (off the live CD) and tried them in ubuntu and LOW AND BEHOLD THEY WORK!!! (to some extent)

I used synaptic to install ndiswrapper along with ndgk (or whatever it's called - the gui) And I installed the driver and it said "driver installed, hardware present"

Now unlike times before where I've gotten this far, the device actually appears in the network dialogue System > Administration > Networking BUT It won't connect to the network!!!!!

Does anyone know where to go from here? I've tried Wireless Assistant (wlassistant). I've tried K Network Manger... I've tried configuring the card by DHCP and using a static address - no network. iwconfig sees the card, but again I can't get it to connect to the network. I've edited the /etc/network/interfaces file manually - no dice.

Does anyone have any suggestions???? I see the light at the end of the tunnel! Please help me out!!!

---

### Post by Count Doofus on 2007-10-21
You'll get that error @ line 174 if the case of the filename  is wrong !
Got Nailed by missing that for a while.


had the same problem with my Marvell card. Looked for every kind of solution that concerned hardware interface on the PCI bus.

The Real Problem was every time I issued the 
blablabla:~$ sudo ndiswrapper -i mrv8000c.inf 
I got - No such file or directory at /usr/sbin/ndiswrapper-1.9 line 174

Until I typed the filename with the correct CASE - Mrv8000c.INF - 

GRRRRRRRRR!%@$#$###!$!@@!$@!@#!

---

### Post by Count Doofus on 2007-10-21
You'll get that error @ line 174 if the case of the filename  is wrong !

That kicked my butt up and down the road for 3 days, always staring me right in the face !!!!!!!

had the same problem with my Marvell card. Looked for every kind of solution that concerned hardware interface on the PCI bus.

The Real Problem was every time I issued the 
blablabla:~$ sudo ndiswrapper -i mrv8000c.inf 
I got - No such file or directory at /usr/sbin/ndiswrapper-1.9 line 174

Until I typed the filename with the correct CASE - Mrv8000c.INF - 

GRRRRRRRRR!%@$#$###!$!@@!$@!@#!

---

