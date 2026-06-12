---
title: "first Ubuntu install -- HP laptop -- wireless does not work"
date: 2008-04-09
forum: Absolute Beginner Talk
---

### Post by Hal Story on 2008-04-09
My HP laptop with Intel processor and Broadcomm wireless works with XP but not Ubuntu (Gutsy).  What can I doto fix it?

---

### Post by deadgobby on 2008-04-09
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)
Gobby

---

### Post by aiphergott on 2008-04-09
I have an HP laptop also. I had to plug in an ethernet cable then click system - administration - Restricted Drivers Manager when it opens up click enable on the firmware for broadcom 43xx chipset family then it was download and install a driver and firmware then your wireless should work.

---

### Post by Hal Story on 2008-05-02
> **deadgobby said:**
> [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)
Gobby
I tried the listed file. I clicked on activate, but it did not activate.  It appears that I do not have the required library in my machine.  I can get on the internet with a cable to my wireless router, but I want to get on by wireless if I can.  Do you have another suggestion?

---

### Post by analoog on 2008-05-03
please list the exact missing library.

and make sure which network card you have, so you can install the right driver.Do you have a broadcom 43xx ?
(type lspci -n in the terminal)

---

### Post by Hal Story on 2008-05-03
> **analoog said:**
> please list the exact missing library.

and make sure which network card you have, so you can install the right driver.Do you have a broadcom 43xx ?
(type lspci -n in the terminal)

I tried to follow some instruction in other threads. My computer now has the name of my local gateway in the wireless box. It mysteriously appeared after I followed some instructions I didn't understand. I manually retyped the WEP key just to be sure it was correct.  The info says it is active -- I have a green check mark by my wireless connection. My wireless chipset is Broadcom 4306.  Something is still not working. I can access the net by wiring directly to my hub, but when I try to get through on the wireless connection, nothing happens. I don't know where to look next.

---

### Post by sam_delta on 2008-05-03
have you tried to activate hardware drivers through system>administration>hardware drivers?, if wireless drivers do not appear on the list try reinstalling b43 drivers

to reinstall b43 drivers

to remove, update repos and install again:
```
sudo aptitude purge b43-fwcutter
sudo aptitude update
sudo aptitude install b43-fwcutter
```

then restart pc, and check if wireless now works, if dont, try to see if they now appear under system>administration>hardware drivers

note: when installing, if you get promptd about fetching  firmware, make sure you answer with a "Y" for yes 

tell us how it goes
sam

---

### Post by Hal Story on 2008-05-03
> **sam_delta said:**
> have you tried to activate hardware drivers through system>administration>hardware drivers?, if wireless drivers do not appear on the list try reinstalling b43 drivers

to reinstall b43 drivers

to remove, update repos and install again:
```
sudo aptitude purge b43-fwcutter
sudo aptitude update
sudo aptitude install b43-fwcutter
```

then restart pc, and check if wireless now works, if dont, try to see if they now appear under system>administration>hardware drivers

note: when installing, if you get promptd about fetching  firmware, make sure you answer with a "Y" for yes 

tell us how it goes
sam

Hi, Sam.  I did system>administration. but did not find "hardware"... does it have as longer name ?

---

### Post by sam_delta on 2008-05-03
> **Hal Story said:**
> Hi, Sam.  I did system>administration. but did not find "hardware"... does it have as longer name ?

yes, the menu name is "hardware drivers" if your using ubuntu 8.04 (hardy)
system>preferences>hardware drivers


EDIT, o nvm i now see ur using gutsy, its called something like "Restricted drivers", 

i havnt tried using b43-fwcutter on gutsy, give it a try and see if it works

sam

---

### Post by Hal Story on 2008-05-03
> **sam_delta said:**
> yes, the menu name is "hardware drivers" if your using ubuntu 8.04 (hardy)
system>preferences>hardware drivers


EDIT, o nvm i now see ur using gutsy, its called something like "Restricted drivers", 

i havnt tried using b43-fwcutter on gutsy, give it a try and see if it works

sam

Thanks, Sam.

I went into "Restricted Drivers Manager" and it lists "firmware for Broadcom 43xx chipset family". There is a black check mark in box under the Enabled column and a green check mark by the words "in use" under the Status column. I think that means that it is installed and turned on.

I am wondering if there is some sort of link I need to close.  I wonder just how much the program snitches out of my XP partition.

Hal

---

### Post by sam_delta on 2008-05-03
stange thing it shows as "in use" and it dosnt work

can you post the output of 
```
iwconfig
```

and what does this returns?
```
sudo iwlist scan
```

have you considered moving to ubuntu 8.04 (hardy)?

if you still want to stay on gutsy, you might want to try the following :

first
try disabling and re-enabling the driver under "restricted drivers manager"

if no luck
try to install b43-fwcutter drivers explained on  post #7, note that you might not need to remove since you probably do not have b43-fwcutter installed (works on hardy, and youll have to disable current "firmware for Broadcom 43xx chipset family" ) 

if none of the 2 options of above works
you might want to search for a Ndiswrapper guide and use windows drivers under Ndiswrapper. (there are alot of ndiswrapper guides out there, just make sure they are for gutsy)
if you cant find an easy to follow guide, tell me ill try to find one/make my own guide

whatever you decide, ill b around to help

sam

---

### Post by Hal Story on 2008-05-04
> **sam_delta said:**
> stange thing it shows as "in use" and it dosnt work
have you considered moving to ubuntu 8.04 (hardy)?

if you still want to stay on gutsy, you might want to try the following :

first
try disabling and re-enabling the driver under "restricted drivers manager"

if no luck
try to install b43-fwcutter drivers explained on  post #7, note that you might not need to remove since you probably do not have b43-fwcutter installed (works on hardy, and youll have to disable current "firmware for Broadcom 43xx chipset family" ) 

if none of the 2 options of above works
you might want to search for a Ndiswrapper guide and use windows drivers under Ndiswrapper. (there are alot of ndiswrapper guides out there, just make sure they are for gutsy)
if you cant find an easy to follow guide, tell me ill try to find one/make my own guide

whatever you decide, ill b around to help

sam

Dear Sam,
  I thought about changing from Gutsy to Hardy, but I had so much grief just getting Gutsy started that I am afraid. gutsy refused to run on two computers. Then I got this used HP laptop and most of Gutsy works. I haven't the foggiest notion of how to replace one version with another.

Do I need to make another image file like I did for Gutsy?  Then what?

Hal

---

### Post by tashmooclam on 2008-05-04
Switch to an Intel wireless card. Sorry if this is not popular with the folks. I switched and it works "out of the box", the cost was $25 on ebay. I messed around for a lifetime with a Broadcom wireless in a Dell laptop. I consider the $25 a "linux tax", but it was worth it. All that "wrapper" stuff didn't work.

---

### Post by sam_delta on 2008-05-04
if you want, you can stay with gutsy
there are still solutions to this problem, like ndiswrapper, or installing b43-fwcutter under gutsy

a good thing to do its to try hardy, you can download hardy iso image and burn it, then run it as a live cd, and check how it works, see what hrdware works out of the box, if you are convinced , go ahead and replace gutsy

sam

---

### Post by Hal Story on 2008-05-04
eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"2wire770"  Nickname:"Broadcom 4306"
          Mode:Managed  Frequency=2.462 GHz  Access Point: Invalid   
          Bit Rate=1 Mb/s   Tx-Power=15 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by Hal Story on 2008-05-04
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:18:F8:65:CC:5E
                    ESSID:"MOE22"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=81/100  Signal level=-71 dBm  Noise level=-67 dBm
                    Extra: Last beacon: 224ms ago
          Cell 02 - Address: 00:14:95:7F:DC:29
                    ESSID:"2WIRE770"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=98/100  Signal level=-37 dBm  Noise level=-67 dBm
                    Extra: Last beacon: 100ms ago

---

### Post by sam_delta on 2008-05-04
the problem seems to be the invalid access point, try the following
make sure your wireless antenna is turned on
Hit the Fn-F2 keys
Run sudo /etc/init.d/networking restart

Check iwconfig, if access point is still invalid, try 

sudo iwconfig eth1 essid 2WIRE770

sam

---

### Post by Hal Story on 2008-05-04
eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"2wire770"  Nickname:"Broadcom 4306"
          Mode:Managed  Frequency=2.462 GHz  Access Point: Invalid   
          Bit Rate=1 Mb/s   Tx-Power=15 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by Hal Story on 2008-05-04
* Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.eth1.pid with pid 6751
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:90:4b:5d:b9:f3
Sending on   LPF/eth1/00:90:4b:5d:b9:f3
Sending on   Socket/fallback
There is already a pid file /var/run/dhclient.eth1.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:90:4b:5d:b9:f3
Sending on   LPF/eth1/00:90:4b:5d:b9:f3
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
                                                                         [ OK ]
hal@hal-HP:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"2wire770"  Nickname:"Broadcom 4306"
          Mode:Managed  Frequency=2.462 GHz  Access Point: Invalid   
          Bit Rate=1 Mb/s   Tx-Power=15 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

hal@hal-HP:~$ sudo iwconfig eth1 essid 2wire770
hal@hal-HP:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"2wire770"  Nickname:"Broadcom 4306"
          Mode:Managed  Frequency=2.462 GHz  Access Point: Invalid   
          Bit Rate=1 Mb/s   Tx-Power=15 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by sam_delta on 2008-05-04
does your router has any type of encryption (password)? have you tryed another network?

sam

---

### Post by Hal Story on 2008-05-04
Hello Sam,

I tried the encryption key that I use when I set  up wireless with my XP system. I also tried to use the unencrypted node that I can detect.  I can't make that one work with XP or Ubuntu 7.10   .... There is also a server password which I tried without success.  I have begun downloading 8.04 on my other computer.  

Hal

---

### Post by sam_delta on 2008-05-04
alright, ive heard that bcm43xx drivers has problems with encryption, you could go either with ndiswrapper or just move to hardy

 in your possition i would give 8.04 hardy a try
sam

---

### Post by Hal Story on 2008-05-04
I have 8.04 downloading right now.  It has about 50 minutes to go at my present speed.  It is also 2 hours past my usual bed time, so I am going to let my other computer do its thing while I sleep.  Broadcom is now on my "avoid" list. Thanks much for your input.

Hak

---

### Post by sam_delta on 2008-05-04
alright, any problems or question ill be around
from what i heard, intel seems to be the way to go with linux wireless
sam

---

### Post by Hal Story on 2008-05-04
> **sam_delta said:**
> alright, any problems or question ill be around
from what i heard, intel seems to be the way to go with linux wireless
sam

I loaded 8.04 (Hardy) last night. This morning I loaded a restricted driver with fw ? cutter in its name.  When I look at my setup under admimistration the box shows the name of my local wireless node. I presume that it got it off the broadcast signal, but it may have gotten it from the ethernet connection I used to get started.  In any case, when I unplug the ethernet cable, I have no internet connection. Firefox says it cannot find the chosen address.  If I have to go out and buy a USB wireless adapter, will USRobotics work? I'd prefer not to give Intel any more of my money. Are there any checks and settings I should look at before giving up?

Hal

---

### Post by sam_delta on 2008-05-04
did you made a full install,, or running as live cd?
is your internet open , or does it has any type of encryption?, are you using the default network manager, click on the two small monitors in the top right of your screen and select the desired wireless connection?

i would aso try reinsalling fwcutter as for some reason it has worked for some people,

plug your wired connection , opne a terminal and type 
```
sudo aptitude purge b43-fwcutter
sudo aptitude update
sudo aptitude install b43-fwcutter
```

restart pc, try re-enabling hardware drivers or just check if it works.

about the wireless, i havnt experienced with USrobotics, you can search through ubuntu forums, and see if it works. I personally have a usb wireless antenna that just works out of the box without any drivers in ubuntu 8.05, it is a D-Link DWL-122 wireless USB adapter, ,, i bought it some years ago, so i duno if it is still on sale, perhaps you might want to check ebay.

sam

---

### Post by Hal Story on 2008-05-04
I downloaded using the updater. The new version is installed in my Ubuntu partition on my hard drive. I also have a new download image CD of version 8.04. 

In my readings about fw-cutter there was some mention of pointing it at an .inf file.  I never did that as I never saw a prompt for it. I wondered if fw-cutter now hunts down the file on its own.

The two small boxes mention only a wired connection when I click there. 
Sure wish I knew a lot more about linux/ubuntu than I do.

Hal

---

### Post by sam_delta on 2008-05-04
nope, fwcutter does not use .inf file, it is itself a driver

about the .inf file, you probably heard that in a ndiswrapper guide. and i think is your last option. all those command might look a bit scary, but is a safe bet, follow the steps very carefully and it should work. if you get stuck in something, post it here, ill get back to you.

ok, lets try ndiswrapper.
first:

uninstall b43-fwcutter by typing
```
sudo apt-get remove b43-fwcutter
```

NOTE: the following steps are codes to be typed into the terminal (aplications>accesories>terminal)

then we blacklist open source BCM43xx drivers by typing
```
echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
```

then, we install ndiswrapper utillis
```
sudo apt-get install ndiswrapper-utils-1.9
```

At this point, you need to download the WINDOWS drivers (the .inf file) for your wireless card (if you dont have em, you can find those under your manufacturer website, or in broadcom website). If you have trouble finding them, type in the terminal "lspci" and post the output here and ill get the drivers for you.

then, we place the drivers into a folder named "wireless_drivers" in the desktop.
so we have the drivers in Desktop>wireless_drivers><place drivers here>

then, we open again the terminal and we change our working directory to the one we have the drivers in, by typing:
```
cd Desktop/wireless_drivers
```

now, we install the windows drivers, using ndiswrapper by typing the following:
```
sudo ndiswrapper -i <file.inf>
```

where the <file.inf> is the name of your windows driver

we can confirm the successfull installation of the drivers by typing 
```
sudo ndiswrapper -l
```
something like "BCM4306 drivers installed ------- Device Present" should appear

now, its time to run the corresponding modules and set it to work in boot time by typing the following
```
sudo depmod -a
sudo modprobe ndiswrapper
sudo cp /etc/network/interfaces /etc/network/interfaces.orig
echo -e 'auto lo\niface lo inet loopback\n' | sudo tee /etc/network/interfaces
sudo ndiswrapper -m
echo 'ndiswrapper' | sudo tee -a /etc/modules
echo 'ENABLED=0' | sudo tee -a /etc/default/wpasupplicant
```

now, we make a script to disable other wireless modules at boot time
```
sudo gedit /etc/init.d/wirelessfix.sh
```
after this command, a empty text file will open, type the following into the file

#!/bin/bash
modprobe -r b44
modprobe -r b43
modprobe -r b43legacy
modprobe -r ssb
modprobe -r ndiswrapper
modprobe ndiswrapper
modprobe b44

now, save the file, and make it executable by typing into the terminal:
```
cd /etc/init.d/ && sudo chmod 755 wirelessfix.sh
```

finally we add the script into the boot time script list by typing
```
sudo update-rc.d wirelessfix.sh defaults 
```

if everything went right, reboot, and you should have wireless

this guide was originaly posted by alex_kent_18 in 
[http://ubuntuforums.org/showthread.php?t=766560](http://ubuntuforums.org/showthread.php?t=766560)

i just copied the steps and explained every step, made some modifications to make it easier for you

if you get stuck in one step, post here, ill get back to you.

sam

---

### Post by Hal Story on 2008-05-18
hal@hal-HP:~$ sudo apt-get remove b43-fwcutter
[sudo] password for hal: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package b43-fwcutter is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
hal@hal-HP:~$ echo "blacklist bcm43xx' | sudo tee -a/etc/modprobe.d/blacklist
> sudo apt-get install ndiswrapper-utils-1.9
> lspci
> cd Desktop/wireless_drivers
>

I was surprised that the response came back blank.  Maybe that is a clue you can use. I tried to find the .inf file in my XP system but was not successful. Your assistance would be appreciated.  -  Hal

---

### Post by sam_delta on 2008-05-18
as i can see, you didnt had b43-fwcutter installed, so before trying ndiswrapper, 

you could try to sucessfull install b43 as it might be way easier. try the following:

you will need a internet connection for the following 2 things, so plug your computer to a wired connection and try the following

with a internet connection, go into system>administration>hardware drivers , and check if there is any broadcom drivers listed, if they are , try to enable them, if not, try installing b43-fwcutter by typing the following

```
sudo aptitude update
sudo aptitude install b43-fwcutter
```
it will ask if you want to fetch the firmware, make sure you answer with Yes.

then restart your pc and check if it works/or check if ddrivers now appear under system>administration>hardware drivers



if b43-fwcutter does not work, we´ll go back to ndiswrapper
tell us how it goes, sam

---

### Post by Hal Story on 2008-05-18
Half a hooray! My wireless modem exists in the Systems/drivers listing.
The blue indicator light on my keyboard is now illuminated.  I still cannot log in to my local wireless hub. I do not know how to answer all of the questions in the setup panel.  I know the name of my hub and the encryption key.  I'm unsure of which line they belong on, and how to answer the rest of the questions.  Can you help?  Please?

---

### Post by sam_delta on 2008-05-18
yeah, but you should be able to log into your network by clicking on the 2 little monitors located on the top right corner (in the notification area or task bar in the top right pannel) then there under the little menu that pops down, you should be able to see your own network, just right click or click on it and it will ask for the encryption key, enter the key, and you should be good to go

sam

---

### Post by Hal Story on 2008-05-21
Hmmmm.... It does not work like you said.  The drop-down box shows a dot beside "Wired Newtwork"  and below it is a prompt marked "Connect to 802.1x Protected Wired Network".  My wireless network is not listed.  Is there another way in?  Do I need to unplug my wired connection first?

---

### Post by sam_delta on 2008-05-21
humm, how strange, when you right click the monitor on the top, then click on manual configuration, is wireless set to "roaming mode"?, also, your router/hub is not hidden? some routers are hidden and you have to manually type the ESSID which i think its not the case.

also, i would like to see the output of 
```
 iwconfig 
```

sam

---

### Post by sam_delta on 2008-05-21
also, try installing another network manager, go into the terminal and type 
```
sudo apt-get install wifi-radar
```
then open wifi radar and try searching for a network with it

sam

---

### Post by Hal Story on 2008-05-21
hal@hal-HP:~$  iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

eth1      IEEE 802.11g  ESSID:"2wire770"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

When I go to  System  ->  Admin  -> Network I get a panel showing my local network hub's name and there is an entry for WEP encryption key. 
I have carefully checked and re-entered the encryption key.

I will try WiFi Radar as you suggest.  

Thanks for sticking with me, Sam. There has to be a solution to this problem. I sure wish it were easier to find.

---

### Post by Hal Story on 2008-05-21
WiFi Radar shows three networks detected. One of them is mine. I show "Connected to 2WIRE770 (IP address: None)"  I think I need an IP address before things will work.  Is that right?  How do I get one?

---

### Post by sam_delta on 2008-05-21
yeah, you need an ip adress, but your network for some reason wont give you one

does your network have any type of encryption or access restriction?

try to connect to other network and check if it works, if it works, then its gonna be something with your router/computer config

sam

---

### Post by Hal Story on 2008-05-23
I have two unencrypted servers within range. I can connect to both of them according to the WiFi Radar box. I do not get an IP address with either of them. I sure wish I knew more about internet protocols. I don't who is supposed to do what. I have no idea where the ball is getting dropped.

---

### Post by sam_delta on 2008-05-23
ok hal, sry this is taking too long. i think its a driver problem, not actually a router problem, so , lets try to use another driver with the following instructions  , instead of b43-fwcutter.

type the following commands with a internet cable pluged
```
sudo aptitude remove b43-fwcutter
sudo aptitude install bcm43xx-fwcutter
```

answer with yes when it asks if you want to fetch the firmware

then, we need to check if bcm43xx is blacklisted, and if it is, remove it.
go into a terminal and type
```
sudo gedit /etc/modprobe.d/blacklist
```

search for a line that reads "blacklist bcm43xx" and type "#" before it so it should look like this

```
# blacklist bcm43xx
```

save the file, restart and check if it works

if this dosnt work, well go straight to ndiswrapper. but trust me, its worth trying to get a native linux driver to work instead of a windows driver through ndiswrapper
sam

---

### Post by maclenin on 2008-05-23
I would take a peek at this [_post_]("http://ubuntuforums.org/showpost.php?p=4644002&postcount=373"),  to note the Hardy mods, and then have a go at the install [_guide_]("http://ubuntuforums.org/showthread.php?t=340689") - on the first page of the thread. I've used the guide for my bcm4306 (Edgy on a Dell) as well as bcm4310/11 (Feisty on a HP6910p) wireless configurations. Though the guide was originally written for Edgy - it's continued to work for folks through Hardy. Good luck!

---

### Post by Hal Story on 2008-05-30
I figured that my system was all confused by the mant attempts to get wireless working.  I chose to re-install 8.04 from the "live" CD and sart over.  I was successful ingetting it to work.  No idea exactly what I just did.  Re-reading the help posts as I went, I kept on trying.  Thanks for your help. b43-fwcutter was the driver which worked.

---

### Post by Hal Story on 2008-05-30
THANKS! I made so many tries and changes that I suspected my computer was thoroughly  confused.  I used the "live" CD to reload 8.04 and started over. I referred to you notes from when I first saw the blue indicator on my console.  I am totally unclear on exactly what I did, but it now is working using b43-fwcutter.  I went looking for a box to click for official registration of a THANKS, but could not find it.


> **sam_delta said:**
> ok hal, sry this is taking too long. i think its a driver problem, not actually a router problem, so , lets try to use another driver with the following instructions  , instead of b43-fwcutter.

type the following commands with a internet cable pluged
```
sudo aptitude remove b43-fwcutter
sudo aptitude install bcm43xx-fwcutter
```

answer with yes when it asks if you want to fetch the firmware

then, we need to check if bcm43xx is blacklisted, and if it is, remove it.
go into a terminal and type
```
sudo gedit /etc/modprobe.d/blacklist
```

search for a line that reads "blacklist bcm43xx" and type "#" before it so it should look like this

```
# blacklist bcm43xx
```

save the file, restart and check if it works

if this dosnt work, well go straight to ndiswrapper. but trust me, its worth trying to get a native linux driver to work instead of a windows driver through ndiswrapper
sam

---

### Post by inportb on 2008-05-30
It's on the lower-right corner of each post ;p

---

### Post by sam_delta on 2008-05-30
no problem hal, after few days finally its working :):) 
im glad its working and i was able to help
now... enjoy ubuntu :)
sam

---

### Post by Hal Story on 2008-05-31
I just remembered one CRITICAL difference in my last attempt: I had a live ethernet connection to the internet plugged in before I booted the LIVE CD. The system seemed to know what had to be done and did nearly everything except enter my password during setup.  After all the battle to get going (since January) I managed to blunder my way through the setup fairly easily.

  I also had to find out the hard way that for a re-installation the correct "mount point" was "/".

  It may be of assistance to other troubled newbies to suggest a reload as an avenue of approach. As a newbie, I have little or no valuable information to lose!

  The note about having a live ethernet link during installation escaped my notice. Perhaps it needs to be featured more prominently. Can I be the only one who is that dense? Maybe a "read me" popup at the start of installation would have helped. I could have used a list "Do This Before Proceeding" added to the setup queue.

  Thanks again to all for hanging with me as I get going !

---

### Post by sam_delta on 2008-05-31
no problem hal, thanks for writing your experiences as they are helpful for future peopple installing or in similar situations
enjoy ubuntu :)
sam

---

