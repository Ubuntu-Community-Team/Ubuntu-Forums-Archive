---
title: "Dell Inspiron 600m"
date: 2008-01-17
forum: Absolute Beginner Talk
---

### Post by mdock2003 on 2008-01-17
I have just installed Ubuntu 6.06.1 on my Dell Inspiron 600m. Every thing seems to work fairly well except it will not play DVDs and my wireless will not work. I also have XP pro installed and everything works fine when I boot to XP. 
I am fairly knowledgeable when it comes to hardware, though no expert, this is also my first experience with Linux and  I know jack about programming so be patient with me.   
My wireless card is Pro/Wireless LAN 2100 3B Mini PCI Adapter that came with my laptop. I can see it in the device manager, the network settings and it comes up as Ethernet Interface (eth1) in the Network tools,but it won't connect to my wireless router. If I plug it directly into the router I can access the internet, but not wirelessly. On  the desktop/Connection properties it only list "eth0" (the hardline) and "lo" as my connections, but does not list the wireless. I downloaded wifi assistant and it sees my network, but still won't connect. 
Since it obviously sees the wireless why will it not connect? Any advice would be appreciated.
Also do I need to download some kind of codex to play my dvds?

---

### Post by Rocket2DMn on 2008-01-17
I use a del 600m with a 2200 wireless card.  I would suggest installing 7.10 "Gutsy Gibbon".  I started with Feisty (7.04) and i've never had problems getting my wireless to work.  In any case, 7.10 runs great so there is no reason to use 6.06.
In order to watch DVDs and listen to mp3s and other proprietary formats, you will have to install some stuff - start here - [https://help.ubuntu.com/community/RestrictedFormats#head-6c1adf157cf1aaf47a391922036b3ecc98f01796](https://help.ubuntu.com/community/RestrictedFormats#head-6c1adf157cf1aaf47a391922036b3ecc98f01796)
Also note the bottom of that page for more details and help.
You won't need to know any programming unless you're interested in learning, but there are tutorials for that.

---

### Post by mdock2003 on 2008-01-17
thank you very much. 
I am downloading 7.10 right now. I don't know what you mean by Gutsy Gibbon...

I will check out the link and let you know if it works out.

---

### Post by Paulmd on 2008-01-17
> **mdock2003 said:**
> thank you very much. 
I am downloading 7.10 right now. I don't know what you mean by Gutsy Gibbon...

I will check out the link and let you know if it works out.

The cute animal names are an Ubuntu thing, they are aliases for distributions. They have been in alphabetic order for a while. 

6.06 = Dapper Drake
6.10 = Edgy Eft
7.04 = Feisty Fawn
7.10 = Gutsy Gibbon
8.04 = Hardy Heron (currently an Alpha)

---

### Post by Rocket2DMn on 2008-01-17
6.06 is called Dapper Drake
6.10 is called Edgy Eft
7.04 is called Feisty Fawn
7.10 is called Gutsy Gibbon
the next release (currently in testing) is called Hardy Heron.
You will often refer to the different versions referred to by their numbers or by their name (or more specifically, their first name).

---

### Post by mdock2003 on 2008-01-17
I got 7.10 and installed it and I still can't connect with the wireless.  It is weird because it sees the wireless connection in the network settings, and the network in enabled on the desktop.
I understand that Linux tends to be less user friendly than window,and things like that usually don't bother me, but even I'm getting a little aggravated. :confused:
I know there is a something obvious I am probably missing, but being new to this system I'm not sure what to look for.

---

### Post by Rocket2DMn on 2008-01-17
First, please check that the hardware is powered on with the Fn hotkey on the keyboard, should be something like (Fn+F2).  It won't tell you, but sometimes this is a problem.  You can also check in your BIOS if it's turned on.  If you still can't do anything, do the shortcut again to get back to the original state (hopefully on).

Otherwise can you post the output of the following commands:
```
lshw -class network
dmesg | grep ipw
lsmod | grep ipw
iwconfig
```

I've saw a lot of threads with people having problems with their 2100 cards, but there must be a fix.  If all else fails, we can try using ndiswrapper which runs windows drivers under linux for wireless cards.

Also, are you using the NetworkManager applet?

---

### Post by mdock2003 on 2008-01-17
description: Wireless interface
       product: PRO/Wireless LAN 2100 3B Mini PCI Adapter
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       logical name: eth1
       version: 04
       serial: 00:0c:f1:3d:75:b6
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2100 driverversion=git-1.2.2 firmware=712.0.3:3:00000001 latency=32 maxlatency=34 mingnt=2 module=ipw2100 multicast=yes wireless=unassociated


[   79.760000] ipw2100: Intel(R) PRO/Wireless 2100 Network Driver, git-1.2.2
[   79.760000] ipw2100: Copyright(c) 2003-2006 Intel Corporation
[   79.760000] ipw2100: Detected Intel PRO/Wireless 2100 Network Connection

ipw2100                72240  0 
ieee80211              35656  1 ipw2100

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  Nickname:"ipw2100"
          Mode:Managed  Channel=0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

I hit FN F2 and several times and still nothing.

---

### Post by mdock2003 on 2008-01-17
I just went into the bios, turned wireless off, restarted and turned it back on and restarted again.

---

### Post by mdock2003 on 2008-01-17
I don't know if it matters but I have a Buffalo WHR-G125 router.With all my other machines I hit the AOSS button and connected in a matter of minutes.
I have no idea what my Wep key is and I have never needed a password to connect the other machines.

---

### Post by Rocket2DMn on 2008-01-17
It looks like everything is detected well.  Can you see other wireless networks when you scan for them using the applet?  Can you see your wireless router?
Otherwise check from terminal with
```
sudo iwlist eth1 scan
```
If you are using WEP security, you will have to find out what the key is.  You can check this in your router's wireless settings page.

---

### Post by mdock2003 on 2008-01-17
Now I am really confused. 
I played around with a few things and the connection icon on the desktop says 
Wireless Network Connection to (here is shows my connection name) 100%. 
the crazy part is I still can't get on the internet.
It required me to put in a password, which I have never had to do before so I just entered the SSID and it connected, but like I said no internet. I don't want to enter a password each time.

---

### Post by Rocket2DMn on 2008-01-17
Can you post some screenshots or other information?  It's very difficult to help without details.
Like I said though, if there is a WEP key, you need to know what it is.  Ubuntu might ask you for your password sometimes because dealing with the networking is an adminstrative task.
While you have this connection can you post the output of these commands, it will tell us if your DNS is working
```
ping google.com
ping 64.233.187.99
```
Hit Ctrl+C after a few seconds otherwise it will keep running.

---

### Post by mdock2003 on 2008-01-17
I keep getting the Wireless Network Key Required box. I enter the SSID as the passphraseand it shows I'm connected and signal strength is 100%. Internet doesn't come up and after a few minutes I get the box again asking for the passphrase.

---

### Post by mdock2003 on 2008-01-17
ping google.com
unknown host google.com

ping 64.233.187.99
network is unreachable

---

### Post by mdock2003 on 2008-01-17
did this work?

---

### Post by Rocket2DMn on 2008-01-17
Clearly it's not connecting you.  you HAVE to find out what the WEP key is or you can never connect.  Wire yourself back in with ethernet and get to your router's configuration - you will have to refer to your router's manual on how to do this.  It will require you to open a web browser and navigate to the router's IP and look at the wireless settings where you can see the WEP key.  IP will probably be 192.168.11.1 with username "root" and no password (this is just what I read online for your router).  See here - [http://www.buffalotech.com/support/downloads/wireless-g-high-speed-router/](http://www.buffalotech.com/support/downloads/wireless-g-high-speed-router/)

---

### Post by mdock2003 on 2008-01-17
sudo came back 
ethl interface doesn't support scanning.

---

### Post by mdock2003 on 2008-01-18
Before I came here for help I tried to get the WEP key off of my router, but I can't find it. I've checked every page.
On the router's wireless config security page it has 
Wireless authentication: open
Wireless encryption: open

I can enable WEP on this page and it will give me the option to enter up to 4 WEP keys if I want.

---

### Post by mdock2003 on 2008-01-18
another thing I just noticed is the only way I can get the wireless connection to come up is if I go into Network settings and set my wireless connection to "Enable Roaming Mode".Then the desktop manager will give me the option to enable wireless networking. 
When I open that I can see the router, but can't connect.

I'm going back through every page on the router to make sure I didn't miss anything.

---

### Post by Rocket2DMn on 2008-01-18
that scan was for eth1 (that's a ONE not an L).
Keep checking around your router, refer to the manual, and setup your own WEP key if you need to (maybe just use your phone number with area code since that's 10 hexadecimal characters).
You also need to know if you're using 64 bit encryption or 128 bit encryption.  You're PROBABLY using WEP 64 / 128bit hex.

---

### Post by mdock2003 on 2008-01-18
After I enabled the roaming on the wireless the scan did work.

eth1      Scan completed :
 
Cell 01 - Address: 00:16:01:9A:93:1F
                 
ESSID:"50BFE1EE6F27110A6716B2C01A3A5
Protocol:IEEE 802.11bg

Mode:Master
                    
Channel:1
                    
Frequency:2.412 GHz (Channel 1)
Encryption key:on
                    
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s

11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
48 Mb/s; 54 Mb/s
 
Quality:96  Signal level:0  Noise level:0
Extra: Last beacon: 112ms ago

If I enable the WEP on my router and put in keys will it screw up the other 4 machines hooked into the network? Like I said before with the other wireless machines I just installed the buffalo connection mgr and hit AOSS to connect them. The wired machines were also pretty straight forward. This one running linux is the only one giving me headaches and the only one to ask for WEP or passphrases to connect. it is a WEP 64/128 hex but when I look up the info for this particular machine it shows WEP64/WEP128/WPA-PSK-TKIP (this is apparently the connection under XP, it still connects fine in windows)

I would really like to get this up and running, so if you need any other info just let me know. I will check back here first thing in the morning.

thanks again for you help and patience.

---

### Post by Rocket2DMn on 2008-01-18
Ah, I made the bad assumption that you had already enabled roaming.  If you do enable WEP, you will have to setup the other computers with the key, but you should only have to do it once.  It is a great feature because it keeps other people from stealing your bandwidth if they connect to your router.  If you look on your router's status page (or something similar) you can see the DHCP client table, which is basically a list of everybody connected to your router - you can see if your neighbors are stealing your internet.
Using something like your phone number is nice because it's easy to remember and give to other people if they bring laptops over (or iphones or something).  I suggest setting up WEP, but it's really your call.

---

### Post by mdock2003 on 2008-01-18
I did find a page that listed the Encryption Keys according to Encryption type, but when I put the keys in the Passphrase Required by Wireless Network box it doesn't work. I've tried all four Encryption Keys.

---

### Post by Rocket2DMn on 2008-01-18
Sometimes when you generate a WEP key, it asks for a passphrase which is just anything you want, which is then converted to a WEP key which is generally 10 hex characters.  In Ubuntu you will put in the WEP key, not the passphrase.  Which encryption type are you using?  I would suggest 64 bit 10 hex digits with no authentication (open).

---

### Post by mdock2003 on 2008-01-18
I set the wireless on the router to wep 64 hex, entered my key. 
in the wireless network key required box on the laptop I changed the wireless security to wep 64/128 entered the key and it still didn't work. After a few minutes the box came back up the security setting was on web 128 passphrase. I changed the setting and tried it several times and it did the same thing.

---

### Post by Rocket2DMn on 2008-01-18
You'll have to post screenshots of your router's settings page and yourself trying to connect to the network.

---

### Post by mdock2003 on 2008-01-18
I will continue this in the morning and post both screen shots. Got to get up in a few hours.

Thanks again.

---

### Post by Rocket2DMn on 2008-01-18
I will be leaving town tomorrow morning, I will check back before I leave but won't have access all weekend.  If after that you still have problems, I suggest starting a new thread in the Networking and Wireless forum to get help setting up WEP - [http://ubuntuforums.org/forumdisplay.php?f=136](http://ubuntuforums.org/forumdisplay.php?f=136)
Good luck.

---

### Post by mdock2003 on 2008-01-18
If you get this before you leave, Thanks a bunch for the help.

---

### Post by mdock2003 on 2008-01-18
Problem solved. I reset the router and all of the wireless in the house to WEP. When I did that I was able to connect. It must have been the fact that Ubuntu just doesn't like AOSS. Though I did manage to set up AOSS using some info of the net, it just didn't work. I got aggravated and reset the whole wireless network.
Now I just have to tackle the DVD problem.

so thank you very much for the time and help.

---

