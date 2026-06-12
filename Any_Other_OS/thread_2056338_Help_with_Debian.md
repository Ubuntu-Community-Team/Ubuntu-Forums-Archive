---
title: "Help with Debian"
date: 2012-09-11
forum: Any Other OS
---

### Post by Not install on 2012-09-11
Hello after trying to install Ubuntu and failing on dell latitude I somehow installedvdebian and went thought the auto wizard for dchp

But I see no Internet logo 

Since Debian is based of Ubuntu what do I have to do as I normally use Ubuntu and it automatically has the Internet icon on the top task bar this is not the case on debian 

Please help

---

### Post by nothingspecial on 2012-09-11
*Thread moved to **Other OS/Distro Talk**.*

---

### Post by Not install on 2012-09-11
> **nothingspecial said:**
> *Thread moved to **Other OS/Distro Talk**.*

What's this link  for please

---

### Post by nothingspecial on 2012-09-11
> **Not install said:**
> What's this link  for please

So you know who moved it, ie me.

---

### Post by Not install on 2012-09-11
> **nothingspecial said:**
> So you know who moved it, ie me.

Right ok can you help me please nothing special there no Internet icon like there should be because Ubuntu has Internet icon on he top task bar after install but I don't see one here I have no Internet access on that computer

I did want to nstall Ubuntu but it would not install n that dell for some reason I have a post here some where asking for support but regret installed Debian but no Internet connectivity even after I did the dchp setup at install wizard it said successful but I don't see how to connect online 

Please help

---

### Post by mips on 2012-09-11
What desktop environment are you using?

---

### Post by Not install on 2012-09-11
> **mips said:**
> What desktop environment are you using?



Thank you for your reply I'm using the [http://cdimage.debian.org/debian-cd/6.0.5/kfreebsd-i386/iso-cd/debian-6.0.5-kfreebsd-i386-CD-1.iso](http://cdimage.debian.org/debian-cd/6.0.5/kfreebsd-i386/iso-cd/debian-6.0.5-kfreebsd-i386-CD-1.iso)

---

### Post by Not install on 2012-09-11
> **Not install said:**
> Thank you for your reply I'm using the [http://cdimage.debian.org/debian-cd/6.0.5/kfreebsd-i386/iso-cd/debian-6.0.5-kfreebsd-i386-CD-1.iso](http://cdimage.debian.org/debian-cd/6.0.5/kfreebsd-i386/iso-cd/debian-6.0.5-kfreebsd-i386-CD-1.iso)

Gnome 2 enviro

---

### Post by tartalo on 2012-09-11
[http://forums.debian.net/viewtopic.php?f=17&t=69460](http://forums.debian.net/viewtopic.php?f=17&t=69460)

---

### Post by d3v1150m471c on 2012-09-11
> Debian is based of Ubuntu
Ubuntu is based off Debian

---

### Post by Not install on 2012-09-11
[QUOTE=d3v1150m471c;12232215]Ubuntu is based off Debian[

Hi do you know what I can do to get online from the Debian distro please 

Do I do /etc/network/interfaces?

---

### Post by mips on 2012-09-11
yes you should be able to manually specify your ip settings in /etc/network/interfaces

Will have to do it with sudo or root.

---

### Post by Not install on 2012-09-11
> **mips said:**
> yes you should be able to manually specify your ip settings in /etc/network/interfaces

Will have to do it with sudo or root.



Can you please please tell me how to as I understand it his right in terminal as root


 sudo nano /etc/networking/interfaces

Then I add  

Eth0 
Hot-plug eth0

Then save by pressing control and o

Then close the /etc/networking/interface. A warning message appears a process is still going but I still press the close button and then I go into the empheny browser but it still says offline

Have I got the instructions wrong? Mips

---

### Post by mips on 2012-09-11
This is what mine looks like, you will have to change your address to whatever is in use on your network/router.

```

# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.0.10
netmask 255.255.255.0
network 192.68.0.0
broadcast 192.168.0.255
gateway 192.168.0.1
```

or if you want automatic config via dhcp you can try

```
iface eth0 inet dhcp
```

You might also have to setup your DNS servers, /etc/resolv.conf
```
nameserver 192.168.1.1
```

Point the above to your router or to a DNS server of your isp or the opendns ones.

To make the network config active you have to stop, start or restart the service as root/sudo, these are available options,

```
/etc/init.d/networking stop
/etc/init.d/networking start
/etc/init.d/networking restart
```

[http://www.cyberciti.biz/faq/howto-configuring-network-interface-cards-on-debian/](http://www.cyberciti.biz/faq/howto-configuring-network-interface-cards-on-debian/)

The above should get you a network connection and then you can do a apt update and install network manager.

---

### Post by Not install on 2012-09-11
> **mips said:**
> This is what mine looks like, you will have to change your address to whatever is in use on your network/router.

```

# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.0.10
netmask 255.255.255.0
network 192.68.0.0
broadcast 192.168.0.255
gateway 192.168.0.1
```

or if you want automatic config via dhcp you can try

```
iface eth0 inet dhcp
```

You might also have to setup your DNS servers, /etc/resolv.conf
```
nameserver 192.168.1.1
```

Point the above to your router or to a DNS server of your isp or the opendns ones.

To make the network config active you have to stop, start or restart the service as root/sudo, these are available options,

```
/etc/init.d/networking stop
/etc/init.d/networking start
/etc/init.d/networking restart
```

[http://www.cyberciti.biz/faq/howto-configuring-network-interface-cards-on-debian/](http://www.cyberciti.biz/faq/howto-configuring-network-interface-cards-on-debian/)

The above should get you a network connection and then you can do a apt update and install network manager.


Hi sorry for my stupidity I typed iface eth0 inet dhcp

And it got

Bash 
:command not found


How do you find the router address btw

---

### Post by Not install on 2012-09-11
Hi MIPS I have tried to edit the sudo nano etc/networking/interfaces. File

And have tried to add the following line


# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.0.10
netmask 255.255.255.0
network 192.68.0.0
broadcast 192.168.0.255
gateway 192.168.0.1


But when I press control and zero it has a error writing /etc/networking/interface no such or director the file is empty to begin with

.??????

---

### Post by Not install on 2012-09-11
Hello

 Have edit the nano /etc/network/intefaces

And now it reflects like this

#The loop back interface
Auto lo eth0
Iface lo inet loopback



#the primary network interface
Allow-hot plug eth0
#networkmanager#iface eth0 inet dhcp


Then I saved the network interface file by pressing  control then o then close the terminal 

Then reopen terminal as root  typed sudo /etc/init.d/networking restart

Running /etc/init.d/networking restart is deprecated because it may not enable a gain some features... (Warning)

Reconfiguring network interfaces...ingnoring unknow interface eth0=eth0.
Done.



Then I click on ice weasel or epiphany and server not found check the address if unable to load check computers connection

Can anyone help me sort the situation out please in trouble getting connected I would have thought Debian would have automatically set this all up for me as I was plugged in wired Ethernet at the time of installation?

Any ideas

---

### Post by mips on 2012-09-11
Try

```
sudo /etc/init.d/networking stop
sudo /etc/init.d/networking start
```

Do you have windows on that computer or any other computer on the same network?

If you do open a dos prompt, Select run from the menu and type **ipconfig /all** and post the output here, this will give you all your networking details.

Debian might not be for you, what went wrong with your Ubuntu install? Maybe it's easier to get that going for you.

Do you have access to X-Chat while installing this from another PC? If you do you I can try and talk you through things on the freenode server on the #mips1911 channel

---

### Post by Not install on 2012-09-11
> **mips said:**
> Try

```
sudo /etc/init.d/networking stop
sudo /etc/init.d/networking start
```

Do you have windows on that computer or any other computer on the same network?

If you do open a dos prompt, Select run from the menu and type **ipconfig /all** and post the output here, this will give you all your networking details.

Debian might not be for you, what went wrong with your Ubuntu install? Maybe it's easier to get that going for you.

I ran you code. 
[CODE]sudo /etc/init.d/networking stop(code). Reconfiguring network interfaces done 



sudo /etc/init.d/networking start[/CODE). Configuring network interfaces... If config : interface lo does not exist 
Failed to bring up lo

Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Ifconfig: interface eth0 does not exist
Can't attach interface eth0 to bpf device /dev/bpf0: no such device or address
Failed to bring up eth0
Done.


Any ideas


Well Ubuntu just stay stuck on the four lights with purple background like it freezes here the link of my machine and Ubuntu freezing [http://i.imgur.com/5Qoof.jpg]("http://i.imgur.com/5Qoof.jpg"). Still was like that after 3 hours


I would make a xchat but I don't know what that is are you saying a walk through of the ubuntuninstall through xchat. I haven't got windows on here or another machine

How do I get to the schat free node channel for you I can get to social chat ubuntu this link?  [http://webchat.freenode.net/?channels=ubuntuforums](http://webchat.freenode.net/?channels=ubuntuforums)

---

### Post by mips on 2012-09-11
This part of your /etc/network/interfaces is incorrect,

```
#The loop back interface
Auto lo **eth0**
Iface lo inet loopback
```

That part should read,

```
#The loop back interface
auto lo
iface lo inet loopback
```

---

### Post by Not install on 2012-09-11
> **mips said:**
> This part of your /etc/network/interfaces is incorrect,

```
#The loop back interface
Auto lo **eth0**
Iface lo inet loopback
```

That part should read,

```
#The loop back interface
auto lo
iface lo inet loopback
```

I have changed to to the above but still no luck. It now reflects as
And now it reflects like this

#The loop back interface
Auto lo 
Iface lo inet loopback



#the primary network interface
Allow-hot plug eth0
#networkmanager#iface eth0 inet dhcp

---

### Post by mips on 2012-09-11
> **Not install said:**
> 
How do I get to the schat free node channel for you I can get to social chat ubuntu this link?  [http://webchat.freenode.net/?channels=ubuntuforums](http://webchat.freenode.net/?channels=ubuntuforums)

Just change #ubuntuforums to #mips1911 use whatever nickname you want and connect.

---

### Post by Not install on 2012-09-11
> **mips said:**
> Just change #ubuntuforums to #mips1911 use whatever nickname you want and connect.

Ok great be there soon thanks

---

### Post by mips on 2012-09-11
> **Not install said:**
> I have changed to to the above but still no luck. It now reflects as
And now it reflects like this

#The loop back interface
Auto lo 
Iface lo inet loopback



#the primary network interface
Allow-hot plug eth0
#networkmanager#iface eth0 inet dhcp

Make it look like this
```
#The loop back interface
auto lo 
iface lo inet loopback


#the primary network interface
allow-hot plug eth0
iface eth0 inet dhcp
```

---

### Post by mips on 2012-09-11
Just an update.

Not install was actually using the Debian GNU/kFreeBSD cd image.

His laptop is a Dell Latitude CSX with 650 MHz P3 & 320MB ram & 3Com based PCMCIA lan adapter.

I also doubt the Ubuntu 12.04 desktop image would install on this machine dues to lack of memory.

I have advised him to download and gave him links to,
Lubuntu 12.04 i386 alternate image
Crunchbang 10 Stable i386 image
Macpup 529 image

He'll get back to me once he has the images and tried them out.

---

### Post by Not install on 2012-09-13
> **mips said:**
> Just an update.



Not install was actually using the Debian GNU/kFreeBSD cd image.

His laptop is a Dell Latitude CSX with 650 MHz P3 & 320MB ram & 3Com based PCMCIA lan adapter.

I also doubt the Ubuntu 12.04 desktop image would install on this machine dues to lack of memory.

I have advised him to download and gave him links to,
Lubuntu 12.04 i386 alternate image
Crunchbang 10 Stable i386 image
Macpup 529 image

He'll get back to me once he has the images and tried them out.

As above that's right Ubuntu would not install due to the old system I have. I had also made the big mistake of installing Debian kfreebsd which I now under Stand was never Linux to begin with and I think it was pretty confusing the way Debian had listed it among all the other normalmlinux distros I feel they should state that the image is not Linux and quite complicated if download as a beginer can not tell the difference and would just download the ISO without thinking about wether it is Linux or not how would someone know until they run into errors and someone in this support forum points it out that it is not Linux as MIPS did point out that's when I found out that it was not Linux 



 If I had know it was not Linux I would not have continued to try and fix the wifi and wireless issue on Debian kfreebsd and would have just installed pup mac if I had know this from the very start. As kfreebsd has too many problems as you propley know by reading my post 



Thank you very much MIPS for you help and support I have tried all the distros have the one with the most success was mac puppy it installed all the wireless and wired connection by auto configured so all went very smoothly it is running very fast too which I am quite surprised all in all worked very well with the help of your support


MIPS was the one who suggested the above distro as with his knowledge knew best which distro would run best on my old pc


The other iso above Lubuntu ISO as above would once again not install  the screen would just go blank i even tried it in nomodeset but still no install success mostly propley due to my system or maybe a error in the way i was installng i dnt know very old system I admit I did not try crunch bag as I was happy once mac pup installed and did not want any more problems by trying cruchbag as it may not have worked but once again I did not try that distro



the successfull was mac pup 529 image 



I could not have done this without the help and effort on the part of this forum user MIPS for which I am very greatfull for the upmost support provided by MIPS thank you very much

---

