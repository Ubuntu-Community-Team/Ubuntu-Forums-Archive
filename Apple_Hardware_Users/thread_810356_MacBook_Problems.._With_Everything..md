---
title: "MacBook Problems.. With Everything."
date: 2008-05-28
forum: Apple Hardware Users
---

### Post by sabamanga on 2008-05-28
So I read in about 7 different online articles that the best portable platform for running Ubuntu was the MacBook, it even beat Linux's own brand portable.

I downloaded Hardy Heron, burnt it onto a CD, and installed it on my sisters computer, and that worked great, I really liked it- Hence proceeding to install it on my MacBook, as a dual boot with Leopard.

Its great, but none of my hardware works. It wouldn't be so much of a problem if I could install the drivers, but I've not no ethernet connection. When I plug my ethernet in, it sets all the address values to 0.0.0.0. I've no idea why, and it means I can't connect to the internet, but it SAYS it's connected.

So when I'm trying to install drivers, of course sudo apt-get won't work without the internet.
I've tried installing them on my memory stick from other Windows, Ubuntu, and Mac OS X based computers, but when I plug my memory stick into Ubuntu, it says it's a read only drive, so I can't retrieve anything from there.

So, no wireless, no trackpad working properly (I have to use my whole fist to make the mouse move), no iSight, no sound, no brightness control, the only thing working is Video.
I'm a complete Ubuntu n00b, so I'm not very secure with any of the terminal commands, despite running 2 UNIX based operating systems :S

Is there anything I can do?
Help... Please..!
:(

---

### Post by hajk on 2008-05-28
Well, your being a noob, the first lesson to learn is to have a look at the sticky posts in this forum and also at the Ubuntu community wiki, where there is a lot of info on precisely the problems that you mention.

---

### Post by sabamanga on 2008-05-28
I read through the entire Ubuntu Wiki article on the MacBook and how to get all the drivers working, but I still don't have ethernet. Without that it's going nowhere :/
And yeah... I am a n00b, hah.

---

### Post by Brightbelt on 2008-05-28
Hi, I have Ubuntu dual-booting on my Macbook Air, so hang tight; things are possible here.

As for your USB stick, I have an idea which may or may not work, but it's worth a try. It might be a permissions problem in Ubuntu that is keeping you from accessing your usb drive.

First, open a terminal; you can access that in the menus through the Applications/Accessories menus. 

once you're at a command prompt there, type this:
```
sudo nautilus
```
Then it will ask you for your password. It may take a second for it to work, but you'll get your computer/home directory opening up in a new window. This means you're getting new access as a root user.

Using the new window, navigate to your USB drive and see if you can open it there. 

Like I said, this may not work, but it's worth a try...
Frank B.

---

### Post by hajk on 2008-05-28
Give the output of```

$ sudo ifconfig
```so that people here may assess what the problem is.

---

### Post by cyberdork33 on 2008-05-28
> **sabamanga said:**
> So I read in about 7 different online articles that the best portable platform for running Ubuntu was the MacBook, it even beat Linux's own brand portable.
Well, OK... Macs are nice, but not really the best for Linux per se IMHO.

> **sabamanga said:**
> So when I'm trying to install drivers, of course sudo apt-get won't work without the internet.
I've tried installing them on my memory stick from other Windows, Ubuntu, and Mac OS X based computers, but when I plug my memory stick into Ubuntu, it says it's a read only drive, so I can't retrieve anything from there.
even as read only, you can copy items off the drive... i.e. read them.

You can go into the admin menu and add the Ubuntu cdrom as a source for packages. Then many of the items can be installed via apt-get. (You still need to download other things, like the wifi drivers).

I don't know why your Ethernet does not work. It should not have an issue.

---

### Post by dustynus on 2008-05-28
Hmm ok, the ethernet has worked for me right on install and I've installed different versions of ubuntu on 2 different model macbooks many times.

Make sure the ethernet works with another computer if you can..or in OSX. Does it work in OSX, just to make sure it's not a problem with the router.
If it works with OSX, try doing the following :

Plug in the ethernet, once you've booted into Ubuntu, and wait to see if the network manager little icon in the top loads itself, and then try connecting to the internet. Then go into terminal and type:

Please post the results of
```
ifconfig
```
and
```
sudo dhclient eth0
```
The 2nd command is asking for an ip from the ethernet.

What model macbook do you have as well? 
:guitar:

---

### Post by aysiu on 2008-05-28
> **sabamanga said:**
> So I read in about 7 different online articles that the best portable platform for running Ubuntu was the MacBook, it even beat Linux's own brand portable. > **cyberdork33 said:**
> Well, OK... Macs are nice, but not really the best for Linux per se IMHO. Can you link to one of these 7 different articles? Macs (with the possible exception of Sony Vaios) have to be just about the worst laptops to buy for compatibility with Ubuntu. You're much better off with a Dell, Asus, or IBM Thinkpad. A little late now, I guess, but who is feeding you this misinformation?

---

### Post by sabamanga on 2008-05-28
Alrighty..
So.. I tried the sudo nautilus command, and that worked more or less great, thanks to Brightbelt :)
Though I'm still pretty stuck on how to install any drivers without the internet.
Results for commands were:
sabrina@sabrina-macbook:~$ sudo ifconfig 
[sudo] password for sabrina: 
eth0      Link encap:Ethernet  HWaddr 00:1e:c2:17:73:69  
          inet6 addr: fe80::21e:c2ff:fe17:7369/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:57 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:6592 (6.4 KB) 
          Interrupt:17 

eth0:avahi Link encap:Ethernet  HWaddr 00:1e:c2:17:73:69  
          inet addr:169.254.5.193  Bcast:169.254.255.255  Mask:255.255.0.0 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:1684 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:1684 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:84504 (82.5 KB)  TX bytes:84504 (82.5 KB

sabrina@sabrina-macbook:~$ sudo dhclient eth0 
There is already a pid file /var/run/dhclient.pid with pid 6256 
killed old client process, removed PID file 
Internet Systems Consortium DHCP Client V3.0.6 
Copyright 2004-2007 Internet Systems Consortium. 
All rights reserved. 
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/) 

Listening on LPF/eth0/00:1e:c2:17:73:69 
Sending on   LPF/eth0/00:1e:c2:17:73:69 
Sending on   Socket/fallback 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6 
No DHCPOFFERS received. 
No working leases in persistent database - sleeping. 
sabrina@sabrina-macbook:~$ 


and I got some of the MacBook/Ubuntu advice from an online Ubuntu magazine, here:
[http://fullcirclemagazine.org/issue-3/](http://fullcirclemagazine.org/issue-3/)
among other friends recommending, and YouTube users, and general forums...
I didn't buy the MacBook specifically for Ubuntu, so it's not so much of a big problem for me, but hey,it's free, and it seems pretty cool, so I thought I'd install it there alongside Leopard.

EDIT: I have the 4th gen MacBook which came out last March 08. 2.1GHz, 13" model.
Also yep, the ethernet works on OS X, as well as other computers. I'm using it to type right now on my sister's Hardy desktop :)

---

### Post by cyberdork33 on 2008-05-28
Your Router / DHCP server is not assigning an IP address for some reason.

---

### Post by sabamanga on 2008-05-29
Marr... This is causing way too many problems, I've been trying to set it up for more than a week now. I think it's best if I just reformat my hard drive to just run Leopard.
I've still got Ubuntu working fine on my other home computer I suppose.
Thanks for all the help anyway :)

---

### Post by pxwpxw on 2008-05-29
sabamanga

As a last resort, you might try reinstalling hardy, but this time make sure you have the ethernet cable connected and router running so the installer can set up the network connection as part of the install.

---

### Post by stueng on 2008-05-29
> **sabamanga said:**
> Marr... This is causing way too many problems, I've been trying to set it up for more than a week now. I think it's best if I just reformat my hard drive to just run Leopard.
I've still got Ubuntu working fine on my other home computer I suppose.
Thanks for all the help anyway :)

Sabamanga, could I suggest that you follow my instructions on my website at [http://www.lostpeg.co.uk/content/view/27/68/]("http://www.lostpeg.co.uk/content/view/27/68/") I have tried to explain in more detail than you would normally find and am not about to copy and paste the whole thing into a forum paste - the instructions should allow you to get your sytem dual booting, all hardware working - including wireless which should solve your internet connectivy issues

If you need the wired connection I am happy to help you out on msn or IRC or something but if you would do the honours of testing out my install instructions as I haven't had any feedback yet so I can update accordingly

Stu

---

### Post by dustynus on 2008-05-30
I'd do as pxwpxw said

Reinstall it and keep the ethernet plugged in during the install. It really should work right off install

---

### Post by russo.mic on 2008-05-30
It's pretty easy to compile ndiswrapper and such without the need for ethernet.  Just download the source with OSX, mount it, copy it over, compile it, and get the windows drivers from the 3 or 4 different places one could obtain them.

Russo

---

