---
title: "[SOLVED] Zd1211"
date: 2007-10-08
forum: Absolute Beginner Talk
---

### Post by Will PJ on 2007-10-08
hi everyone, i am totally new to any sort of linux, i chose ubuntu, and one of the first things to install was my wireless network usb card. It is a zydas, ZD1211. A linux driver did come with it but i was recommended not to build it, cos it would be built into the kernel and i would not be able to update the kernel. i was told to get a deb package for it, and i did downloaded it in windows and tranfered it onto my desktop in ubuntu. I double click the deb and a messege came up in the deb opener (which name's escape me) saying

'Dependency is not satisfiable: module-assistant'

how can i just simply get the thing installed and my internet working.
:confused:

I have been usin xp to post this.

---

### Post by julian67 on 2007-10-08
The driver is already in the kernel. If you are running feisty it should be plug and play. If not then plug it in and reboot.

---

### Post by ncappel1 on 2007-10-08
try firing up the synaptic package manager under System > Administration > synaptic package manager, and searching for the dependancy files, install them, then try your deb again, it should work at that point.

---

### Post by julian67 on 2007-10-08
> **ncappel1 said:**
> try firing up the synaptic package manager under System > Administration > synaptic package manager, and searching for the dependancy files, install them, then try your deb again, it should work at that point.

ncappel in feisty driver is already installed. It's part of the kernel. And the guy doesn't have a connection (or believes he doesn't) so synaptic is not an option anyway. 

Will PJ just plug it and try it.

---

### Post by Will PJ on 2007-10-08
ok, i'll just boot up and try, cheers all

---

### Post by Will PJ on 2007-10-08
all my dependencies are up to date, tried unpluging the usb dongle out and in, but still says not connected, and firefox has its problem loading page messenge, so any other ideas? my home network does have a pass key to connect-i do know what it is
[COLOR="Red"]PLEASE[/COLOR]
by the way it can take some time for me to reply because i have to shut down windows and boot up ubuntu.:-k

---

### Post by julian67 on 2007-10-08
can you enter the following commands and post the output?

```
lsmod | grep zd1211
```

and making sure the wireless adapter is plugged in:

```
lsusb
```

---

### Post by Will PJ on 2007-10-09
here are

will@will-desktop:~$ lsmod | grep zd1211
zd1211rw               52868  0 
ieee80211softmac       31232  1 zd1211rw
ieee80211              34760  2 zd1211rw,ieee80211softmac
usbcore               134280  7 zd1211rw,usblp,usb_storage,libusual,ehci_hcd,ohci_hcd
will@will-desktop:~$ lsusb
Bus 003 Device 005: ID 0ace:1215 ZyDAS 
Bus 003 Device 004: ID 050d:0234 Belkin Components F5U234 USB 2.0 4-Port Hub
Bus 003 Device 002: ID 0204:6025  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 03f0:1104 Hewlett-Packard DeskJet 959c
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
will@will-desktop:~$ 

any help, just shows its plugged in

---

### Post by julian67 on 2007-10-09
> **Will PJ said:**
> here are

will@will-desktop:~$ lsmod | grep zd1211
zd1211rw               52868  0 
ieee80211softmac       31232  1 zd1211rw
ieee80211              34760  2 zd1211rw,ieee80211softmac
usbcore               134280  7 zd1211rw,usblp,usb_storage,libusual,ehci_hcd,ohci_hcd
will@will-desktop:~$ lsusb
Bus 003 Device 005: ID 0ace:1215 ZyDAS 
Bus 003 Device 004: ID 050d:0234 Belkin Components F5U234 USB 2.0 4-Port Hub
Bus 003 Device 002: ID 0204:6025  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 03f0:1104 Hewlett-Packard DeskJet 959c
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
will@will-desktop:~$ 

any help, just shows its plugged in

It also shows the hardware ID  here "Bus 003 Device 005: ID **0ace:1215** ZyDAS" and also confirms that the correct driver and networking subsystem is working. I have exactly the same  output from my working USB wireless adapter. 

> any help, just shows its plugged in

This comment is ambiguous but may be very important.  Do you mean that the device is seen by network-manager/your network config tools or are you referring only to the output you posted? Please be specific.

---

### Post by Will PJ on 2007-10-09
sorry i was just reffering to what the terminal said, it did not come up in the network manager at all.

I was also installing the ati drivers and i typed 'su -' to be super user, like i did with my old ubuntu 6.10, but it doesn't work in 7.04. is there any other way. i did not manage to get the dongle working in 6.10 either, because i did not have it! i had a rubbish dongle that broke before, so anyway  how do i become super user?

thanks for all your help!

---

### Post by julian67 on 2007-10-09
> **Will PJ said:**
> sorry i was just reffering to what the think said, it did not come up in the terminal.

I was also installing the ati drivers and i typed 'su -' to be super user, like i did with my old ubuntu 6.10, but it doesn't work in 7.04. is there any other way. i did not manage to get the dongle working in 6.10 either, because i did not have it! i had a rubbish dongle that broke before, how to becoe super user?

I'm not sure I understand exactly but never mind. I don't know why you would need to su to install ati drivers, perhaps you should open a different thread for that specific problem. afaik the restricted drivers manager will take care of installing ati driver  from repository and reconfiguring xorg without any command line input from you. This worked fine with my nvidia card and previously with an ati card. So my tip is be kind to yourself and let the OS do the work for you ;-) 

I suspect you've got yourself into some difficulties here because you believed you needed to install various drivers via the terminal or by downloading and clicking packages like in Windows. Actually the hardware you have should all be useable without any of that work. Your wireless adapter is recognised by the system and the correct driver is loaded. Perhaps you can run the commands

```
ifconfig
```

and 

```
iwconfig
```

and post the output?

---

### Post by ncappel1 on 2007-10-09
> **julian67 said:**
> ncappel in feisty driver is already installed. It's part of the kernel. And the guy doesn't have a connection (or believes he doesn't) so synaptic is not an option anyway.
good point...	#-o

but this next one I do know, for root access, its sudo, not su.

---

### Post by Will PJ on 2007-10-10
hold on a sec

---

### Post by Will PJ on 2007-10-10
will@will-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:01:2E:10:22:AC  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:5 Base address:0x8000 

eth1      Link encap:Ethernet  HWaddr 00:02:72:62:05:9E  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:78 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:3276 (3.1 KiB)

eth0:avah Link encap:Ethernet  HWaddr 00:01:2E:10:22:AC  
          inet addr:169.254.4.114  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:5 Base address:0x8000 

eth1:avah Link encap:Ethernet  HWaddr 00:02:72:62:05:9E  
          inet addr:169.254.5.55  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:34 errors:0 dropped:0 overruns:0 frame:0
          TX packets:34 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2564 (2.5 KiB)  TX bytes:2564 (2.5 KiB)

will@will-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"zd1211"
          Mode:Managed  Frequency:2.472 GHz  Access Point: Invalid   
          Bit Rate=1 Mb/s   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

will@will-desktop:~$

---

### Post by Will PJ on 2007-10-10
that smiley face is just one of the automatic patterns in the keys, i did not put it there! it is just this     :,-,o,     ignore commas, or somethibg similar , you can guess!

---

### Post by julian67 on 2007-10-10
ok there is eth1, your wireless adapter. but it looks like it doesn't see a wireless access point. I assume your wireless router is on. Perhaps your essid is hidden?

If you're using network-manager applet you can click on the applet>Connect to Other Wireless Network and then add the essid  etc. as prompted.

---

### Post by Will PJ on 2007-10-11
I have found the Network program in administration-Network, but it is asking for a WEP key, when i use a wpa. I am unsure if it is wpa-tkip, which the Wii uses, or WPA PSK AES or PKIP which windows uses. but anyway, do you know how to enter the wpa key rather than a wep?:-k:confused:

---

### Post by Will PJ on 2007-10-11
:confused:

---

### Post by julian67 on 2007-10-11
By default Ubuntu uses network-manager. There is an applet in your system tray. You should try to use this to access your network config in preference to the admin tools.
   
It's important after someone offers you some help that you offer  feedback, such as stating if you followed the advice, if so then what happened, if there was some problem or reason to not follow the advice and so on. Atm I don't really know what you did or how you got where you are now. 

Do you see the network-manager applet in the tray?

Did you try to use it as described previously?

---

### Post by Will PJ on 2007-10-11
julian, i am now connected tempererly by wire so i could post to you without having to go in and out of linux to windows.

Sorry if i have been unclear, and ill try to be alot more helpful, as you are being helpful to me.

I used the program in [COLOR="Red"]*[/COLOR]System>Administration>Network[COLOR="Red"]*[/COLOR].  I do not believe this is applet, but applet is in the task bar, but i cant enter any keys into applet, so i found this [COLOR="Red"]**[/COLOR], which i could only enter a wep key rather than wpa key, which is my routers security type. If anything is unclear, please quote it and i will explain

---

### Post by Will PJ on 2007-10-11
i am installing the 122 updates there are for Ubuntu know!:), this might let me install the deb.

---

### Post by shof2k on 2007-10-11
Have faith friend.  ZD1211 is supported and does work.

Can you give details of the wireless network you are using.

1) Is the ESSID being broadcast.   Find out by typing
```
iwlist eth1 scanning
``` and posting the output.

2) What sort of encryption, if any, you are using?  It may be worth using no encryption to confirm you can connect to your network, then to add on encryption later.

---

### Post by Will PJ on 2007-10-11
it may not matter shof2k, becuase it is know letting me install the package, should i try to do what you say first, and if all fails install package, please answer asap:)

---

### Post by Will PJ on 2007-10-11
will@will-desktop:~$ iwlist eth1 scanning
eth1      No scan results
will@will-desktop:~$

---

### Post by Will PJ on 2007-10-11
i am using ( in windows ) wpa2 psk aes or tkip, and for my nitendo wii i am using wep tkip, which i dont know, i did not set the wii up

---

### Post by shof2k on 2007-10-11
No harm in running those commands before installing.

---

### Post by shof2k on 2007-10-11
Looks like you need the packages.  Not sure why though, since Feisty supports ZD1211 out of the box.

---

### Post by Will PJ on 2007-10-11
the package does not seem to work,  i re-opened the deb, but it said it was installed, but i cant find the program itself on my computer. have i done it wrong?:confused:

---

### Post by julian67 on 2007-10-11
> **Will PJ said:**
> julian, i am now connected tempererly by wire so i could post to you without having to go in and out of linux to windows.

Sorry if i have been unclear, and ill try to be alot more helpful, as you are being helpful to me.

I used the program in [COLOR="Red"]*[/COLOR]System>Administration>Network[COLOR="Red"]*[/COLOR].  I do not believe this is applet, but applet is in the task bar, but i cant enter any keys into applet, so i found this [COLOR="Red"]**[/COLOR], which i could only enter a wep key rather than wpa key, which is my routers security type. If anything is unclear, please quote it and i will explain

ok, thanks for the feedback. When you click on the applet does it display your network's name?

If yes then what happens when you click on the named network to connect?

---

### Post by Will PJ on 2007-10-19
hi i have upgraded to gutsy and i can get wpa working along with the dongle!

Thanks a lot for all your help - problem solved!!!
(i will make a new post if anything goes wrong!)KS:KS:):):):popcorn::popcorn::guitar: :guitar:

---

