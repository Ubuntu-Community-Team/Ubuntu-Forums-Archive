---
title: "Downloads stop"
date: 2007-05-16
forum: Absolute Beginner Talk
---

### Post by aws910 on 2007-05-16
Having a really frustrating problem.  Kinda like [[COLOR="Blue"]_this problem_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=442211") but worse.

When I tried to download anything, the download would stop at random points, usually wouldn't grab more than 1000k at a time.  If I keep on doing the cancel/retry thing, it eventually gets the whole thing but it can take up to 20 tries on larger files.  It happens when I'm downloading from repositories in Synaptic, when I'm using apt-get, when I'm using wget from various websites, when I download things in firefox... anything that involves downloads from the internet(my LAN doesn't have problems).  Thankfully, most of the programs can resume broken downloads but it's still a big hassle.

There's no error message, the site is still accessible from my XP machine, my net connection is still up.  If I leave the download for a while, it will say that the connection timed out.

I've heard that changing the MTU will help.  I used the command 
```
sudo ip link set eth0 mtu 1492
sudo /etc/init.d/networking restart
```...to no avail.  After that I ran
```
sudo ip link set eth0 mtu 1400
sudo /etc/init.d/networking restart
```and that didn't help either.

I changed my firewall(netscreen10) to specifically allow Path MTU Discovery but it always defaults to 1500 if I don't set it with the code above.  Is there any way to force PMTU discovery?  Is my problem elsewhere?  Any ideas?  Thanks in advance.

---

### Post by Happy_Man on 2007-05-16
How fast is your internet connection? Do you torrent a lot? Sometimes, ISPs will try to kill Internet connections if they think you're torrenting.

---

### Post by aws910 on 2007-05-16
No torrenting done from this connection.  1.5 SDSL, at the office, 20 users.

The first couple times it happened, I chalked it up to server load/outage or someone going on a photoshop contest or something.

I'll try to set myself up on a static IP outside the firewall... maybe that'll narrow things down a bit.

---

### Post by aws910 on 2007-05-18
Hmm, so I am outside the firewall and the downloads are coming in fine.  This narrows it down quite a bit.

I seriously despise this crappy hardware firewall.  We paid like ten grand for it back in '01.  Since then, the company that made it has changed hands several times, and their "average lifetime" on products is three years or so.

I should really just replace it with an IPCop box.  That would be capital.  Wouldn't need to worry about "re-buying things every couple years" (hmm like ms office 97/2000/xp/2003/2007)

O well, in the meantime, I better get back to the (perceived) safe haven of a firewalled connection.  Thanks for the assistance.

---

