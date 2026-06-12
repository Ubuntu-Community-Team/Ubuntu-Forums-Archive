---
title: "Bittorrent incredibly Slow"
date: 2007-02-25
forum: Absolute Beginner Talk
---

### Post by Elliot.strumlauf on 2007-02-25
Hey, 
I am having trouble breaking 10kbps download speeds in Bittorent or bittornado. No previous guides have been helpful in expediting my downloads. Can someone please help? 

Thanks!

---

### Post by george29 on 2007-02-25
have you checked that you are forwarding ports correctly if you are using a router.. 
that you have uPNP enabled correctly.

it's possible that your isp is shaping your traffic if you are using the default ports - so if you can change them.

also try Azureus - which is probably the best bittorrent client around... it's java based so you'll need to install the sun java 1.5 run time environment. check out 

[www.ubuntuguide.org](www.ubuntuguide.org)

for instructions for both java and azureus.

edit: Azureus also allows you to encrypt bittorrent traffic making it harder for your ISP to identify the traffic you are generating as P2P traffic - which means they are less likely to traffic shape it.

---

### Post by Elliot.strumlauf on 2007-02-25
Hey, thanks for responding:

I have no clue how to forward a port or to measure traffic. I tried Azureus once, found it too cumbersome to use (I like lightweight software that just works) unfortunately, none of this junk works! I use a router, couldn't tell you how to edit it, and I am quite confused and want to DL some torrents!

---

### Post by george29 on 2007-02-25
you should really give Azureus a go - it is so much more powerful than bittornado or the standard bittorrent client. allows you to configure your connection much more easily, restart downloads etc..

i use azureus so i can only give you advice for that - some stuff will be applicable to other clients...

with port forwarding you really need to read your router documentation.. however if you use Azureus the easiest thing to do is to use uPNP to set up the connection. other clients may use this too.

you should log in to your router via a web interface it'll probably be at the address 192.168.2.1 (type that into a browser address bar). find the section on uPNP if it has it and make sure it is enabled.

then find the the plugins section for azureus... (i'm on an XP machine at my girlfriends so can't look at my machine to give you better directions) and make sure uPNP is enabled also enable encyrption for bittorrent traffic.

also change the port used from the default 8600 (i think thats the one used) to something like 500000 or higher.

that should be all you need to do. 

if you search google - you'll find lots of how to documents on port forwarding and probably one for your specific router.. but most work in exactly the same way - just the web interface looks different.

---

### Post by Elliot.strumlauf on 2007-02-26
Thanks! 
Should I download Azureus via Terminal or Automatix (already have it, and Java).

---

### Post by muguwmp67 on 2007-02-26
Also, Azureus has a test tool you can use after you've installed it to check whether the ports are forwarded correctly.  It is the NAT/Firewall test option under the Tools menu.

---

### Post by Zzl1xndd on 2007-02-26
Also its worth asking what ISP you have. A Great number of Cable and Some DSL providers thortle BT Traffic way down.

---

### Post by balan on 2007-02-26
I'm dual booting Ubuntu Edgy and XP.

In XP I am able to get download speeds of around 90KB with BitCommet, however if I boot to Ubuntu Edgy & try to download the same torrent file the speed is only around 17KB with the built in torrent client or with Azureus.

Does anyone know why and how to fix this problem because it would seem that the problem has nothing to do with the ISP.

---

### Post by bryan.taylor on 2007-02-28
Have you verified that the ports you are using aren't blocked?  In each bittorrent client there will be a config option that sets what ports you would like to listen on.  They can be different in Windows and Linux.  You need go to this website: [http://www.whatsmyip.org/ports/](http://www.whatsmyip.org/ports/) and type in the port number in the "Custom Port Test" box.  If your port is open it will come back with "open", and if it's blocked it will come back with "timeout".

I would recommend opening bitcomet in windows and checking it's configuration options to see what ports it's using.  Then you should test some of those ports on the above website.  If they are open then you should configure your Linux bittorrent application of choice to use those ports.

If all of your ports are blocked, then post back with your router details (brand, model number, etc.) and I'm sure that someone here could help you out. :)

---

### Post by Marc_UK on 2007-04-20
I remember trying Ubuntu 6.04 and it had fine torrent speeds, since 6.10 speeds have been slow.

---

### Post by centy on 2007-04-20
Same here with the slow speeds in bit torrent and bit tornado. I couldn't work out what was making it so slow, although I'm pretty sure it wasn't firewall/router rules. As soon as I switched to azureus and configured it for the port that was forwarded in my router the speeds shot up from 50kbps to 650kbps.

Azureus wins.

---

### Post by paark.s on 2007-04-20
I recommend you rtorrent.It is a text base torrent client that eat very little resource.

more info here [http://en.wikipedia.org/wiki/RTorrent]("http://en.wikipedia.org/wiki/RTorrent")

I usually download at 104kbyte/sec and you can run it seemlessly under tty(ctrl+alt+f1-f6, f7 is xwindow)

---

### Post by centy on 2007-04-21
> **centy said:**
> Same here with the slow speeds in bit torrent and bit tornado. I couldn't work out what was making it so slow, although I'm pretty sure it wasn't firewall/router rules. As soon as I switched to azureus and configured it for the port that was forwarded in my router the speeds shot up from 50kbps to 650kbps.

Azureus wins.

Whoops I spoke too soon. I did a fresh install of feisty because I messed a few things up and now azureus seems capped at about 50kbps like bit torrent and bit tornado where yesterday.. anyone got an idea why this may be happening.

For your information: My ISP does use traffic shaping, but not at off peak times, i.e now. The ports I have selected to use in azureus are open in the router/firewall and pointing at the correct local ip. Azureus NAT test passes. Tried allowing everyone the service with firestarter and applying policy etc, no change. Any ideas?

Truly annoying to be getting 50kbps at max when I know I should be getting 650kbps at least.

EDIT: And now it's back at 650+kbps.. either my ISP is playing a very late very unfunny april fools joke or... ubuntu is.

---

### Post by Thangalin on 2007-04-24
Hi,

Remove GIJ and install Sun's JVM.

It seems GIJ, which is the Java Virtual Machine installed by Feisty, cannot handle the connection load required for Azureus to perform properly.

1. sudo apt-get remove gij
2. rm /usr/bin/java
3. Download Sun's JVM ([http://java.sun.com](http://java.sun.com)); try "Java Runtime Environment (JRE) 6u1"
4. Install Sun's JVM into /opt/jdk1.6.0
5. Set your PATH to include /opt/jdk1.6.0/bin
6. Close your shell window.
7. Open a new shell window.
8. Run Azureus.
9. Help -> About
10. You should see "Java 1.6.0" in the "System" pane.
11. Enjoy faster download speeds!

---

### Post by Efros on 2007-04-24
under edgy I too experienced low torrenting speeds with Azureus, ktorrent and a couple of other clients, before anyone asks I am quite experienced and I know how to open and forward ports correctly. My solution was to install utorrent under wine, result torrents can hit my DL limit of about 550 Kb/s seeds permitting,

---

### Post by gReEnT3a on 2007-04-28
Hi, I am having the same problem ever since Dapper but I never got it fix until now. My BT download speed in Ubuntu is n-times slower than my BT speed on Windows. Azureus shows NAT OK, and the required port I set for it is opened and router port-forwarding is also configured. But for some reason I am still having incredibly slow speed.

This is the only reason for me to dual-boot Windows. Help to troubleshoot and fixing this problem is very much appreciated.

---

