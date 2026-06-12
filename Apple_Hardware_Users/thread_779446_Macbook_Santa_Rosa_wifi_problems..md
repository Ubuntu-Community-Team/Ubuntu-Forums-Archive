---
title: "Macbook Santa Rosa wifi problems."
date: 2008-05-02
forum: Apple Hardware Users
---

### Post by d0b33 on 2008-05-02
I installed the windows driver of the bootcamp disc using the ndiswrapper wireless driver tool for the Broadcom BCM43xx 1.0 card but still am not able to connect to my wireless network.
:(

Anybody know of a fix that works?

Edit:
Got the wlan0 device working but still cant connect to the net.

---

### Post by cyberdork33 on 2008-05-02
please give information....

ndiswrapper -l

ifconfig

---

### Post by d0b33 on 2008-05-03
ndiswrapper -l
```

bcmwl5 : driver installed
        device (14E4:4328) present
```

ifconfig
```
eth0      Link encap:Ethernet  HWaddr 00:1b:63:bc:ae:4e
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3074 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3074 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:153700 (150.0 KB)  TX bytes:153700 (150.0 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1e:52:c6:8f:6f
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 Memory:50500000-50504000
```

---

### Post by cyberdork33 on 2008-05-03
ok then your hardware is working... wlan0 is your wireless device.

If you are having problems you have to be more specific about the issue what exactly is not working?

---

### Post by d0b33 on 2008-05-04
I am unable to connect to my router, it just searches for a wifi device but never finds it, I have entered the correct ssid and wifi passkey.

---

### Post by d0b33 on 2008-05-04
I even followed the macbook air wifi tutorial but the same result
[https://help.ubuntu.com/community/Macbook_Air](https://help.ubuntu.com/community/Macbook_Air)
Wifi works but cant connect.

This is a WAP secured router.

---

### Post by d0b33 on 2008-05-04
Resolved!

I did not notice the unlock button for network settings after I unlocked it wifi worked, newbie mistake sorry.

How do I get PPPoE to work over wifi? I only have the eth0 option no wlan

---

### Post by d0b33 on 2008-05-04
Actually NO it's not resolved yet :(

I still can't connect to the net.. 

when I try to visit a site using firefox all I get is "looking up.. " then a timeout.

:(

---

### Post by cyberdork33 on 2008-05-04
try using wicd instead of network manager.

---

### Post by d0b33 on 2008-05-04
> **cyberdork33 said:**
> try using wicd instead of network manager.

Well I tried sudo pppoeconf and I got a message that the access concentrator did not respond :confused:

What's wicd?

Thanks

---

### Post by JCasper on 2008-05-04
wicd is a replacement for network manager. It didnt do much for me, but since you atleast got your wireless showing, Id try it.

You can find it in the repos.

---

### Post by d0b33 on 2008-05-04
> **JCasper said:**
> wicd is a replacement for network manager. It didnt do much for me, but since you atleast got your wireless showing, Id try it.

You can find it in the repos.

I'll give it a shot although it's not found in my local repo server, so I'll need to source it internationally.

---

### Post by JCasper on 2008-05-04
Oh sorry, come to think of it...I did have to add a 3rd party source.

Here are install instructions.

[http://wicd.sourceforge.net/wiki/doku.php?id=faq]("http://wicd.sourceforge.net/wiki/doku.php?id=faq")

---

### Post by d0b33 on 2008-05-05
> **JCasper said:**
> Oh sorry, come to think of it...I did have to add a 3rd party source.

Here are install instructions.

[http://wicd.sourceforge.net/wiki/doku.php?id=faq]("http://wicd.sourceforge.net/wiki/doku.php?id=faq")

Thanks

I'm gonna use the repository method...
[http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php)

---

### Post by d0b33 on 2008-05-08
No Luck!

I give up on this till there's a definite fix available

---

### Post by harobed on 2008-05-11
> **d0b33 said:**
> I am unable to connect to my router, it just searches for a wifi device but never finds it, I have entered the correct ssid and wifi passkey.

I exactly same issue. Network Manager detect all essid around my place but I can't connect to my wireless network. I've entered essid and passkey correctly... but it don't work.

---

### Post by philipp. on 2008-05-11
enter "ndiswrapper -l", what does it say?

I am sure we can solve your problems. I solved mine too:

[http://ubuntuforums.org/showthread.php?t=787889](http://ubuntuforums.org/showthread.php?t=787889)

---

### Post by d0b33 on 2008-05-11
> **harobed said:**
> I exactly same issue. Network Manager detect all essid around my place but I can't connect to my wireless network. I've entered essid and passkey correctly... but it don't work.

what's your macbook model number?  Macbook 3,1(santa rosa)?

---

### Post by jdriessen on 2008-05-11
I had problems with the regular madwifi drivers from (latest svn) instead I installed the Macbook Madwifi variant - if you visit their website its quite easy to find.

i own a macbook2,1 and after installing the madwifi macbook drivers I'm able to connect to wireless networks using NetworkManager. I am still having trouble with NetworkManager connecting to Ad-hoc networks...

---

### Post by d0b33 on 2008-05-11
> **jdriessen said:**
> I had problems with the regular madwifi drivers from (latest svn) instead I installed the Macbook Madwifi variant - if you visit their website its quite easy to find.

i own a macbook2,1 and after installing the madwifi macbook drivers I'm able to connect to wireless networks using NetworkManager. I am still having trouble with NetworkManager connecting to Ad-hoc networks...

I believe you have the atheros chipset then?

I'm having a problem with the broadcom.

---

