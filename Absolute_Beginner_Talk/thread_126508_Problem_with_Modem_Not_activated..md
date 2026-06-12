---
title: "Problem with Modem? Not activated."
date: 2006-02-06
forum: Absolute Beginner Talk
---

### Post by Cerbz on 2006-02-06
Ok, I have recently install Ubuntu, the system itself, as far as I am aware, has installed fine, but for some reason that I cant figure out, it wont connect to the internet.

I'll try and go through all the details, so its easier to help.

My modem is 'Actiontec 54 MPBS Wireless DSL Gateway', I have my internet running from the modem to my PC Via USB, and a CAT5 Crossover Cable, from my PC's Network Card to my XBox. In the Networking box, it says that my Network Card is active, but my modem isnt. I tried to autodetect my modem, but I got a error box pop up saying something about the ppp0 configuration and making sure its correct. 

I thought that if I tried to connect from my modem to my PC Via Ethernet cable, then it might work, but I got the same problem. 

If possible also, could you provide a step by step solution, this is my first experiance with Linux and am still not aquired with the terminologies and controls.
I know this isnt much to go by, but I hope its enough to offer any help that can help me solve this problem.

---

### Post by Hygelac on 2006-02-06
I'm also a noob but since you have no responses yet I'll offer this. As far as I know, this is only valid if your modem is connected with the ethernet cable instead of the USB one. I recently set-up a DSL modem, and I was having no luck until I found out that I had no IP address. So that is one thing to check for. Type 'ifconfig' into the command-line. You'll get something like this (note that 'wlan0' refers to my wireless adaptor, and for you will instead read 'eth0' if your ethernet is running; and if your internet is running you will have ppp0 too): ```
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:17 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1045 (1.0 KiB)  TX bytes:1045 (1.0 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:90:4B:F6:21:06
          inet addr:192.168.0.101  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::290:4bff:fef6:2106/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:18907 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8515 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:9448678 (9.0 MiB)  TX bytes:1349665 (1.2 MiB)
          Memory:b0204000-b0205fff
``` 
Do you see the 'inet addr:192.168.0.101' thing? That is my computer's IP, so if that whole line is missing for you it means you don't have an IP address for your machine, meaning you cannot communicate with the modem. If so, step one is to get an IP. After I resolved that problem with my own system, I ran 'sudo pppoeconf' to set up the connection.

---

### Post by saphil on 2006-02-06
Your modem is a dsl modem and is not the modem the network dialog is thinking about. That modem is a dial-up modem. Does your xbox have an internet signal? I sugest running an ethernet cable to a router and then an ethernet cable from the router to your eth card and another ethernet cable to the xbox. Dump the USB cable altogether. 

USB is absolutely great when it works and completely crazy-making when it doesn't .  :cool:

---

### Post by Cerbz on 2006-02-07
About using the ethernet cabel, I tried it with that, and in the Networking box, I ser it to DCHP and it activated something...but the internet still wouldnt work...could that be again what Hygelac about my Int Addr? I'll be having a look at that soon, but before I do, where do I type in 'ifconfig'? Is it in the FireFox browser? Or the Terminal? or somewhere else? Also, how do I get to the Terminal? And I read somewhere about logging in as 'Root' user tohelp solve some problems. Is this correct? And how do I go about logging into Root user?

Sorry if I sound like a complete pain in the backside, its just I want to try and understand everything about it that I can.

---

### Post by Hygelac on 2006-02-07
You type 'ifconfig' into the Terminal.  I don't use GNOME right now, but I think I remember it being in "Applications."  Maybe not, but on a default Ubuntu install it will be on the menu at the most left on the upper panel, and under the top menu that pops up there ('Terminal').  If you are successfully using DHCP you will have an IP, but if you were having my problem you will have some weird problem with DHCP and need to manually configure your IP to have one.  If you have an IP, and all your other hardware is working, then you can type 'sudo pppoeconf' into the Terminal.  This will run a DOS-like program to configure your DSL connection.  I used all the defaults and only had to tell it the username and password from my ISP to get online.

If you don't have an IP, I think there is an easy way to configure it in GNOME, but I don't know where that is.  I'm sure a GNOME user will know.  The other way is to manually edit a text file in the Terminal by typing 'sudo vim /etc/network/interfaces'.  To edit it with Vim, you have to press the «Insert» key to make changes, and to save and exit Vim hit «Esc», then «Shift-Q», then «wq» (write + quit) and «Enter».  I found-out how to do that here: [http://ubuntuforums.org/showthread.php?t=111956](http://ubuntuforums.org/showthread.php?t=111956).  Much of that thread relates only to Kubuntu, but the stuff about how to edit that text file would be the same.  The GNOME (and KDE) network configuration utility actually runs by editing this file, so it's good to know where it is even if you don't have to resort to manually editing it.  Good luck! :)

---

