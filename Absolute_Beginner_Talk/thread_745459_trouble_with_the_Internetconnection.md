---
title: "trouble with the Internetconnection"
date: 2008-04-04
forum: Absolute Beginner Talk
---

### Post by JokkeW on 2008-04-04
Hi there!
I just installed Ubuntu 7.10 yesterday and I've been trying to fix two things, which is to install the newest release of Elisa and to get a working internetconnection. So far, I've failed both of these goals, since internet isn't working as it should. The funny thing is, it's working if i run windows on the other partition, but not when i'm trying the same thing with ubuntu. I've been messing around with the different available settings, but I really can't find a sollution. Something i should tell you is that it actually works to ping different domainnames. Downloading an updated list in the "Add/Remove" application is not possible.

Answer fast, I want to get this running, i'm quite excited about this whole linux thing :)

---

### Post by northern lights on 2008-04-04
Do you have a wired or wireless connection?

Can you post the outputs of ```
lspci | grep Network
``` and ```
lspci | grep Ethernet
```In case you don't get results, just post ```
lspci
```

---

### Post by JokkeW on 2008-04-05
i've got an wired connection. i really couldn't figure out how to do that symbol you're using between "lspci" and "grep" so I've only got the answers for the regular lspci.

```
00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 0e)
00:01.0 PCI bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL PCI Express Root Port (rev 0e)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FR/FRW (ICH6R/ICH6RW) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc R480 [Radeon X800 GTO (PCIE)]
01:00.1 Display controller: ATI Technologies Inc R480 [Radeon X800 GTO (PCIE)] (Secondary)
02:09.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 61)
02:0a.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
02:0b.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 13)
```

---

### Post by tehkain on 2008-04-05
This '|' is a pipe and  it is found on your \ button. He is using grep to filter the results using the pipe(which sends the results to grep)

---

### Post by JokkeW on 2008-04-05
Oh, soo that's what it does. Here's my result for "lscip | grep ethernet".
```
02:0b.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 13)
```

---

### Post by ugm6hr on 2008-04-05
Some more info:
```
lshw -C network
ifconfig
route -n
```

How do you connect - router-modem or ethernet modem?

---

### Post by northern lights on 2008-04-05
Yup. You got it. Given your entire lspci output, the latter post was sort of predictable. ;-)

The problem lies in the fact, that there ain't no wireless controller listed. That's weird, since you're saying you should have one.

Sorry to ask, but are sure you have a wireless adapter?
Is this a desktop or a laptop machine?
If it's a desktop, can you check whether it's well fastened in a PCI socket?

[EDIT]late. lshw good idea to post the output of also...[/EDIT]

---

### Post by JokkeW on 2008-04-05
Results:
```
w@wimmerstedt-mediadator:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:30:1B:B9:D9:18  
          inet addr:192.168.1.109  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::230:1bff:feb9:d918/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2167 errors:0 dropped:0 overruns:0 frame:0
          TX packets:532 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:915117 (893.6 KB)  TX bytes:43808 (42.7 KB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

w@wimmerstedt-mediadator:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 eth0
w@wimmerstedt-mediadator:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 88E8001 Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: b
       bus info: pci@0000:02:0b.0
       logical name: eth0
       version: 13
       serial: 00:30:1b:b9:d9:18
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=skge driverversion=1.11 firmware=N/A ip=192.168.1.109 latency=32 maxlatency=31 mingnt=23 module=skge multicast=yes
```


We're connected to internet through a ADSL-router type D-LINK DSL-504T. I'm not sure if that's either of...

---

### Post by JokkeW on 2008-04-05
I didn't say anything about a wireless adapter, i said I was on a wired connection!

EDIT: Forgot to mention that it's a desktop computer, not a laptop. I don't think that there's any problem in the PCI socket, since internet works just fine when i'm booting windows instead for ubuntu.
EDIT2: Man, i spell bad.

---

### Post by ugm6hr on 2008-04-05
> Something i should tell you is that it actually works to ping different domainnames

Missed that before.

And the outputs from those commands tell me:

1. Driver installed for ethernet
2. You are assigned IP by router

So - can you visit different domain names from Firefox?

Let's try something:
```
ping www.google.com
ping 66.249.91.104

```

---

### Post by JokkeW on 2008-04-05
Ping works just great. Visiting different domainnames with firefox is a little worse, since it's not working.
If i write "google.com" forexample, it's just like "Firefox can't establish a connection to the server at www.google.com.".

Do you guys have any idea about what's wrong?

---

### Post by ugm6hr on 2008-04-05
Go here in Firefox:
[http://66.249.91.104/](http://66.249.91.104/)

---

### Post by JokkeW on 2008-04-05
Yes, that's working!

---

### Post by northern lights on 2008-04-05
> **JokkeW said:**
> I didn't say anything about a wireless adapter, i said I was on a wired connection!

That's what I had missed. Now obviously the PCI question is rendered useless.

I'm a bit dumbfounded now. If it's working under another OS or on another comp, it points to your Linux OS. Have u somehow shot your browser maybe? Tried a different one? Then again, updates didn't work either?

Screw it, I'm out of ideas...

[EDIT]
What? It just can't resolve the URL? Funny.
[/EDIT]

---

### Post by JokkeW on 2008-04-05
> **northern lights said:**
> That's what I had missed. Now obviously the PCI question is rendered useless.

I'm a bit dumbfounded now. If it's working under another OS or on another comp, it points to your Linux OS. Have u somehow shot your browser maybe? Tried a different one? Then again, updates didn't work either?

Screw it, I'm out of ideas...

Don't be sad, i'm quite happy that you tried to help. I guess that it's firefox who is screwing with me, but i can't really go and download another browser since i don't know how to do that now.

---

### Post by ugm6hr on 2008-04-05
This is an ipv6 issue.

I'll try and find the solution for you - but you might be able to google just as quick now ;)

---

### Post by JokkeW on 2008-04-05
I'll try on my own too, but I'd appreciate if you helped me :)

---

### Post by ugm6hr on 2008-04-05
2 possible solutions given here:
[http://ubuntuforums.org/showthread.php?t=87798&page=14](http://ubuntuforums.org/showthread.php?t=87798&page=14) (post 131 & 133)

---

### Post by JokkeW on 2008-04-05
It's working now. Thank you! :)

---

### Post by ugm6hr on 2008-04-05
Hang on....  Those are possible solutions.... but...

You can resolve addresses from Terminal, but not Firefox?  Maybe it is just a Firefox issue?

Can you use Synaptic Package Manager?

If it is only Firefox with the problem - then this might solve it more easily: [http://en.opensuse.org/Disable_IPv6_for_Firefox](http://en.opensuse.org/Disable_IPv6_for_Firefox)

---

### Post by ugm6hr on 2008-04-05
> **JokkeW said:**
> It's working now. Thank you! :)

Maybe post in the thread to say which worked for you?

And mark solved (in Thread Tools menu).

And welcome to the internet in Ubuntu :)

---

### Post by JokkeW on 2008-04-05
I can use firefox now, but Synaptic Doesn't appear to be working :(

---

