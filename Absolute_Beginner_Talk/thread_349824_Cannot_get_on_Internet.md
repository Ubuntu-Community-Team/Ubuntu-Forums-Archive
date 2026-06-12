---
title: "Cannot get on Internet"
date: 2007-01-30
forum: Absolute Beginner Talk
---

### Post by st33med on 2007-01-30
I have installed Ubuntu 2 days ago. I installed the correct driver for it (it was a specific Dell Mini WLAN 1390). It now says there is Wifi, but when I try to connect to the Internet, Firefox will not show it. I tried pinging, confirming the WEP connection, and checking the Connection via the Terminal, but nothing works.:confused: 

:( Please help.:(

---

### Post by deadgobby on 2007-01-30
try this link and see if it works if not. we'll go to the next step. sound cool :guitar: 
[https://help.ubuntu.com/community/WifiDocs/WirelessNetworking](https://help.ubuntu.com/community/WifiDocs/WirelessNetworking)

---

### Post by st33med on 2007-01-30
Nope. Does not work. done that thousands of times. *sigh*
I also looked up why I can't and the most likely answer is that it doesn't support ipv6. Problem is that I can't rewrite a read-only file.
[URL="https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide"]
Here[/URL] is the link.

Also, this is my wireless configuration:
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"mason"  Nickname:"Broadcom 4311"
          Mode:Managed  Frequency=2.437 GHz  Access Point: 00:13:10:C8:97:8D   
          Bit Rate=11 Mb/s   Tx-Power=18 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=116/100  Signal level=-19 dBm  Noise level=-70 dBm
          Rx invalid nwid:0  Rx invalid crypt:2  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

---

### Post by mangoti on 2007-01-30
Ping and wep are Ok? What's the output of:

```
ifconfig
```
```
route
```
Try to disable eth0 to see if you can get on internet.

---

### Post by st33med on 2007-01-31
Alright, I'll play along. Here is the ifconfig:


[PHP]eth0      Link encap:Ethernet  HWaddr 00:15:C5:B7:17:A9  
          inet addr:192.168.1.104  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::215:c5ff:feb7:17a9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:935 errors:0 dropped:0 overruns:0 frame:0
          TX packets:892 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:823345 (804.0 KiB)  TX bytes:142068 (138.7 KiB)
          Interrupt:209 

eth1      Link encap:Ethernet  HWaddr 00:18:F3:57:D5:3D  
          inet6 addr: fe80::218:f3ff:fe57:d53d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:58 errors:0 dropped:0 overruns:0 frame:0
          TX packets:795 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6535 (6.3 KiB)  TX bytes:38549 (37.6 KiB)
          Interrupt:4 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:300 (300.0 b)  TX bytes:300 (300.0 b)
[/PHP]
Funny thing is that route shows the table, but nothing appears below it...

---

### Post by jkeyes0 on 2007-01-31
Well, you don't have a wireless IP address. I had a similar problem and resolved it by disabling my wired connection (eth0).

Since you have a Broadcom 4311 card, I can only assume you went through the Ndiswrapper setup to get your card working? (link [here]("http://www.ubuntuforums.org/showthread.php?t=297092"))

Either way, it seems your card is being recognized and is talking, so at this point, have you done a "sudo dhclient eth1"?

If for some reason that doesn't work, you might try giving it a static IP address, just to see if it works at all. To do that, click System -> Preferences -> Networking, and change the configuration on the wireless card to use Static IP (looking at your eth0 settings, 192.168.1.XXX as the IP address, 255.255.255.0 as the subnet mast, and 192.168.1.1 as the gateway).

---

### Post by st33med on 2007-01-31
Heh... I did not do the HOWTO... I looked on google first... stupid,  stupid me... and I did what they told me to do... I'll try this one!! 

:KS THANK YOU FOR PUTTING THAT THERE:KS 

I am still trying this right now. Wish med luck!

---

### Post by dannyj on 2007-01-31
Let me know how it goes. I'll be installing Feisty when it comes out. I have a broadcom wireless too.

---

### Post by st33med on 2007-01-31
Is it possible to enable this driver if I enable Ubuntu to read and write from windows, because I have a dual boot for Windows+Ubuntux86.

---

### Post by saadakhtar on 2007-01-31
if you guys have broadcom wlan cards then you should try "wlan-ng" this package works for me. had the right driver for broadcom hardware and is the easiest to install.
you can use wifi-radar or kwlan to manage your connection.

if needed i can walk you thru into installing wlan-ng,

hope this helps.

cheers

---

### Post by st33med on 2007-02-01
Well, when I get to the part about the sudo modprobe ndiswrapper, it comes up with this ugly and scary response:
[PHP]andrew@andrew-laptop:~$ sudo modprobe ndiswrapper
FATAL: Could not open '/lib/modules/2.6.17-10-generic/misc/ndiswrapper.ko': No such file or directory
[/PHP]

On top of that, I could not get the eth1 to be recognized. I tried lspci, shows squat about eth1.

---

### Post by st33med on 2007-02-02
Someone??? Anyone????

---

### Post by st33med on 2007-02-04
HELP!!!!](*,) ](*,) ](*,) [-o< [-o< :cry: :mad:

---

### Post by shareMenaPeace on 2007-02-04
You following this howto?
[http://www.ubuntuforums.org/showthread.php?t=297092](http://www.ubuntuforums.org/showthread.php?t=297092)

---

### Post by st33med on 2007-02-04
:neutral:  uhhh... yeah.

---

### Post by shareMenaPeace on 2007-02-04
So after which part of the howto you get this error?

You installed ndiswrapper and rebooted?

---

### Post by shareMenaPeace on 2007-02-04
- If you are using a Dell laptop that's NOT model E1505, you need to go to Dell.com and search for the drivers that correspond to your specific model. Use those instead.

---

### Post by st33med on 2007-02-04
The ndiswrapper modprobe wouldn't work. I already put the error above in the post.

What should I do?

---

### Post by shareMenaPeace on 2007-02-04
Did you installed linux-headers-generic?

> For ndiswrapper you must install the package build-essential and linux-headers-generic (if you are under edgy). They are necessary to compilation.

[http://translate.google.com/translate?u=http%3A%2F%2Fforum.ubuntu-fr.org%2Fviewtopic.php%3Fpid%3D709669&langpair=fr%7Cen&hl=de&ie=UTF-8&oe=UTF-8&prev=%2Flanguage_tools](http://translate.google.com/translate?u=http%3A%2F%2Fforum.ubuntu-fr.org%2Fviewtopic.php%3Fpid%3D709669&langpair=fr%7Cen&hl=de&ie=UTF-8&oe=UTF-8&prev=%2Flanguage_tools)

Im not sure but it seems you need to install header generic kernel files.

[http://www.ubuntuforums.org/showthread.php?t=321202&highlight=linux-headers-generic](http://www.ubuntuforums.org/showthread.php?t=321202&highlight=linux-headers-generic)

Maybe wait a little and let someone else reply ...

---

### Post by st33med on 2007-02-17
Well, that didn't help.

And I think that I made it worse. The wifi light comes on but my wireless card is not recognized. It doesn't show up as its own port (eth1, wlan0, nada).

Actually, it was always this way.

---

### Post by st33med on 2007-02-20
OK, I reinstalled Ubuntu, and tried the thing again...

[SIZE="5"]IT WORKED!!!:KS [/SIZE]

Well sorta. It tells me now that I can scan finally, but I cannot get on the internet. I tried to put in the WEP code, but it tells me it won't connect.

What now?

---

### Post by saadakhtar on 2007-02-21
if you guys have broadcom wlan cards then you should try "wlan-ng" this package works for me. had the right driver for broadcom hardware and is the easiest to install.
you can use wifi-radar or kwlan to manage your connection.

start synaptic package manager:
in terminal:
sudo synaptic

then

search for *"**wlan-ng**"*
and install it.
for terminal or konsole the command should be ***sudo apt-get install wlan-ng***

now install a connection manager
in synaptic search for *"**kwlan**"*
or in terminal type in ***sudo apt-get install kwlan***

now restart the system to make sure the hardware initializes.
when system comes back up. 
goto ***ADMINISTRATION --> NETWORKING** *          * make sure "Wireless Connection" is enabled and set to DHCP.*
NOW
goto ***APPLICATIONS --> INTERNET --> kwlan***
or
in terminal type in ***sudo kwlan***
you should see a new taskbar icon for kwlan click that and click scan on kwlan gui and the rest is to be configured by your network settings.
For me it worked perfectly but i am not able to use wep or wpa yet so as an alternative i am using mac filter with a open system.


hope this helps.

cheers

---

### Post by st33med on 2007-02-21
That's not really what I'm looking for saadakhtar. I'm looking for a way to get it to realize that my thing is working.

PS: BUMP IT!

---

### Post by st33med on 2007-02-21
bump again

---

### Post by st33med on 2007-02-21
still bumpin it up

---

### Post by igknighted on 2007-02-21
As a general rule, only bump once every 24 hrs.  People do read back several pages.

I have read the thread, and I have several questions.  When you attempted to install via ndiswrapper, are you positive that you got the proper windows wireless drivers?  Also, the method saad has outlined is probably the best choice for your card, as it uses a linux native driver.  What program are you using to set yp the connection?  I use wifi-radar and it works perfectly for me.  Others swear by network-manager.  Try downloading these programs and seeing if you can set up you connection through them.

Finally, if you believe that the connection should be fine but you are foiled by the WEP key, try disabling that on the router and checking that it will connect.  Then we can isolate the problem at least.

---

### Post by st33med on 2007-02-21
Yes, I have the proper wireless drivers, but I haven't tried wifi-radar. I will try that sometime.

And sometime as in tommorow. I get tired of fiddling on Ubuntu after a while. (No, that doesn't mean I hate Ubuntu):-$

---

### Post by igknighted on 2007-02-21
> **st33med said:**
> Yes, I have the proper wireless drivers, but I haven't tried wifi-radar. I will try that sometime.

And sometime as in tommorow. I get tired of fiddling on Ubuntu after a while. (No, that doesn't mean I hate Ubuntu):-$

Haha, understood... it's a lot to take in at once.  But I think that in the end (for me at least) it was worth every problem and then some, so stick with it.  I can't imagine ever going back now.

---

### Post by st33med on 2007-02-22
Well I didn't use wifiradar, but I did use Wireless assistant. It walked me through very easily. It was able to sense the netwok, but not able to get on. I double-checked the WEP key, and it was correct. I've also tried disabling the Ethernet connection, no gives.

I'm not sure if this will help:
```
andrew@andrew-laptop:~$ ndiswrapper -l
bcmwl5 : driver installed
        device (14E4:4311) present (alternate driver: bcm43xx)

```

I've noticed that, but I'm not sure if that's the problem or not. If so, do I remove the alternate driver? It is already blacklisted though. And how do I get it to say driver present?

---

### Post by saadakhtar on 2007-02-22
try changing your wireless connection to insecure and then connect. i am too going thru the same problem. cant seem to get any kind of encryption to work so had to use MAC Filter feature on my router.
however i did find some tutorials on getting wpa to work but none of them were broadcom specific but i am sure if i use a little common sense along with those instructions i can get it to work. Just need to find some free time.
you should check this link out:
[http://ubuntuforums.org/showthread.php?t=202834&highlight=wpa+supplicant]("http://ubuntuforums.org/showthread.php?t=202834&highlight=wpa+supplicant")

see if it helps.

---

### Post by st33med on 2007-02-25
Well, I don't have a WPA connection, I have a WEP.(Sad, ain't it:( ) Anyways, dmesg says this:
```
[17179593.076000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[17179593.076000] IPv6 over IPv4 tunneling driver
```

---

### Post by saadakhtar on 2007-02-27
you are probably having the same problem as me. try and connect to a open wireless system w/out wpa or wep encryption.

Please read my post on page 3, its the last one the very bottom of the page.
it should make things a little more clear for you.

regards

---

