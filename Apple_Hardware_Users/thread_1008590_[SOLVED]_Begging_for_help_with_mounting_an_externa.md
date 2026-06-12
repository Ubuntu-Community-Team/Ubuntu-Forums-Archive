---
title: "[SOLVED] Begging for help with mounting an external hd"
date: 2008-12-11
forum: Apple Hardware Users
---

### Post by elyjet on 2008-12-11
Hi,
my macos crashed today. The applecare dudes werent able to help, told me to erase the whole damn HD. I tried the ubuntu 8.10 live-cd and was able to see all my data. Now im about to transfer them somewhere. The timecapsule (external hd) is already connected via ethernet cable. Regardless of spending hours of finding a solution I wasnt able to mount it.
Can someone help me please? 


Please newbe-language and thanks in advance.

---

### Post by wd5gnr on 2008-12-11
I am not up on the mac, but doesn't the time capsule have ethernet OR USB connection? If so, plug the USB cable in and I"m betting Ubuntu will detect it and mount it for you automatically.

---

### Post by elyjet on 2008-12-11
no usb cable

---

### Post by albinootje on 2008-12-11
Try this : [http://ubuntuforums.org/showthread.php?t=670535](http://ubuntuforums.org/showthread.php?t=670535)
The one from March 23rd, 2008 by user "ytene".

---

### Post by tiresia on 2008-12-11
Here I found what can help you. Maybe.
[http://ubuntuforums.org/archive/index.php/t-670535.html](http://ubuntuforums.org/archive/index.php/t-670535.html)
In this link they explaine how to mount the TimeCapsule in /etc/fstab (i.e. already when the computer starts). But for you should be enough tho use the command 'mount.cifs' 

Do you know the IP Address of your Time Capsule?

I don't have a TimeCapsule, but I think it should be quite easy to access it.
It should have an IP address that you assigned. You should be able to start your computer with the LiveCD and then connect to it. Maybe, you can even try going to Places>Connect to Server> Windows Share. There you can give the IP address, name of the folder you want to connect to, and password 

If you don't know the IP address, you can connect the Time Capsule with a Router.

---

### Post by elyjet on 2008-12-11
thx!

mount.cifs doesnt work because: "is currently not installed" / I typed "sudo apt-get install smbfs" (was recommended) but this failed to, no internet connection.

I got the IP-Adresse and the Router-Adresse!


some suggestions?

---

### Post by tiresia on 2008-12-11
I'm afraid that you need that package. Therefore you can connect via ethernet and try to install it.
But before doing this try that way I suggest you. I'm not sure that it will work, but you can try. You don't need the Router Adresse. 
Places>Connect to Server> Windows Share

---

### Post by elyjet on 2008-12-11
it says: "Cannot display location smb://..." No application is registered as handling this file

but managed to get it online. if the package is installed what exactly do I type?
sudo mount.cifs //192.168.1.20/"Tom Smith's Time Capsule"/tom /media/capsule -o pass=passw0rd

/"Tom Smith's Time Capsule"/ => my Capsules name plus or minus = ".."
/tom / => stands for ?


thanks a lot guys

---

### Post by tiresia on 2008-12-11
Ok, if you are going this way, let's try.

1.Make a mount point for the TC
```
sudo mkdir /media/capsule
```


2. If the IP Adress is 192.168.1.20, your name is Tom and the name of the TimeCapsule is TomsCapsule and the password it PWCapsule

```
sudo mount.cifs //192.168.1.20/TomsCapsule /media/capsule -o user=Tom,pass=PWCapsule
```

---

### Post by elyjet on 2008-12-11
alright, it says: mount error 113 = No route to host Refer to the mount.cifs( 8 ) manual page (e.g.man.mount.cifs)

and a second question, why the user name? TimeCapsule has no usernames and i started from the live-cd!?

but i really appreciate your effort / very important data on that MacBook

---

### Post by elyjet on 2008-12-11
i just tried the Router-Adresse and it gave me this: mount error 111 = Connection refused

---

### Post by tiresia on 2008-12-11
Ok, let's start again. TimeCapsule is after all just a NAS, that means an external HD that you can access via Ethernet. 
On the TimeCapsule you have a Folder to backup your data and a Passwort to access it.
When you configure your TimeCapsule you set a folder a user and a Password. Maybe the user name is the user name you use in MacOSX. Do you remember them?

---

### Post by elyjet on 2008-12-11
so, the folders name is: 42 
but I definitely did set up a user name, just a name for the TimeCapsule. There are some user and 2 computers as a total which access it. I just checked that with an special apple program on a other mac. I really checked everything you can check! any ideas?

But it takes a few seconds to say mount error 113 = no route to host

---

### Post by tiresia on 2008-12-11
If you made a 'usual' configuration of the Time Capsule with the Time Machine, the configuration could be like this:

EXAMPLE
If your User Name in MacOSX is Tom
"Tom's Time Capsule" is the main folder on the Time Machine  (without ""!)
"Tom" is the User Name you have in MacOSX
"PWCapsule" is the Password to access it

To mount it

1. Make a mount point
```
sudo mkdir /media/capsule
```

2. Mount it with the command 'mount.cifs' or like this
- try these four different solutions:

```
sudo mount -t cifs //192.168.0.20/"Tom's Time Capsule" /media/capsule -o user=Tom,pass=PWCapsule
```
# without username
```
sudo mount -t cifs //192.168.0.20/"Tom's Time Capsule" /media/capsule -o pass=PWCapsule
```
#adding a subdirectory
```
sudo mount -t cifs //192.168.0.20/"Tom's Time Capsule"/Tom /media/capsule -o user=Tom,pass=PWCapsule
```
```
sudo mount -t cifs //192.168.0.20/Tom's\ Time\ Capsule /media/capsule -o user=Tom,pass=PWCapsule
```
```
sudo mount -t cifs //192.168.0.20/Tom's\ Time\ Capsule/Tom /media/capsule -o user=Tom,pass=PWCapsule
```

---

### Post by elyjet on 2008-12-11
no TimeMichine, i never used it
just an external HD

---

### Post by tiresia on 2008-12-11
If you never used TimeMachine, it should be easier. Just to be sure, if you can access the Capsule from another Mac, can you please connect it to the other Mac, open a Terminal and tell me what you see if you run
```
ls /Volumes
```

---

### Post by elyjet on 2008-12-11
ls /volumes
=>
42
Macintosh Hd
The Sims 2 Bon Voyage.localized (my mom loves it)

the codes you gave me didnt work, I even copy pasted them.

---

### Post by tiresia on 2008-12-11
Make a mount point
```
sudo mkdir /media/capsule
```

You need a username, maybe you can find it with the other mac. It is the owner of /42. 
```
sudo mount -t cifs //192.168.1.20/42 /media/capsule -o user=Tom,pass=PWCapsule
```

---

### Post by tiresia on 2008-12-11
What do you get if you run just
```
sudo mount -t cifs //192.168.1.20/42 /media/capsule
```

What do you get if in the other Mac you run```
ls -l /Volumes
```

---

### Post by elyjet on 2008-12-11
ahhh, now i know what you meant. I read something in a discussion board on apple.com. you can secure Your HD with accounts, but also with just the TimeCapsule Password. I choosed the latter one, just TP-Password.

Im trying your code

---

### Post by elyjet on 2008-12-11
Ubuntu:
sudo mount -t cifs //192.168.1.20/42 /media/capsule

It asks me for the Password:
I entered it, but the same failure occurred: mount error 113 = No route to host


Leopard:
ls -l /Volumes
total 40
drwx------  14 irina  staff   432 25 Nov 09:18 42
lrwxr-xr-x   1 root   admin     1 10 Dez 21:26 Macintosh HD -> /
drwxr-xr-x@ 12 irina  staff   408 28 Nov  2007 The Sims 2 Bon Voyage.localized

---

### Post by tiresia on 2008-12-11
> **elyjet said:**
> Ubuntu:
sudo mount -t cifs //192.168.1.20/42 /media/capsule

It asks me for the Password:
I entered it, but the same failure occurred: mount error 113 = No route to host

Ok, I expected this, I wanted just to be sure that it's working
It looks that 'irina' can accesses '42'
```
sudo mount -t cifs //192.168.1.20/42 /media/capsule -o user=irina,pass=PWCapsule
```

P.S. When you are done with your backup, you should better change username. You shouldn't tell your private data on a public forum :)

---

### Post by elyjet on 2008-12-11
didnt work, the same failure: mount error 113 = No route to host

no problem about the private data. I alter every time the password and the Ip-Address. the pass and ip is from an other thread, I posted it as an example, because I didnt know what exactly to do with it.

---

### Post by tiresia on 2008-12-11
> **elyjet said:**
> didnt work, the same failure: mount error 113 = No route to host

It means that either the IP address is not correct either that you are not connect to the router.
Can you check the IP address with the other mac? Are you sure you are connected to the Network?
Or you can ping the TimeCapsule```
ping 192.168.0.20
```
ctrl-C to stop. What do you get?

---

### Post by elyjet on 2008-12-11
ok, that weird. I checked the Ip-Address of my TimeCapsule. It was always right. I pinged from ubuntu and it says: Destination Host Unreachable.

Its connected via ethernet cable. I just plug out and plug in one end between both computers!

I typed the same command in the Leopard Terminal and got data!

What does it mean?

---

### Post by tiresia on 2008-12-11
So, it is not the right IP. Do you have a Router? You could connect the TimeCapsule and your computer to the router. If you can access the router you should see the ip address.

What do you get here
```
route
```
```
ifconfig
```

---

### Post by elyjet on 2008-12-11
wait. I pinged from Ubuntu with "Network Tools" my Leopard with no result! Dont you think its the ethernetcard?

I checked the ip, the ip is good. I got it direct from the TimeCapsule. The IP-Address. I even tryed it with the Router-Address just to be sure

---

### Post by elyjet on 2008-12-11
ubuntu@ubuntu:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.0     *               255.255.255.0   U     2      0        0 eth1
link-local      *               255.255.0.0     U     1000   0        0 eth1
default         speedport.ip    0.0.0.0         UG    0      0        0 eth1


ubuntu@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:23:32:c3:d2:6e  
          inet6 addr: fe80::223:32ff:fec3:d26e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:449 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:135772 (135.7 KB)  TX bytes:1876 (1.8 KB)
          Interrupt:253 

eth1      Link encap:Ethernet  HWaddr 00:23:6c:82:88:01  
          inet addr:192.168.2.20  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::223:6cff:fe82:8801/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8910 errors:0 dropped:0 overruns:0 frame:2986
          TX packets:7008 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10278968 (10.2 MB)  TX bytes:1094068 (1.0 MB)
          Interrupt:23 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:526 errors:0 dropped:0 overruns:0 frame:0
          TX packets:526 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:42936 (42.9 KB)  TX bytes:42936 (42.9 KB)

yes, i have an other router, but i can access it only wireless

---

### Post by tiresia on 2008-12-11
I think, the easiest solutions
1.Restart the Computer with timecapsule. Or
2.Connect computer and TimeCapsule to a Router.
3.Do you have a FireWire cable? If you connect the two computers together and start the mac 'with problems' pressing the T-key, you can access the HardDisk (target modus).
Please, tell me, what do you get. Now I go to bed, but tomorrow I can help you.

---

### Post by elyjet on 2008-12-11
its the new macbook alu, no firewire.

ubuntu@ubuntu:~$ route
Kernel IP routing table
Destination Gateway Genmask Flags Metric Ref Use Iface
192.168.2.0 * 255.255.255.0 U 2 0 0 eth1

192.168.2.0 is my ubuntu ip, is that right? I pinged it with leopard and got no data

---

### Post by tiresia on 2008-12-11
What do you get from 'ping 192.168.2.0' from ubuntu

---

### Post by elyjet on 2008-12-11
I typed in ubuntu "route", as you told me, and got this data:

ubuntu@ubuntu:~$ route
Kernel IP routing table
Destination Gateway Genmask Flags Metric Ref Use Iface
192.168.2.0 * 255.255.255.0 U 2 0 0 eth1
link-local * 255.255.0.0 U 1000 0 0 eth1
default speedport.ip 0.0.0.0 UG 0 0 0 eth1

I connected Leopard and ubuntu via the same ethernet cable and ping from the leopard terminal: 192.168.2.0

---

### Post by elyjet on 2008-12-11
the update manager gives me 168 updates. Is it possible that i just dont have the right drivers, or something, i mean the macbook is really new. I would install them, but I still can access my internal drive only with the live-CD, all other things do not work.

---

### Post by tiresia on 2008-12-11
We are making confusion.
1. Please, check the IP Address of the TimeCapsule in the other MacOSX
2. You get the IP Address of Ubuntu with ifconfig (inet addr=)
3. In route you get the Kernel IP Table (if you have a router you can see its IP)

---

### Post by tiresia on 2008-12-11
> **elyjet said:**
> the update manager gives me 168 updates. Is it possible that i just dont have the right drivers, or something, i mean the macbook is really new. I would install them, but I still can access my internal drive only with the live-CD, all other things do not work.
Don't do it now. You need to backup you HD before. Ignore the update manager

---

### Post by elyjet on 2008-12-11
Both computers are accessing the same modem via wireless, in the moment. Can this be interfering?

Where can I find my ethernet card ip, I mean the eth0 (not eth1) / I pretty sure that something is wrong with my ubuntu ethernet-card. I would ping it from leopard in order to wipe out this possibility!

---

### Post by tiresia on 2008-12-11
> **elyjet said:**
> Both computers are accessing the same modem via wireless, in the moment. Can this be interfering?

Where can I find my ethernet card ip, I mean the eth0 (not eth1) / I pretty sure that something is wrong with my ubuntu ethernet-card. I would ping it from leopard in order to wipe out this possibility!

You see it in ifconfig. You don't have an IP via eth0 but via eth1.
I didn't know that you have a modem.
What you can do, beside the other suggestions, is to access the second Mac and copy your data there (you can enable it in System preferences).
In ubuntu you can access the mac osx internal hd starting nautilus with ```
gtksudo nautilus
``` 

As I told before, you should really check again the IP Address Of the TimeCapsule. We made some confusion. 
I must really go to sleep, let me know if you get it.

---

### Post by elyjet on 2008-12-11
me too, in germany we got 4:13 o'clock!

i know about gksudo nautilus but how can i transfer to the other computer?

I am pretty sure about the ip. IP-Address: 169.254.210.217
Mask: 255.255.255.0
Router-Address: 192.168.2.1

I can take a screen pic, but lets do that later on, im really tiered, tooooo.
Oh, I see you are from Berlin, we could have talked in german. ;-)

---

### Post by elyjet on 2008-12-12
up and about, but still wonder why ifconfig dont show me a inet addr: of my eth0. But "Auto eth0" goes on under Wired Network when I connect both computers!

If i ping from leopard my timecapsule i get data
if i ping from ubuntu i get no data

---

### Post by tiresia on 2008-12-12
Morgen! 
Can you please tell me the definitive IP Adresse of the TimeCapsule in MacOSX?

After that try following:
```
sudo ifdown eth1
sudo ifup eth0
ifconfig
```
What do you get?

---

### Post by elyjet on 2008-12-12
Morge! ;-) thx man

[IMG]http://img212.imageshack.us/img212/5403/testea3.jpg[/IMG]

I get this:
ubuntu@ubuntu:~$ sudo ifdown eth1
ifdown: interface eth1 not configured
ubuntu@ubuntu:~$ sudo ifup eth0
Ignoring unknown interface eth0=eth0.
ubuntu@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:23:32:c3:d2:6e  
          inet6 addr: fe80::223:32ff:fec3:d26e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:577 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:151213 (151.2 KB)  TX bytes:3606 (3.6 KB)
          Interrupt:253 

eth1      Link encap:Ethernet  HWaddr 00:23:6c:82:88:01  
          inet6 addr: fe80::223:6cff:fe82:8801/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:2046 errors:0 dropped:0 overruns:0 frame:3367
          TX packets:1830 errors:13 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2429460 (2.4 MB)  TX bytes:195827 (195.8 KB)
          Interrupt:23 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:343 errors:0 dropped:0 overruns:0 frame:0
          TX packets:343 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:22736 (22.7 KB)  TX bytes:22736 (22.7 KB)

---

### Post by tiresia on 2008-12-12
What do you see in the GNOME Menu:
System > Administration > Network

---

### Post by elyjet on 2008-12-12
you mean network tools?
Devices> Ethernet Interface (eth0): Interface Information like: Hardware address / Multicast / MTU / Link speed / State => all not available

---

### Post by tiresia on 2008-12-12
Ok, forget it.
```
netstat -i
```
What is the image you send me? The IP of the Time Capsule?

---

### Post by elyjet on 2008-12-12
yes, direkt form TimeCapsule

[HTML][SIZE="1"]ubuntu@ubuntu:~$ netstat -i
Kernel Interface table
Iface   MTU Met   RX-OK RX-ERR RX-DRP RX-OVR    TX-OK TX-ERR TX-DRP TX-OVR Flg
eth0       1500 0       687      0      0 0            15      0      0      0 BMRU
eth1       1500 0      4264      0      0 0          3527     13      0      0 BMRU
lo        16436 0       399      0      0 0           399      0      0      0 LRU[/SIZE][/HTML]

---

### Post by tiresia on 2008-12-12
Ok, last information I need - actually it is quite simple.
You can see it in gnome. In the Panel right, close to the Date & Time you have an Icon with two computers. If you select it with the right button you can gather the Network Information. Can you please make a screenshot and send it to me?

---

### Post by elyjet on 2008-12-12
no problem, how to do a screenshot?

---

### Post by tiresia on 2008-12-12
Applications>Accesories>Take Screenshot

---

### Post by elyjet on 2008-12-12
[IMG]http://i36.tinypic.com/sxj8zc.png[/IMG]

i hope its the right on, got only connection information. Ubuntu is connected to a modem via wireless right now.

---

### Post by tiresia on 2008-12-12
Ok, please, don't change anything right now. 
What do you get if you do```
ping 169.254.210.217
```
ctrl-C to stop it

---

### Post by elyjet on 2008-12-12
ubuntu says: Destination Host Unrechable

just to let you know. ubuntu is connected to TimeCupsel via ethernet.
Both computers (ubuntu / Leopard) are connected to cupofcoffee (modem) wireless

---

### Post by elyjet on 2008-12-12
ubuntu@ubuntu:~$ ping 169.254.210.217
PING 169.254.210.217 (169.254.210.217) 56(84) bytes of data.
From 192.168.2.20 icmp_seq=1 Destination Host Unreachable
From 192.168.2.20 icmp_seq=2 Destination Host Unreachable
From 192.168.2.20 icmp_seq=3 Destination Host Unreachable

but if I disable the wireless connection, this comes along:
ubuntu@ubuntu:~$ ping 169.254.210.217
connect: Network is unreachable

seems like ubuntu tries to ping over wireless

---

### Post by tiresia on 2008-12-12
The situation right now is:
Router Address(your modem cupofcoffee): 192.168.2.1
**Ubuntu IP Address (eth1 - wireless): 192.168.2.20**
MacOSX: ?
...
The Screenshot you send me of TimeCapsule shows:
Router Address: 192.168.2.1 (the same as above)
**TimeCapsule Address: 169.254.210.217**

The TimeCapsule Address is not correct.
It looks like the Router for Time Capsule is the same as for Ubuntu.
Can't the Time Capsule have a wireless connection? If so, disconnect it from Ubuntu (the cable). 
Can you connect via Browser to the Modem cupofcoffe and sees if it see the Time Capsule?

---

### Post by elyjet on 2008-12-12
yes, i never disabled TimeCapsule Wireless ability. should i do it?

Router Address(your modem cupofcoffee): 192.168.2.1
Ubuntu IP Address (eth1 - wireless): 192.168.2.20
MacOSX: AirPort IP: 192.168.2.23

just taken:
[IMG]http://img265.imageshack.us/img265/2924/bild6sy8.jpg[/IMG]

---

### Post by tiresia on 2008-12-12
No, you should disconnect the ethernet cable from Ubuntu

---

### Post by elyjet on 2008-12-12
done

I can connect to TimeCapsule via wireless

---

### Post by tiresia on 2008-12-12
I must go out. I'm back in a couple of hours. 
Now you need to check the IP Address of the TimeCapsule, when it is connected wireless to the modem (and not connected to anycomputer!)
Can you access your Modem with a webbrowser (open a Browser and digit in the address 192.168.2.1)

---

### Post by elyjet on 2008-12-12
sure, i can access modem and TimeCapsule over my Browser. 

This is the pic of TimeCapsule without any cable connections, only wireless
[IMG]http://img265.imageshack.us/img265/2924/bild6sy8.jpg[/IMG]

---

### Post by tiresia on 2008-12-12
Can you please try to 'ping 169.254.210.217' from Ubuntu and from Mac

---

### Post by elyjet on 2008-12-12
leopard is getting data when I ping 169.254.210.217, while connected to TimeCapsule

ubuntu doesnt connect to TimeCapsule at all

---

### Post by tiresia on 2008-12-12
Can Ubuntu do
'ping [www.google.com](www.google.com)'

---

### Post by elyjet on 2008-12-12
jup, while connected to cupofcoffee (modem, not TimeCapsule)

I dont know why but ubuntu cant connect to TimeCapsule at all, not via cable nor wireless

---

### Post by tiresia on 2008-12-12
Ok, but can you open Firefox and connect to google or any web site?

---

### Post by elyjet on 2008-12-12
yes, connected to the modem i can access any site!

---

### Post by elyjet on 2008-12-12
I have no clue why ubuntu wont access TimeCapsule, the password is right, no mac-filtering, compatible with any wireless standarts. I can even see from leopard, while connected to Timecapsule, that ubuntu tries to connect to TimeCapsule! but the connection fails always.

---

### Post by tiresia on 2008-12-12
And can you 'ping 192.168.2.23'
It should be the ip address of the mac.
&#8230;&#8230;&#8230;
So if I understand, you have two macs, the time capsule, a modem, and the airport?
In a couple of hours I am back

---

### Post by elyjet on 2008-12-12
yes, pinging the leopard system works!

And right, thats the hardware

---

### Post by elyjet on 2008-12-12
Just an alternativ, could my 8GB Ipod be an solution?

---

### Post by tiresia on 2008-12-12
Hi, I'm back. No, we don't need the iPod.
The easiest solution is to connect to the MacOSX, and upload there everything you want. 
But I would like to understand why you can't connect to the TimeCapsule.
&#8230;&#8230;&#8230;&#8230;&#8230;
Before trying that way, just a last question:
what does it happen, when you ping from MacOSX the Time Capsule
in Mac OSX Terminal 'ping 169.254.210.217'

You haven't told me that you have an airport.
You have actually a local network, with the modem as Router that assignes IP Addresses via DHCP', and a 'second local network' with the Airport.
Or what?

---

### Post by elyjet on 2008-12-12
Hi :-)

Lets do this!

There are two routers online right now. A Modem, which ist online and accessable for both machines (ubuntu / leopard). And the TimeCapsule, which is only accessable for leopard (ubuntu could not access it, neither over ethernet nor wireless).

Modem:          cupofcoffee (only wireless, hangs in the cellar)
Timecapsule: potofcoffee (stands in front of both computers)

Both routers are not connected to each other. So, if i connect leopard to Timecapsule i get data from pining, I see also all data, over ethernet and wireless.

and sorry for the misunderstanding, or thin info.

---

### Post by elyjet on 2008-12-12
computer to computer network via wireless, would not be a good idea, would it?

---

### Post by tiresia on 2008-12-12
Ok, may be I understood. 
Most probably the TimeCapsule gets its IP from the Airport (which kind of Airport do you have?). 
But this second 'subnetwork' is closed. You need to start in MacOSX (do you have Leopard?) the Apple Airport Utility (Airport Dienstprogramm) and in File Sharing to allow connections from outside.

---

### Post by elyjet on 2008-12-12
You distinguish Airport and TimeCapsule, It is one machine (maybe i dont get it). The second network: cupofcoffee connects both machines. They are connected over a modem, not over the Timemachine.
Yes Leopard
File Sharing is on, 
Apple Airport Utility cant connect TimeCapsule over the modem(cupofcoffe).

---

### Post by tiresia on 2008-12-12
Ok, I understood that you have an Airport (Airport is not TimeCapsule).
Anyway if you open the Aiport Utility (Airport Dienstpromgramm) you can see an Icon with Laufwerk - I think there you can make the TimeCapsule accesible for other computers. If you can't we try connecting the two computers.

---

### Post by tiresia on 2008-12-12
**Accessing from the Ubuntu LiveCD MacOSX on the second computer**

**In MacOSX**
System Preferences (Systemeinstellungen) > Sharing
Check > File Sharing 
*in German*
Freigegebene Ordner
> Optionen (Right Down)
Check > Dateien und Ordner über SMB bereitstellen
Check > Your name and choose a Password

**In Ubuntu**
Places > Connect to Server> Service Type: Windows Share
Server: 192.168.2.23
User Name: Your Name (as above!)
When you are asked for your Password, give the password you choose in MacOSX (as above!) 
Now you should see the 'Freigegebene Ordner'

---

### Post by elyjet on 2008-12-12
Allright, I checked everything, i even disabeled any passwords. I did that with the Airport-Utility witch is only managing the TimeCapsule. It means that i have no internet in the meantime. Ubuntu does not connect to my TimeCapsule (potofcoffe - Network)

---

### Post by elyjet on 2008-12-12
So again, ubuntu is not able to connect in any way TimeCaspule (potofcoffee-Network). Both can connect to the modem (cupofcoffee-Network). I enabled smb connection on leopard. As I reconnect to the modem (cupofcoffee-Network) ubuntu showed me the leopard-machine. If i double click the leopard-machine ubuntu says: Unable to mount location   Invalid reply.
smb connection vie "Windows Share" didnt work it say: Cannot display location "smb://192.168.2.23/"    No application is registered as handling this file.

---

### Post by tiresia on 2008-12-12
I guess that if you connect everything as it was before, and  do 'ping 192.168.2.1' it should at least work...

---

### Post by elyjet on 2008-12-12
pinging from ubuntu to 192.168.2.23 works fine

but the Windows Share doesnt work at all, it seems like the program do not even try to connect, it just pop and says: No application is registered as handling this file.

---

### Post by tiresia on 2008-12-12
Yes, but you should try to ping from ubuntu to 192.168.2.1 (its router)

---

### Post by elyjet on 2008-12-12
oh, im sorry, that works too.

---

### Post by elyjet on 2008-12-12
PING 191.168.2.1 (191.163.2.1) 56(84) bytes of data.
64 bytes from 191.163.2.1: icmp_seq=1 ttl=255 time=8.98 ms
64 bytes from 191.163.2.1: icmp_seq=2 ttl=255 time=3.76 ms
64 bytes from 191.163.2.1: icmp_seq=3 ttl=255 time=3.66 ms
64 bytes from 191.163.2.1: icmp_seq=4 ttl=255 time=3.91 ms
64 bytes from 191.163.2.1: icmp_seq=5 ttl=255 time=3.87 ms
64 bytes from 191.163.2.1: icmp_seq=6 ttl=255 time=4.06 ms

---

### Post by elyjet on 2008-12-12
[https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/209520](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/209520)
[http://www.mail-archive.com/ubuntu-server-bugs@lists.ubuntu.com/msg06608.html](http://www.mail-archive.com/ubuntu-server-bugs@lists.ubuntu.com/msg06608.html)

I read here that this could be a bug, is that possible?

---

### Post by tiresia on 2008-12-12
No, I don't think.
Can you please try now

Make a mount point
```
sudo mkdir /media/capsule
```

You need a username (here a used Tom - replace it with yours). 
It is the owner of /42. Use the Password you use for accessing the Capsule (replace PWCapsule)

```
sudo mount -t cifs //192.168.2.1/42 /media/capsule -o user=Tom,pass=PWCapsule
```[/CODE]

---

### Post by elyjet on 2008-12-12
sudo mount -t cifs //191.163.2.1/42
why the 42? It was the name of timecapsule. Right know they are connected via modem. Ubuntu cant access timecapsule 42=potofcoffee

---

### Post by elyjet on 2008-12-12
I think we are confusing the networks!
TimeCapsule is Airport-Extreme, a Router without a modem: Ubuntu can not access it in any way. This network is called: potofcoffee

modem is and router and modem: Both machines can access it. This network is called: cupofcoffee

---

### Post by elyjet on 2008-12-12
I got it! I connect TimeCapsule with an ethernet cable to the modem and mount it from ubuntu

---

### Post by elyjet on 2008-12-12
I can copy files to my timecapsule, but i cant copy files from the nautilus window. it says Error while copying. The file *** cannot be handled because you do not have permissions to read it! can you help me?

---

### Post by tiresia on 2008-12-12
Yes, I understand this. 
The question is: the Modem is connected to Internet. The Time Capsule works as Router for MacOSX and for Ubuntu (via dhcp). 
It means that the Router Address 192.168.2.1 (that you see in Ubuntu and in MacOSX) is the IP Address of the Time Capsule for the Local network. 
Can it be that the IP Address 169.254.210.217 is the IP Address that the TimeCapsule gets from the Modem.
Therefore can you please try that command I told you before?

---

### Post by elyjet on 2008-12-12
the modem works as a router, too.

No thats not possible. Both of them are routers. And they were not connected in any way. Both separated Networks.

but hey, your cammand worked: sudo mount -t cifs //192.168.2.1/42 /media/capsule -o user=Tom,pass=PWCapsule
I only changed the ip into the IP of the TimeCapsule: 169.254.210.217 
and
I only connected TimeCapsule with the ethernet cable to the modem (which is a router too, and which connects both computers)

---

### Post by tiresia on 2008-12-12
> **elyjet said:**
> I can copy files to my timecapsule, but i cant copy files from the nautilus window. it says Error while copying. The file *** cannot be handled because you do not have permissions to read it! can you help me?
You need root privileges. Do not open Nautilus just selecting it. 
Use```
gksudo Nautilus
```

---

### Post by elyjet on 2008-12-12
:confused:

how? Im a new-be

you mean i can only copy files via command line?

I mean there is a lot of data!

---

### Post by tiresia on 2008-12-12
Well, you should trust me a bit more :p
When you run that command in the Terminal in Ubuntu, Nautilus will open and you can use it as always but you can also access files, that without root privileges usually you don't see

---

### Post by elyjet on 2008-12-12
I do, I do. but nothing happen, at the bottom of my display pops up something, says: Starting Administrativ... . But thats it. Nothing happened.

I can however open a window with: alt + F2. If I type in the gksudo Nautilus command, a window opens. but if want to copy something from this windows somewhere it blocks and says: Error while copying. The file *** cannot be handled because you do not have permissions to read it!





Okey foget it, I dont know what happend, i thing i write nautilus in small letter instate: Nautilus. It works. Im copying!

---

### Post by elyjet on 2008-12-12
man, Im happy. How can I thank you?

---

### Post by tiresia on 2008-12-12
Great! Let me know when you are ready with your backup.

---

### Post by elyjet on 2008-12-12
it should be done tomorrow. One question. Do I have to use bootcamp in order to install on a second partition ubuntu? I hate bootcamp.

---

### Post by elyjet on 2008-12-12
i dont know what happened, but it doesn work again: Error while copying. The folder *** cannot be handled because you do not have permissions to read it.

but i can read it, i can open it.

---

### Post by elyjet on 2008-12-12
ubuntu@ubuntu:~$ gksudo nautilus
seahorse nautilus module initialized
Initializing nautilus-share extension

** (nautilus:22846): WARNING **: Unable to add monitor: Operation not supported
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

---

### Post by tiresia on 2008-12-12
Can you please tell me what you get from
```
ls -l /media
```

---

### Post by elyjet on 2008-12-12
hi,
I restarted the machine and worked for about 600MB, Than an Error window poped up: Error while copying"Create Event from Message\cE" There was an error copying the file into /media/capsule/documents/Microsoft User Data/Entourage Script Menu items

now the copy process stopped entirely.

---

### Post by elyjet on 2008-12-12
ubuntu@ubuntu:~$ ls -1 /media
capsule
Macintosh HD
ubuntu@ubuntu:~$ 


and this happened by gksudo nautilus:

ubuntu@ubuntu:~$ gksudo nautilus
Initializing nautilus-share extension
seahorse nautilus module initialized
** (nautilus:8174): WARNING **: Unable to add monitor: Operation not supported
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

---

### Post by tiresia on 2008-12-12
I asked to run 'ls -l /media' 
(they are always letters not numers - it is not 'one' )
Anyway it is more reliable to copy smaller files or small directories - not just very big directory.
If you want you can copy using a command line.
So you can see all your files
```
ls /media/Macintosh\ HD/Users/yourname
```
To copy a file that is on the Desktop
```
sudo cp /media/Macintosh\ HD/Users/yourname/Desktop/nameothefile /media/capsule  
```
To copy a directory (a folder) use the option **-r **
```
sudo cp -r /media/Macintosh\ HD/Users/yourname/Desktop/nameofthefolder /media/capsule  
```

---

### Post by elyjet on 2008-12-12
****, sorry man.
ls -l /media:
ubuntu@ubuntu:~$ ls -l /media
total 0
drwxrwxrwx 1 root root  0 2008-12-12 22:02 capsule
drwxrwxr-t 1 root   80 38 2008-10-29 13:53 Macintosh HD
ubuntu@ubuntu:~$

command line is pretty complicate, because there are many files, and i dont want copy them all. Is there a other way?

---

### Post by tiresia on 2008-12-12
It's OK. You should be able to copy your files. 
I would try those commands - at the beginning can look a bit difficult but you will get used to them
You don't need to rewrite always the same line. You can use the arrows keys (up to go back) or you can change directory to the place where you have more file. If you have a lot of files in Movies:
```
cd /media/Macintosh\ HD/Users/yourname/Movies
```
Now you are in that directory, and if you do 'ls' you will see all your movies

---

### Post by elyjet on 2008-12-12
allright, thank you man, a lot. That helps.

Im not used to this system. 2 Phases: ls to look out and cp to copy

cd is just to hang around somewhere, to list the files for instance.

---

### Post by elyjet on 2008-12-12
.

---

### Post by cyberdork33 on 2008-12-12
> **elyjet said:**
> allright, thank you man, a lot. That helps.

Im not used to this system. 2 Phases: ls to look out and cp to copy

cd is just to hang around somewhere, to list the files for instance.
cd = change directory

---

### Post by elyjet on 2008-12-13
Everything baked-up,

Thx again, a lot.

---

### Post by cyberdork33 on 2008-12-13
> **elyjet said:**
> Everything baked-up,

Thx again, a lot.

If everything is working, please mark this thread as solved from the thread tools menu at the top of the page.

---

