---
title: "Internet Help."
date: 2008-04-10
forum: Absolute Beginner Talk
---

### Post by hossiam on 2008-04-10
I unplugged the Ethernet wire now nothing.   It is working but will not allow my browser or updates to connect.  I found this.....

 Re: Internet stopped working mysteriously
Just an idea, worked for me when I had similar problem but no idea if it will help you. Check that you have
nameserver 192.168.1.1 in /etc/resolv.conf (replace 192.x.x.x with your routers address)

but not sure what i should do with it.  I found no such file on my computer.  It is just my Ubuntu machine all others work.   All other computers in the house are having no issues.

---

### Post by wolfen69 on 2008-04-10
this may seem simplistic, but did you try just rebooting?

---

### Post by spiderbatdad on 2008-04-10
As far as I know, /etc/resolv.conf gets written by the program Network manager. It would normally contain the namesevers you use to resolve urls.
If you have no such file, It sounds like you had no internet connection at the time of install.
Can you plug an ethernet cable directly into your computer and reboot?

---

### Post by hossiam on 2008-04-11
OK i tried rebooting...no luck.   The icon that displays internet connection(right next to the update notifications) says im connected.   Updates and browser will not connect.   I had a similar problem with my xp in the past but I cant remember what it was.   Thanks for the help so far.

---

### Post by superprash2003 on 2008-04-11
is your ubuntu machine getting an ip?please go to the terminal and type ifconfig and post results here , also type ping google.com and post results here

---

### Post by Gulyan on 2008-04-11
When I have a problem with Ubuntu I try to boot from the live cd and see if it works from there, if it does I do a fresh install. :)

---

### Post by smurphy_it on 2008-04-11
Did you reboot your router ?  Some older routers (depending on make) kinda get hung up.  They still dole out IP addresses, you can ping the router etc.... but you can't get an internet connection.

If you can reboot your router and it works, you might want to take a look at your MTU settings within your router's advanced settings as well as some TCP timeout values (try decreasing them).

---

### Post by hossiam on 2008-04-11
eth0      Link encap:Ethernet  HWaddr 00:08:0D:CC:05:D0  
          inet addr:192.168.2.19  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::208:dff:fecc:5d0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:29564 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1251 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1797128 (1.7 MB)  TX bytes:56738 (55.4 KB)

eth1      Link encap:Ethernet  HWaddr 00:02:2D:BA:D8:2B  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:16 Base address:0xc100 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1432 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1432 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:140516 (137.2 KB)  TX bytes:140516 (137.2 KB)

ping: unknown host google.com


I have rebooted my router and in my home network summary it says im connected.   I will try the ubuntu cd.

---

### Post by bumanie on 2008-04-11
The only way I could get the internet to work on gutsy was to disable ipv6 in firefox. It may not work for you but what you are describing sounds similar ie all settings indicate connection, but can't connect to server.
Open firefox. In the address bar type about:config. In the filter type ipv6. Right click on the line that appears and then left click on toggle to change the value to true. Reboot.
If it doesn't fix the problem, navigate back to toggle and change the value back to false and your system will be back to how it is now.

---

### Post by bt224 on 2008-04-11
I have to agree with smurphy_it. If you had issues like this with XP, it might be the router hanging. Our old Linksys does this every so often. Turn off the computer, reboot  the router, then reboot the computer. Worth a try anyway.

---

### Post by spiderbatdad on 2008-04-11
It seems to me your issue is with /etc/reslov.conf
If you have no namesevers, how can you resolve any urls?

/etc/resolv.conf should look something like this:

```
### BEGIN INFO
#
# Modified_by:  NetworkManager
# Process:      /usr/bin/NetworkManager
# Process_id:   4672
#
### END INFO



nameserver xx.xxx.xxx.x
nameserver xx.xxx.xxx.xx
nameserver xx.xxx.xxx.xx


```

The namesevers are how the urls are resolved. Contact your internet service provider. Find out what namservers they  use, and put that in there...some public nameservers are also available like 4.2.2.6  4.2.2.1  4.2.2.2

In your original post, you list some local machine ip addresses...those are not nameservers.
Clearly you are connected to the router, but the cable modem may need to be rebooted...or the router. You appear to have no internet connection.

---

### Post by hossiam on 2008-04-11
in etc/resolvconf all i have is a file called avahi-daemon.....am i looking in the right place?  inder file system>etc>resolvconf   there is no . in the file name?  Im using gusty if thats ant help.

---

### Post by spiderbatdad on 2008-04-11
Here's a screenshot for you...scroll down below the folders... click the screenshot a second time after it opens, to enhance the resolution. I believe your modem or router needs to be rebooted.

---

### Post by hossiam on 2008-04-11
SOLVED.......thanks guys it was the nameserver  that screen shot is what put me into the know.   Thaks a bunch.  One more question....how do you figure this stuff out?  I Google until i get but i mean actually dissect the problem and rationally figure it out.  with all the files and commands  to try i am very impressed.

---

### Post by hossiam on 2008-04-12
Hate to do this again but.....now I cant network to my xp machine....was working before all this occured but now.....nothing.   If anyones got an idea I would appreciate greatly.

---

