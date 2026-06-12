---
title: "Linksys Networking Troubles"
date: 2006-09-02
forum: Absolute Beginner Talk
---

### Post by CoreyE on 2006-09-02
Well ive been debating whether to get linux for months, and i finnaly decided that since im going into a computer oriented field its about time i start learning it. So i chose Unbuntu through alot of recomendations. Well ive ran into my first problem.

Ive been trying for the past 3 hours now to get wirless networking working. Ive googled out the wazoo and gone through many guides. Ive actually started learning terminal from just trying to get this working, but im lost ](*,) 

I have a Linksys Wirless-G Notebook Adapter, Model WPC54G Ver. 2.0

Ive also tried this howto:
[http://www.ubuntuforums.org/showthread.php?t=233565&highlight=wpc54g](http://www.ubuntuforums.org/showthread.php?t=233565&highlight=wpc54g)

But that was to no avail. i dont even know if i did that how to right, as i said this is my first time with linux. I found another one on using ndiswrapper but unless im even stupider than i though, i dont think i can get that without the computer having the internet.

Any help would rock. Ive tried just about all i can on my own, and thought it was time to ask on here :D

Oh and also, when i tried to set the essid in terminal, i got an error, which said:

> Error for wirless request "Set ESSID" (8B1A) :
SET failed on device wlan0 ; Operation not permitted.

---

### Post by TFX360 on 2006-09-02
> **CoreyE said:**
> Well ive been debating whether to get linux for months, and i finnaly decided that since im going into a computer oriented field its about time i start learning it. So i chose Unbuntu through alot of recomendations. Well ive ran into my first problem.

Ive been trying for the past 3 hours now to get wirless networking working. Ive googled out the wazoo and gone through many guides. Ive actually started learning terminal from just trying to get this working, but im lost ](*,) 

I have a Linksys Wirless-G Notebook Adapter, Model WPC54G Ver. 2.0

Ive also tried this howto:
[http://www.ubuntuforums.org/showthread.php?t=233565&highlight=wpc54g](http://www.ubuntuforums.org/showthread.php?t=233565&highlight=wpc54g)

But that was to no avail. i dont even know if i did that how to right, as i said this is my first time with linux. I found another one on using ndiswrapper but unless im even stupider than i though, i dont think i can get that without the computer having the internet.

Any help would rock. Ive tried just about all i can on my own, and thought it was time to ask on here :D

Oh and also, when i tried to set the essid in terminal, i got an error, which said:


I added this script for easy creating of the output. It generates what I need to help you to output.txt.
You can paste this output in this thread.

The file -> [broadcom]("http://home.casema.nl/d.sluijter/broadcom")

open a terminal and go to the folder you downloaded the file do:


```
sudo chmod +x broadcom; ./broadcom
```


Copy and paste the contents of output.txt here in the forum. Gedit starts automatically showing you the output.txt.
Copy & Paste!

---

### Post by HamCoder on 2006-09-02
I've been working with Ubuntu for 2-3 weeks - 1 week successfully.  It's probably good for you to know whether I have experience, Experience, or EXPERIENCE.

If you get your Linksys to work, then you're a better person than I.  After a week of fussing, I gave up and bought Netgear.

You're right about one thing -- without an internet connection, it's difficult (if not impossible) to get new packages and update the system.

I've got a P3 laptop and a P3 desktop, both on Linksys wireless network cards.  I did everything I could think of and find on the net.  Nothing worked, including ndiswrapper, ndisgtk, and a couple of detailed How To/Walk Through postings.  I finally gave up.

I also had a Netgear wired card for the laptop.  When I was wired, everything was OK; so I was able to get the updates, change cards, reboot and get the wireless working.  It still helped to have the detailed How To's.

I put a WG511 in the laptop and something similar in the desktop; both are working well.

I hate to tell you to run out and spend money, but it may be the only answer.  Linksys has gotten some pretty unfavorable comments in some of the Linux pages because of difficulty getting the wireless cards to work.

Hope this helps

---

### Post by CoreyE on 2006-09-02
> **TFX360 said:**
> I added this script for easy creating of the output. It generates what I need to help you to output.txt.
You can paste this output in this thread.

The file -> [broadcom]("http://home.casema.nl/d.sluijter/broadcom")

open a terminal and go to the folder you downloaded the file do:


```
sudo chmod +x broadcom; ./broadcom
```


Copy and paste the contents of output.txt here in the forum. Gedit starts automatically showing you the output.txt.
Copy & Paste!

alright ill do that as soon as i get ubuntu working... again. Currently trying to get both windows and ubuntu on my laptop, and for some od reason windows just destroyed ubuntu, so im curently working on reinstalling both, hopefully have it done in the next few hours :D

---

### Post by TFX360 on 2006-09-02
> **HamCoder said:**
> I've been working with Ubuntu for 2-3 weeks - 1 week successfully.  It's probably good for you to know whether I have experience, Experience, or EXPERIENCE.

If you get your Linksys to work, then you're a better person than I.  After a week of fussing, I gave up and bought Netgear.

You're right about one thing -- without an internet connection, it's difficult (if not impossible) to get new packages and update the system.

I've got a P3 laptop and a P3 desktop, both on Linksys wireless network cards.  I did everything I could think of and find on the net.  Nothing worked, including ndiswrapper, ndisgtk, and a couple of detailed How To/Walk Through postings.  I finally gave up.

I also had a Netgear wired card for the laptop.  When I was wired, everything was OK; so I was able to get the updates, change cards, reboot and get the wireless working.  It still helped to have the detailed How To's.

I put a WG511 in the laptop and something similar in the desktop; both are working well.

I hate to tell you to run out and spend money, but it may be the only answer.  Linksys has gotten some pretty unfavorable comments in some of the Linux pages because of difficulty getting the wireless cards to work.

Hope this helps


Got it working like a charm. Also thanks to this Forum.

I have a Linksys WPC54G version 1.2 using driver version 2.0 from Linksys



0000:06:00.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
eth0      IEEE 802.11g  ESSID:"XxXxXx"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:13:10:7A:C0:2A   
          Bit Rate:54 Mb/s   Tx-Power:14 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Encryption key:XXXX-XXXX-XXXX-XXXX-XXXX-XXXX-XXXX-XXXX-XXXX-XXXX-XXXX-XXXX-XXXX-XXXX-XXXX-XXXX
          Power Management:off
          Link Quality:100/100  Signal level:-56 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      Link encap:Ethernet  HWaddr 00:XX:XX:XX:XX:xx  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: XXXX::XXXX:XXXX:XXXX:XXXX/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9183 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8657 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4046875 (3.8 MiB)  TX bytes:1280968 (1.2 MiB)
          Interrupt:11 Memory:26000000-26002000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:11 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:572 (572.0 b)  TX bytes:572 (572.0 b)



Installed ndis drivers:
lsbcmnds		driver present, hardware present 
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
#address 192.168.1.4
#netmask 255.255.255.0
#gateway 192.168.1.1
#dns-nameservers 192.168.1.1
#broadcast 192.168.1.255
pre-up wpa_supplicant -Bw -Dndiswrapper -ieth0 -c/etc/wpa_supplicant.conf; sleep 5
pre-down killall -q wpa_supplicant; sleep 5


#auto eth1
#iface eth1 inet static
#address 192.168.1.6
#netmask 255.255.255.0
#gateway 192.168.1.2

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

#auto wlan0
#iface wlan0 inet dhcp

blacklist bcm43xx


ndiswrapper



Bit wierd that Ubuntu sees the wlan card as eth0, this is were many people go the wrong way!

---

