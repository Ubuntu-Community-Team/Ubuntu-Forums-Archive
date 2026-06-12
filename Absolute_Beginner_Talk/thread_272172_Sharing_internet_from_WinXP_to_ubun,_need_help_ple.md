---
title: "Sharing internet from WinXP to ubun, need help please~"
date: 2006-10-05
forum: Absolute Beginner Talk
---

### Post by UnknownVariable on 2006-10-05
My built-in wireless card is unsupported as of now, so I'm trying to share my internet connection from my desktop computer (running windows xp) over to ubuntu on my laptop, and I'm having a bit of trouble.

The windows box is receiving a signal from my router via wireless card. My ubuntu box and windows box are connected directly via crossover cable. I have internet connection sharing enabled on the wireless connection on my desktop, which automatically set my IP on the lan to 192.168.0.1 and the subnet mask to 255.255.255.0. I went into system > administration > networking and changed my setting from DHCP to manual and put 192.168.0.2 for the IP address and 255.255.255.0 for the subnet mask.

Now, from system > administration > networking tools, I'm able to ping 192.168.0.1, which should be my desktop computer. Ping response is very quick. From places > network server, I'm able to view my shared folder on my desktop and retrieve files (yay!).

However, despite all this, I still get an "unknown host" error in konqueror when trying to connect to a website, and in firefox it says "server not found." That tells me I'm not getting any internet connection at all.

So the big question here is.. What did I miss? lol I'm *this* close to getting it, yet I'm kinda lost at this point...

Thanks for the help. :) You guys have always been very helpful to me.

---

### Post by brt on 2006-10-05
hmm maybe you should look into one of those wondose forums around ;)

isn't there a setting called "Share Internetconnection" in the preferences dialog of the networkcard?

---

### Post by UnknownVariable on 2006-10-05
Lol, I wouldn't even know where to start to find a decent windoze forum where the people are nice and willing to help a linux-user. :lol: I figured someone here might be able to help. :)

If you mean on my windows box, then yes, there's a setting that says "share internet connection," a little checkbox. I ticked it and set settings for different types of data to be allowed to go through the network. :) 

If you mean on the ubuntu box, some kind of sharing internet setting needed to accept it... Then I have no idea. :mrgreen:

---

### Post by UnknownVariable on 2006-10-05
New note: Using a browser on my windows box and entering 192.168.0.2, I'm able to access apache on my ubuntu box. I'm not sure if this is of any relevance, but at least it's info. :P

---

### Post by psycosmyth on 2006-10-05
it's like giving xp a dose of tequila and red bull. I had the same issue with my mom's box but the cable-modem was the issue there, I did not use a direct link, what kind of cable? hope you dont mind me tagging in, this is a learning topic for me too, my problem is, i'm forgetting how to use windows!:-D

---

### Post by UnknownVariable on 2006-10-05
psycosmyth: I've got a crossover cat5 cable for the direct connection between the two computers. :)

---

### Post by po0f on 2006-10-05
UnknownVariable,

On the Windows box, go to the Control Panel, double-click on the Network Connections option.  In there, right-click on your internet connection and go to the Status option.  Click on the Support tab.  In there, click on Details.  You will see a listing of information about the connection.  Write down the DNS server IPs and enter those on your Ubuntu box (don't know exactly where, not at my box atm).  Try looking somewhere under System->Administration->something about networking.

---

### Post by UnknownVariable on 2006-10-05
Hi po0f, we meet again. :)

Good news however, Google came to the rescue and I solved the problem!

[http://www.annoyances.org/exec/show/ics_xp](http://www.annoyances.org/exec/show/ics_xp)

That page worked perfectly for me. The only thing I was missing was entering the gateway IP address on my ubun box. :mrgreen: It's all fixed now, however!

---

### Post by po0f on 2006-10-05
UnknownVariable,

I forgot about entering the gateway information.  I had to do this the other night on my FC5 box, I forget so quickly.  ;)

---

### Post by james_san on 2006-10-05
Also, when you enable ics in windows xp, it starts a dhcp server for you, so if you had left ubuntu setup for dhcp it would have worked automatically :D
Funny how too much knowledge can be a burden...

---

### Post by UnknownVariable on 2006-10-05
Actually, leaving it at just DHCP on Ubuntu didn't work. That's one of the first things I'd tried. I did have to specify the network IP settings all the way, it seems.

---

