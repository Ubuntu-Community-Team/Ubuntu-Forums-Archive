---
title: "I'm an Apache newb... quick questions..."
date: 2008-02-09
forum: Absolute Beginner Talk
---

### Post by SZF2001 on 2008-02-09
Alright, so if I want to make an index.html file leading to my website to host, I use /var/www ? I heard something about /etc/init or something...

When I used my IP address given by the router (192.168.etc) I get the "It Works!" page. When I use my real IP number to connect to teh internetz, it wants me to log on. Whats this? I don't even know the log on or whatever... If anything I would hope to make it so my outside world IP would direct to the website I want to host...

And I know nothing of security. I dunno what to do. :(

Help please?

---

### Post by amingv on 2008-02-09
Did you configure your router to forward port 80 requests to that PC?

---

### Post by PinkFloyd102489 on 2008-02-09
/var/www is the web directory.

---

### Post by vinnybad on 2008-02-09
Hey SZF2001,

When you type in your 'real ip' or your ip to the rest of the internet world, it seems like you are accessing your router.  If you have a router, it will automatically take you to your 192.168.0.1 or 1.1 or whatever you have it set up as.  

You'll have to type in your user/pass for the router (if you don't know it look up the model number of the router and look in the manual and you'll find the default user/pass in there -- it's usually something like admin and password or administrator and password).  

Then you'll have to go to port forwarding (there should be an option like that.  Port 80 is for http...so any request for port 80 should be transferred to your computer's internal network ip...that's the one that starts with 192.168....etc.  

If you have port forwarding set up properly, the following will happen: 
1) person types in ip aaddress of your home internet
2) that makes a request for port 80
3) your router automatically recognizes it and forwards it to your computer.

So the settings on your comp ahould be fine if you see "It Works!" on your localhost page.

mess around with your network settings.

If you don't believe me, temporarily disable the network and hard-wire your computer to the modem and you'll see what I'm saying is true and it works..that is unless you also have a firewall that is blocking port 80 on your computer.

But since it asks you for the user/pass automatically, I'm able to tell you have a wireless network port forwarding problem to start with :).

---

### Post by SZF2001 on 2008-02-09
> **PinkFloyd102489 said:**
> /var/www is the web directory.

OK. So, if I have an index.html (or .php or whatever) file there, that will be whatever my IP in my network is, right?

> **amingv said:**
> Did you configure your router to forward port 80 requests to that PC?

I did a Port Scan with my IP, and the only port that seems to be open is port 80. Should I still try forwarding?

---

### Post by amingv on 2008-02-09
> **SZF2001 said:**
> 
I did a Port Scan with my IP, and the only port that seems to be open is port 80. Should I still try forwarding?

What I think is happening is that it is accessing your router for remote management, just disable this (or make it use another port if you need it) then forward port 80 to your server's IP address.

I am sorry I cant give you many pointers in doing this, but it changes dramatically from router to router. If you don't know this password then it must be the router's default (which is also insecure).

---

### Post by SZF2001 on 2008-02-10
OK, here's my set up - I'm on my computer right now, which I'd like to host with apache on, that is connected to a wireless connection. My computer is sending signals out to reach this, so the router is in another room.

There is a modem and a router - I'm behind the router, with the probability that I'm behind a router. I will screw around with the default router's IP but I gotta find the modem's IP and even then it's more strict about what I do there than on the router.

---

### Post by lespaul_rentals on 2008-02-10
Try the following:

From first router/modem, port 80 --> second router.  From second router, port 80 --> static IP of your Apache server.

---

### Post by SZF2001 on 2008-02-10
Lespaul, it's three in the morning right now so I can't go around my house to get to the other computer that has the passwords and stuff... But I am DEFINITELY going to try the idea tomorrow when I get access! Not bad at all.

---

### Post by lespaul_rentals on 2008-02-10
I can guarantee it's what you need to do.

---

### Post by SZF2001 on 2008-02-13
Oh man, figured out what I needed to do.

Freakin put my files in /var/www, NOT /var/www/apache_crap

Went into Nautilus as sudo (I know it's not a good idea, but whatever) and gave permissions for people to only see/read the files, but not excecute or write.

Good GOD, that seemed like it took forever to figure out and I have a huge headache.

---

