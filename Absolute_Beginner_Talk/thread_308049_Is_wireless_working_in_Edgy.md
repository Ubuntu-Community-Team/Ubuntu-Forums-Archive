---
title: "Is wireless working in Edgy?"
date: 2006-11-27
forum: Absolute Beginner Talk
---

### Post by kilou on 2006-11-27
Hi,

I read on several threads that wireless in Edgy was not working "as well as" in Drapper. I'm trying to setup a wireless connection with the Edgy LiveCD but it doesn't seem to work. Ethernet works but is slow (probably because it's the LiveCD...). 

I checked System / Administration / Networking and I enabled the wireless connection. In properties I manually wrote the ESSID of my network and entered the WEP key under network password. Is this right?? I had to manually wrote the ESSID of my network because it did not appear in the drop down menu (it seems this is a problem with Edgy but it should only concern the detection of network name and not cause trouble to connect).

My WiFi card is Intel 2200BG.

Any help? (or should I switch to Drapper???)

---

### Post by duality on 2006-11-27
Im not sure, but i think that the Intel drivers are proprietary and they are not included in the LiveCD because of that. But i am not sure of this, will have to do a search for the Intel drivers.

---

### Post by unarmedninja on 2006-11-27
to answer your question, wireless does work in edgy. your card might work with ndiswrapper, its on the list. im not sure how it would work on a live cd though ... 
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Main_Page](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Main_Page)

i use ndiswrapper for my dlink usb g122 and it works perfectly fine. good luck.

---

### Post by NoNo_231 on 2006-11-27
Check this [http://ubuntuforums.org/showthread.php?t=275805&highlight=intel+2200](http://ubuntuforums.org/showthread.php?t=275805&highlight=intel+2200)

Maybe it could help. I have the same card as yours and I experienced same problems (I think before edgy though). Never got in the mess to try it due to cable dsl connection. However there is a private network in the neighbourhood and now I tried the **wifi-radar** and found it but cannot say any more because I don't have access. Also tried **wlassistant** which seems easy to use and detected the network.

Seems that this is not a driver issue but the problem is something with some apps.

---

### Post by Tomosaur on 2006-11-27
I just managed to get my wireless network working, after I lost the ethernet connection (more accurately, the guy who I stole the massive cable off took it back home :( ). It seems the devs decided to be awkward and change how firmware loading works. I ended up dumping firmware all over the place trying to get it working, now begins the cleanup :)

And no, I didn't need wpasupplicant or ndiswrapper.

---

### Post by kilou on 2006-11-27
Thanks for your replies! I managed to get the wireless working (connected) but I still cannot display any page in Firefox :( 

What I did is install the Gnome network manager. This brought a computer icon next to the date and I could enable wireless. It detected my wifi network, I entered the WEP key and then it gets connected. I used the guide here then to troubleshoot the connection: [https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#head-1b12c0a8c765a0d0d623e3ee60daf197a5bf2b59-2](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#head-1b12c0a8c765a0d0d623e3ee60daf197a5bf2b59-2)

Basically I can ping an external site when entering its IP address but not when entering its name! Formally it means that 

ping -c 4 216.239.57.99 works
but
ping -c 4 [www.google.com](www.google.com) doesn't work (unknown host)

The guide suggests its a DNS issue. I checked cat /etc/resolv.conf and it displays the correct DNS informations......

Any idea on how to set DNS or solve this issue? (I don't know what all means...)

---

### Post by 56phil on 2006-11-27
You need to check with your Internet service provider (ISP). They will give you the Internet protocol (IP) address of their Domain Name Server (DNS).:) Do you have a router? That's where I put mine DNS IP. Wireless works in edgy.

---

### Post by g33knik on 2006-11-27
Wireless is working in Edgy. I am an uber-noob to linux and I started w/ Ubuntu 5.0 soemthing. As I was trying to get the wifi antennae in my laptop working I found info on google for an app called wpa_supplicant. I run my home wifi network w/ WPA. I then realized I needed the current version of Ubuntu which I just installed last night. But I am still having problems. Networking will detect other wifi networks around me as well as my own. I am just having problems configuring wpa_supplicant. I have no experience writing linux scripts or any scripts for that matter. I want to learn this though but a lot of the info I found thru Google was over my head. If you were to tell some Windows person to goto the Control Panel, they know what you mean, so a lot of the instructions to write script in Ubuntu is like that, written for people who have some good knowledge of Linux, which I don't, for now, have. ](*,) could someone help me and walk me through this or just send me an email with the things I need. I'd really appreciate it. I have an IBM Thinkpad T40,the recent ver of Ubuntu, and an Intel based integrated wireless antennae using WPA-TPK. I need help configuring wpa_supplicant. Tahnk you.:KS :KS :KS :KS :KS :KS

---

