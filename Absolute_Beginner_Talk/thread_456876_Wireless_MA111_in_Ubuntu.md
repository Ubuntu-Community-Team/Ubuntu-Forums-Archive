---
title: "Wireless MA111 in Ubuntu"
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by Andrew Garn on 2007-05-28
Hello

Firstly, I am completely new to linux, I installed in multibooted with Winxp on my laptop as a test.

I have a MA111 v1 usb wireless adapter I want to install and set up. So I googled it and found these two sites:

[http://ubuntuforums.org/showthread.php?t=22995](http://ubuntuforums.org/showthread.php?t=22995)
[http://www.linuxquestions.org/linux/answers/Networking/Netgear_MA111_USB_Wireless_Howto](http://www.linuxquestions.org/linux/answers/Networking/Netgear_MA111_USB_Wireless_Howto)

I tried the method described in the first link

sudo apt-get install ndiswrapper-utils - cannot find ndiswrapper utils or something similar, even though I had downloaded ndiswrapper from the sourceforge site and extracted it to home directory. I was in the ndiswrapper folder in terminal.

sudo gedit /etc/hotplug/blacklist - cannot find file

sudo ndiswrapper -i NETMA111.INF - cant find ndiswrapper

and so on...

Can someone tell me what I am doing wrong or tell me a solution to installing the usb adapter?
Thanks

---

### Post by Mnew2Linux on 2007-05-30
I am in the same boat, I have the MA111 and was able to get it working with 6.06 but I caused a problem when trying to install beryl and haven't been able to get online since.  I am working on a clean install on 7.04 but I can't do anything with the OS unless I'm online.  I have tried the wiki on the MA111 at **[https://help.ubuntu.com/community/Wi...e/NetgearMA111](https://help.ubuntu.com/community/Wi...e/NetgearMA111)** but unless I'm doing something wrong, I have the similar output the author suggests in the wiki.  

Furthermore, I tried to install the ndiswrapper but to that end, I have no clue what I'm doing.  I've tried the commands tar #### ndiswrapper.1.45.tar.gz (#### denotes some letters I can't remember) and that only results in the dreaded ndiswrapper...file not found...it's on the desktop, how can it not be found?  I have the MA111 drivers and the ndiswrapper right on my ubuntu desktop but I don't really know where to go from there.  I've read the wiki  on the ndiswrapper but that doesn't really explain how to install it...unless I'm not reading into everything.  I'm not online at all on the ubuntu side and so that makes it more frustrating have to switch between hd's.  Any help would be much appreciated...

---

### Post by Dougie187 on 2007-05-30
The package for ndiswrapper is:

ndiswrapper-common
for ndiswrapper-utils it is
ndiswrapper-utils-1.9

You can look any package names up in Synaptic Package Manager under System->Administration

Let me know if you have any more problems.

---

### Post by Mnew2Linux on 2007-05-30
> **Dougie187 said:**
> The package for ndiswrapper is:

ndiswrapper-common
for ndiswrapper-utils it is
ndiswrapper-utils-1.9

You can look any package names up in Synaptic Package Manager under System->Administration

Let me know if you have any more problems.

ok, so in the terminal I enter:
```
ndiswrapper-common
```?

What is that going to get me?  It will unpack the contents of the ndiswrapper that is on the desktop?

---

### Post by Dougie187 on 2007-05-30
Sorry no. To install these packages you use the following commands.
*sudo apt-get install ndiswrapper-common* 
OR
*sudo apt-get install ndiswrapper-utils-1.9*

Since the guide you guys are following calls for the utils package you probably want the latter command.  I have not gone through the guide, but What you would normally do to install packages is use *sudo apt-get install **Packagename*** in a terminal. And the package name is what i was reffering to. The sudo apt-get install ndiswrapper-utils command didnt work because thats not a package that exists in the repositories your computer is using. I was just saying, more for future reference then anything, if you have a package you want, but dont know the name (or get a name that doesnt work) you can look up the basic name of the program in the Synaptic Package Manager, and then either install it using that or do a sudo apt-get install with it.

---

### Post by Mnew2Linux on 2007-05-30
> **Dougie187 said:**
> Sorry no. To install these packages you use the following commands.
*sudo apt-get install ndiswrapper-common* 
OR
*sudo apt-get install ndiswrapper-utils-1.9*

Since the guide you guys are following calls for the utils package you probably want the latter command.  I have not gone through the guide, but What you would normally do to install packages is use *sudo apt-get install **Packagename*** in a terminal. And the package name is what i was reffering to. The sudo apt-get install ndiswrapper-utils command didnt work because thats not a package that exists in the repositories your computer is using. I was just saying, more for future reference then anything, if you have a package you want, but dont know the name (or get a name that doesnt work) you can look up the basic name of the program in the Synaptic Package Manager, and then either install it using that or do a sudo apt-get install with it.

Ok, I just tried both of the suggestions and both times I received 

**Couldn't find file ndiswrapper-common/utils-1.9**

Is there something that I'm doing wrong?  I have a Belkin Wireless G unit that I put in the USB port on my PC and I can get much further...but everytime I sudo gedit etc/network/interfaces new stuff comes up...I'm pretty shot on what to do now...

---

### Post by Dougie187 on 2007-05-30
I dont know. Maybe its in some repo that you dont have. Ill look around for it, but for now here is a guide to installing ndiswrapper.

[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,installation/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,installation/)

---

### Post by Dougie187 on 2007-05-30
Do you have it in your synaptic package manager?

---

### Post by Mnew2Linux on 2007-05-30
> **Dougie187 said:**
> Do you have it in your synaptic package manager?

I thought you had to be online to use it?  

If I have the file on my Windows desktop I can move the file to my Ubuntu desktop cleanly, can I install it through synaptic then or not?  I also have the MA111 drivers as well.

I did a clean install last night, only took 20 minutes, but my /etc/network/interfaces file was all over the place so I just started fresh (because I had plugged in a belkin wireless G adapter that it liked but added text to the file).  So just 10 minutes ago I tried to manually edit the /etc/network/interfaces file and unplugged/replugged in the adapter and still nothing.  It is looking for wlan0 but that's just for a wired lan no?

---

### Post by Dougie187 on 2007-05-30
You do have to be online to do that. But you also have to be online to use sudo apt-get install. They both grab packages from the Synaptic list, just Synaptic is a GUI way of doing it, and sudo apt-get install is the command line way.

---

### Post by Mnew2Linux on 2007-05-30
> **Dougie187 said:**
> Do you have it in your synaptic package manager?

And no, I do not have it in my synaptic package manager...how can I get it there...

---

### Post by Dougie187 on 2007-05-30
Well i think they should be in there, but you can edit your sources.list file.
To do this do the following:
hit alt+f2
type in *gksudo gedit /etc/apt/sources.list*

After you have the file opened you need to make sure the following repositories are in it, I think they should be by default, but you can add them just to make sure. So at the bottom of the file add these two lines

[I] deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted
[/I]

then save the file and close it. And open Synaptic Package Manager. Make sure you have All Selected over on the left and click on a package, then type *ndiswrapper* and see what comes up. You should see two packages called *ndiswrapper-common* and *ndiswrapper-utils-1.9* Then you can go through your guide substituting in *ndiswrapper-utils-1.9* for *ndiswrapper-utils*

---

### Post by Mnew2Linux on 2007-05-30
> **Dougie187 said:**
> You do have to be online to do that. But you also have to be online to use sudo apt-get install. They both grab packages from the Synaptic list, just Synaptic is a GUI way of doing it, and sudo apt-get install is the command line way.

Ok, well I have ndiswrapper and in System > Administration > Windows Wireless Drivers I try to install the .inf file but currently installed drivers have nothing in it.  I'm thinking it's a gui ndiswrapper so I don't have to do anything in terminal to work on the ndiswrapper...I'm so confused seriously, I have no clue what I'm doing...I have the MA111.inf file and it's not installing it...go figure!

---

### Post by Dougie187 on 2007-05-30
Go here and download this driver for the MA111, this is the driver that is **known** to work with ndiswrapper.

[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_m-n/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_m-n/)

let me know if you get anywhere with that one. Ive never actually used ndiswrapper but it says that it supports your network card.

---

### Post by Mnew2Linux on 2007-05-30
> **Dougie187 said:**
> Go here and download this driver for the MA111, this is the driver that is **known** to work with ndiswrapper.

[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_m-n/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_m-n/)

let me know if you get anywhere with that one. Ive never actually used ndiswrapper but it says that it supports your network card.

Hey thanks, I actually got it working  (not with NDISwrapper) but I don't have WEP, are there any hints as to  how to encrypt my wireless again?

---

### Post by Dougie187 on 2007-05-30
Glad you got it working. I have no idea on the encryption. My computer just has it working. But i have an onboard wireless card on it.

---

### Post by Mnew2Linux on 2007-05-30
> **Dougie187 said:**
> Glad you got it working. I have no idea on the encryption. My computer just has it working. But i have an onboard wireless card on it.

Yes, I was able to get the encryption working actually...I went into my router and configured the key to open key with a 64 bit encryption and created a pass phrase and then generated the wep key.  I then went into the /etc/network/interfaces and configured it to look like 

```
auto lo
iface lo inet loopback

iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

iface wlan0 inet dhcp
wireless_mode managed
wireless-essid Wireless
wireless-enc on
wlan-ng-key0 zz:zz:zz:zz:zz
wlan-ng-authtype opensystem
wireless-key zzzzzzzzzz

auto wlan0
```

And it currently works.  The z's are my WEP key but I took the liberty to take it out.  Furthermore, I'm not sure if I'll need the wlan-ng-key0 zz:zz:zz:zz:zz in there but I'm leaving it for good measure!

---

### Post by Dougie187 on 2007-05-30
Cool. Well thats awesome that its working now.

---

