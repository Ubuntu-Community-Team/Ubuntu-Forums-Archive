---
title: "How do I forward a port?"
date: 2007-07-22
forum: Absolute Beginner Talk
---

### Post by szaemon on 2007-07-22
Help me Please. I know other posts exist with this request but following them has not quite done the job. I'm kinda stuck with my thumb up somewhere dark and foul.

I have Ubuntu Feisty Fawn. 
I'm trying to download music from the net.

Using the other posts I've managed to install wine and got half way through uTorrent when I was prompted to test my Speed and Port:

Error! Port 45452 does not appear to be open.

Please see [www.portforward.com](www.portforward.com) for more information about how to map a port.

Please make absolutely sure that PeerGuardian2 or Protowall is allowing utorrent.com (72.20.34.145) in either of those programs. Those of you using ipfilter.dat should make sure the list does not include the website's IP. After making sure of this, re-run this test by refreshing the page (F5).

My router was not listed in [www.portforward.com](www.portforward.com)

I downloaded and installed firestarter.
The Policy Tab in Firestarter is greyed out and unaccessible.

I don't know what to do next. Any advice would be appreciated. 
Thank You.

---

### Post by testube_babies on 2007-07-22
It's probably a router issue, since all ports are open on a default Ubuntu installation.  What type of router do you have?  If you can't find info on it, I'm sure someone here has had to deal with it in the past.

That being said, I have no idea why the Policy tab could be grayed out, so maybe it's something deeper.

---

### Post by Steveway on 2007-07-22
Why are you using utorrent in wine?
There are native torrentapps that give equal speed and configurability.
Deluge for example is very good, and I didn't need to configure any port here on my box for it to work with full speed.
If you use KDE you can try ktorrent, also very good in terms of speed and configuraility.
Just look for torrent in Synaptic and you'll find those and a whole lot more apps.

---

### Post by irish_flu on 2007-07-22
Port "forwarding", in a nutshell, is this:

When you're hitting a device on the internet, it sees the public IP address given to you by your ISP.

For something that requires other machines can hit you (like BitTorrent), they need  to be able to pass through your router and find the machine on your network that's running BitTorrent.  You have to tell the router which private IP address this traffic should be "forwarded" to.

Basically, you have to tell the router "Hey, when traffic comes knocking on port 1234, forward it to 192.168.1.100".

So, this setup will be done in your router config; your Ubuntu machine isn't really even aware of it (nor is the outside traffic).  Only your router knows what's going on.

You can probably access your router by pointing your web browser at its address (for example, maybe it's 192.168.1.1).  You'll be presented with a login, and from there you'll be able to set up port forwarding.  Before you do it, you'll need to know what the private IP of the target computer is, and you'll need to know what port(s) the application wants to use.

---

### Post by ugm6hr on 2007-07-22
A simple suggestion:

What router are you using?  If it supports UPnP - then I would suggest you install *ktorrent* (instead of WINE/utorrent, and "load" the UPnP module (in Preferences).  It should automatically forward relevant ports both in the router and on Ubuntu.

If you want / have to manually forward ports - you need to access the router's setup page (as per irish flu - often *192.168.0.1* or *192.168.1.1* from web browser).

---

### Post by szaemon on 2007-07-22
Why am I using Utorrent in wine?

It was the only one I saw talked about as having a simple Gui.

What router am I using?

RT-200NE

Do *want* to do port forwarding manually?

Absolutely Not! How I can avoid it though, I don't know.

My desktop is gnome. If utorrent is no good, is there a native program that would be easy for a noob to figure out. So far the only p2p I've ever used is Shareaza in Windows, but I read that it doesn't work in FF

---

### Post by forestpixie on 2007-07-22
I use ktorrent - I loaded the upnp plugin and it forwards ports ok for me - others have had problems but I can't say I have. It's a kde program not gnome.

you can get it from the repo

```
sudo apt-get install ktorrent
```

---

### Post by szaemon on 2007-07-22
OK, I downloaded and installed ktorrent. Loaded the UPnP. When I click on the tabs:Devic, Ports Forwarded, WAN Connection. I get no response. same with the buttons: Forward Ports, Undo Port Forwarding, and Rescan.

Could I be missing a more basic step?

---

### Post by annda on 2007-07-22
other than configuring your router, you can try installing firestarter (GUI for the built-in firewall)

```
sudo apt-get install firestarter
```

and making a new policy for incoming traffic. make the port 45452 accessible to anyone.

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#Firewall](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Firewall)

---

### Post by szaemon on 2007-07-22
I installed Firestarter, the policy tab is grayed out. It can't be used.

---

### Post by annda on 2007-07-22
what happens if you start it with root privileges from the terminal with the following command:

```
gksudo firestarter
```

---

### Post by aktiwers on 2007-07-22
I am not sure, but wouldnt this do the trick?
```
sudo iptables -A INPUT -p tcp --dport 45452 -j ACCEPT
```

Worth a try :)

---

### Post by szaemon on 2007-07-22
Thank You All For The Help!

   OK, I think I got my router configured. My router page is in Japanese, I don't read Japanese....
Now, could someone please instruct me on how to check if a certain port has been successfully forwarded?

---

### Post by szaemon on 2007-07-22
> **aktiwers said:**
> I am not sure, but wouldnt this do the trick?
```
sudo iptables -A INPUT -p tcp --dport 45452 -j ACCEPT
```

Worth a try :)


I'm not sure either, but that's a hell of a lot easier than my last 2 hours struggling through a Japanese router config site. Thanks.

Does anyone know if this would work or if it might cause some trouble?

---

### Post by ugm6hr on 2007-07-23
> **szaemon said:**
> I installed Firestarter, the policy tab is grayed out. It can't be used.

There is something not right with this.  

Can you click on the policy tab at all?  Maybe post a screenshot of the "greyed" tab to see if someone else has seen it before.  I certainly have never had that problem.  Do you have any other firewall GUI installed?  Are you running Ubuntu from within another OS or from LiveCD, or was it a direct install to HD?  Did you install Ubuntu yourself (i.e. are you the only user/group) and do you have administrator rights?

Judging by this:
[http://translate.google.com/translate?hl=en&sl=ja&u=http://flets.com/hikaridenwa/subscription/router.html&sa=X&oi=translate&resnum=1&ct=result&prev=/search%3Fq%3Drt-200ne%26hl%3Den%26client%3Dfirefox-a%26rls%3Dcom.ubuntu:en-US:official%26hs%3DFZp](http://translate.google.com/translate?hl=en&sl=ja&u=http://flets.com/hikaridenwa/subscription/router.html&sa=X&oi=translate&resnum=1&ct=result&prev=/search%3Fq%3Drt-200ne%26hl%3Den%26client%3Dfirefox-a%26rls%3Dcom.ubuntu:en-US:official%26hs%3DFZp)
It seems your router has DHCP and handles UPnP, so I would say the issue is probably with the Ubuntu firewall.

One thing worth trying - Open KTorrent, Ensure UPnP is loaded, then just try adding a torrent that you know is well seeded.  See what happens.  My UPnP doesn't always list the port, but it is forwarding, judging by the speeds I get (I have to limit to 30kbps to ensure I don't upset other internet users in the house!)

Other suggestion... learn Japanese, or find someone who has :confused:

---

### Post by szaemon on 2007-07-23
> **ugm6hr said:**
> There is something not right with this.  
 :confused:

You're right. Thank you for questioning my observation. I had noticed only one Policy Tab, at the top of the window, in the middle there is the one that I was supposed to be looking at. I think I got it done now. Just have to figure out how to use both the p2p programs that I got now....
....Ahhh...adventures in Nooberland. I should right a book!

---

### Post by aktiwers on 2007-07-23
> **szaemon said:**
> I'm not sure either, but that's a hell of a lot easier than my last 2 hours struggling through a Japanese router config site. Thanks.

Does anyone know if this would work or if it might cause some trouble?

Im pretty sure it will work. Or atleast im pretty sure it will open that port.

It wont mess anything op. You can always revert it back by typing drop instead of accept like this:
```
sudo iptables -A INPUT -p tcp --dport 45452 -j DROP
```

You can test it by using the bittorrent client that used that port, get a torrent with a lot of seeds and see if it work.

Or use any other torrent client, find out what port it uses and change it in the command like this:
```
sudo iptables -A INPUT -p tcp --dport portnumber -j ACCEPT
```

where portnumber is your portnumber. Again you can revert it back by the chaning ACCEPT to DROP.

---

### Post by stinger30au on 2007-07-23
i dont know if this will help but this site shows how to setup port forwarding on your router.

[http://www.portforward.com/](http://www.portforward.com/)

---

