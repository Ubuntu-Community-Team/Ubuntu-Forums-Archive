---
title: "Aptitude - Install - No Internet"
date: 2007-06-22
forum: Absolute Beginner Talk
---

### Post by SimonM on 2007-06-22
Hey Guys, First post :)

Anyway.

Having had trouble installing ubuntu on my sisters steam powered laptop I finally managed to sort the computer out.

However, I hit a major problem when I discovered that it ignored the internet connection cable. At first this didn't seem to be a problem, as in theory an operating system should run without the internet. Anyway, first of, I wanted to install SciTE. So I tried using the install software, which didn't work because there was no internet. 

No problem I though, just download the source and install it like any other program... Apparently, its slightly hard to do that on ubuntu, according to [http://psychocats.net/ubuntu/installingsoftware ](http://psychocats.net/ubuntu/installingsoftware ) you have to add "aptitude", a program which required the internet. At this point, after fiddling around with more cable and a few other ideas I came here and gave up. 

How can you install software without the internet?

.|Simon

---

### Post by PartisanEntity on 2007-06-22
You could download the packages manually using a computer with internet connection from [http://packages.ubuntu.com](http://packages.ubuntu.com) However you would have to chase down the dependencies.

---

### Post by SimonM on 2007-06-22
Chase down the dependancies?

---

### Post by PartisanEntity on 2007-06-22
> **SimonM said:**
> Chase down the dependancies?

For example, if you were to manually download network-manager and try to install it in Ubuntu you would be notified that you need certain other files (dependencies), so you would have to go back to your internet-enabled machine and download them, and you would have to keep doing that until you have all the packages needed for network-manager for example.

Based on my own experience from when I was new to Ubuntu, in the case of network-manager you only need about 3-4 dependencies, but other applications might require more.

---

### Post by SimonM on 2007-06-22
So I should download network manager?

---

### Post by Phixion on 2007-06-22
Well, how would you get a program in Windows? Aside from either buying it or downloading it elsewhere there aren't many options without an internet connection.

---

### Post by PartisanEntity on 2007-06-22
Have you tried to type the following into the terminal while the ethernet cable was plugged in to the Ubuntu machine?

```
sudo dhclient
```

Sometimes it helps.

---

### Post by SimonM on 2007-06-22
I shall try that now - sorry about the thread issues

That worked, why do you have to  do that before it will connect?

---

### Post by PartisanEntity on 2007-06-22
Your computer needs to obtain a lease for an ip number from your router, the command I gave you requests the lease. Most of the time it happens automatically, but from time to time if it doesn't work right away one can help along a little. 

You can now use aptitude to install software if you like.

---

### Post by SimonM on 2007-06-22
Is there a way to ensure that the computer does that automatically?

And I will get onto aptitude now

OK... not sure if aptitude worked or not it came up with some errors but still said done

```

root@laptop:/# sudo aptitude update
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Ign http://archive.ubuntu.com breezy Release.gpg
Ign http://archive.ubuntu.com breezy Release
Ign http://archive.ubuntu.com breezy/universe Packages
Ign http://archive.ubuntu.com breezy/universe Packages
Ign http://archive.ubuntu.com breezy/universe Packages
Ign http://archive.ubuntu.com breezy/universe Packages
Ign http://archive.ubuntu.com breezy/universe Packages
Err http://archive.ubuntu.com breezy/universe Packages
  404 Not Found [IP: 91.189.89.6 80]
Err http://archive.ubuntu.com breezy/universe Packages
  404 Not Found [IP: 91.189.89.6 80]
Err http://archive.ubuntu.com breezy/universe Packages
  404 Not Found [IP: 91.189.89.6 80]
Err http://archive.ubuntu.com breezy/universe Packages
  404 Not Found [IP: 91.189.89.6 80]
Err http://archive.ubuntu.com breezy/universe Packages
  404 Not Found [IP: 91.189.89.6 80]
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
root@laptop:/# sudo aptitude install build-essential
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```

Did that work?

---

### Post by PartisanEntity on 2007-06-22
From my experience it should work from now on, I have only ever had to run that command the first time on certain machines.

---

### Post by SimonM on 2007-06-22
Right, haven't tried running make yet but I'm still having problems with installing programs the 'proper way'.

```

http://archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz: 404 Not Found [IP: 91.189.89.8 80]
http://gb.archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz: 404 Not Found
http://archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz: 404 Not Found [IP: 91.189.89.8 80]
http://archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz: 404 Not Found [IP: 91.189.89.8 80]
http://gb.archive.ubuntu.com/ubuntu/dists/breezy/main/binary-i386/Packages.gz: 404 Not Found
http://gb.archive.ubuntu.com/ubuntu/dists/breezy/restricted/binary-i386/Packages.gz: 404 Not Found
http://gb.archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz: 404 Not Found
http://archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz: 404 Not Found [IP: 91.189.89.8 80]
http://archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz: 404 Not Found [IP: 91.189.89.8 80]
http://archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz: 404 Not Found [IP: 91.189.89.8 80]

```

It doesn't like downloading them for some reason

---

### Post by YoG%*@ on 2007-06-22
hi there,

> **SimonM said:**
> Is there a way to ensure that the computer does that automatically?


can you post your /etc/network/interfaces file?

---

### Post by SimonM on 2007-06-22
Of course

```

root@laptop:/# cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0
root@laptop:/#

```

---

### Post by John.Michael.Kane on 2007-06-22
Looking at those errors it would seem your using breezy, and the repo is giving you 404 Not Found errors. 

It would help if we know just what kind of hardware your trying to install ubuntu on.

Can your try posting the output of the command below
```
ifconfig
```

Also have you tried dapper 6.06.1?

---

### Post by SimonM on 2007-06-22
I am installing it one a laptop which is in the region of pre-2002.

I will 

```

root@laptop:/# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:08:74:E3:6D:3D
          inet addr:192.168.0.8  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::208:74ff:fee3:6d3d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3593 errors:0 dropped:0 overruns:1 frame:0
          TX packets:3522 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000
          RX bytes:2586367 (2.4 MiB)  TX bytes:661127 (645.6 KiB)
          Interrupt:10 Base address:0x3000

lo        Link encap:Local Loopback
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:9591 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9591 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:874762 (854.2 KiB)  TX bytes:874762 (854.2 KiB)

sit0      Link encap:IPv6-in-IPv4
          inet6 addr: ::127.0.0.1/96 Scope:Unknown
          UP RUNNING NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:28 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

root@laptop:/#

```

I would update to Dapper, but unless there is a BitTorrent I doubt I could download it very quickly (are there upgrades anywhere?) Infact I would probably use the latest version, but at the moment I am using my friends shipit CD

---

### Post by YoG%*@ on 2007-06-22
> **SimonM said:**
> I would update to Dapper, but unless there is a BitTorrent I doubt I could download it very quickly (are there upgrades anywhere?) Infact I would probably use the latest version, but at the moment I am using my friends shipit CD

there's lots of linux torrents at [http://linuxtracker.org/]("http://linuxtracker.org/") - so if bittorrent is an/the only option for you to get a newer version of ubuntu try getting the torrent from there.

hth
mux

---

### Post by YoG%*@ on 2007-06-22
concerning the auto - dhcp, 
try putting something like
```

auto eth0
iface eth0 inet dhcp

```
in your /etc/network/interfaces.

---

### Post by SimonM on 2007-06-22
Adding the auto thing now... will use the Bittorrent site if my current attempt to download it fails. Whilst using this wired connection I am achieveing relatively high speeds

Where would you recommend adding those too lines?

---

### Post by sriram on 2007-06-22
hi ,
i was also an user without internet and i un derstand ur problem..
i found a solution for tat .
there is a tool called aptoncd which will make a synaptic based cd for the libraries for all te packages u download using apt-get..
u can ask ur friend to download tose and make the aptcd ..

---

### Post by SimonM on 2007-06-22
I have the internet on my desktop, its just this laptop which is being ghey. Have decided to download the latest version to see if that fixes the problem

---

### Post by YoG%*@ on 2007-06-22
> **SimonM said:**
> Adding the auto thing now... will use the Bittorrent site if my current attempt to download it fails. Whilst using this wired connection I am achieveing relatively high speeds

Where would you recommend adding those too lines?

just somewhere in the /etc/network/interfaces file.

---

