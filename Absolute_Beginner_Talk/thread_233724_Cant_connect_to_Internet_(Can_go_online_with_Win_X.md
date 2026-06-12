---
title: "Cant connect to Internet (Can go online with Win XP)"
date: 2006-08-10
forum: Absolute Beginner Talk
---

### Post by chucko314 on 2006-08-10
Hey guys, Im a complete newbie to Linux.  I installed the latest version of Ubuntu (Draper Drake 6.06 - 64 bit) without an issue (partioning, dual boot, mounting window drives, etc).  However, I am unable to go online with Ubuntu, while Windows seems to have no issue connecting to the internet.

I am using a Motorolla SB4100 Cable Modem which is connected to a Netgear Router.  I am connected to the Netgear router via an ethernet cable. I have tried reading other posts from users with similar issues, but as of now, nothing seems to work.

Do I have to download a driver for the modem, and if so, do I just dl with winzip files in Windows, save them to a cd, and then open them in Ubuntu?  

Any help or command suggestions would be greatly appreciated.  Thanks

---

### Post by snellgrove on 2006-08-10
If you are connected to the router, you dont need a modem driver.. or any drivers at all.

apart from your network card, that is.

9 times out of 10, Ubuntu will have one but its possible you have a strange network card that Ubuntu doesn't support.

its possible your router isn't handing out DHCP - boot to windows, login to the router and see if DHCP is on. if not, Ubuntu is trying to grab an IP address but the router isn't handing it one, and it will require manual configuration.

Let us know how you get on..  the next step is probably to enable DHCP in the router, and see if Ubuntu works.

if it does, then you are probably good to go, but if you dont want DHCP on (possible security reasons perhaps, but your probably safe to be honest)  you can then post back if you need help setting ubuntu to a manual IP.

---

### Post by xpod on 2006-08-10
I think it`s only us with direct broadband connections that are lucky enough not to have to configour any modems..Mabey im wrong.

These guys will tell you one way or another

---

### Post by chucko314 on 2006-08-10
hey guys...ok, so i booted up XP, and after looking up my IP address/info (ipconfig /all), I was able to see that DHCP is **enabled** under ETHERNET ADAPTEN LAN.  Any suggestions on what I should be doing next?  Thanks for the help.

---

### Post by FenrisAbraxas on 2006-08-10
> **chucko314 said:**
> hey guys...ok, so i booted up XP, and after looking up my IP address/info (ipconfig /all), I was able to see that DHCP is **enabled** under ETHERNET ADAPTEN LAN.  Any suggestions on what I should be doing next?  Thanks for the help.

Of course what's the output of:

```
sudo ifconfig
```

---

### Post by chucko314 on 2006-08-10
eth0   Link encap:Ethernet HWaddr 00:17:31:BA:20:B7
       inet6 addr: fe80:217:31ff:feba:20b7/64 Scope:Link
       UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
       RX packets: 34 errors:0 dropped:0 overruns:0 frame:0
       Tx packets: 0 errors dropped:0 overruns:0 carrier:0
       collisions:0 txqueuelen:1000
       Rx bytes: 2040 (1.9 kiB) Tx bytes:0 (0.0b)
       Interrupt:201 Base address:0x6000

lo     Link encap: Local Loopback
       inet addr:127.0.0.1  Mask:255.0.0.0
       inet6 addr: ::1/128 Scope: Host
       UP LOOPBACK RUNNING MUT:16436 Metric:1
       RX packets: 23 errors ; 0 dropped: 0 overruns:0 frame:0
       Tx packets: 23 errors dropped:0 overruns:0 carrier:0
       collisions:0 txqueuelen:0
       Rx bytes: 1556 (1.5kiB)  Tx bytes:1556 (1.5KiB)

---

### Post by FenrisAbraxas on 2006-08-10
> **chucko314 said:**
> eth0   Link encap:Ethernet HWaddr 00:17:31:BA:20:B7
       inet6 addr: fe80:217:31ff:feba:20b7/64 Scope:Link
       UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
       RX packets: 34 errors:0 dropped:0 overruns:0 frame:0
       Tx packets: 0 errors dropped:0 overruns:0 carrier:0
       collisions:0 txqueuelen:1000
       Rx bytes: 2040 (1.9 kiB) Tx bytes:0 (0.0b)
       Interrupt:201 Base address:0x6000

lo     Link encap: Local Loopback
       inet addr:127.0.0.1  Mask:255.0.0.0
       inet6 addr: ::1/128 Scope: Host
       UP LOOPBACK RUNNING MUT:16436 Metric:1
       RX packets: 23 errors ; 0 dropped: 0 overruns:0 frame:0
       Tx packets: 23 errors dropped:0 overruns:0 carrier:0
       collisions:0 txqueuelen:0
       Rx bytes: 1556 (1.5kiB)  Tx bytes:1556 (1.5KiB)

It looks like your ethernet adapter is using ipv6 :p. 

Do this: 

```
 sudo gedit /etc/networking/interfaces (or something im at work with a crappy windows box)
```

Look at the examples and copy something like:

```


eth0 = "dhcp"


```

I remember the examples were pretty well explained and documented.

Good Luck, post any questions about that file here (if you can paste a copy of the file better).

---

### Post by chucko314 on 2006-08-10
I opened the interfaces file under ETC >> NETWORK >> .

file content:

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth0 inet dhcp

auto eth2
iface eth0 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

---

### Post by FenrisAbraxas on 2006-08-10
> **chucko314 said:**
> I opened the interfaces file under ETC >> NETWORK >> .

file content:

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth0 inet dhcp

auto eth2
iface eth0 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

Hmm i thinks it's alright, everything through dhcp :S 

comment the line of eth0 (put a # in front of the line and change it to be like this)

```
auto eth0
     iface eth0 inet static
     address 192.168.1.1
     network 192.168.1.0
     netmask 255.255.255.0
     gateway 192.168.1.254
     broadcast 192.168.1.255
``` 

Adjust the values to match your network

then do ```
 sudo /etc/networking restart 
```

And post again the output of ```
 sudo ifconfig 
```

Those are the values for my homenetwork, probably yours are a little different.

---

### Post by tappad on 2006-08-11
Hi, im having the exact same problem!

Installed Ubuntu 64 on my brand new computer today, and suprised to see that i couldnt get an inet adress (only inet6).

I do know for a fact that i have DHCP enabled on my router and that it should work with ubuntu. (it does on my old computer, 32-bit ubuntu).

I have allready played around with different ip-settings. Unfortuneatly i couldnt find my router with static-ip.

Is there a good way to force the eth. to only look for an inet adress and stay away from ipv6?

---

### Post by snellgrove on 2006-08-11
There is a file you can edit which completely disables that Ipv6 malarky.

have a quick search, i'll try and find it ...but not right now, as it is late here :P and I want to go to bed.

I have disabled it here though, as it can speed up your internet. (try searching along the lines for a forum post, on how to speed up your internet by disabling ipv6)

Theres something you can do in Firefox too which is also covered in there, but its easy and involves changing a line in the about:config (type that in your address bar)

---

### Post by snellgrove on 2006-08-13
Right, I found it:

[clicky](http://www.ubuntuforums.org/showthread.php?t=87798)

Hopefully this will help :-k

---

### Post by tappad on 2006-08-14
Yeah, ive found it too..
However it didn't fix my problem.

Cant understand why it wont work, i have never had a problem with this before :/

---

### Post by crypthor on 2006-08-14
Hello,

I've had some problems with an onboard ethernetcard in Ubuntu. It was installed correctly, but could not reach my router.

Somewhere i read about after having worked in windows, shutdown your pc and also plug out power completely. For about 20 seconds. After that boot directly into Ubuntu. Worked for me.

Has something to do with windows settings in the ethernet card which get flushed after powerdown.

Hope it works for you.

crypthor

---

### Post by tappad on 2006-08-14
That sounds like a possible solution.
Since i am dualbooting i think that everytime i tried i came from an "soft" reboot out of ms-world.

So, you have to do this every time you boot from MS to ubuntu?

---

### Post by tappad on 2006-08-14
Crypthor, Finally!
Can't thank you enoguh for your reply =)

Finally my connection works, and just like that.
Shutdown, cut the power for a couple of secs.. Boot ubuntu..

Still i was wondering if anyone has any more info on this specific problem?

---

### Post by crypthor on 2006-08-14
amazing eh? Stupid microsofties.

There is something you can do about it software-wise. Something with acpi... i know it's here somewhere.
Let me get back to you when i'm sobered up. ;) 

glad it worked.

crypthor

---

### Post by comppsyco on 2006-08-28
Wow! this just worked for me too! It seems like it happens to me when I hibernate Windows, which makes sense. Did you ever figure out a software solution?

---

