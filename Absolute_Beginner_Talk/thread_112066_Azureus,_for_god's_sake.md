---
title: "Azureus, for god's sake"
date: 2006-01-03
forum: Absolute Beginner Talk
---

### Post by TeeAhr1 on 2006-01-03
Yeah, still.  Two months down the road, and it's come down to this.  If I can get it working, then I am set, I think I can actually, finally, roll my Windows partition up and be done with it.  But god, this has been just a flaming pain in my rear.  Here's my story so far:

It started with NAT errors, which took me days to resolve, but I think I've got it licked.  I've got Azureus going to port 64300, and when I go to ShieldsUp or use the Azureus port checker, it tells me that 64300 is indeed open for business.

Now, however, I get this: "there appears to be a problem with the Distributed Database's UDP port mapping (NAT.)"  I have ports forwarded for both TCP and UDP.

So, anyone know where to go from here?:confused:

---

### Post by gnu2tux on 2006-01-03
Seriously weird business!

I have used Azeureus for years in Linux on all sorts of setups, no problems.

Can you let me know how you have your firewall set up because that will be the source of any UDP/TCP ports being blocked. As Ubuntu doesn't need/use a firewall by default, it is unlikely to be a problem there.

Regards,

Al

---

### Post by TeeAhr1 on 2006-01-03
Someone had previously advised me to install Firestarter and have it forward the ports as well, so I did so.  Both Firestarter and my router are set to send me 64000 - 64999, TCP and UDP.

Wait!  Just now, Firestarter logged this:
Time: Jan  3 14:41:41 Source: 192.168.0.4 Destination: 239.255.255.250 In IF: ra0 Out IF:  Port: 1900 Length: 129 ToS: 0x00 Protocol: UDP Service: SSDP

If I'm reading this right (which I may not be), my computer is trying to use port 1900 for UDP.  Is that correct?

---

### Post by Suger on 2006-01-03
That is

---

### Post by TeeAhr1 on 2006-01-03
Okay, I added 1900 to the allowed ports in the firewall and the router.  Same problem.  I'm told that there are a 1255 users online, but I still get the yellow light and the error message.  I tried turning the firewall completely off and restarting Azureus, to no avail...

---

### Post by Suger on 2006-01-03
What UDP port do you have set in azureus ?

---

### Post by kingsidy on 2006-01-03
you might need to do port fowarding on your router. [http://www.portforward.com/english/routers/port_forwarding/routerindex.htm]("http://www.portforward.com/english/routers/port_forwarding/routerindex.htm") go to this website and click on the model of the router, then on azureus as the client you are using. Open those ports both on your router and on firestarter. you need to know you ip address in order to properly foward ports. when it changes you are going to get that yellow icon again. then test it by downloading a file which had a lot of seeds. If it is still yellow, type in the terminal > gksu firestarter stop the firewall and see if it turns green. If it does then the problem is with the configuration of firestarter. if not double check on the the portfowarding. in my case the problem was firestarteer blocking communication.

---

### Post by TeeAhr1 on 2006-01-03
64300.  I don't know why it was still trying to go to 1900.  Now it's telling me I'm online, all systems go, 80,000 users, and I haven't changed anything since last time.  I'm going to cross my fingers and try to download something.  Wish me luck...

---

### Post by TeeAhr1 on 2006-01-03
The ports are forwarded on my router too.  I've tried it with Firestarted active and off, and in both cases, now the status bar says NAT and UDP are OK, but I'm not connecting to any peers. :confused: I know I'm not lacking peers, because if I try to do it through the gnome bittorrent program, it fires right up.

Thanks for taking the time on this, folks, I know it's a hairy kind of deal, but I am determined to solve this before I sleep...

---

### Post by proventech on 2006-01-03
[QUOTE=TeeAhr1]Someone had previously advised me to install Firestarter and have it forward the ports as well, so I did so.  Both Firestarter and my router are set to send me 64000 - 64999, TCP and UDP.

Wait!  Just now, Firestarter logged this:
Time: Jan  3 14:41:41 Source: 192.168.0.4 Destination: 239.255.255.250 In IF: ra0 Out IF:  Port: 1900 Length: 129 ToS: 0x00 Protocol: UDP Service: SSDP

If I'm reading this right (which I may not be), my computer is trying to use port 1900 for UDP.  Is that correct?[/QUOTE]


192.168.0.4?  Are you using a router?

---

### Post by proventech on 2006-01-03
opps, i see the post now lol

---

### Post by Suger on 2006-01-04
So, if I understand you well, using the same ports, the gnome client works and not azureus ?

---

### Post by TeeAhr1 on 2006-01-04
I don't know what ports the gnome client is using, I can't find the settings for it...

---

### Post by Suger on 2006-01-04
If I'm not mistaken, it's just a GUI for the original BitTorrent Client. Thus, I would say it uses 6881-6999. Does Azureus work if you set it to use 6881 ?

---

### Post by kingsidy on 2006-01-04
yes it does work with that port setting. that is the default

---

### Post by Suger on 2006-01-04
I know it's the default. But TeeAhr1 seems to have changed it. As his BT seem to work without setting anything (that is, using 6881-6999), I think trying to revert azureus to default might be a nice try.

---

### Post by TeeAhr1 on 2006-01-04
My ISP blocks 6881 - 6999, so I was forced to change ports.  A lot of ISPs are starting to block those ports, because they're common p2p ports.

---

### Post by timczer on 2006-01-04
Did you set your PC ip address to static?  I think that I had to do this to make this work.  If you leave it as dynamically assigned, it can change from the one you have forwarding to from the router to something new (192.168.1.104 to 192.1668.1.103 for example).

---

### Post by Suger on 2006-01-04
Yes, timczer is right.
Are you sure your ISP blocks those ports ? How come bittorrent works, then ?

---

### Post by TeeAhr1 on 2006-01-04
Bittorrent is sketchy at best.  One torrent went, at about 6KB even though there were more than 75 peers.  Three timed out.

I think I'm set to DHCP.  If I change it to static IP, do I have to change router settings also?

---

### Post by Suger on 2006-01-04
Well, you have to be in static IP for the router settings to be any use. The router doesn't rout packets to a computer, but to an address and a port. So if you're under DHCP, you're not sure your computer always has the right adress.

---

### Post by sabredog on 2006-01-04
I have given up with azureus. I get set length errors and no one can seem to resolve the issue.  :(

---

### Post by TeeAhr1 on 2006-01-05
Okay, we're on hold until at least tomorrow on this one.  I'm going to have to dig out the CD for my modem to find out how to get a static IP.  I'll come back with an update (and hopefully a How-Solved-It) this weekend.  Thanks, all, for the patience and advice...   -p.

---

