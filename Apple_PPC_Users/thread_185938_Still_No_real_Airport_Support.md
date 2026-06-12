---
title: "Still No real Airport Support"
date: 2006-06-01
forum: Apple PPC Users
---

### Post by areitze on 2006-06-01
Still has no real wifi Aiport Suport for Mac Laptops.   I reinstalled it all under 2 seperate partitions.  One with OSx and the other with the new image of Ubuntu 6.06 

Did all the Updates upgrades, dist upgrade, etc...  but still no support so again back to getting those Fwcutter installed and softmac that made my Aiport Extreme work and be recognized, only hope that soon I can get WEP working...

Well best to all,
ARV.-

---

### Post by slooksterpsv on 2006-06-01
I tried that, couldn't get it to work, even with my Method that worked with Flight 5. Maybe I'll try again later.

---

### Post by slooksterpsv on 2006-06-01
Mine's still sketchy, but it works!!! Here's my SetupInet.sh file and here's how you get things working:
Run this file each time you want internet connectivity:
```

sudo ifconfig eth1 down
sudo modprobe -r bcm43xx
sudo modprobe bcm43xx
sudo ifconfig eth1 up
sudo ifconfig eth1 192.168.0.15
sudo iwconfig eth1 essid ACTIONTEC rate 11M channel 5 key FAFAFAFAFA mode managed ap 00:15:05:03:E5:FB
sudo route add default gw 192.168.0.1
echo "Everything looks ok, if any errors were reported above, it probably did not work."

```
Next I ping the 192.168.0.1, which is my access point. Once I have low times (11.15ms give or take) I can get online, but it'll take a bit. Finally it works.

---

### Post by Biber on 2006-06-02
Is there anything about setting up original Airport with Ubuntu? Open Lan works fine, but as soon as I make it WEP secure, Airport won't connect anymore.

---

### Post by davygravy on 2006-06-02
I was thinking that you might have to prefix the security key with a s or h or some characther that I can't quite remember...

Anyone out there know?

You may be able to find it in this thread about [Exact steps to getting Airport Extreme working in Dapper...]("http://www.ubuntuforums.org/showthread.php?t=142727")

good luck...

EDIT:

OK, it seems to be an s.  See [this page]("http://www.ubuntuforums.org/showthread.php?t=142727&page=4") of the discussion thread listed above.

---

### Post by areitze on 2006-06-02
When I was running Flight 7, I read this post where it was only 2 steps to get my airport extreme card working.  I had somthing to do with the kernel being 2.6.15 and activating somthing from the kernel.  I can't find that post no where, looked in all the fourms of Ubuntu, even the wiki, and nothing.  Wifi worked perfectly at the end, but no WEP.  That was the only problem i had.


Well now with the official Dapper, all up to date, can't even get the Airport Extreme card to work...   I need to get wifi up and running with WEP.  I've tried all the comands posted in every forum...  never have been able to get hold of the AppleAiport2 driver so famously disappeared, plus, softmac now can't even be found.  Every time I try to get Softmac to work, i get this:

-arv@arv-linux:~/source$ sudo make
-Password:
-make -C /lib/modules/2.6.15-23-powerpc/build M=/home/arv/source modules
-make: *** /lib/modules/2.6.15-23-powerpc/build: No such file or directory.  Stop.
-make: *** [modules] Error 2

So well I'm lost, I just have to boot to OS X everytime I need to get online else where than my Desk.  And that is very often...  

this is what I get with iwconfig:

arv@arv-linux:~$ iwconfig
lo        no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"casa"  Nickname:"casa"
          Mode:Managed  Access Point: Invalid   Bit Rate:1 Mb/s
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

sit0      no wireless extensions.


Pls Anyone, HELP!!!
ARV.-

---

### Post by areitze on 2006-06-02
Got it to WORK!!!!  but only on Open wifi, no wep...  still, but this is a good advance.

it's a lot more easy then expected.  The deal is that all the instructions work for foght 5 or 6 or previous, but with 7 and now beta or official, the kernel has the patch included so all we need to do is only install the ieee80211 kernel modules.  

Go to Synaptic and under search paste:  "ieee80211 kernel modules"  with out the quots...  you'll get the ieee80211 for the kernel.  Just isntall, and reboot.

Once rebooted, go to your System, Networking and you'll see that the wireless is active.  Got to properties and select you ssid and leave with no key...

Now under Wifi Radar, you'll see all the wireless networks around, select your's and your set, leave to auto, auto and open, under the prefs of WiFi Radar.

Typing this under my wireless network now... 

All we need is to get wep to work.

Hope this helps...
ARV.-

---

### Post by allon on 2006-06-06
areitze-

I tried the synaptic package manager.  All I found for the kernel modules was the sources which after install made no difference.  Also; what is the "Wifi Radar?"

-Allon

---

### Post by frogtaco on 2006-06-06
I just successfully installed Breezy Badger on my iBook G3, after snagging a used Airport card on eBay. So far it is working great with my network over the Airport Express, using WEP. If I upgrade to Dapper Drake, will I be hosing my connectivity? In other words, should I just leave well enough alone?

Thanks!

---

### Post by ssam on 2006-06-06
Wifi Radar is to make it easier to switch between multiple wireless networks. if you are using gnome rather than kde, you'll probably prefer NetworkManager. see [https://wiki.ubuntu.com/NetworkManager](https://wiki.ubuntu.com/NetworkManager)

---

### Post by eidex on 2006-06-06
there is also KNetworkmanager for KDE...

---

### Post by AlphaMack on 2006-06-06
I have had absolutely no luck in getting NetworkManager to work.

What I have to do is the old method of using Wifi-Radar to create a profile of the base station I want to connect to AND using the Networking control panel to set up a location.  "s:" must prefix the WEP key (and be in the ASCII format).  A reboot is definitely required for the connection to happen (restarting /etc/init.d/networking isn't enough).  YMMV.

---

### Post by Blackhold on 2006-06-10
hello,
I'm using powerbook G4, the one manufacturated in january 2005

I have some problems with the dapper but I wish that I could solve it them eary :-k 

here I go for the airport, I was surprised when wireless icon appeared in network config :D

I tryed to configure but it gives me some problems...

I looked in dmesg and found that:

> bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

I solved this problem reinstalling the bcm43xx microcode:
> 
apt-get install bcm43xx-fwcutter

/usr/share/bcm43xx-fwcutter/install_bcm43xx_firmware.sh


of this moment I could scan for wireless networks :D also I could connect to them, but with one fix... the DHCP give me any ip adress... I looked again in dmesg and returns me that:

> ADDRCONF(NETDEV_UP): eth1: link is not ready

I looked for that error in google for my kind of computer but I found anything...

knows someone what it could be?

thanks you a lot ;)

---

### Post by Digitallysick on 2006-07-06
seems so complicated, why not apt-get install Airport wireless (i wish) any reason we cant make it that easy?

---

### Post by applemacmad on 2006-07-06
I have mine working fine to full usabillity. Here's how I got mine working on a 1.5ghz PB G4. Firstly, I extracted the AppleAirport2 file from a fairly recent install of panther.
Then I put this in terminal

> svn checkout svn://svn.berlios.de/bcm43xx/trunk/fwcutter
cd fwcutter
make
./bcm43xx-fwcutter AppleAirPort2 (then dragged AppleAirport2 into window)
sudo make installfw

I then typed in these commands
> sudo ifconfig eth1 up
sudo iwlist eth1 scan
sudo iwconfig eth1 channel <CHANNEL>
sudo iwconfig eth1 enc <MYKEY>
sudo iwconfig eth1 essid <MYESSID>

I then had wi-fi working, It doesn't start at login, but all I need to do to get it going is open the network prefrences thing, and it starts.

I got all this info from this thread: [http://www.ubuntuforums.org/showthread.php?t=142727&highlight=airport+extreme](http://www.ubuntuforums.org/showthread.php?t=142727&highlight=airport+extreme)

---

### Post by Digitallysick on 2006-07-06
There is where my problem is

"I extracted the AppleAirport2 file from a fairly recent install of panther"

how?? anyway to find this file online to not have to go through this? can we post the file? if someone has it, i will up it to my webspace

---

### Post by robino on 2006-07-07
> **Digitallysick said:**
> There is where my problem is

"I extracted the AppleAirport2 file from a fairly recent install of panther"

how?? anyway to find this file online to not have to go through this? can we post the file? if someone has it, i will up it to my webspace

I got my driver working pretty easy by using the following code:
```
sudo apt-get install bcm43xx-fwcutter
sudo /usr/share/bcm43xx-fwcutter/install_bcm43xx_firmware.sh

```

Please refer to [this post]("http://ubuntuforums.org/showpost.php?p=1158485&postcount=7") for more information and report your progress.

---

### Post by Digitallysick on 2006-07-09
> **areitze said:**
> Got it to WORK!!!!  but only on Open wifi, no wep...  still, but this is a good advance.

it's a lot more easy then expected.  The deal is that all the instructions work for foght 5 or 6 or previous, but with 7 and now beta or official, the kernel has the patch included so all we need to do is only install the ieee80211 kernel modules.  

Go to Synaptic and under search paste:  "ieee80211 kernel modules"  with out the quots...  you'll get the ieee80211 for the kernel.  Just isntall, and reboot.

Once rebooted, go to your System, Networking and you'll see that the wireless is active.  Got to properties and select you ssid and leave with no key...

Now under Wifi Radar, you'll see all the wireless networks around, select your's and your set, leave to auto, auto and open, under the prefs of WiFi Radar.

Typing this under my wireless network now... 

All we need is to get wep to work.

Hope this helps...
ARV.-


I tried this, it seems that wifi radar pics up my wireless network now, when i click connect, it states it cant get an IP address?? any idea why?   ( i havented tried tie FWcutter apple kext thing)

---

### Post by rasec on 2006-07-09
So you got your network card to work without its firmware? What does dmesg show after you "sudo modprobe -r bcm43xx; sudo modprobe bcm43xx". If it says something about a missing firmware, than search for wl_apsta.o, either on this forum or on google, and fw-cut it.

If you do have a firmware installed, then you're probably having problems with wifi-radar. If that the case, I suggest that you ditch wifi-radar and use network manager instead. When I first installed dapper on my powerbook I tried using wifi-radar to connect to my wpa encrypted network, but I never got it to work. Network manager didn't work either initially, but I downloaded the source and I found that libnm-util0 wasn't compiled with the proper flag to support wpa on the powerpc. Once I recompiled it, it worked like a charm. Let me know if you're using wpa and I'll upload the updated libnm-lib0 deb so that you won't need to recompile it.

---

### Post by Digitallysick on 2006-07-10
sweet my airport works! nice! thanks to all!

---

### Post by AlphaMack on 2006-07-11
I recently had success in getting my AirPort to work with Network Manager.  WEP, too.  See [this thread](http://www.ubuntuforums.org/showthread.php?t=211315) for details.

---

