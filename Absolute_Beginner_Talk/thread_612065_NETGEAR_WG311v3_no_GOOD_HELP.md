---
title: "NETGEAR WG311v3 no GOOD HELP"
date: 2007-11-13
forum: Absolute Beginner Talk
---

### Post by Church.Cameron on 2007-11-13
I have the netgear WG311v3, and i cannot figure out how to set it up i have on my desktop of ubuntu 7.04 madwifi which was recomended to use with the atho chipset, but i am not good with terminal so i need some help getting this card to work, i have no internet on that machine so its been a hand off from my laptop to my desktop with crap. please help me get this machine going with ubuntu

---

### Post by Pumalite on 2007-11-13
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsByVersion](https://help.ubuntu.com/community/WifiDocs/WirelessCardsByVersion)

---

### Post by Church.Cameron on 2007-11-13
didn't help mad me just really confused

is there anymore walkthoughs on how to get madwifi to work

its from what i can tell what i need. i can't seem to wrap the drivers

---

### Post by eldepeche on 2007-11-13
According to [this page](http://madwifi.org/wiki/Compatibility/Netgear), that card is not supported by the madwifi driver. 

Apparently, this card will work through ndiswrapper. You should get the Windows drivers for this card from the Netgear website, then follow [these instructions](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper).

---

### Post by Church.Cameron on 2007-11-13
for some reason i don't have ndiswrapper

how do i get it i tried sudo but it will not work ?

it says it should be already installed but when i try to run it its saying its not there

---

### Post by eldepeche on 2007-11-13
ndiswrapper is installed by default, but maybe you need to install ndiswrapper-utils .

---

### Post by Church.Cameron on 2007-11-13
how do i do that i am so confused never had to do this before sorry for the annoyance i might be causing

---

### Post by Church.Cameron on 2007-11-13
so i sudo ndiswrapper and i get this E: invalid operation ndiswrapper?

---

### Post by eldepeche on 2007-11-13
You want to run:
```
sudo apt-get install ndiswrapper-utils
```

After that, you would run
```
sudo ndiswrapper -i /path/to/driver.inf
```
where /path/to/driver is the actual path and file name for the driver that you got from the Netgear website.

---

### Post by Church.Cameron on 2007-11-13
ARRRGH!!!

ok so i did the first string and i got this 

cameron@cameron-desktop:~$ sudo apt-get install ndiswrapper-utils 
Reading package lists... Done 
Building dependency tree       
Reading state information... Done 
E: Couldn't find package ndiswrapper-utils 
cameron@cameron-desktop:~$ 
 
what am i doing wrong?

this util is sitting on my desktop should i have it somewhere else?

---

### Post by eldepeche on 2007-11-13
Sorry, my fault. If you're running 7.10 Gutsy Gibbon, use 
```
sudo apt-get install ndisgtk
```
This should install a graphical tool under System -> Administration.

---

### Post by Church.Cameron on 2007-11-13
[IMG]http://i47.photobucket.com/albums/f164/ice_kenshin/Screenshot.png[/IMG]


what is it i am doing wrong

---

### Post by bapoumba on 2007-11-13
Please read my sig, last line.

---

### Post by Church.Cameron on 2007-11-13
no i do have my laptop on gusty but not this machine (lost the disk) this one is running fiesty

---

### Post by Church.Cameron on 2007-11-13
ok i will not thank you...

---

### Post by eldepeche on 2007-11-13
Do you have all the repositories enabled? Go to System -> Administration -> Software Sources and make sure main and universe are checked.

---

### Post by Church.Cameron on 2007-11-13
yea its checked is it hopeless or what?

---

### Post by amingv on 2007-11-13
Hi,

I'll just throw some stuff to the pool and see if it floats; seeing it from a different angle. I also have a Netgear card, but unlike yours it's an USB "wireless stick". Still, maybe it will work, who knows?

I was working around it a couple of hours ago because of an odd behavior (for some reason it would work on Kubuntu Feisty (Knetworkmanager[KDE]) but if I tried my server (Ubuntu feisty + XFCE) or even in my Gnome session in the same Kubuntu machine it wouldn't work). Ndiswrapper is not an option for me (personal issues) But hey, I had a KDE-Gnome machine. I did the obvious and opened Knetworkmanager in Gnome, (almost unsurprisingly) it worked. But using Knetworkmanager under Gnome was not elegant, and I wanted a better solution. If you don't mind trying a newbie-made solution, based on an almost-absolute guess-job and lots of serendipity here's what I did:

-Go to System>Administration>Network, in my case the card was listed there*, in roaming mode. For the moment never mind the **wmaster0** one, just double-click on the **wlan0** one.

-Uncheck the "Enable roaming mode" option. Now enter your ESSID** (it must be EXACTLY as defined by your wireless point, so mind every detail). Then enter your WEP code and finally, under "Configuration" choose "Automatic Configuration (DHCP)". Ckick on OK and close your network settings.

-Now unplug your wired connection (if any). Open a Terminal and run this code:

```
sudo ifup -a --force
```

This will go trough all your connections, if at any moment you get something like this:

```
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.254 [COLOR="Blue"]#<--Or whatever your access point address is[/COLOR]
bound to 192.168.1.1 -- renewal in 1597 seconds.

```

Then you have hit the jackpot. Open your firefox and see if it works.

[SIZE="1"]*From the beginning I had the hunch it was not a driver thing (mostly because it worked with Knm) but this seemed like a quite odd behavior to me.
**Here's when I had my "Moment of clarity", one would expect to get the ESSID from the list, but for some reason it wouldn't come up (neither my neighbor's nor anyone else's; a bug in network-admin, maybe?). So i typed it manually and somehow it worked.[/SIZE]

---

### Post by TheIrishGuy on 2007-11-13
[http://ubuntuforums.org/showthread.php?t=592137&highlight=wg311v3](http://ubuntuforums.org/showthread.php?t=592137&highlight=wg311v3)

---

### Post by Church.Cameron on 2007-11-14
amingv,

nice try but unfortunately  this will not work for me its a good shot but not for me.

thank you for trying. i will make sure if this post relates to something with that sort i will forward that knowledge to them

---

### Post by macenroe0 on 2008-01-16
Yes, I am also having same problem of this give me a [NETGEAR WG311v3]("http://www.ehpdeals.com/") suggestions as soon as possible. i will make sure if i get any post related to this  with that sort i will forward that to you.

---

