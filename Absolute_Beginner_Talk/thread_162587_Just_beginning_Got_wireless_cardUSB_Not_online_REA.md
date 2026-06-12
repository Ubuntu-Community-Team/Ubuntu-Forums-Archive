---
title: "Just beginning? Got wireless card/USB? Not online? READ THIS!"
date: 2006-04-19
forum: Absolute Beginner Talk
---

### Post by TrojanSkin on 2006-04-19
Compiled and modified from posts by vcelis. With MANY thanks! I'm posting 
it here in one hit for simplicity and later linking.

This should get you online wirelessly with Windows drivers on most 
wireless cards or USB adapters.

OK. I have only used Linux and Ubuntu for two days. I could NOT get 
online! I just tried this with my 3Com Office Connect 802.11g 54g USB wireless adapter with no problems at all, on Ubuntu 6.06. Straight online 
after! Yesterday I was ready to give up! ](*,) 

- Get ndiswrapper-utils by typing "sudo apt-get install ndiswrapper-utils" 
in a terminal.
Give the root password when necessary.
- Get the Microsoft Windows drivers from your installation CD. Copy the 
.inf and .sys file. Paste these into a new folder on the desktop and name 
it driver. 
(eg. /home/<USERNAME>/Desktop/driver/)

- Open a terminal
- Type the following commands:

$ cd Desktop/driver/
$ sudo ndiswrapper -i <name>.inf
$ sudo modprobe ndiswrapper

You have to repeat the last step whenever you want to use your 
device within a session.

(If you are not online, the command "sudo apt-get install 
ndiswrapper-utils" will check your CD drive for your Ubuntu CD and get it 
from there).

You can use the Network tool to configure your wireless connection and 
connect with the network, or you can follow these steps:

- Open a terminal
- Type the following commands:

$ sudo iwlist wlan0 scan (look for your access point in the list)
$ sudo iwconfig wlan0 channel YOUR_CHANNEL essid YOUR_ESSID mode Managed 
(YOUR_CHANNEL and YOUR_ESSID should come from the iwlist)
$ sudo ifup wlan0

The second didn't work for me, but I know it has for other people.
Enjoy and DON'T give up!

Thanks again to vcelis for spelling it out, so even I could do it!

P.S. Copy and save this for when you're offline!

EDIT:
Install Wifi-Radar
Click on your connection
Click edit
Enter #sudo modprobe ndiswrapper (without #)
Save
Close

When you restart, just click on Wifi-Radar, click on your connection, and connect. 

Works for me on Breezy.

---

### Post by az on 2006-04-19
Dapper users will find a number of their previously unsupported cards now have native linux drivers.  This will bork using ndiswrapper.  As well, this will brok ndiswrapper.

The solution is to try using the card without ndiswrapper when you upgrade to Dapper (remove the windows driver:  sudo ndiswrapper -e XXXXX) and reboot to see if you have wireless support.  If you don't, reinstall ndiswrpaper.

If you do, but still prefer to use ndiwrapper, you need to blacklist the linux driver module from being loaded so that you don't have two drivers trying to use the same device - this doesn't work!

To blacklist a module, add it to /etc/modprobe.d/blacklist

---

### Post by khightower on 2006-04-19
Just purchased a SMC Networks Wireless Card ($29.00). Works automatic under Dapper. 802.11 G.

Model # SMCWPCI-G

---

### Post by RedFoxEvan on 2006-04-21
I can't do it :S Could anyone fancy doing remote assistance for me? Maybe I will pay too :D

MSN: [email]Evan@sure-hosting.net[/email]

Regards

---

### Post by Jason_25 on 2006-04-21
You'll find plenty of remote assistance on this forum if you actually take the time to describe exactly what your hardware is, where you got stuck, etc...

---

### Post by tpubunutu on 2006-04-22
great!  got it working in no time following your directions.

Why do I need to do this (well a few of the steps) every time I reboot?

**Is there a way to save the settings?**



Any ideas?

Thanks.

Three nights on ubuntu... first exposure to Linux.  I like it but have lots to learn.  like what does sudo mean...

---

### Post by Jason_25 on 2006-04-22
sudo stands for superuser do.  I also think of it like pseudo, like becoming a pseudo-root user when you use it, or something like that.  

Modules you want loaded go in /etc/modules and networking settings go in /etc/network/interfaces.

---

### Post by tpubunutu on 2006-04-22
[QUOTE=Jason_25]sudo stands for superuser do.  I also think of it like pseudo, like becoming a pseudo-root user when you use it, or something like that.  

Modules you want loaded go in /etc/modules and networking settings go in /etc/network/interfaces.[/QUOTE]
Thanks.  So what would I do with the directions above to keep the wlan0 settings.  Still unsure.

---

### Post by Jason_25 on 2006-04-22
The interfaces file should look something like this:
```

auto lo eth0

iface lo inet loopback

iface wlan0 inet static
address ?.?.?.?
netmask 255.255.255.0
wireless-essid insertessidhere

```
The netmask may be different if you don't use a 192.X.X.X address.

---

### Post by Maria_Firewire on 2006-04-22
So I to have been having problems with getting my wireless interent to work. I have a Proxim Orinoco Gold 11abg PCI card...I followed the steps and installed the ndiswrapper utility and then installed the driver (inf) file. I configured my wireless setting and it is "seeing" the available networks in my neighborhood and says that wlan0 is "active" but I still can't connect to the internet.

Any ideas...I feel like this is probably some small dumb thing I'm forgetting. Any help is much appreciated!

Thanks,

Maria

---

### Post by Maria_Firewire on 2006-04-22
Also, when I try to do it manually using "sudo iwlist wlan0 scan".....it says that wlan0         interface doesn't support scanning

Is there another util i need to install?

---

### Post by tpubunutu on 2006-04-22
[QUOTE=Jason_25]The interfaces file should look something like this:
```

auto lo eth0

iface lo inet loopback

iface wlan0 inet static
address ?.?.?.?
netmask 255.255.255.0
wireless-essid insertessidhere

```
The netmask may be different if you don't use a 192.X.X.X address.[/QUOTE]

OK.  I checked the interfaces and looks like above except not set to static.

I do not have etc/modules

Should I have it?

If so what should go there?

---

