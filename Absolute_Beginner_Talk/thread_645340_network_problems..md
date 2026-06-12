---
title: "network problems."
date: 2007-12-19
forum: Absolute Beginner Talk
---

### Post by fenixfox on 2007-12-19
i can bring up google and a couple other sites but i cant access many other sites. Ive checked my router configuration and it is at default settings no ports blocked or anything blocked from the router. this computer is set up through the same router and it works fine. though it is running xp. i have tried putting in a static ip address of the router.

---

### Post by gilf on 2007-12-19
Check your security and other settings in firefox preferences

---

### Post by fenixfox on 2007-12-19
its set to direct connection.  warn if sites try to install addons, tell me if site is suspected of forgery, accept cookies from sites.

---

### Post by gilf on 2007-12-20
If you're getting Google it's a problem probably pretty high up the chain. Check your hosts file, Check any firewalls. Check for filtering. Make sure your router has the right DNS addresses. Probably other people can help better than I can. Maybe there are timeouts because something is slowing you down. Wish I could help more.

Can you try to hook up to another network at a friend's house or at work? If you can browse properly there, that might narrow it down to your router or router settings rather than the computer or installation..

---

### Post by fenixfox on 2007-12-20
no firewalls vigin install of unbuntu. hosts file? how do i check those? this computer is connected to the same router no problems here.

---

### Post by fenixfox on 2007-12-20
when i checknetwork device is set to loopback i think thats the problem. but when i chnge it to ethernet and close it then reopen it it goes back to loop

---

### Post by shadow-of-sin on 2007-12-20
What does your /etc/network/interfaces file look like? It should look like this:
```
auto eth0
iface eth0 inet dhcp
```

If it isn't, try changing it, remember to backup the file first:
```
sudo cp /etc/network/interfaces /etc/network/interfaces.backup
```

---

### Post by fenixfox on 2007-12-20
how do i do that?

---

### Post by shadow-of-sin on 2007-12-20
Open up the terminal (Applications-->Accessories-->Terminal) and then backup the file:
```
sudo cp /etc/network/interfaces /etc/network/interfaces.backup
```
Now open up the file in nano:
```
sudo nano /etc/network/interfaces
```
Now just change the contents to:
```
auto eth0
iface eth0 inet dhcp
```
Press Ctrl+X and then Enter to save and exit.
Now restart networking and see if it works:
```
sudo /etc/init.d/networking restart
```

---

### Post by fenixfox on 2007-12-20
ok heres my result 
litening on    lfp/eth0/00:01:xx xx xx xx
sending on   lfp/eth0/00:01:xx xx xx xx
sending on  socket/fallback
dhcprelease on eth0 to 192.168.1.1 port 67
there is already a pld file /war/run/dhclient.eth0.pld with pld 134519120
copyright 2004-2005 internet systems consortium.
all rights reserved.
for info please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

listening on lfp/eth0/00:01:xx:xx:xx
sending on  lpf/eth0/00:01:xx:xx:xx
sending on socket/fallback
dhcpdiscover on eth0 to 255.255.255.255 port 67 interval 6
ip length 314 disagrees with bytes recieved 534.
accepting packet with data after udp payload.
dhcp offer from 192.168.1.1
dhcprequest on eth0 to 255.255.255.255 port 67
ip length 314 disagrees with bytes recieved 534.
accepting packet with data after udp payload.
dhcpack 192.168.1.1 
bound to 192.168.1.2 -- renewal is in 38516 seconds.

---

### Post by shadow-of-sin on 2007-12-20
So do sites other than Google work now or is it the same as before?

---

### Post by fenixfox on 2007-12-20
so now i dont know what to do. any more ideas?

---

### Post by fenixfox on 2007-12-20
it was funny i got purple.com up google can find results but i cant connect to much else it makes no sense. like i try to go to java it says waiting for reply forever, it does the same with unbuntu website the unbuntuforums.org its confusing.

---

### Post by fenixfox on 2007-12-20
i think it is having a problem receiving. i just tried to connect to my router and it says tranferring data from   192.168.1.1 but nothing is happening.

---

### Post by Presto123 on 2007-12-20
Err...stupid question...but have you installed all the updates?

---

### Post by fenixfox on 2007-12-20
i tried but it says it cant connect

---

### Post by Presto123 on 2007-12-20
Now is it saying this in System/Administration/Update Manager ?

---

### Post by fenixfox on 2007-12-20
checked says up to date. i clicked for it to check again it says 
failed 0kb translation_us cdrom/ubuntu 7.10 gutsy gibbon release i386 (20071016)
failed 0kb translation_us cdrom/ubuntu 7.10 gutsy gibbon release i386 (20071016)
failed 0kb translation_us cdrom/ubuntu 7.10 gutsy gibbon release i386 (20071016)
doine 0b release  cdrom/ubuntu 7.10 gutsy gibbon release i386 (20071016)
done 191b release.gpg [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy release.gpg
failed 0b transmission en_us [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted translation-en_us
failed 0b release [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy release

---

### Post by Presto123 on 2007-12-20
Okay, thank you for that. ;)

You never know what those updates can fix. (I don't, anyway.)

Most of all I could suggest is to reset your router to factory in Windows, but this could cause more problems depending on your setup. 

With me, I messed around with my Linksys wireless router, but it just kept giving me problems. I reset it to factory, and haven't had problems with it since. Where this could be a problem can consist of several factors: if you need a static address, if you have to have the security (city/town). 

With my network, we have 2 routers so fixing the Linksys -being the second router- wouldn't cause harm to my internet connection.

This is probably a lot of babble that may not get you anywhere, but, eh, you never know.

---

### Post by fenixfox on 2007-12-20
it does the same thing with the router bypassed. it pulls a valid 73. ip when the routr is bypassed. modem the only changes on the router are wireless wep (its hardwired btw) and an admin password. all the other settings are factory. his omputer is onthe same rouer. i can access he uter from tis machine but nt on th other on  unbuntu.i can even access my gmail.

---

### Post by Presto123 on 2007-12-20
Well...you are past me on this one. I'm definitely not a network guru. I'm better at basic trouble shooting than this.

Good luck with it, though and don't give up on it! :)

---

### Post by shadow-of-sin on 2007-12-20
This may or may not help you but did you try and disable IPv6? You can find a guide here:
[http://www.simonscullion.com/2007/11/20/ipv6-issues-with-ubuntu-710/](http://www.simonscullion.com/2007/11/20/ipv6-issues-with-ubuntu-710/)

---

### Post by fenixfox on 2007-12-20
didnt do a thing thank you all for your suggestions though!

---

### Post by fenixfox on 2007-12-20
i can ping all the sites fine from the command prompt though. so it must be something with firefox.

---

### Post by shadow-of-sin on 2007-12-20
Ok, try disabling IPv6 in Firefox:
> Finally, with Mozilla browsers (Firefox or Suite), you can enter about:config in the address bar, locate the line starting with network.dns.disableIPv6 and change the value to true.
([http://ubuntuforums.org/showpost.php?p=27259&postcount=1](http://ubuntuforums.org/showpost.php?p=27259&postcount=1))

Also, does wget also work from the command line?

---

### Post by fenixfox on 2007-12-20
still nothing :/

---

### Post by fenixfox on 2007-12-20
doesnt seem to work. i went to command line and when i try to update from there it hangs up at 99%

---

### Post by fenixfox on 2007-12-20
eth0      Link encap:Ethernet  HWaddr 00:01:6C:F7:72:5F 
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask: 255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3989 errors:157 dropped:0 overruns:0 frame:157
          TX packets:3193 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:3022731 (2.8 MB)  TX bytes:847090 (827.2 KB)
          Interrupt:22 Base address:0xdead

if that helps. i dont know why im losing packet recieving. this computer is on the same router. it gives the same result directly connected to the modem too.

---

### Post by fenixfox on 2007-12-20
..

---

### Post by fenixfox on 2007-12-20
bump

---

### Post by fenixfox on 2007-12-20
bump

---

### Post by fenixfox on 2007-12-20
dont know if this will help

00:00.0 Host bridge: Silicon Integrated Systems [SiS] 761/M761 Host (rev 01)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS965 [MuTIOL Media IO] (rev 48)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] 191 Gigabit Ethernet Adapter
00:05.0 RAID bus controller: Silicon Integrated Systems [SiS] 182 SATA/RAID Controller (rev 01)
00:06.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:07.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:0a.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 46)
00:0b.0 Multimedia audio controller: Yamaha Corporation YMF-740C [DS-1L Audio Controller] (rev 03)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7600 GT] (rev a1)

---

### Post by gilf on 2007-12-20
I think modifying your interfaces file had nothing to do with your problem since you already could connect to Google.

I suggest you undo all of the changes so far and concentrate on high level problems, as I mentioned before.

One possibility as I already mentioned is your DNS setup.

To simplify what is meant by that:  DNS servers look up the address you type into Firefox and translate that into numerical addresses. If they are far away from you or slow, your web pages may time out.

If you want to change to an alternate pair of DNS servers, you might consider the following:

[https://www.opendns.com/start/ubuntu.php](https://www.opendns.com/start/ubuntu.php)

I would follow the instructions to try it out temporarily rather than make the change  permanent. Actually, their instructions seem more complicated than needed. In Gutsy,you can just click System>Administration>Network then DNS tab, then enter each of the following DNS entries **above** the existing entries (so they are tried first before your possibly slower ones):

208.67.222.222

208.67.220.220

If they don't work, and you didn't delete your old server addresses, just remove these two and you are back with your original setup.

here's another article on the same subject:

[http://ubuntu-tutorials.com/2007/03/14/how-to-setup-opendns-on-ubuntu/](http://ubuntu-tutorials.com/2007/03/14/how-to-setup-opendns-on-ubuntu/)

[COLOR="Red"]But I would definitely undo the recent  changes you made in this thread before you do this since your system is getting further and further from its initial state, without resolving your problem..[/COLOR]

---

