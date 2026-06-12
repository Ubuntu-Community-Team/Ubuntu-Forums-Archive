---
title: "Need help -&gt; Wireless"
date: 2007-01-01
forum: Absolute Beginner Talk
---

### Post by VoXoM on 2007-01-01
I installed Ubuntu 6.10 a few hours ago and I couldn't manage to get internet to work. My network card is this one
[http://catalog.belkin.com/IWCatProductPage.process?Product_Id=184399](http://catalog.belkin.com/IWCatProductPage.process?Product_Id=184399)
When going to the network stuff it only shows wired connection and modem connection.

Can anyone help?

P.S. I'm a total Linux newbie so bear with me.

---

### Post by dawg on 2007-01-01
Just found this how-to, give it a try [http://ubuntuforums.org/showthread.php?t=262465&highlight=belkin+wireless](http://ubuntuforums.org/showthread.php?t=262465&highlight=belkin+wireless)

---

### Post by VoXoM on 2007-01-01
> **dawg said:**
> whats your output when you do a 
ifconfig

nicolas@nicolas-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0E:A6:0D:16:FF  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:185 Base address:0xa400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

nicolas@nicolas-desktop:~$

---

### Post by MkfIbK7a on 2007-01-01
everything is connected so try to install wifi-radar in synaptic then run it then connect to your wifi

---

### Post by VoXoM on 2007-01-01
> **wert613 said:**
> everything is connected so try to install wifi-radar in synaptic then run it then connect to your wifi

I'm really a newb in Linux so can you explain a little more? Also every time someone asks me to check something on Linux I need to restart (dual booting) to access it. So I need to know exactly what to do if I don't wanna loose time.

---

### Post by dawg on 2007-01-01
uhm you should have either a eth1 or wlan0 for that pcmcia card.  follow the how-to, im pretty sure wifiradar will be pretty useless because the card itself is not being detected.  your output should have looked something like this
ario@2[~]$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:03:25:0D:A7:FC
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:177 Base address:0x1800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5509 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5509 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:418293 (408.4 KiB)  TX bytes:418293 (408.4 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:90:4B:C6:57:2F
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:137246 errors:0 dropped:0 overruns:0 frame:0
          TX packets:103632 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:174249160 (166.1 MiB)  TX bytes:13499158 (12.8 MiB)
          Interrupt:209 Memory:d0000000-d0002000
eth0 is ofcourse the lan, and wlan is my wireless connection.

---

### Post by Atomic Dog on 2007-01-01
No your card is not showing up so forget about wifi-radar for the moment.  You need to get the wireless card working..

Have a look here: [http://ubuntuforums.org/showthread.php?t=259037](http://ubuntuforums.org/showthread.php?t=259037)

---

### Post by MkfIbK7a on 2007-01-01
go **System > Administration > Synaptic Package Manager** and click search type "wifi" scroll down find "wifi radar" check it to install afterwards go **Applications > internet > Wifi-radar**
put in your password when the box comes up then see if it shows a network if it does click on it and try to connect

---

### Post by MkfIbK7a on 2007-01-01
isnt eth0 his card?

---

### Post by dawg on 2007-01-01
WERT, he doesnt have it set up.  He needs to configure his wireless card.  wifiradar will not do anything if the card isnt functioning.

nope, eth0 is the first ethernet connection, eth1(sometimes wirelessbecause its not configured properly) is the second

---

### Post by VoXoM on 2007-01-01
> **dawg said:**
> uhm you should have either a eth1 or wlan0 for that pcmcia card.  follow the how-to, im pretty sure wifiradar will be pretty useless because the card itself is not being detected.  your output should have looked something like this
ario@2[~]$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:03:25:0D:A7:FC
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:177 Base address:0x1800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5509 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5509 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:418293 (408.4 KiB)  TX bytes:418293 (408.4 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:90:4B:C6:57:2F
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:137246 errors:0 dropped:0 overruns:0 frame:0
          TX packets:103632 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:174249160 (166.1 MiB)  TX bytes:13499158 (12.8 MiB)
          Interrupt:209 Memory:d0000000-d0002000
eth0 is ofcourse the lan, and wlan is my wireless connection.

Okay. I'm really sorry, but what do I need to do exactly? I'm reading that how-to right now  too.

---

### Post by dawg on 2007-01-01
ok, let me ask you this.  are you currently using your ubuntu box to get online?  if not why?/use ethernet to connect.  then pretty much follow the commands on the howto

---

### Post by whwillisiv on 2007-01-01
i am having the same problem with ubuntu 6.06 and [*_this_*]("http://www.atheros.com/pt/AR5004GBulletin.htm") internal wireless card

i am attempting my first linux install and am unsure what you mean by ifconfig and how i would determine that information

using ethernet to connect is not an option

---

### Post by Atomic Dog on 2007-01-01
> **wert613 said:**
> isnt eth0 his card?

No he needs to get the card working first.  If he searches the forum or starts with the link I gave him he will be on his way. 

I would probably suggest he then install network manager instead of wifi radar as it will support WPA without the hassle.

Just my opinion...

---

### Post by MkfIbK7a on 2007-01-01
ok disregard everything i said

---

### Post by VoXoM on 2007-01-02
> **dawg said:**
> ok, let me ask you this.  are you currently using your ubuntu box to get online?  if not why?/use ethernet to connect.  then pretty much follow the commands on the howto

Not sure about what you meant but I'm connected to wifi atm on Windows.
Also, last I checked I couldn't get network manager cause it didnt support my type of computer (i386)

---

### Post by dawg on 2007-01-02
ifconfig is an interface configuator and the output will give you all interfaces.  normally, all ETHERNET/RJ45/CAT5 are listed as "eth0"  most of the time, my wireless is picked up as "eth1"  so i have my eth0 and my eth1 listed.  now, that i've got it set up properly, it'll say wlan0 instead of eth1.  now, if you can't connect to the interent via ethernet, then setting up your wireless will probably be the hardest thing in the world to do.  having net simplifies things by like 100%.  im also new to linux so i hope that if im wrong im corrected.

---

### Post by dawg on 2007-01-02
> **VoXoM said:**
> Not sure about what you meant but I'm connected to wifi atm on Windows.
Also, last I checked I couldn't get network manager cause it didnt support my type of computer (i386)

VoXoM, does your laptop have an ethernet connection that you could use while using ubuntu.

---

### Post by marx2k on 2007-01-02
> **dawg said:**
> ifconfig is an interface configuator and the output will give you all interfaces.  normally, all ETHERNET/RJ45/CAT5 are listed as "eth0"  most of the time, my wireless is picked up as "eth1"  so i have my eth0 and my eth1 listed.  now, that i've got it set up properly, it'll say wlan0 instead of eth1.  now, if you can't connect to the interent via ethernet, then setting up your wireless will probably be the hardest thing in the world to do.  having net simplifies things by like 100%.  im also new to linux so i hope that if im wrong im corrected.

How did you get your PCMCIA card to become wlan0 from eth1? Its not a big deal to me, but I would like to see mine listed as wlan0 vs. eth1

---

### Post by osinangi on 2007-01-02
You need some basic directions. Try the following link. I found it very helpful. [URL="https://help.ubuntu.com/community/CommonQuestions"].

I am assuming that you plugged the ubuntu on the Ethernet of your router and picked up all the updates. Update utility is under System --> Administration --> Update Manager. Also check EasyUbuntu and Automatix to complete your install. (Do a search for both on the forum). 

Coming to your Wifi. When you type ifconfig in the terminal window (same as ipconfig in windows), you should see wlan0 for the Belkin card (or ath0 if has Atheros chip). If you are ntot seeing any of them, your card is not recognized.

Good luck.

---

### Post by whwillisiv on 2007-01-02
i have a [*_pantech px-500 evdo card_*]("http://www.evdoforums.com/thread3784.html&highlight=linux+pantech+sprint") that i use for my internet, the only wireless network is the neighbors ... 
the site i linked to gives advice on the evdo card, but i was told by a forum user (not this forum)  that i should get on the wireless to configure my evdo ... is that backwards? or do i need to get a landline to start?  once again, i am a noob, so please explain in terms recognizable to a moderately advanced xp user or if possible link to a 'dictionary'
thank you

---

### Post by osinangi on 2007-01-02
You do not control eth0 or 1 etc. They are assigned. Most recent laptops may have multiple ethernet interfaces. One for the doc and one for the visible port on the side or the back. Wifi cards are assigned ether wlan or ath .

---

### Post by dawg on 2007-01-02
> **marx2k said:**
> How did you get your PCMCIA card to become wlan0 from eth1? Its not a big deal to me, but I would like to see mine listed as wlan0 vs. eth1 
I don't have a PCMCIA card its an internal broadcom 4306.  And as for your question, well, if I knew what i did, I'd share it with you.  but here's a start.  [http://www.seungpyo.com/stacksandpiles/](http://www.seungpyo.com/stacksandpiles/)  this person is a genius and he's pretty much that got it done for me,

echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
sudo rmmod bcm43xx
sudo rmmod ndiswrapper
sudo apt-get remove ndiswrapper-utils
sudo rm -r /etc/ndiswrapper/
sudo rm -r /etc/modprobe.d/ndiswrapper
sudo apt-get install ndiswrapper-utils
sudo ndiswrapper -i /home/dave/Desktop/bcmwl5.inf
sudo ndiswrapper -m
sed -e 's/RadioState|1/RadioState|0/' /etc/ndiswrapper/bcmwl5/*.conf
sudo modprobe ndiswrapper

thats what i did, and presto, it not only got my card up and running but it changed it from eth1 to wlan0.  hope it helps

---

### Post by osinangi on 2007-01-02
Start with the community documentation site. [http://help.ubuntu.com/community/]("http://help.ubuntu.com/community/"). Don't know much about EVDO on linux. You don't need to step throug LAN then Wifi than EVDO. If you can figure out how to do it. You can step to EVDO.

---

### Post by dawg on 2007-01-02
> **osinangi said:**
> You do not control eth0 or 1 etc. They are assigned. Most recent laptops may have multiple ethernet interfaces. One for the doc and one for the visible port on the side or the back. Wifi cards are assigned ether wlan or ath .

thats not always the case, my broadcom was assigned eth1.  but then when i followed the how-to at the stacks and piles website, it was changed to wlan0.  i dont know what did it, maybe ndiswrapper or something, could you explain how this happened.

---

### Post by osinangi on 2007-01-02
You installed the ndiswrapper. This software package makes windows driver work in Linux. For EVDO check this link. [http://www.linux.com/article.pl?sid=06/03/08/2138237](http://www.linux.com/article.pl?sid=06/03/08/2138237)

---

### Post by VoXoM on 2007-01-02
When I try to install ndiswrapper I get an error.

nicolas@nicolas-desktop:~$ tar zxvf ndiswrapper-1.33.tar.gz
tar: ndiswrapper-1.33.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
nicolas@nicolas-desktop:~$ 

Since I really can't access internet on Linux, I download stuff from Windows (Dual-Boot) and then transfer the files from Windows to Linux. The file was on my desktop when trying to install it.

---

### Post by VoXoM on 2007-01-02
help?

---

### Post by LookTJ on 2007-01-02
I think it's on your Desktop

so

```
cd Desktop
```

then try the other commands again

---

### Post by VoXoM on 2007-01-02
> **Taylor said:**
> I think it's on your Desktop

so

```
cd Desktop
```

then try the other commands again

Same problem even after cd Desktop.

---

### Post by MkfIbK7a on 2007-01-02
use the attached ndiswrapper debian files this is assuming you use i386

---

### Post by VoXoM on 2007-01-03
> **wert613 said:**
> use the attached ndiswrapper debian files this is assuming you use i386

Yes I use i386, but what do I need to do with this?

---

### Post by MkfIbK7a on 2007-01-03
install themthen replace the old ndiswrapper with them

---

### Post by VoXoM on 2007-01-03
> **wert613 said:**
> install themthen replace the old ndiswrapper with them

I installed them but then I don't really know what to do.. Replace the old one with them? How?.. Sorry but it's the first time I try Linux.

To anyone else who would like to help me out, could you please go step-by-step? Thanks.

---

### Post by MkfIbK7a on 2007-01-03
try this
```
sudo mv /usr/sbin/ndiswrapper /usr/sbin/ndiswrapper_backup
```
this creates a backup of the old one
```
sudo cp /usr/sbin/ndiswrapper-1.8 /usr/sbin/ndiswrapper
```
this replaces the old one

---

### Post by MkfIbK7a on 2007-01-03
after that do what you normally would to make ndiswrapper work

---

