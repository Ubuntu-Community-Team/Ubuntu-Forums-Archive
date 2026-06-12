---
title: "Frustrated!! Newbie needs help!"
date: 2006-12-18
forum: Absolute Beginner Talk
---

### Post by mr_boo1711 on 2006-12-18
:( Hi all!

First off - I feel like the most frustrated guy on the planet! 

I have just installed ubuntu 6.10 Edgy Eft and on the whole the install went without a hitch. Now I am using an ASUS P5B Deluxe M/B with built in Wifi Adaptor, and as much as the adaptor appears in the 'network' section, it just wont connect to my wifi AP (Belkin router).

Here's what I've done/attempted so far.... (Now bare with me - I am a COMPLETE newb to Linux, so apologies)

I tried investigating the wifi adaptor (Identified as 'wlan0') and why it wouldnt connect. I tried running a scan using 'iwlist wlan0 scan' and it detected my Belkin router ok but still wouldnt appear in the drop down within the adaptors network preferences.  Even setting it manually with the SSID it wouldnt work.  Thinking my adaptor itself may not be installed correctly I tried to get some information using another command (I think it was iwconfig?!) and certain articles advise that this should return info on the adaptor, in amongst which should be the driver name - If NOT then it wasnt installed properly.  Well it did return info, but no driver path.

So thinking the driver required updating I read about using NDISwrapper.  After installing the NDISwrapper package that came the OS disk (v1.8), I encountered an error msg when following the setup proceadure.  I used the 'ndiswrapper -i [driver.inf]' command and it reported an error on line 144.  All it did in the end was create a folder labelled with the driver name but no actual files (Which I then deleted manually using the rm -rf command).......  wtf?!? :confused: 

Then I removed it and downloaded the latest ndiswrapper on my other windows pc and moved it acorss via CDR.  I checked that all the kernel/headers were installed and then attempted to install the latest ndiswrapper but couldnt - I tried using the terminal and following guidlines to use 'make distclean', and then 'make install' from the new extracted ndiswrapper directory... and all it gave me was another error msg (which I cant remember, but it had loads of asteriks at the beginning of it!).

The Linux OS looks really good, and other than this I have no issues - but connecting to the internet is a bit of a problem and I'm getting frustrated now.  Apologies for lack of detail on error msgs etc, but my desktop has a hardware issue which isnt allowing it to boot just now (Will be fixed by tomorrow morning though).

Anyone got any ideas?? :( :( 

Cheers in advance,
Steve

---

### Post by bulldog on 2006-12-18
Take a look in this part of the forums,maybe you can find what you're looking for.

[http://ubuntuforums.org/forumdisplay.php?f=136](http://ubuntuforums.org/forumdisplay.php?f=136)

[http://ubuntuforums.org/forumdisplay.php?f=100](http://ubuntuforums.org/forumdisplay.php?f=100)

---

### Post by netdicted on 2006-12-18
I'm not a fan of the original Edgy WLAN manager. At work we have a WPA encrypted access point so I needed to do something with the original connection anyway as it didn't support WPA connections (btw...there isn't any reference in your post to what type of broadcast or authentication is being used to connect). Incidentally, if your computer is listing your wireless connection as wlan0 it sees it and therefore it is unlikely that it is a driver problem. I would strongly suggest switching your network manager to the Gnome network Manager. 

sudo apt-get install network-manager-gnome

Logout/Reboot.

You should have a new icon on your taskbar at the top right which is a much easier interface to help control the wireless connections.

---

### Post by mr_boo1711 on 2006-12-18
My AP isnt WPA encrypted - I left it open just in case while I was configuring linux. :confused: 

I'll try that gnome manager and see what happens...

---

### Post by netdicted on 2006-12-18
Sorry I didn't mean to get stuck on the WPA. Gnome Network Manager supports all of the popular security measures...WPA just happened to be the one that made me go look somewhere else for a better interface.

You will more than likely have to comment out all of your network interfaces in /etc/network/interfaces, except -

auto lo
iface lo inet loopback

hope it helps!

---

### Post by netdicted on 2006-12-18
Here's a link with decent destructions:

[http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html](http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html)

just ignore the wpa stuff or if you want to be able to use it go verbatim.

---

### Post by mr_boo1711 on 2006-12-19
Thanks for the help so far guys.  I took a look at the threads and it's still a little daunting! :confused:

Maybe I'm overcomplicating it too much - so I've decided to start from scratch....

Making the assumption my wifi adaptor is working correctly, I re-tried some of the basics.  My PC is up and running again so here's some more specific info...

The card appears in the network settings and is identified as 'wlan0'.  It also appears in my device manager as a RTL8187 USB WiFi adaptor.  All seems ok.

Running iwlist wlan0 scan in terminal it returns the following.....

wlan0       scan completed:
               cell 01 - Address: 00:11:50:83:A8:65
                           ESSID: "Belkin54g"
                           Protocol: IEEE 802.11bg
                           Mode: Master
                           Channel: 11
                           Encryption Key: Off
                           Bit Rates: 54Mb/s
                           Extra:  Rates  (Mb/s):  1  2  5.5  6  9  11  12  18  22  24  36  48  54
                           Quality: 14  Signal Level: 0  Noise Level: 29
                           Extra: Last Beacon: 17ms ago


Again, all seems ok (to me anyway).  Points to note:  The router mac address is correct all apart from the last digit when compared to the bottom of the router - its 64 instead of 65?! The router is through a standard wall (Brick) and only 13ft away.  The security is disabled and the router is set to DHCP.

iwconfig returns the following...

lo       no wireless extensions

eth0   no wireless extensions

wlan0 802.11b/g   Mode:Managed   Channel: 11
         Access Point:  Not-associated   Bit Rate= 11 Mb/s
         Retry: on     Fragment thr: off
         Link Quality:0   Signal Level:0    Noise Level:0
         Rx invalid nwid:0   Rx invalid crypt:0  Rx Invalid Frag:0
         Tx Excessive retries:0  Invalid Misc:0   Missed beacon:0

sit0    no wireless extension



Hope i'm making sense so far!?

Hmm, what else....  tried configing the IP settings manually but same result.

Any ideas or suggestions?

Steve

(..i'm still smiling.... just.... ;))

---

### Post by netdicted on 2006-12-19
how about an ifconfig to see if you are getting an address? how did the gnome network manager go? there's a kde network manager if you are using that flavour.

---

### Post by mr_boo1711 on 2006-12-19
the gnome network manager just didnt happen?! I couldnt find any reference to it on synaptic, and anything that sounded v.similar was already installed according to the system (little green box thingy).

Running ifconfig wlan0 returns the following....

link encap: Ethernet    HWaddr 00:15:AF:05:7C:4A
UP BROADCAST MULTICAST MTU: 1500  Metric: 1
Rx Packets: 2083  errors: 9  Dropped: 1 Overruns: 0 Frame: 0
Tx Packets:0  errors:0  dropped:0  overruns:0  carrier:0
collisions:0  txqueuelen:1000
Rx Bytes:512453 (500.4KiB)  Tx Bytes:0  (0.0 b)

:confused:

---

### Post by mr_boo1711 on 2006-12-19
Interesting.....  I just plugged in a cat5e ethernet cable in to the router and the PC and it seems the ath0 aint talking to the router either (although the router light is on...  maybe it isnt the actual wifi adaptor...

---

### Post by mr_boo1711 on 2006-12-19
I'm off to watch Arsenal give Liverpool a skelping, but i'll be back in about 1 1/2 hours to wrestle with this thing some more...  i'm not working tomorrow, so it could be a long night...   Any suggestions then i'll be eager to read through them when I get back.

Thanks for your help too Netdicted :)

---

### Post by mr_boo1711 on 2006-12-19
The more i play about with this, the more i feel its not an issue specific to the wifi adaptor... could it be the protocols or something similar maybe?

---

### Post by netdicted on 2006-12-19
you're absolutely correct! its not an adapter issue. I found that edgy with the default network manager doesn't switch between wifi and lan well at all even when the wifi worked. like i said the gnome-network-manager is the way to go. there is a hybrid already running and that's what you can see in the top right corner. you'll probably need to add a repository to get the correct one. i'll see if i can find the instructions i used to install it....

sudo apt-get install network-manager-gnome

what does it say when you try and do it..i'll add my IM details in my profile if you want to get to it real time. when i find the article i'll post it....how did the game go?!

---

### Post by mr_boo1711 on 2006-12-19
I dont see anything in the top-right hand corner though??  I suppose its good news that its not an adaptor issue - I'm hoping that means its a little easier to sort....

Arrgghh!  I just found the network-manager-gnome in synaptic but it cme up with 3 or 4 errors - each one relating to each file it tried to install.  When I ran your command in terminal it just said the following....

E: Could not get lock /var/lib/dpkg/lock - open (11 resource temp unavailable)

E: Unable to lock the amin directory (/var/lib/dpkg/), is another process using it?

:confused: :confused:

[Oh, the damn game was postponed due ot heavy fog... I walked all the way to the pub in the Scottish rain and wind for nowt...   just not my night] :(

---

### Post by netdicted on 2006-12-19
> **mr_boo1711 said:**
> 
E: Could not get lock /var/lib/dpkg/lock - open (11 resource temp unavailable)

E: Unable to lock the amin directory (/var/lib/dpkg/), is another process using it?

You had the synaptic console open when you typed that command. You can't run that command when synaptic is open. it needs an exclusive access (lock) to the dpkg (debin package) directory stuff.

---

### Post by mr_boo1711 on 2006-12-19
Hmmm....  I just re-booted and now when I run the command in the terminal window (Without synaptic open) it says...

Reading package lists.... done
building dependency tree
Reading state information... done
E:  Couldnt find pacakge network-manager-gnome

wtf?!  When I went into synaptics the network-manager-gnome isnt present anymore :confused:  I dont understand - where did it go?!

*sigh*

---

### Post by netdicted on 2006-12-19
you may need to add some repositories - see here

[http://ubuntuguide.org/wiki/Ubuntu:Edgy/Repositories](http://ubuntuguide.org/wiki/Ubuntu:Edgy/Repositories)

that will help get them there then you will need to do an 

***apt-get update***

that will update the software available...then you can do a 

***apt-cache search network-manager-gnome***

that will tell what packages if any are similar or exactly like what you are looking for 'netowrk-manager-gnome' i sent you off an email with my IM details in it.

---

### Post by jbutler12 on 2006-12-19
I eventually gave up using the GUI tools and just used the command line to configure my USB wireless device.

Since you are finding the network with iwlist, but iwconfig is listing your essid as unavialible, you probably (1) havent brought the network up and more importantly, (2) havent told the wireless device which network you want.  LIke i said, installing my Belkin router i found the GUI tools to be pretty worthless.

FIrst, i would disable all encryption on your router just to make it easier.  We can bring it back up later once you have a working connection.  Try:

```
sudo iwconfig wlan0 essid <ESSID>
```

where <ESSID> is the essid listed by iwlist wlan0 scan that you want to connect to, without quotes of course.  IF this executs OK, then type iwconfig again.  YOu should see ESSID: <ESSID> with the one you just added.  If this works, bring up your wireless:

```
sudo ifup wlan0
```

and see if you get a bunch of lines saying DHCP RENEW blah blah blah

if so, we're on the right track.  IF not, post up your results.  Remember to disable encryption on the router or this wont work.

-John

---

### Post by pissedoffdude on 2006-12-19
you might want to try this [http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/44780-getting-wireless-lan-card-work-linux.html]("http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/44780-getting-wireless-lan-card-work-linux.html")

---

### Post by mr_boo1711 on 2006-12-19
jbutler12/Netdicted,

I have just reinstalled linux again to double check I hadnt got a poor installation - no luck - still experiencing the same issues.

I tried reconfiguring everything manually again, but to no avail.  Its definitely not a wifi issue i've got, cause after plugging in the ethernet cable and running std cat5 I found that it behaves EXACTLY the same way more or less.



I feel like a complete novice! ](*,)  :-k 

lol!

Nedicted - I'll give you a shout tomorrow.  jbutler12 - I'll try this in the morning (Or if i'm running late, i'll check when I get back from xmas shopping) and then post my results.  I WILL get this to work!  I will... I will.....  ;)

---

### Post by Spinelli on 2006-12-19
> **jbutler12 said:**
> I eventually gave up using the GUI tools and just used the command line to configure my USB wireless device.

Since you are finding the network with iwlist, but iwconfig is listing your essid as unavialible, you probably (1) havent brought the network up and more importantly, (2) havent told the wireless device which network you want.  LIke i said, installing my Belkin router i found the GUI tools to be pretty worthless.

FIrst, i would disable all encryption on your router just to make it easier.  We can bring it back up later once you have a working connection.  Try:

```
sudo iwconfig wlan0 essid <ESSID>
```

where <ESSID> is the essid listed by iwlist wlan0 scan that you want to connect to, without quotes of course.  IF this executs OK, then type iwconfig again.  YOu should see ESSID: <ESSID> with the one you just added.  If this works, bring up your wireless:

```
sudo ifup wlan0
```

and see if you get a bunch of lines saying DHCP RENEW blah blah blah

if so, we're on the right track.  IF not, post up your results.  Remember to disable encryption on the router or this wont work.

-John

I would highly recommend trying out jbulter12's suggestions. This is exactly what I do when the GUI wireless tools don't work. I would like to add that you may need to use the "--force" option with ifup like this ...
```
sudo ifup --force wlan0
```

I never had a problem with the GUI wireless tools in Dapper, but ever since I upgraded to Edgy the GUI tools almost never work.

---

### Post by mr_boo1711 on 2006-12-20
Ok - here's the latest...

I followed jbutler12's instructions and all appeared to work according to plan. No nasty error msgs....   HOWEVER....  Still no change...! :(

In the network tools section it shows the wlan0 as receiving packets, but not sending ANY?! Not sure on the significance of that though-  does that help us any...?  It also states in there that the protocol being used is IPv4 - is this correct, or am I barking up the wrong tree? 

I tried the force option too, but got an error msg 

SIOCADDRT: File exists

I cant help feeling that i'm missing something obvious...  but i've double checked anything I can think of - but then again, I aint to linux expert so that means nothing! ;)

---

### Post by mr_boo1711 on 2006-12-20
...oh, and when I did the..  sudo ifup wlan0   ...command, it didnt say anything in response.  It just jumped to the next line and reported to no error. :confused:

---

### Post by mr_boo1711 on 2006-12-20
Ok - here's some more info.....  (I hadnt removed my static IP settings from when I was messing about)  When removed, and doing the above again it returns the following results...

There is already a pid file /var/run/dhclient.wlan0.pid with pid 6263
killed old client process, removed PID file

Internet systems consortium DHCP Client v3.0.4
Copyright 2004-2006 Internet systems Consortium
All rights reserved.

listening on LPF/wlan0/00:15:af:05:7c:4a
Sending on LPF/wlan0/00:15:af:05:7c:4a
Sending on socket/fallback
DHCP Discover on wlan0 to 255.255.255.255 port 67 interval 8
DHCP Discover on wlan0 to 255.255.255.255 port 67 interval 11
DHCP Discover on wlan0 to 255.255.255.255 port 67 interval 7
DHCP Discover on wlan0 to 255.255.255.255 port 67 interval 15
DHCP Discover on wlan0 to 255.255.255.255 port 67 interval 18
DHCP Discover on wlan0 to 255.255.255.255 port 67 interval 2
No DHCP offers received
No working leases in persistant database  - sleeping.

That help?

---

### Post by wirelessmonkey on 2006-12-20
try this:


sudo ifconfig wlan0 down
sudo ifconfig wlan0 up
sudo dhclient wlan0 (if this errors, try sudo dhcpcd wlan0)

Your problem is a result of not receiving a dhcp address.   I don't use either of the network managers with my wireless, so all I can give is command line advice.


Best of Luck

---

### Post by jbutler12 on 2006-12-20
interestingly, i had the EXACT same problem.  BUt we are on the right track (which is why i said what i said above about the DHCP).  For some reason, my router refused to give my wireless device an ip address.  Heres what i did:

Can you get a connection to your router through some other computer?
IF so, we are almost there.  Log into your router's firmware through your web browser and add a static IP corresponding to the Mac address of your wireless device (avalible through iwconfig its the numbers and : after "Access Point").  This will bypass DHCP; your router sees that MAC address, it automatically gives it the same ip.

If you dont know what im talking about, let me know and ill post up very detailed directions.  Trust me, you are almost there.  Your linux seems configured fine, now we just have to deal with the router.

---

### Post by jbutler12 on 2006-12-20
Just out of curiosity, is this a D-Link 5x4 router?  I found my solution on the web in a post where someone had the same problems both of us experienced.  I wonder if its a router issue...

Anyway, try that out above and you should be OK.  Post if you dont know how to do that and ill walk you through setting up a static IP and also how to make these changes permanent (So you dont have to configure and bring up the wireless connection each time you boot).

I saw where you wrote you hadnt removed your static ip changs... was this on the linux box or the router?  Also, can you post your /etc/network/interfaces file?  Basicly, the way i think it works best is to have linux think you are using DHCP (since your dhcp looks fine) but have the router just give the same ip every time.  At least, thats how i solved that error message.

-John

---

### Post by mr_boo1711 on 2006-12-21
Thanks jbutler12.

Well with the help of netdicted we've managed to get connectivity using ethernet on my LAN NIC (eth0), but the wlan0 still remains a mystery.  What I CAN say is that I'm certainly not alone with this problem and it seems to revolve around my onboard wifi adaptor (RTL8187).  Seemingly this adaptor just hates ubuntu and everyone i've read online can SEE there ESSID, and are also prompted to enter their security key when they attempt to connect (I tried adding security and my router asked me to confirm the key also.) - but when ever anyone actual submits the key to finally connect to it, it then times out.  It appears all my settings are correct wihtin linux though, and there were one or two people reporting intermitent success (The connection randomly drops seemingly) using an older WIN98/ME driver in conjunction with ndiswrapper - although I havent tried this yet.

The router in question is a Belkin 54g Router (Cant remember part number though - i'm at work just now), and I'm ok with alterning the settings within the firmware - so I'll try this when I get home jbutler12 and then post my results.  Your suggestion certainly makes sense, so fingers crossed!

I'll let you know how I get on later tonight.... :)

---

### Post by jbutler12 on 2006-12-21
Quick Correction on how to get your MAC Address (hopefully you check this before you try out giving yourself a static IP).  at the terminal, type "ifconfig".  Under wlan0, look at where it says HWAddr: on the first line.  That is your card's MAC (i was confusing ifconfig and iwconfig... iwconfig gives your router's ip).

-John

---

### Post by mr_boo1711 on 2006-12-21
No worries John - I've become very familiar with the ifconfig and the iwconfig commands over the past few days... ;)  (I couldnt begin to guess at how many times I've type those commands in!)

I'm stuck at work till later on cause every other person has done a dissappering act and left me to man the phones.... so nice of them!  So i'll try it when I get back in and report back.  

Steve

---

### Post by mr_boo1711 on 2006-12-21
Ok, that didn't work - router still didnt let the wlan connect to it.  It thought about it, then decided no.......  

hmm....  answers on a postcard please...:-k

---

### Post by DrMilo on 2006-12-21
I wouldn't recommend Edgy for a noob. Go with stable instead.

---

### Post by hfdragon on 2006-12-21
Hi !

I installed edgy yesterday on my new computer (asus P5B Deluxe/Wifi + Core2 Duo E6600), and I have the exact same problems as descibed above.

I've read somewhere (I think on asus website's forums) that there is a new realtek driver release.

Did anyone tried it ?

---

### Post by macogw on 2006-12-21
> **DrMilo said:**
> I wouldn't recommend Edgy for a noob. Go with stable instead.

Edgy is the most recent stable release.  It was released in October.  The current unstable version is Feisty Fawn.

---

### Post by jbutler12 on 2006-12-21
Same problem?  Just doesnt get an ip from DHCP and goes to sleep?  Could you take a screenshot of your router's configuration page?

If the card is finding wireless networks in your area, and you are getting to the point where DHCP is asking for an ip, you have correctly configured (1) your card, (2) your network interface, (3) any encryption.  The problem has to be at your router... are you sure you configured it to auto-ip correctly?

hfdragon: there are many problems described above!  do you mean your card requests DHCP and the router doesnt give one and the interface sleeps?  Have you tried the auto-ip solution?

---

### Post by mr_boo1711 on 2006-12-22
I'm pretty sure John that its the Adaptor - I've trawled forums all over the net and the only that is consistent in this problem is that everyone is using the onboard RTL8187 WiFi setup.  The routers vary, as does the security applied (Some arent even using any), so I can only guess that it is the adaptor.

On most linux forums, the end conclusion has been to use another wifi interface until an update comes out that will properly support the RTL8187.  Only problem is I tried that with a F5D7050 Belkin dongle and the minute I plugged it in (Even prior to boot) it froze my OS and I hard to a hard restart...   ](*,)  ](*,)  ](*,) 

It was just never meant to happen for me - I'm destined to have a long grey Cat5 cable running through my house for the foreseable future.... :( 

P.S.  Has anyone got a recommendation for a wifi interface (make/model?) that is proven to work with this os?  I'm thinking the small expense might just outweight the hassle!  ;)

---

### Post by Spinelli on 2006-12-22
I think wireless cards that use the rt2500 chipset are supposed to work very well with GNU/Linux. The driver is licensed under the GNU GPL. I have a wireless card in my laptop that uses the rt2500 chipset and it works great with Ubuntu Dapper and Edgy. Here is a link with more information

[http://www.fsf.org/resources/hw/net/wireless/cards.html]("http://www.fsf.org/resources/hw/net/wireless/cards.html")
 
Gook Luck!

---

### Post by jbutler12 on 2006-12-22
Id recommend the Belkin G USB Wireless adapter.  Its cheap ($30), doesnt require you to open your computer, and has a cool kinda base thing that goes on your desktop.  It doesnt work with linux out of the box but ndiswrapper does.

---

### Post by mr_boo1711 on 2006-12-23
Hmmm, sounds like the one I have sitting here spare John - It keeps freezing my OS when I plug it in.  You think if I do the ndiswrapper stuff first and then plug it in i'll be ok?  I even tried disabling my onboard wifi in BIOS in case that was doing it but it didnt help.

Cheers Spinelli - I'll check out the link and see what its like. :)

---

