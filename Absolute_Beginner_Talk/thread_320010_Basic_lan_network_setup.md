---
title: "Basic lan network setup"
date: 2006-12-16
forum: Absolute Beginner Talk
---

### Post by DrMega on 2006-12-16
Hi all.

I'm a recent convert to Ubuntu, having worked with Windows for years. I'm not an expert in either linux or networking, so please forgive me if this sounds really dumb.

I've been using Ubuntu for a couple of months on one of my PCs now. Today I installed it on my other PC. Coming from a Windows background, what I want to do is share a folder on one machine that the other one can access. The problem is Ubuntu is so different to Windows I don't really know where to begin (I don't mean to imply that Windows is better, if it was I wouldn't have switched to Ubuntu).

My setup is as follows:
Two PCs each connect directly to a router. The router goes to a cable modem, which takes me out onto the net.

The problem is, in the network card properties, I can choose either DHCP (the default), which allows me to get onto the net, or static IP. If I leave it on DHCP, both machines have the same local IP address, so if I ping that address obviously it just pings the local card rather than the other machine.

I knowe this is basic stuff, but how do I set up my home lan?

---

### Post by benuski on 2006-12-16
If you go to System=>Administration=>Shared Folders, it should set you up with everything you need to get, and  then you can choose what folders you want to share on the network.

---

### Post by xlulux on 2006-12-16
> **DrMega said:**
> Hi all.

I'm a recent convert to Ubuntu, having worked with Windows for years. I'm not an expert in either linux or networking, so please forgive me if this sounds really dumb.

I've been using Ubuntu for a couple of months on one of my PCs now. Today I installed it on my other PC. Coming from a Windows background, what I want to do is share a folder on one machine that the other one can access. The problem is Ubuntu is so different to Windows I don't really know where to begin (I don't mean to imply that Windows is better, if it was I wouldn't have switched to Ubuntu).

My setup is as follows:
Two PCs each connect directly to a router. The router goes to a cable modem, which takes me out onto the net.

The problem is, in the network card properties, I can choose either DHCP (the default), which allows me to get onto the net, or static IP. If I leave it on DHCP, both machines have the same local IP address, so if I ping that address obviously it just pings the local card rather than the other machine.

I knowe this is basic stuff, but how do I set up my home lan?


are you going to be using any windows machines to access the shared folders on this Linux pc? if not, NFS is the way to go for file sharing between Linux computers.

If you are going to have windows computers access these folders occasionally or at all, you will be better off going with SAMBA which is an open source infrastructure that makes the SMB protocol work on Linux and most of the time it makes it work from Linux to Windows. 


hope this steers you into the correct direction.

---

### Post by pgmario on 2006-12-16
You might want to have a look at the [Ubuntuguide]("http://www.ubuntuguide.org"), especially section 1.13.

---

### Post by scrooge_74 on 2006-12-16
> **DrMega said:**
> Hi all.

I'm a recent convert to Ubuntu, having worked with Windows for years. I'm not an expert in either linux or networking, so please forgive me if this sounds really dumb.

I've been using Ubuntu for a couple of months on one of my PCs now. Today I installed it on my other PC. Coming from a Windows background, what I want to do is share a folder on one machine that the other one can access. The problem is Ubuntu is so different to Windows I don't really know where to begin (I don't mean to imply that Windows is better, if it was I wouldn't have switched to Ubuntu).

My setup is as follows:
Two PCs each connect directly to a router. The router goes to a cable modem, which takes me out onto the net.

The problem is, in the network card properties, I can choose either DHCP (the default), which allows me to get onto the net, or static IP. If I leave it on DHCP, both machines have the same local IP address, so if I ping that address obviously it just pings the local card rather than the other machine.

I knowe this is basic stuff, but how do I set up my home lan?

Before sharing folders you need to get your network wroking properly, if I understand well you are not doing it yet if you have both manchines with the same IP address.

First let your router manage IP assignments is a lot easier this way.

Then tell each one of your PCs to use DHCP to acquire IP numbers, in this way one should be something like xxx.yyy.zzz.001 and the other is going to be xxx.yyy.zzz.002

After you get that going and both pc can get into the internet when both are on (you should be able to ping each one) you can configure folder share

You can do NFS to share folders, or you can share them in gnome using the connect to server option, I connect them using SSH, so I can check any file in the system and connection is secure (but that is another way to do it)

---

### Post by Portable_Jim on 2006-12-16
> **DrMega said:**
> I've been using Ubuntu for a couple of months on one of my PCs now. Today I installed it on my other PC. Coming from a Windows background, what I want to do is share a folder on one machine that the other one can access. The problem is Ubuntu is so different to Windows I don't really know where to begin (I don't mean to imply that Windows is better, if it was I wouldn't have switched to Ubuntu).


Right click a folder and click 'Share Folder'. If you just want to share the the folder to a Windows PC as well as a Linux (Ubuntu included) machine, share with SAMBA, but if you just want to share the folder with a Linux machine use NFS to share.

NFS is the best to use for sharing, but the downside is that windows computer cannot see or access the shares.

Please post any problems you have and any parts / steps you cannot understand.

---

### Post by Portable_Jim on 2006-12-16
> **Portable_Jim said:**
> Right click a folder and click 'Share Folder'. If you just want to share the the folder to a Windows PC as well as a Linux (Ubuntu included) machine, share with SAMBA, but if you just want to share the folder with a Linux machine use NFS to share.

NFS is the best to use for sharing, but the downside is that windows computer cannot see or access the shares.

Please post any problems you have and any parts / steps you cannot understand.
by the time I wrote my reply, others had posted before me, but hopefull my info helps.

---

### Post by billyboyred on 2006-12-16
Where do you get samba from?

---

### Post by scrooge_74 on 2006-12-16
samba is in the repositories, also you can check [http://www.samba.org](http://www.samba.org)

But if you want to connect Linux to Linux the other options are easier to setup, samba is more  for Linux to Windows, so Windows PC can see directories or printers on your Linbox

---

### Post by DrMega on 2006-12-17
> **scrooge_74 said:**
> Before sharing folders you need to get your network wroking properly, if I understand well you are not doing it yet if you have both manchines with the same IP address.

First let your router manage IP assignments is a lot easier this way.

Then tell each one of your PCs to use DHCP to acquire IP numbers, in this way one should be something like xxx.yyy.zzz.001 and the other is going to be xxx.yyy.zzz.002

After you get that going and both pc can get into the internet when both are on (you should be able to ping each one) you can configure folder share

You can do NFS to share folders, or you can share them in gnome using the connect to server option, I connect them using SSH, so I can check any file in the system and connection is secure (but that is another way to do it)

I've left my network configuration at the default, which tells it use DHCP to get the IP addresses. If I go to System->Administration->Networking and then choose the Hosts tab, I see, among other things, two IP addresses with aliases. There is localhost at 127.0.0.1 and my-desktop at 127.0.1.1. Both of which are, as far as I can tell, this machine that I'm on now (ie the same machine). If I go to my other machine, it says exactly the same, except that my-desktop is labeled media-pc.

Under Windows, I would use ipconfig /all to get the local IP address, it it would always be different for the two machines. Both machines can access the internet at the same time so I know I must be missing something really simple. I'm not entirely sure I'm even looking in the right place to determine the local IP. Once I know I've got that right, I intend to get VNC up and running so I can control one machine remotely from the other.

---

### Post by scrooge_74 on 2006-12-17
Your PCs are not communicating with the router, 127.0.1.1 is the local address.

you can use the ifconfig  at a terminal window to display information about your network cards

when you use this command you should get info on devices:

lo wil be your local adress and should be someting like 127.x.x.1, then should have other entries as eth0 or eth1 for your network card.

you can also use the command sudo ifdown eth0 to release the card and then use sudo ifup eth0 so your router can assign it an IP

---

### Post by DrMega on 2006-12-18
Problem solved. I sort of figured it out myself, but it was ideas and comments from people here that set me down the right track.

For the benefit of anyone else that has the same problem, the solution really couldn't be any simpler. I was looking in the wrong place for the machine's IP address. Here's what I did (sorry in advance to all hardcore Linux users, I used the GUI throughout):

1. System->Administration->Networking
2. Go to the General tab
3. Give the machine a domain name (just as you would in Windows). I'm not totally sure if this was necessary but it doesn't hurt.
4. Repeat steps 1 to 3 on the other machine, being sure to et the same domain name on both machines.
5. On the machine where I want to share a folder, navigate through Places until I see the folder I want to share.
6. Right-click to bring up the context menu, and say Share Folder. At this point I was prompted to install either Samba or NFS or both. I chose Samba. Ubuntu went off and got it. I gave the folder a share name and that was it. Job done.

To access the shared folder from the other machine, I went to Places->Network Servers. For some confusing reason the only icon that appeared said Windows Network but I double clicked it anyway. Lo and behold, there was my other machine. Double click that and there's my shared folder.

I'm not sure if Ubuntu was picking up settings out of my router, I can't remember what I set in there (it was over a year ago), but if, like me, you had it going on Windows then this is all you need to do to get the same arrangement going in Ubuntu.:-D 

Oh, nearly forgot. The place to look for your IP address is System->Administration->Network Tools and then change the devices dropdown to your ethernet card rather than the loopback adapter. Do that and the IP address appears under IP Information. I was originally looking in the properties of the network card in the Networking dialog.

---

