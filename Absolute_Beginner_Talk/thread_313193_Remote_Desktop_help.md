---
title: "Remote Desktop help"
date: 2006-12-05
forum: Absolute Beginner Talk
---

### Post by Bloch on 2006-12-05
I am trying to login remotely to a friend's computer so I can do some basic maintenance etc.

My steps so fart have been:

1. I rang the friend and got him to change System>Preferences>Remote Desktop so a remore login is allowed.

2. I got him to find his IP address on whatismyip.net. He also got the "other" IP addresses from his Network Tools and read them out to me. (there is one IP address for Loopback Interface and another for Ethernet Interface)

3. I opened Terminal Server Client, changed the protocol to VNC and tried entering the data above. The computer is his IP address as reported by the website, for Domain I'm not sure.

I have searched a lot of threads but most seem to be on a local network or refer to logging in to a college network. I am trying to connect from a regular asdl broadband to another computer on broadband: I am not even sure if it is possible at all.

So, is it possible, and what mistakes could I be making?

---

### Post by mahy on 2006-12-05
Never tried VNC by myself, but i can tell you this: It doesn't matter what kind of network connection the two machines have! That said, it doesn't matter if it's home network, college network or Internet. However, make sure no router is blocking the way. If that's the case, you have to set up port forwarding. More info on that topic can be found on [www.azureuswiki.com](www.azureuswiki.com) (NAT problem). Make sure you forward the right port for VNC. Good luck, but it should be fairly easy.

---

### Post by Bloch on 2006-12-05
We both have just a single computer connected to broadband modem connected to an ADSL broadband provider - does that mean we don't have a router?

However in conversation with the friend over the phone, it turned out that his IP address (as reported by [www.whatismyip.net](www.whatismyip.net)) changed while we were speaking. I suspected this when 
ping 194.46.180.23
stopped working.

I think I'll give up - there is little information on how to use Terminal Server Client. It seems you need a degree in networking to even start.

---

### Post by mahy on 2006-12-05
> **Bloch said:**
> We both have just a single computer connected to broadband modem connected to an ADSL broadband provider - does that mean we don't have a router?

However in conversation with the friend over the phone, it turned out that his IP address (as reported by [www.whatismyip.net](www.whatismyip.net)) changed while we were speaking. I suspected this when 
ping 194.46.180.23
stopped working.

I think I'll give up - there is little information on how to use Terminal Server Client. It seems you need a degree in networking to even start.

Not necessarily a degree, but some knowledge about TCP/IP protocol stack comes in handy ;)

Yes, IP addresses do change, usually once in 24 hours with decent ISPs. Rogue ISPs can change them more frequently.

As for the broadband modem, i guess it's connected to your computer via ethernet cable. In that case, yes it is a router, it uses NAT and you'll have to setup port forwarding. Do you download torrents? Then you should know how to set it up. It can be done using the modem's maintenance page.

Just in case: BOTH of you'll have to set up separate port forwarding.

---

### Post by bmt on 2006-12-07
> **mahy said:**
> Just in case: BOTH of you'll have to set up separate port forwarding.
It isn't necessary for both routers to have ports forwarded -- only at the machine that has to receive a start request.  Router firewalls, by default, generally have no restriction on outgoing connections, only incoming.  It's also possible to have vnc sessions working via a repeater (on the Internet), in which case both computers start an outgoing connection and neither needs port forwarding.

For more information on VNC, have a Google for RealVNC, TightVNC and UltraVNC.  Not all of them have native Linux support, but there's loads of information available.  The UltraVNC forum is particularly helpful.

There is also plenty of VNC stuff on these forums -- search on 'vnc'.

As with most things, it can be quite difficult to get started, but it is certainly doable.

---

### Post by Spitfire567 on 2006-12-07
> **Bloch said:**
> 

1. I rang the friend and got him to change System>Preferences>Remote Desktop so a remore login is allowed.

2. I got him to find his IP address on whatismyip.net. He also got the "other" IP addresses from his Network Tools and read them out to me. (there is one IP address for Loopback Interface and another for Ethernet Interface)

3. I opened Terminal Server Client, changed the protocol to VNC and tried entering the data above. The computer is his IP address as reported by the website, for Domain I'm not sure.


Step 3 is where you are going wrong, unless your friend actually installed a VNC server.  The Remote Desktop service that you enabled in step 1 is different from VNC.  The protocol you want to use in Terminal Server Client is called RDP.  Everything else you are doing is fine.

One more thing to check would be the Windows Firewall settings on your friend's computer.  I am not sure, but I do not think it automatically allows Remote Desktop traffic when the service is enabled.  You have to specifically enable it.  There should be a check box for "Remote Desktop".  If not, the port you need to allow through the firewall is 3389.

If it still does not work, then your friend's computer is behind a router and you need to forward port 3389 to the computer, using the above suggestions that other people have posted.

---

### Post by musicinmybrain on 2006-12-16
> **Spitfire567 said:**
> Step 3 is where you are going wrong, unless your friend actually installed a VNC server.  The Remote Desktop service that you enabled in step 1 is different from VNC.

On Windows, that's true. However, the poster is talking about a machine running Ubuntu, and what Ubuntu calls Remote Desktop is indeed VNC.

P.S. The port you need to forward for VNC is TCP 5900.

---

### Post by SuperMike on 2006-12-16
I think I recalled I had to add either ":0" or ":1" on the end of the name or IP address of the remote computer in order for me to connect to it. This was in an Ubuntu to Ubuntu remote desktop connection.

---

### Post by chrisfay on 2006-12-16
> On Windows, that's true. However, the poster is talking about a machine running Ubuntu, and what Ubuntu calls Remote Desktop is indeed VNC.

But, doesn't the host still have to install VNC server to allow the connection in the first place?

---

### Post by musicinmybrain on 2006-12-16
> **chrisfay said:**
> But, doesn't the host still have to install VNC server to allow the connection in the first place?

Sort of. A program called vino is included with Gnome/Ubuntu that functions as a standard vnc server. It's enabled when you turn on "Remote Desktop" in the system --> preferences menu. Vino is separate from the vncserver package, which does not need to be installed. I don't know if Kubuntu or Xubuntu users have a vnc server installed by default, but the original poster's mention of the system --> preferences menu indicates he's using standard Ubuntu with Gnome.

P.S. I'm presently having trouble connecting via Terminal Server Client from an Edgy box to a Dapper box. It works fine when I use Alt+F2 or a terminal to run vncviewer directly, so you might try that if your port forwarding (if needed) is correct but you're still having problems.

---

### Post by chrisfay on 2006-12-16
> Sort of. A program called vino is included with Gnome/Ubuntu that functions as a standard vnc server.

Good to know....:-D

---

