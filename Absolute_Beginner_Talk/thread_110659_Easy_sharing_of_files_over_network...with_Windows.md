---
title: "Easy sharing of files over network...with Windows"
date: 2005-12-31
forum: Absolute Beginner Talk
---

### Post by psaulnier on 2005-12-31
Basically all I'm trying to do is transfer some very large files (too large for usb flash drive or CD-R) to a Windows computer. The two are connected with a crossover cable (which I must say is very usefull for sharing an Internet connection without going through the trouble of buying a router). Now, on the Windows machine my Ubuntu computer is listed in Mshome as "<computer name> server (Samba, Ubuntu) (<computer name>)". I try to access it in Windows, but entering my username and password has no effect.

All I want is an easy way to transfer files over the network without the trouble of using the command prompt. What's the easiest way?

---

### Post by cwaldbieser on 2005-12-31
[QUOTE=psaulnier]Basically all I'm trying to do is transfer some very large files (too large for usb flash drive or CD-R) to a Windows computer. The two are connected with a crossover cable (which I must say is very usefull for sharing an Internet connection without going through the trouble of buying a router). Now, on the Windows machine my Ubuntu computer is listed in Mshome as "<computer name> server (Samba, Ubuntu) (<computer name>)". I try to access it in Windows, but entering my username and password has no effect.

All I want is an easy way to transfer files over the network without the trouble of using the command prompt. What's the easiest way?[/QUOTE]

On the XP box, share the folder that has the files you want to copy.  Then in Ubuntu, open nautilus and type this URL into the location bar:

SMB://XP-Computer-IP-Address/share-name

where "XP-Computer-IP-Address" is the IP address of your XP computer and "share-name" is the name of the share folder.

It helps if the share name does not have a space in it.

---

### Post by psaulnier on 2005-12-31
Hmm, that's not exactly how I thought of doing it, but it worked okay. You see, I'm transferring from the Ubuntu computer *to* the Windows one, but a simple copy-paste did the job (I thought Linux couldn't write to NTFS, though?).

But a 1.3 GB file shouldn't take five hours to transfer, should it? I mean, I could probably download a file that large off the Internet quicker than that.

---

### Post by cwaldbieser on 2005-12-31
[QUOTE=psaulnier]Hmm, that's not exactly how I thought of doing it, but it worked okay. You see, I'm transferring from the Ubuntu computer *to* the Windows one, but a simple copy-paste did the job (I thought Linux couldn't write to NTFS, though?).

But a 1.3 GB file shouldn't take five hours to transfer, should it? I mean, I could probably download a file that large off the Internet quicker than that.[/QUOTE]

This is not an issue of Linux writing to NTFS, but a lot of people get confused about that.  Any Windows PC that supports file sharing is actually running a server that speaks Microsoft's SMB file sharing protocol.  So Ubuntu just speaks that protocol and the server (on your Windows XP box) actually takes the data and writes it to the NTFS filesystem.

WinXP can't write to an ext3 file system natively, either, so if you had the reverse setup where Ubuntu is running an SMB server (samba), Windows would talk to the server, and Ubuntu would write the data to ext3.

The reason I opted for the other way around, is that a samba server is not installed by default with Ubuntu, and configuration usually takes a couple minutes at the command line, or you use SWAT, etc.

I would not think the transfer should take 5 hours-- is that how long nautilus is telling you it will take?  That seems excessive for a crossover cable connection.

---

### Post by psaulnier on 2005-12-31
[QUOTE=cwaldbieser]I would not think the transfer should take 5 hours-- is that how long nautilus is telling you it will take?[/QUOTE]
Exactly. And the countdown isn't really consistent either, which has me worried.
[QUOTE=cwaldbieser]That seems excessive for a crossover cable connection.[/QUOTE]
I was thinking the same thing; I've transferred files over a network with Windows at much faster speeds. Is there something in particular that would cause the transfer speed to be so slow?

---

### Post by cwaldbieser on 2005-12-31
[QUOTE=psaulnier]Exactly. And the countdown isn't really consistent either, which has me worried.

I was thinking the same thing; I've transferred files over a network with Windows at much faster speeds. Is there something in particular that would cause the transfer speed to be so slow?[/QUOTE]
The only thing that comes to mind would be that the NIC was somehow configured oddly?

There should be a "Networking Tools" application somewhere on the menu, I think (I am in Kubuntu right now, so I forget the menu).  There should be two tabs accross the top-- one for ping and one for traceroute.  Try using those to ping your WinXP PC, and see if the times seem off.

Also, you might check to see if you are running interference with a firewall on either PC.

The last thing I can think of would be that maybe some more advanced NIC setting is out of whack.  From the Terminal application, if you type in:
```

$ ifconfig

```
You should get a couple paragraphs describing the status of your network cards.  Here is mine, for example:
```

$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:07:E9:56:1C:AD  
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::207:e9ff:fe56:1cad/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:32186 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28042 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:38995354 (37.1 MiB)  TX bytes:4307336 (4.1 MiB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:33 errors:0 dropped:0 overruns:0 frame:0
          TX packets:33 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1703 (1.6 KiB)  TX bytes:1703 (1.6 KiB)

```
The eth0 card is my network card, and the relevant statistics are MTU (maximum transfer unit-- about 1500 is normal), RX packets and errors (no errors is good), and TX packets and errors (0 errors is good).  If you see you have a very low MTU or high numbers of errors, that could be the problem.

---

### Post by Bigdeath on 2007-09-11
I tried this and It keeps saying cannot display folder contents.

---

