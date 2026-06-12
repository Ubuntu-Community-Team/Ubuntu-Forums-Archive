---
title: "Wireless card is detected, networks are seen, but when connected no internet"
date: 2007-05-05
forum: Absolute Beginner Talk
---

### Post by yomero2k2 on 2007-05-05
Hi everyone. I have another noob question to ask. I just recently installed 7.04 and have it dual booting with XP. I love it. It worked great right out of the box, it's really smooth and fast and everything was detected...except for my wireless of course. I have been looking all over for help, and came upon [this thread]("http://ubuntuforums.org/showthread.php?p=1071920&mode=linear"), which helped immensely. Now, my card is detected, as the light turns on and when I go to network manager, it lists the local networks and their strengths. It even seems like it connects to mine, but then it doesn't pump any internet through. I've asked everyone I know to see if they know anyone who can help me, and haven't found anyone. I'd really really love to be able to get on my wireless network with ubuntu so I can ween myself off of windows. Some information... I have a [Compaq Presario C303NR]("http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00796374&lc=en&cc=us&dlc=en&product=3289285&query=c303nr&dest_page=product"). My wireless card is the Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card. The router in trying to connect to is a Linkysys BEFW11S4. I 'm not really sure what other information is needed, but I can try to give anyone any other information they need. Thanks a lot for taking time to read my thread, I really appreciate it.

---

### Post by e_james on 2007-05-05
Wired or wireless, I have several times found myself in an apparently similar situation. There is another test which can clarify the situation. Can you "ping" a suitable IP address? I usually use my ISP's dns address (62.241.162.200). If this works, then it would seem that you need to sort out your dns addresses. If ping doesn't work then I am stumped.

---

### Post by yomero2k2 on 2007-05-05
This is on wireless. If I connect wired, then everything works perfect. I will figure out how to ping it and then get back to you, thanks for your help!

---

### Post by yomero2k2 on 2007-05-05
How would I go about sorting dns addresses? sorry, i am pretty clueless here. thanks again

---

### Post by e_james on 2007-05-05
System / Administration / Network tools .... select Ping tab, type the address, click the button.

I have never used it but I think this is also correct    (edit - this is correct. It seems you need to use Ctrl-C to stop it.)
- open a terminal window
- type "ping 62.241.162.200"

In either case you will likely see very little if it doesn't work and several responses if it does.

---

### Post by e_james on 2007-05-05
I must admit to very limited expertise here but there are a few key steps. First a question. Are you using DHCP or a static IP address? I'm assuming that, if you have it working with Windows, then you have suitable settings for wireless encryption.

Using Windows. Open Network connections, right click your network adaptor and select status / details. you should see your current IP address, the default gateway address (router) and probably 2 DNS server addresses. Linux needs to get to the same position.

---

### Post by ubnewbie2 on 2007-05-05
> **yomero2k2 said:**
> Hi everyone. I have another noob question to ask. I just recently installed 7.04 and have it dual booting with XP. I love it. It worked great right out of the box, it's really smooth and fast and everything was detected...except for my wireless of course. I have been looking all over for help, and came upon [this thread]("http://ubuntuforums.org/showthread.php?p=1071920&mode=linear"), which helped immensely. Now, my card is detected, as the light turns on and when I go to network manager, it lists the local networks and their strengths. It even seems like it connects to mine, but then it doesn't pump any internet through. I've asked everyone I know to see if they know anyone who can help me, and haven't found anyone. I'd really really love to be able to get on my wireless network with ubuntu so I can ween myself off of windows. Some information... I have a [Compaq Presario C303NR]("http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00796374&lc=en&cc=us&dlc=en&product=3289285&query=c303nr&dest_page=product"). My wireless card is the Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card. The router in trying to connect to is a Linkysys BEFW11S4. I 'm not really sure what other information is needed, but I can try to give anyone any other information they need. Thanks a lot for taking time to read my thread, I really appreciate it.

Connecting, but no data, sounds like a security problem.  Wireless networks can be set up to only accept known mac addresses. If this is the cause, you need to add yours to the list in the access point's config.  Also, more probably I suspect, are you using the correct encryption and key. It could be WEP or WPA.  Check this is configured, and the right key has been entered into your linux card setup

---

### Post by yomero2k2 on 2007-05-05
I do have mac address filtering and he laptops mac address is definitely on the list, since I am able to be online when I boot into XP.  I dont have WPA or WEP enabled, just mac address filtering. The pinging doesnt work, maybe I'm not even connected to my router then? Although like I said, it shows up and I can click on it and it gives me the icon with the bars, but no bars are filled. I am using DHCP. Thanks again guys for taking time to try to help me out, its very appreciated.

---

### Post by seetho on 2007-05-05
First thing is to check if your DHCP has given you an appropriate address.  Use terminal and type the following:

```
seetho@st-x31:~$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:0C:F1:1C:C6:19
          inet addr:192.168.1.104  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:f1ff:fe1c:c619/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1319 errors:1 dropped:1 overruns:0 frame:0
          TX packets:1271 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1000033 (976.5 KiB)  TX bytes:182125 (177.8 KiB)
          Interrupt:11 Base address:0x8000 Memory:c0200000-c0200fff

```

I assume your wireless is eth0.  Change it to eth1 if that's your wireless.

Let me know what you get.

---

### Post by yomero2k2 on 2007-05-06
Here is the output```
jcoria@jcoria-laptop:~$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:16:D4:43:EB:4D  
          inet addr:192.168.2.104  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::216:d4ff:fe43:eb4d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1188 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1248 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1080965 (1.0 MiB)  TX bytes:184099 (179.7 KiB)
          Interrupt:17 Base address:0x4000 

```
Let me know what else you need to be able to help me. Thanks!

---

### Post by ubnewbie2 on 2007-05-06
Are you sure eth0 is your wireless card, because that looks like it's working. It's got an IP address and has sent and received over 1000 packets.

---

### Post by yomero2k2 on 2007-05-06
Hmm... I thought it was.... how can I check to make sure that it is? Sorry, I am really really new at this. thanks!

---

### Post by Whiffle on 2007-05-06
Please post the output of 

```

sudo iptables -L

```

This sounds exactly like what my problem is/was.  I have a workaround for it but I'm still working on a better solution.

---

### Post by yomero2k2 on 2007-05-06
Hi thanks for responding. This is the output ```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination   
```
What is your workaround, if I may ask?

---

### Post by yomero2k2 on 2007-05-06
I also tried eth1 and this is the output```
jcoria@jcoria-laptop:~$ ifconfig eth1
eth1      Link encap:Ethernet  HWaddr 00:14:A5:E2:9D:E3  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:103 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:4266 (4.1 KiB)
          Interrupt:3 
```
Again, I am not sure which is my wireless, I hope this helps. Thanks again!

---

### Post by Fitzy_oz on 2007-05-06
> **yomero2k2 said:**
> Here is the output```
jcoria@jcoria-laptop:~$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:16:D4:43:EB:4D  
          inet addr:192.168.2.104  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::216:d4ff:fe43:eb4d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1188 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1248 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1080965 (1.0 MiB)  TX bytes:184099 (179.7 KiB)
          Interrupt:17 Base address:0x4000 

```
Let me know what else you need to be able to help me. Thanks!

Hi there,
don't mean to butt in, but i've recently just been through this problem with another user on this forum and the long and short of it is that Broadcom cards under linux suck **** due to bc's well lack of support.  That being said we were able to get it to work using the ndiswrapper and the windows XP driver, I suggest trying this.  [Here is the link]("http://ubuntuforums.org/showpost.php?p=2561941&postcount=1")

Any questions feel free to post, I will monitor this thread for a while.  :)

---

### Post by yomero2k2 on 2007-05-06
Thanks for your help. I also dont know what module to use... my card is Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card. Thanks again!

---

### Post by Fitzy_oz on 2007-05-06
> **yomero2k2 said:**
> Thanks for your help. I also dont know what module to use... my card is Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card. Thanks again!

it will be bc45xx, which you will need to blacklist

---

### Post by Pulka on 2007-05-06
Hi everyone.


I´m having the same problem as described in the beggining. Light on, essid listed, wlan0 recognized. My wireless network is opened to listed MAC adress, essid hidden and no WEP.
I have a Acer IPN2220 wireless Lan Card.

---

### Post by yomero2k2 on 2007-05-06
Ok, I blacklisted bc45xx and now, it wont connect to the router. The good thing is that it still sees wireless networks so the wireless card seems to be working. It also doesn't connect to neighbors wireless, which I could also connect to in XP. Any other help that could be given would be very welcome. Thanks!

---

### Post by seetho on 2007-05-06
If you really want to check which is your correct wireless adaptor then use iwconfig.

```
seetho@st-x31:~$ iwconfig
lo        no wireless extensions.

irda0     no wireless extensions.

eth0      IEEE 802.11b  ESSID:"Afghan"  Nickname:"ipw2100"
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:14:7C:AD:26:D4
          Bit Rate=11 Mb/s   Tx-Power:off
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=93/100  Signal level=-65 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:1   Missed beacon:0

eth1      no wireless extensions.

sit0      no wireless extensions.

```

So on my system eth0 is my wireless.  Yours may be different.  

If you have an IP address assigned but still unable to use the net then it may well be a driver problem.  I've seem many posts in this forum regarding BC wireless peoblems.

---

### Post by yomero2k2 on 2007-05-07
I've had enough headaches over this, I'm just gonna go ahead and remove the ubuntu partition. Thanks to everyone who offered their help, maybe one day bc will come out with the drivers i need to allow me to use ubuntu successfully.

---

### Post by e_james on 2007-05-07
I would like to add a comment now, mainly for the benefit of future readers of this thread.

I was running ubuntu 6.06 on my laptop and, when it was initialially installed, I was pleasantly surprised that my buit-in Intel wireless adaptor was immediately detected and configured. At that time I was using a Netgear wireless adsl router. I have recently switched to an ADDON GWAR3000 wireless adsl router and, as I verified a few hours ago, I couldn't connect to the internet wirelessly but I could connect by ethernet. There's something about a change of router which I don't understand.

I decided now was a good time to upgrade ubuntu. I tried upgrading 6.06 to 6.10 using the dvd but the process kept aborting. There was no useful error message, but I suspect that there was insufficient space on the hard drive. So I decided to do a fresh install of 7.04. I had a separate /home partition and didn't format that one. Everything went pretty much according to plan although it took 3 reboots before I got to the user login. I have found with this laptop and my shuttle that rebooting without power-off sometimes doesn't work. Power-on must initialise something extra.

Next step wireless networking. 
First System / Adminstration / Network, select the wireless adaptor and turn off roaming. Select the access point (already detected), set the WEP key and DHCP. Turn roaming on again. 
Click the network icon on the top panel and select the ADDON again, add the WEP key again, and add a password to the keyring. Another click on the network icon and the connection is up and working. 

I don't suggest that I did everything correctly or in the right order but it is now working. The sequence of events may be helpful to someone else in a similar situation. 
A further bit of information. This laptop is configured for dual boot with Windows XP. All of the hardware always worked with XP although the Netgear router was easier to use than the ADDON. The ADDON needed a little bit of DNS tweaking.

---

### Post by cajunaggie on 2007-05-11
I'm having the same issue with a Netgear WG311t wireless card. My internet connection works find and dandy under WinXP, and I'm connecting to an unencrypted network. In Ubuntu, I can connect to the network (@ approx 44-48%) but I can't access the internet.
This is my output for pinging what I'm assuming is the DNS address for the ISP:
```
--- 192.168.1.1 ping statistics ---
62 packets transmitted, 0 recieved, 100% packet loss, time 61044 ms
```

ifconfig ath0 output:
```
link encap: Ethernet   HWaddr 00:0F:B5:F8:1B:44
inet addr:192.168.1.4   Bcast:193.168.1.255  Mask:255.255.255.0
inet6 addr:  fe80::20f:b5ff:fef8:1b44/64 Scope:Link
UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
RX packets:147  errors:0 dropped:0 overruns:0 frame:0
TX packets:143  errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:21401 (20.8 Kib) TX yles:14565 (14.2 Kib)
```

iwconfig output (pertaining to ath0):
```
IEEE 802.11g ESSID:"cunningham" Nickname:" "
Mode:Managed Frequency 2.462 GHz Access Point: 00:0F:B5:62:83:C6
Bit Rate:36 Mb/s   Tx-Power:18 dbm   Sensitivity=0/3
Retry:off   RTS thr:off   Fragment thr:off
Power Management:off
Link Quality: 41/94  Signal level=-53 dBm   Noise level=-94 dBm
Rx invalid nwid:8821  Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0   Invalid misc:0   Missed beacon:0
```

Can anyone out there help me make translate/make sense of this? I'm in way over my head here.

---

### Post by partiallydecapitated on 2007-05-11
Hello, I am a complete newbie.
 I have a similar problem, but intermittently. 
I have a dell inspiron e1505, BC wireless. I am running fiesty as a standalone OS - no dual boot.
I installed it 2 days ago, everything went well. wireless was recognized, flashing then steady light. Wireless networks found, but would not connect. I kept forcing it to try (by just clicking on the button) to connect approx 10 times. Then it connected??
Rebooted, same thing happened but only took 4 or 5 attempts.
rebooted, same thing, connected in 4 attempts which is what keeps happening now. it will connect, display the bars etc after 3 or 4 attempts.
Now it is down to 2 or 3 attempts. I do have variable signal strength but now I connect with average SS of 50%,  
I have done nothing else, but it seems to get smarter each session. I know it is not much help, but wanted to voice this odd behavior. All drivers are correct and I have not used ndiswrapper. 

:confused: :)

---

### Post by e_james on 2007-05-12
Rather like the global warming issue, there is, for me, an accumulating amount of evidence that there is some subtle but fundamental difference in the way that ubuntu interacts with adsl routers in comparison with Windows XP. My experience is limited but I have found that my laptop will connect properly to the internet while using one router but not with 2 others. Wired or wireless doesn't seem to make much difference except that the wireless connection has an extra step or two which can also go wrong. Feisty Fawn (7.04) seems to minimise or eliminate some of these problems.

I also found that disabling ipv6 can be useful as a last resort. On one pc using Edgy (6.10), when I disabled ipv6 for Firefox, I could view web pages. When I disabled ipv6 for Thunderbird, I could retrieve email. I still could not download updates. There is a general ipv6 setting for the whole system. See this link

[http://ubuntuforums.org/showthread.php?t=6841&highlight=disable+ipv6](http://ubuntuforums.org/showthread.php?t=6841&highlight=disable+ipv6)

but, if I remember correctly, the results were not entirely satisfactory. Changing the router was noticeably more successful. Diagnostic results seem to be of limited value, especially for me. I suspect that even the software authors would not find it easy to identify the source of the problems.

cajunaggie. 
This result ("Bcast:193.168.1.255") looks wrong. IP adresses beginning 192 are in one of the sets allocated for local area networks and not used on the internet. 193 is outside this set. Is it a typing error?

If you are running ping tests, I would expect (if everything is in order), that you would get responses from your router (probably 192.168.1.1 but it can be changed - mine is 192.168.0.102), from other pcs on your network and from valid internet addresses. The ISP's dns addresses are usually a good test. Try mine - 62.241.162.200

Just a point to note. Most routers have a setup option which can disable the response to pings, and firewalls generally can do the same; so if you don't get a response, it might still be working properly, just ignored. In my experience dns machines always respond to pings. In case you don't know, the command "ping 62.241.162.200" should also work in a dos window (command prompt)  using Windows XP.

---

### Post by partiallydecapitated on 2007-05-12
Thank you e_james for the information. Networks are a mystery to me. I just turned my machine on and this time it connected the first time. Although it is decidedly un-linux-like, at this juncture I will adopt the sleeping dog approach, i will not kick it unless it acts up again.
Another note, I installed fiesty Beta version on another dell laptop, inspirion 6000 bc wireless, and it worked flawlessly the first time, and connected immediately.
An alternative idea specific to me, and perhaps others, I am forced to use satellite access to bet online. It is relatively stable, but it is prone to lose the connection sporadically depending on the weather. I have no idea how that affects the networking behavior, but in XP it would force me to reboot regularly. Once I connect with Fiesty, it seems to be much more stable. Just wanted to offer more info to the wizards that create this stuff.

---

### Post by cajunaggie on 2007-05-12
I figured out mine. Something in my firewall was conflicting with my connection. Now all I have to is figure out what it is and rewrite the iptable. :rolleyes:

---

### Post by WNDS1701 on 2007-05-20
> **cajunaggie said:**
> I figured out mine. Something in my firewall was conflicting with my connection. Now all I have to is figure out what it is and rewrite the iptable. :rolleyes:

Hello,


Can somebody write a how-to on this topic? I have the same problem like you but can't even connect to the WLAN here.


Thanks a lot!

---

### Post by WNDS1701 on 2007-05-29
Nobody? Is it a bug? Is someone working on it?

---

### Post by partiallydecapitated on 2007-05-29
I continue to have the same problem as well. I must attempt to connect multiple times, and eventually it will. When it does, it is very stable.
If I plug it in, it connects immediately, then when I unplug it, the wireless stays connected.
I have tried everything I could find in the forums, as well as tricks obtained elsewhere.
I believe the broadcom powers that be, have not made the drivers etc. available to the OS wizards. 
I have also learned that Linux needs to be tweaked to perform on a given machine. 
Sorry I can't help further.

---

### Post by WNDS1701 on 2007-05-30
> **partiallydecapitated said:**
> I continue to have the same problem as well. I must attempt to connect multiple times, and eventually it will. When it does, it is very stable.
If I plug it in, it connects immediately, then when I unplug it, the wireless stays connected.
I have tried everything I could find in the forums, as well as tricks obtained elsewhere.
I believe the broadcom powers that be, have not made the drivers etc. available to the OS wizards. 
I have also learned that Linux needs to be tweaked to perform on a given machine. 
Sorry I can't help further.

It worked with me fine after the first time, I set it up manually. It was pretty stable and worked for 2 weeks or so. Now what happens is, that the wired connection is enabling itself automatically, although there is a good wireless network available...

I'm getting confused, because I don't know the tools that you need, in order to edit the networking files manually. Otherwise, I would have sat down and done it manually...

---

### Post by ncappel1 on 2007-06-08
I would like to add that I was having the same problem just yesterday and today. I brought my computer to my family's house, tried to connect to a their (unencrypted)(apple)wireless network. I knew my card functioned, it worked perfectly just the other day!

Everything *seemed* to be working, iwconfig listed my wireless as connecting to the correct network and access point, I even would get a signal (78%), but the internet still wouldn't work. I couldn't use firefox or synaptic.

I then used the "iwlist scan" command and saw the channel it was connecting on. for some unknown reason, I decided to try and connect to that channel with "iwconfig <device> channel <the channel that was listed>", and bingo! everything worked fine.

---

### Post by WNDS1701 on 2007-06-10
@ncappel1: I tried this but it didn't work out...

---

