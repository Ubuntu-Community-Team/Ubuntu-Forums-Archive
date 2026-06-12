---
title: "Hardware working when using Live CD, not working after full install"
date: 2007-06-18
forum: Absolute Beginner Talk
---

### Post by Opz on 2007-06-18
Hi,

After finally getting my own pc to run Ubuntu properly (getting the soundcard and dual monitor setup up and running), i was thinking on installing it on my dad's pc as well. So i used the live cd to check if it ran ok. It ran ok and everything worked, i had sound, good resolution on the screen and internet was working correctly using a USB Wireless adapter after i entered the correct WEP Key and told my router the MAC address of the USB adapter to get access.

I decided to install the whole thing and partitioned everything and so on before installing, thereby removing any trace of Windows XP. After the reboot everything worked fine, except for my wireless internet connection. So i did the same thing i did to get the wireless network running as when i did using the live cd. In the network manager i selected the correct network along with using DHCP and the WEP key. The MAC address of the USB adapter was still in my router's settings. No connection at all.

So i tried to do it all manually, giving it a static IP address, subnet mask was generated automatically (which indicates some connection to the router, doesn't it?) and entering the gateway ip. Selecting the correct network and entering the WEP key didn't resolve anything though. Still no connection.

After that i put the USB adapter to 'Roaming' and now the icon with the two monitors (on the upper panel next to the clock etc) changed into a 'network strength' icon (as if there was a wireless network connection) and even showed me a percentage of the wireless network strength (around 85%) when hovering over it with my mouse. I'm thinking: It works!
WRONG, when i want to go to a website, i get nothing. There's no actual connection i guess. Update manager also can't connect to the internet.

Doing the 'iwconfig' and 'iwlist scan' commands in the terminal gave me all the correct listings of my USB adapter as well as any wireless network present including my own.
But i just can't get connected to the internet!!

Anyone had the same problem or know what the solution is?

What puzzles me is the fact that it worked when using it with the Live CD, but doesn't work after a full install of Ubuntu. Why is that? I would really like to know, because initially i had a similar problem with my own computer and it's graphics card's resolution. This has been solved now though.

I wouldn't like to solve this problem by drilling a whole in my ceiling and connect it through a wire :p It has worked before and should work again. I hope.

---

### Post by mxrten on 2007-06-18
The subnet-mask is determined by the ip-address you choose, and does not indicate any connection with the router... however I think the 'network strength'-icon does... hmm...

Have you tried pinging the router? (open a terminal, type: "ping 192.168.1.1", or whatever ip-address the router has) what does it say?

---

### Post by candtalan on 2007-06-18
It may be possibe to use the live CD and note the content of various relvant files, and compare them with the content of the installed files.

I do not know which files though, and this would not explain the reasons, just suggest an ad hoc solution.

---

### Post by Opz on 2007-06-18
When i ping my router's ip address, it shows:

PING (Ip address) (ip address) 56(84) bytes of data
64 bytes from (ip Address): icmp_seq=1 ttl=225 time=2.20 ms

The second line keeps on going where icmp_seq gets one number higher and the time at the end of the line keeps changing from  1 to about 5 ms. This process doesn't stop until i close the terminal btw.

---

### Post by Opz on 2007-06-18
Now this is really strange, all of a sudden it started to work for some reason. It's a slow connection though, but it works.

Although i'm happy that it workes now, i would still like to know what made it work. Just in case it happens again. I would like to have control over 'getting things to work' in Ubuntu.

---

### Post by lazyart on 2007-06-18
That means you are communicating with the router.  The problem lies elsewhere.  What are your subnet and gateway set to?

---

### Post by Opz on 2007-06-18
No i mean i can now actually go on the internet. I already tried a few websites, they'ra all ok.
And after a reboot it works at my connections maximum speed.
Very strange that it started to work all of a sudden, but i'm not complaining anymore, because it works.
Now i'm hoping it will keep on working :p

Thanks for any ideas, i wish i started using Ubuntu earlier, it's really nice once things start to work and i'm beginning to understand and appreciate the terminal more and more.

---

### Post by candtalan on 2007-06-18
> **Opz said:**
> No i mean i can now actually go on the internet. I already tried a few websites, they'ra all ok.
And after a reboot it works at my connections maximum speed.
Very strange that it started to work all of a sudden, but i'm not complaining anymore, because it works.
Now i'm hoping it will keep on working :p

Thanks for any ideas, i wish i started using Ubuntu earlier, it's really nice once things start to work and i'm beginning to understand and appreciate the terminal more and more.

DNS entries are crucial for normal web use.
I think there is a way of using ping to get out to - say- google (if I knew what the IP address of google was)(for a test).
May be your DNS is wrong somehow. The DNS entries you would normally use are supplied by your isp, however, any dns on the net will work, if your machine can find them, so I was told once.

---

### Post by orestesm on 2007-06-25
I am having this same exact issue only not as lucky as Opz since it did not just randomly start work.  I tried a few changes in /etc/modules and /etc/modprobe.d/blacklist that were suggested in other posts but no luck.  Then after several reboots between bootCD and isntalled image it actually connected to the internet after booting from the HD and everything was working!  Then I tried repeating the connection by rebooting from the HD again and went back to no connection (just like Opz, it always works when I boot from the CD).

Anyone know which files I can copy from the liveCD filesystem to the HD filesystem in order to fix this once and for all.  Also, I am new to Linux to I would appreciate a pointer to how I can find the installed image on the HD while I am running from the boot CD (what directory is it under?).

Thanks in advance.

---

### Post by daimaru on 2007-06-25
dont know if this will help, but since you did everything else; did you guys check the output of the 
```
route
```
command?

should list your default gateway

if it does not enter
```
route add default gw 192.168.2.1
``` 
or whatever address your router has.

---

### Post by orestesm on 2007-06-25
Output of route was:
Kernel IP routing table
Destination     Gateway     Genmask        Flags  Metric  Ref     Use Iface
Link-local        *                  255.255.0.0  U        0          0         0     eth0
default           *                  0.0.0.0          U        1000    0         0     eth0

After performing command: route add default gw 192.168.1.1
route gives:
Output of route was:
Kernel IP routing table
Destination     Gateway       Genmask        Flags  Metric  Ref     Use Iface
Link-local        *                    255.255.0.0  U        0          0         0     eth0
default           192.168.1.1  0.0.0.0          UG      0         0          0     eth0
default           *                    0.0.0.0          U        1000    0         0     eth0

And no connection after that...

---

