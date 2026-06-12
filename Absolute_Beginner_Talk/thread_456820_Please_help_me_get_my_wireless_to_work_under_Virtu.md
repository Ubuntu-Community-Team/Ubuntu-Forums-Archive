---
title: "Please help me get my wireless to work under Virtualbox"
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by ArrowApollo on 2007-05-28
I'm running on a thinkpad t42, in ubuntu 7.04 as host, and windows vista as guest. I've searched all over, installed the guest additions and then did the special driver install for vista but all it did was install the wired ethernet, which i dont have. I even went to the ibm site and got the right *i think* wireless drivers and installed them in vista but nothing. I've done all the google searches I can think of, but so far my wireless has yet to even detect a network in vista.

---

### Post by dan171717 on 2007-05-28
> **ArrowApollo said:**
> I'm running on a thinkpad t42, in ubuntu 7.04 as host, and windows vista as guest. I've searched all over, installed the guest additions and then did the special driver install for vista but all it did was install the wired ethernet, which i dont have. I even went to the ibm site and got the right *i think* wireless drivers and installed them in vista but nothing. I've done all the google searches I can think of, but so far my wireless has yet to even detect a network in vista. does your wirleless work in ubuntu.ifit doesnt you need tomeke it work in ubuntu. try ndiswrapper or havea dig on google. p.s. most routers havea lan socket. my wireless doent work in ubuntu and i am using lan on a livebox.

networking **_DOES NOT_** work in vista in virtualbox. i think there is a fix. please check the virtualbox website.
hope this helps

---

### Post by bodhi.zazen on 2007-05-28
There is a fix for newtorking in Vista, it is a problem with Vista not virtualbox :

[http://forums.virtualbox.org/viewtopic.php?t=224](http://forums.virtualbox.org/viewtopic.php?t=224)

---

### Post by ArrowApollo on 2007-05-28
Yah it works perfectly in ubuntu. ill try the fix and tell you how it went . thanks.

---

### Post by ArrowApollo on 2007-05-28
I already tried that fix and it's what gave me the ethernet but not wireless.

---

### Post by bodhi.zazen on 2007-05-28
OK

half-way home

For wireless you should try paraprouted

[http://doc.gwos.org/index.php/VirtualBox#Wireless](http://doc.gwos.org/index.php/VirtualBox#Wireless)

I would be interested to know if this works for you :)

---

### Post by ArrowApollo on 2007-05-28
When i run the command to install paraprouted it can't find the package. are there any repositories i need to add?

---

### Post by ArrowApollo on 2007-05-28
I think its renamed as parprounted. I googled and looked it up and it seems right. i'm trying it.

---

### Post by bodhi.zazen on 2007-05-28
> **ArrowApollo said:**
> When i run the command to install paraprouted it can't find the package. are there any repositories i need to add?

Ah, typo sorry

```
suod aptitude install parprouted
```

It is in Universe

---

### Post by ArrowApollo on 2007-05-28
k i installed parprouted. but the next commands not working

:~$ chown root:vboxusers /dev/net/tun
chown: changing ownership of `/dev/net/tun': Operation not permitted

---

### Post by ArrowApollo on 2007-05-28
What if I go into users and groups and check root in vboxusers? will that allow me to?

---

### Post by ArrowApollo on 2007-05-28
Nope didn't work. still wont allow me

---

### Post by bodhi.zazen on 2007-05-28
> **ArrowApollo said:**
> k i installed parprouted. but the next commands not working

:~$ chown root:vboxusers /dev/net/tun
chown: changing ownership of `/dev/net/tun': Operation not permitted

sudo chown root:vboxusers /dev/net/tun

---

### Post by ArrowApollo on 2007-05-28
before i go on, thanks so much for helping me.

but more problems

brian@brian-laptop:~$ chown root:vboxusers /dev/net/tun
chown: changing ownership of `/dev/net/tun': Operation not permitted
brian@brian-laptop:~$ sudo chown root:vboxusers /dev/net/tun
Password:
brian@brian-laptop:~$ tunctl -t tap1 -u brian
Failed to open '/dev/net/tun' : Permission denied
brian@brian-laptop:~$ sudo tunctl -t tap1 -u brian
Set 'tap1' persistent and owned by uid 1000
brian@brian-laptop:~$ ip link set tap1 up
SIOCSIFFLAGS: Permission denied
brian@brian-laptop:~$ sudo ip link set tap1 up
brian@brian-laptop:~$ sudo ip addr add 192.168.1.101 dev tap1
brian@brian-laptop:~$ echo 1 > /proc/sys/net/ipv4/ip_forward
bash: /proc/sys/net/ipv4/ip_forward: Permission denied
brian@brian-laptop:~$ sudo echo 1 > /proc/sys/net/ipv4/ip_forward
bash: /proc/sys/net/ipv4/ip_forward: Permission denied
brian@brian-laptop:~$

---

### Post by bodhi.zazen on 2007-05-28
:lolflag:

All those commands need to be run as root (thus the permission denied errors)

I just updated the wiki,

Start with :```
sudo -i
```

Then, as root run those commands

---

### Post by ArrowApollo on 2007-05-28
eth1 or wlan0?

---

### Post by bodhi.zazen on 2007-05-28
In a terminal type 

```
ifconfig
```

See if you wireless card is eth1 or wlan1

use what it is listed as :)

---

### Post by ArrowApollo on 2007-05-28
Now what's supposed to happen or what do I do to get it to work? just run vista?

---

### Post by bodhi.zazen on 2007-05-28
> **ArrowApollo said:**
> Now what's supposed to happen or what do I do to get it to work? just run vista?

Shut down Vista

In VirtualBox :

Click "Network" on the Right

Under Adapter 0, in the "Attached to" pull down menu select "Host Interface" Under Interface Name type "tap1" (without quotes)

Save and exit ...

Now start you machine and you should be good to go.

---

### Post by ArrowApollo on 2007-05-28
It's not working but its different. instead of a red x on the network icon its a yellow alert. but it wont find any wireless networks and it says it has limited connectivity to some unknown network but i have no idea what its talking about. could this have to do with the ethernet drivers i installed before?

---

### Post by bodhi.zazen on 2007-05-28
he he he ...

Yea that is working

Windows complains about an IP conflict on the network (yellow box), but it should be working.

Open a terminal on windows

Start -> cmd

In the black box enter 

```
ipconfig /all
```

You should get an IP address on your network (not 10. ....)

You can get rid of that by setting an IP manually on the windows guest.

---

### Post by ArrowApollo on 2007-05-28
So the IP i put in before has to match the IP im seeing in the ipconfig /all? Which? The tunnel adapter local area connection? or the ethernet adapter LAN? cuz only the ethernet is giving me a straight foward ip address. I'd post what it gave me but isnt that a little dangerous?

---

### Post by ArrowApollo on 2007-05-28
[IMG]http://img458.imageshack.us/img458/9648/screenshot1wj4.png[/IMG]

---

### Post by bodhi.zazen on 2007-05-28
[http://www.computerswv.com/docs/vistaip.html](http://www.computerswv.com/docs/vistaip.html)

[http://www.hotcomm.com/FAQ/FAQ_staticIPXP.asp](http://www.hotcomm.com/FAQ/FAQ_staticIPXP.asp)

Just enter a new IP (change the last two numbers) under IP Address

---

### Post by ArrowApollo on 2007-05-28
can the new ip be anything or does it have to match the tap1s?

---

### Post by bodhi.zazen on 2007-05-28
> **ArrowApollo said:**
> can the new ip be anything or does it have to match the tap1s?

Change ONLY the last number !

For example 192.168.0.xx

Change the xx

Not the 192 or 168 or 0

You may use any number that is not in use on your network 

So, no, Do not use the IP of the host or TAP (or any other computer / device on your network).

---

### Post by ArrowApollo on 2007-05-28
I entered the new IP, subnet, and gateway perfectly, but it still says it the local area connection still does not have a valid IP config. Should i change the IPv6 settings too?

---

### Post by bodhi.zazen on 2007-05-28
I must admit I have no idea of the problem at this point.

I suspect it is with Windows, but I am not sure.

I have never run Vista and if the links did not work for setting a static IP my only other piece of advice is to check if you can in fact use dhcp rather then a static IP.

---

### Post by shownoregrets on 2008-01-02
Hey guys, I was looking at this forum for some help and I tried everything you guys suggested, but to no avail. Eventually I just gave up and decided to run a fresh install on vbox. However, this time I kept the network settings on "NAT"...lo and behold, after installing the guest additions, vista connects to "network" and I can go on the internet again! just thought I'd share this little bit that helped me out.:)

---

