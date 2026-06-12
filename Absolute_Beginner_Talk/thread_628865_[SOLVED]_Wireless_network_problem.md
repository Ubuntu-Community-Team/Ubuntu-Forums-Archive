---
title: "[SOLVED] Wireless network problem"
date: 2007-12-01
forum: Absolute Beginner Talk
---

### Post by itix on 2007-12-01
I just recently got my wireless network up'n running (wohoo, ps3 online market!) with the windows native software **** that came with the wireless router. Of course since it was a windows windows install, I had to fight an entire army of problems to get it working, but I did. Now that I just got back to my beloved Ubuntu partition again, I discovered that the wireless network didn't work. I have had the problems at school before wen trying to connect to the open wireless browser logon protected network there, but I just switched to wired network and sat down at one of the wired ports by the windows.

My wireless unit is a Atheros AR5005G, and my router is a Belkin G (in a one room apartment, something bigger would be unnecessary).

I'd hate to be stuck in Windows because of the wireless network, and I won't switch to wired, mainly because I don't want to buy another router, but also because I'ts easier. Please help.

---

### Post by gigaferz on 2007-12-01
first look up if your device is in the system, open a terminal window and type 
sudo lshw     - this command stands for list hardware

scroll down and look at the network section

if its there , youre almost done, open synaptic package manager and type "ndiswrap" and search for it and install it, then get the drivers ready, and follow this next link

[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,installation/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,installation/)

go to the install windows driver section,  please read carefully ,and at the end 
type dhclient wlan0 (or your interface could be ath0 or even eth1 or something)

it looks scary but is really simple,

---

### Post by kevdog on 2007-12-01
Can you list 

lshw -C network

---

### Post by itix on 2007-12-01
Sorry, kinda forgot some important bits of information. On roaming mode, it finds my network, and it tells me to enter my WPA key. After having that done, it still wont "respond". I mean, it doesn't complain about not having any connection with the DNS, but any internet bound application can't connect. I'll try your package though, but I'll download it from windows and run it through the package manager in Ubuntu. Unplugging the router makes me kinda nervous after the montain of trouble I had to overcome to get it working (plus; I'm a networking retard).

---

### Post by gigaferz on 2007-12-01
no , you dont have to,
 have tried checking the forums for wpa networking, ???

i believe there is a package called wpa supplicant,,,,. try disabling the security for a while and check if you can get access to the internet...

---

### Post by itix on 2007-12-01
As I said: I'm a network retard. How do you diable the security?? :#

---

### Post by itix on 2007-12-01
I can now inform you that I am writing to you from the beloved Ubuntu Partition. Dunno what happened, but when I logged on to the Ubuntu desktop, it worked. Thanx for all your help, and sorry for taking your time when there was no problem (apparantly).

---

### Post by gigaferz on 2007-12-02
dont worry,im not a pro either but, its always better to ask,,,

good thing it worked just like that...

---

### Post by tentel on 2007-12-02
hello. i am having a similar problem, but i have hit a smalll snag.

when i go to synaptics manager and try to inmstall ndiswrapper, i get this error

E: /cdrom//pool/main/n/ndiswrapper/ndiswrapper-
common_1.43-1ubuntu2_all.deb: trying to overwrite ' /sbin/
loadndisdriver', which is also in package ndidwrapper




also, when i plug my computer into a wired connection, it does not work.

i tried all the steps in the help menu, and nothing.

---

### Post by itix on 2007-12-03
E: ??

Are you sure you're even using ubuntu?? ^^ (of course you are, I just got kinda startled).

Ubuntu don't label drives and devices by letters as widows do, but names them appropriatley instead. I'm a Ubuntu n00b too, so start a new thread about it, and ask the professional guys about some fancy terminal code that gives them an output that they can watch and think dirty thoughts about xD

---

### Post by kajillin on 2007-12-06
hope this will help a little

in your windows machine open your browser type "home" into the address bar, this should bring your router up, and from there u can disable the security.

tentel  

your still accessing repositories from the cd rom which u have to disable first. do this by entering add/remove select prefrences and de-select "cd-rom with ubuntu".

---

