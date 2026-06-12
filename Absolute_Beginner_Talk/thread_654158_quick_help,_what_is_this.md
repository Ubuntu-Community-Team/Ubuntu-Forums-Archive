---
title: "quick help, what is this?"
date: 2007-12-30
forum: Absolute Beginner Talk
---

### Post by myolbug on 2007-12-30
Hey, while my computer was booting, I noticed that it entered run level 2, then it started a program called avanti-daemon.  What is this? I am running Ubuntu 6.06.
Thanks.

---

### Post by myolbug on 2007-12-30
The full name of it is mDSN/DNS-SD Daemon Avahi-Daemon.

I have googled it, but I am too new to really  know what it is.  Have I been hacked?

Please someone help.

---

### Post by ^rooker on 2007-12-30
No. no. don't worry... 

[http://en.wikipedia.org/wiki/Avahi_(software)]("http://en.wikipedia.org/wiki/Avahi_(software)")

That thing does some "magic" to configure things on demand and automagically.... Related to "Zeroconf" (similar to "bonjour" on Mac)

---

### Post by myolbug on 2007-12-30
Thanks, but here is the weird thing.  I have Firestarter as my firewall, and it usually shows that IP addresses tha I am connected to, such as the address for this page that I am on.  This isn't showing, also, it is showing that BitTorrent is connecting to different ip addresses.  I didn't even know I had BitTorrent.  Also, it isn't showing any events on the main page.

And as far as magic things, i really would like to know what the purpose of this is.  When I go to reboot, it keeps going to the scripts page during boot up, and it keeps showing errors.  It is fixing these by itself, I guess, because before i would have to do it manually, then I could boot up.  This is totally new to this and I haven't made any changes.  What is going on?

---

### Post by Crumpets and Jam on 2007-12-30
I think GNOME comes with a BitTorrent client. Don't worry all your firewall ports are closed by default.

---

### Post by myolbug on 2007-12-30
Well that is a relief, because my firewall is getting hammered by BitTorrent from a lot of different address's.  I mean about every two seconds.  Also, I am getting hit by Radmin-port.

---

### Post by Dr Small on 2007-12-30
If you are getting hit on Radmin ports, that not good.
Anyhow, do you have these ports open, or is just showing as it being blocked ?

---

### Post by myolbug on 2007-12-30
I don't know.  How do I check?

---

### Post by Dr Small on 2007-12-30
Well, if you go into Firestarter, and look under the Policies tab, you can see what ports you have opened, and what hosts you have allowed.

If none of those ports which are getting attacked are open, it's like setting inside during a hail storm. The hail hits your roof but doesn't get inside.

Same principle if your ports are closed. You may be getting attacked on certain ports, but as long as they are closed, no body can get inside.

Dr Small

---

### Post by myolbug on 2007-12-30
It is showing in the list of blocked connections.  What is with the BitTorrent attacks?  They are literally every one to two seconds.  Thet keep trying to hit port 6881

---

### Post by myolbug on 2007-12-30
> **Dr Small said:**
> Well, if you go into Firestarter, and look under the Policies tab, you can see what ports you have opened, and what hosts you have allowed.

If none of those ports which are getting attacked are open, it's like setting inside during a hail storm. The hail hits your roof but doesn't get inside.

Same principle if your ports are closed. You may be getting attacked on certain ports, but as long as they are closed, no body can get inside.

Dr Small

I did as you said, and it doesn't show anything in the inbound traffic or outbound traffic side.

---

