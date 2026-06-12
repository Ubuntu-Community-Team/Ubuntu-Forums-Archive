---
title: "Some questions setting up the network"
date: 2006-01-29
forum: Absolute Beginner Talk
---

### Post by deavik on 2006-01-29
Hi there,

I just switched from Windows XP, and before anything else I wanted to congratulate the developers (if they're watching) on a great job! I'm loving Ubuntu.

Now, I've got my ethernet card and pppoe dsl service configured with pppoeconf. But, by default network-admin does not activate the eth0 connection on start up. How can I change this?

Second question: After getting eth0 active I have to run a command from terminal-
pon dsl-provider

Can I get this to run at startup as well?

Thanks,
Avik

---

### Post by cmongini on 2006-01-29
hi i just came to solve this problem 8 installed ubuntu some days ago....
have you already been at the menu:
system>administration>networking
there you can activate your connection ( and put also the right identification values) i did this and then it remained activated. 
if then you want to biuld a little home network, i suggest you this link as it worked for me: 
[http://ubuntuforums.org/showthread.p...=share+network](http://ubuntuforums.org/showthread.p...=share+network) ?
about the second question i have no idea....

---

### Post by deavik on 2006-01-29
Hi cmongini, I am having to activate my eth0 interface everytime ubuntu starts, that's exactly what I want to automate. I didn't get what you meant by the right identification values ... :confused:

---

### Post by cmongini on 2006-01-30
hi deavik, i gave you these suggestions because i thought you would have activated the connection in some other way ( maybe during the installation process) and this was why you hat to reactivate it every time...but  if you activated it  already through system> administration>networking, then, sorry, i´ m clueless....... 
by identification values i meant the IP adress, standard gateway and so on....
maybe: do you put in the Ip adress manually or have you got DHCP activated? 
i put in mine manually, and it´ s working.....
hope you solve your problem 
regards 
claudia

---

### Post by imrumpf on 2006-01-30
I had the same problems and played around till I finally came up with a soultion. Here is the thread i started outlining my experiences:

[http://ubuntuforums.org/showthread.php?t=110480](http://ubuntuforums.org/showthread.php?t=110480)

Maybe that will help you at all? Nobody replied to the thread so I have no idea if it would work for anybody else either :(

---

### Post by deavik on 2006-01-30
@cmongini

I don't have DHCP, so I had to put in a guessed (?) IP address, which is working OK. But  as I said it does not activate the interface on startup

@imrumpf

Thanks for the helpfl link. I just have pppoeconf installed. It's working oK, so I'm guessing I don't need the pppoe package? I tried putting `pon dsl-provider' in sessions > startup, but it didn't work. I guess the main problem is getting network to activate eth0.

The file `/etc/network/interfaces' looks interesting. pppoeconf added an entry in there, `auto eth0'. Does that help any?

---

### Post by imrumpf on 2006-01-30
When i installed pppoe AFTER doing ppoeconf, it overwrote the configuration file and added a lot more stuff to the file which enabled it to actually work properly. Don't ask how or why, because I don't know :p I just know it worked for me. If i remember correctly pppoe is a KDE package, and i've noticed that Kubuntu has much better network support than Ubuntu. I don't have DSL at home here so I cannot include the file, but you are going to have to trust me that it did make a difference. without that pppoe package i had to run pppoeconf every single time i wanted to connect to the internet.

if you're scared that pppoe will break something, you can do this:

To install:
```
sudo cp /etc/ppp/peers/dsl-provider /etc/ppp/peers/dsl-provider_backup
sudo apt-get install pppoe
```

To remove:
```
sudo apt-get remove pppoe
sudo cp /etc/ppp/peers/dsl-provider_backup /etc/ppp/peers/dsl-provider

```

Let me know how things go.

---

### Post by deavik on 2006-01-31
No that didn't work, I had to revert back to my old copy of dsl-provider, sorry. Thanks for the help anyway, imrumpf. :)

---

### Post by mips on 2006-01-31
deavik,

I see you are using ethernet ? ou 'might' not need all this PPPoE crap.

What brand&model is your ADSL device ?
Who is your ISP, weblink please ?

---

### Post by carlosqueso on 2006-01-31
if the card activates fine in the network manager, but doesn't at startup, type ```
sudo gedit /etc/network/interfaces
``` and post that if you wouldn't mind.   I think you can add ```
auto eth0
```to the end and it may work.

---

### Post by deavik on 2006-02-01
@mips

I would be very happy if I didn't :D 

I have a Realtek RTL8139 PCI card. My ISP you would probably not know, but here it is anyway: BSNL India.

@carlosqueso

auto eth0 is already at the end, and IIRC pppoeconf added it there. For the benefit of your advice I am going to attach the whole of my network/interfaces file:

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth0

iface eth0 inet static
address 127.0.0.0
netmask 255.255.0.0







#auto dsl-provider
#iface dsl-provider inet ppp
#provider dsl-provider

# added by pppoeconf
auto eth0

    pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf

```
The lines
#auto dsl-provider
#iface dsl-provider inet ppp
#provider dsl-provider
I had commented earler on I don't remember why ... I could put them back in again, do you think it will help?

---

### Post by mips on 2006-02-01
[QUOTE=deavik]@mips

I would be very happy if I didn't :D 

I have a Realtek RTL8139 PCI card. My ISP you would probably not know, but here it is anyway: BSNL India.
[/QUOTE]

No, not the network card. What ADSL Modem/Router do you have Brand & Model ??? (Cisco, Dlink, Netgear, Siemens etc)

---

### Post by deavik on 2006-02-01
Oh sorry. The modem is a UTStatcom UT-300R

---

### Post by mips on 2006-02-01
Please be a bit more specific, there are several different models.
Pick yours from this page [http://www.utstar.com/Solutions/CPE/ADSL_CPE/](http://www.utstar.com/Solutions/CPE/ADSL_CPE/)
and let me know which one you have, exact model number.

The good news is that it looks like you wont need the PPPoE stuff :) It will only take a minute or two to configure your UT-300? once you told me which one you have.

---

### Post by alamba on 2006-02-01
Deavik...another way to get this sorted out quickly would be to drop in a post in Delhi LUG (Linux user group). I know a number of people have do this specific model working from BSNL. Also, are you using the USB or ethernet interface? If it's USB u need to change to ethernet.

Akshay

---

### Post by deavik on 2006-02-01
@mips

You're giving me a lot of encouragement, thanks for the help. And about the model, it's the very last one on the page you linked to (UT-300RA). I was searching for a link to the manufacturer to give you (which you found) but google kept turning up results in chinese :???: 

@ alamba

I'm already using ethernet, and thanks for LUG tip--do you have a link? I googled, and it turned up lots of results (which is good I suppose) :)

---

### Post by deavik on 2006-02-04
I've fixed it! For the reference of anybody who has similar problems, pppoeconf messed up my /etc/network/interfaces file. I sat down with its manual (`man interfaces') and tweaked it a bit. Now it even synchronizes the system clock with an Ubuntu server on start-up! Here is my interfaces file itself:

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth0


auto eth0
iface eth0 inet static
	post-up /sbin/ifconfig eth0 up
	post-up /usr/bin/pon dsl-provider
	address 192.168.1.10
	netmask 255.255.255.0
	gateway 192.168.1.1

```
Three cheers for man pages :)

---

### Post by alamba on 2006-02-04
[http://frodo.hserus.net/mailman/listinfo/ilugd](http://frodo.hserus.net/mailman/listinfo/ilugd)

Just incase.

Akshay

---

### Post by mips on 2006-02-04
So I assume it is working then.

For UTStar model routers and BSNL ISP the reference below provides all the correct parameters.
[http://blog.taragana.com/wp-content/upload/bb7.swf](http://blog.taragana.com/wp-content/upload/bb7.swf)

---

