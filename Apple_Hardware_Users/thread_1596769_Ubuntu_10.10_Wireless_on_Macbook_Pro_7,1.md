---
title: "Ubuntu 10.10 Wireless on Macbook Pro 7,1"
date: 2010-10-14
forum: Apple Hardware Users
---

### Post by ryanczak on 2010-10-14
Since I installed 10.10 on my macbook 7,1 I have noticed that occasionally the wireless (BCM4322 using wl driver) is flaky when I cold boot or wake up from sleep. The behavior is that I can connect to a wireless network but I get a lot of packet loss and see huge amounts of latency. I also observe a lot of out of order packets in tools like mtr which I assume is related to dropped frames at layer 2. 

If I:

```
rmmod wl
```

and

```
modprobe wl
```

and rejoin the wireless network everything will be OK again. 

I've also noticed that using WPA causes similar performance issues to what I describe above. 

Anyone else having this issue? 

Is the wl driver in 10.10 based on the newly opensourced driver from broadcom? 

Is there a version of the old driver from 10.04 available for 10.10? I have much better performance out of that driver. 

Also, does anyone know of a good place to follow the development of the new broadcom driver?

---

### Post by ryanczak on 2010-10-26
For anyone else that experiences this problem I was able to signifigantly improve performance by disabling power management on the wifi interface:

```
/sbin/iwconfig eth1 power off
```

I also wrote a script to automate this. Place the following script in /etc/NetworkManager/dispatcher.d:

```

!/bin/sh
# /etc/NetworkManager/dispatcher.d/wifipower.sh
# Matt's Macbook Pro 7,1 wifi power adjuster
#
# I've found that turing off power management fixes performance problems with the
# BCM4322 802.11a/b/g/n Wireless Controller found in the Macbook Pro 7,1
#
# Placing (a link to) this in /etc/NetworkManager/dispatcher.d causes NM to 
# invoke this every time network state changes

# The WIFI interface
WIFIINT="eth1"

if [ -z "$1" ]; then
    echo "$0: called with no interface" 1>&2
    exit 1;
fi

if [ "$1" != "$WIFIINT" ]; then
    exit 1;
fi

/sbin/iwconfig eth1 power off

```

---

### Post by opulentorca on 2010-10-27
I am also finding the wireless to be a little flaky as of recent on my macbook 2,1. The connection tends to disconnect itself and then can take a while to reconnect.

I tried to the "/sbin/iwconfig ethl power off" code but received the following message:
Error for wireless request "Set Power Management" (8B2C) :
    SET failed on device ethl ; Operation not permitted.

Adding a sudo to the front of the command got this:
Error for wireless request "Set Power Management" (8B2C) :
    SET failed on device ethl ; No such device.

---

### Post by Alienth on 2010-10-27
Here is a post I wrote on how to disable the wireless power management entirely:

[http://uselessuseofcat.com/?p=67](http://uselessuseofcat.com/?p=67)

Short answer: simply create a blank file named "/etc/pm/power.d/wireless". This will disable all power management of your wireless devices.

---

### Post by ryanczak on 2010-10-27
opulentorca you must be root to run the script. try using 
```
sudo /sbin/iwconfig ethl power off
```

Alienth's method is probably a better overall solution though. I have not tested it yet but I intend to today. 

Thanks for the tip Alienth!

---

### Post by ryanczak on 2010-10-27
Alienth's solution does not work in my tests. I place an empty file named wireless in /etc/pm/power.d/ and it does not seem to work for me.  

However, If I place a file named wireless in /etc/pm/power.d/ with the following contents it works:

```

#!/bin/sh

/sbin/iwconfig eth1 power off


```

---

### Post by opulentorca on 2010-10-28
Thank you for the help Ryanczak. Adding the file seemed to improve wireless connectivity (still not perfect) although now the computer's fan is running full tilt and shows no signs of slowing. There must be a better solution for all of this. I have no trouble staying connected and cool under MAC OS X. hmm...

---

### Post by ryanczak on 2010-10-28
Did you add the mactel support ppa apt repository? If so did you install the macfanctld package? It does a good job of regulating my macbook's temp. 

You definitely needs something to control temperature.

---

### Post by fhjlx on 2010-10-28
I installed both ryanczak's script and Alienth's script however I still experience periods in which my wifi card will seemingly stop transferring. I don't get disconnected from the network but network traffic seems to slow to absolutely nothing and then start up again. Any ideas guys?

---

### Post by ryanczak on 2010-10-28
you should not need both. I suggest you try to use only one of them. Why don't you try this: place a file named wireless in /etc/pm/power.d/ with the following contents it 

```
#!/bin/sh

/sbin/iwconfig eth1 power off

```
make sure it is executable 

```
sudo chmod +x /etc/pm/power.d/wireless
```

A reboot is not strictly required for the script to kick in, you could just plug into power and then unplug (change pm state) as well. 

Once you do that, post the output of:

```
sudo iwconfig eth1
```

Your output should look something like this: 
(note the Power Management:off)


eth1      IEEE 802.11abgn  ESSID:"foo"  
          Mode:Managed  Frequency:5.66 GHz  Access Point: 00:26:CB:94:12:50   
          Bit Rate=16 Mb/s   Tx-Power:24 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=5/5  Signal level=-54 dBm  Noise level=-91 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by uvaio on 2010-11-17
Hi everyone.

I'm having same issue on my pro 7,1 with on exception that I have quite bad ping all the time. Setting power management off doesn't seem to help at all.
I originally thought that signal of my old g router is not good enough when I started to use Mac and bought new n router. Still having same issues. 
Just checked with my older Vaio laptop and can confirm that it doesn't have any issues with g nor n router and ping is good and stable. Both laptops are running Ubuntu 10.10.
Just to compare while on vaio I get 20-40ms this is what I have right now on Mac
PING google.com (209.85.135.147) 56(84) bytes of data.
64 bytes from mu-in-f147.1e100.net (209.85.135.147): icmp_req=1 ttl=51 time=47.9 ms
64 bytes from mu-in-f147.1e100.net (209.85.135.147): icmp_req=2 ttl=51 time=61.4 ms
64 bytes from mu-in-f147.1e100.net (209.85.135.147): icmp_req=3 ttl=50 time=117 ms
64 bytes from mu-in-f147.1e100.net (209.85.135.147): icmp_req=4 ttl=50 time=395 ms
64 bytes from mu-in-f147.1e100.net (209.85.135.147): icmp_req=5 ttl=51 time=299 ms
64 bytes from mu-in-f147.1e100.net (209.85.135.147): icmp_req=6 ttl=50 time=409 ms
64 bytes from mu-in-f147.1e100.net (209.85.135.147): icmp_req=7 ttl=51 time=329 ms
64 bytes from mu-in-f147.1e100.net (209.85.135.147): icmp_req=8 ttl=51 time=226 ms
64 bytes from mu-in-f147.1e100.net (209.85.135.147): icmp_req=9 ttl=50 time=368 ms
^C
--- google.com ping statistics ---
10 packets transmitted, 9 received, 10% packet loss, time 9002ms
rtt min/avg/max/mdev = 47.941/250.578/409.466/134.899 ms


I noticed excesive retries number is increasing constantly over time.

eth1      IEEE 802.11abgn  ESSID:"StanN"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:23:CD:1B:87:A4   
          Bit Rate=19.5 Mb/s   Tx-Power:24 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=2/5  Signal level=-74 dBm  Noise level=-94 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:160  Invalid misc:0   Missed beacon:0

any help would be appreciated.

---

### Post by la1234uk on 2011-01-17
> **ryanczak said:**
> you should not need both. I suggest you try to use only one of them. Why don't you try this: place a file named wireless in /etc/pm/power.d/ with the following contents it 


I am running Ubuntu 10.10 on a home-made desktop PC. 

I am using an USB wireless "pen" (Buffalo WLI-UC-AG300N Wireless LAN Adapter).

Had similar problems, slow connection, often wifi seemed to stop or slow down without apparent reasons, just as described here.

I followed the suggestions of ryanczak and problem seems solved. Now I am watching a streaming video, and system-monitor show peaks of 300Kb/sec, whereas before the trick video was just stuck buffering... 

So this problem seems to be general, not related in particular to Macbook wifi hardware.

Thank you ryanczak, thank you guys !

Greg Ruo

:p

---

### Post by Geremia on 2011-04-20
> **opulentorca said:**
> I tried to the "/sbin/iwconfig ethl power off" code but received the following message:
Error for wireless request "Set Power Management" (8B2C) :
    SET failed on device ethl ; Operation not permitted.

Adding a sudo to the front of the command got this:
Error for wireless request "Set Power Management" (8B2C) :
    SET failed on device ethl ; No such device.
Run [FONT=Courier New]iwconfig[/FONT]. Your wireless interface could be, e.g., wlan0, as it is on my Macbook 2,1 with Ubuntu 10.10.

Also, my wireless power-management has been off, and I am still getting the symptoms of the OP. My laptop is on 24/7, and after a few hours it'll just drop the connection with the wireless router. I have to go into suspend, wake it, then that'll snap the wireless driver back into connecting with the router. Although [FONT=Courier New]iwconfig[/FONT] for me says power-management is off, perhaps turning it on would help in my case. I think the wireless driver also causes my CPU fan to go to high RPMs, too. Is anyone else experiencing this? Thanks

---

### Post by ducuit on 2011-06-17
Thank you, Geremia, your post solved my problem. Alienth's and ryanczak's solutions didn't work for me because my iwconfig returned wlan0 (not eth0 or eth1).

In case what Geremia said is not clear (as it wasn't for me at first), you should always run iwconfig on your config to know what you interface is.

In my case, ASUS Eee PC 1015p, it returned wlan0. Therefore, the script becomes:

#!/bin/sh  /sbin/iwconfig wlan0 power off
now everything works.

---

### Post by bdentremont on 2011-06-20
> **ryanczak said:**
> ... Also, does anyone know of a good place to follow the development of the new broadcom driver?

I also have a MBP 7.1 with Ubuntu 10.10.  I've had nothing but trouble with the broadcom driver version 5.60.48.36-2 which is in the repository.  Notably, it was not responsive to the "/sbin/iwconfig ethl power off" command that everyone has been suggesting.  I've been using version 5.100.82.38 since December and it's has solved all my problems.  Latency is down dramatically both on battery and plugged in and throughput is slightly responsive to battery state (or the manual command) as it should be.

You can get the driver as source here
[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

I'm glad to see some kind soul has posted a patch for compatibility with the > 2.6.37 kernels.  I had to track that line down on my own from the compiler errors.

---

