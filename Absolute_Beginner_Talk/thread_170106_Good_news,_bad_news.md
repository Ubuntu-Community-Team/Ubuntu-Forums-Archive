---
title: "Good news, bad news"
date: 2006-05-03
forum: Absolute Beginner Talk
---

### Post by bt224 on 2006-05-03
I finally got this installed (woot woot), but it's running slooooooooowwwwww. We're talking several minutes to respond to any commands. It's running on a PII 400. What have I done wrong?

---

### Post by aysiu on 2006-05-03
400... as in 400 MHz processor?
How much RAM do you have?

---

### Post by nalmeth on 2006-05-04
What system specs do you have?
Include your video card.

---

### Post by wylfing on 2006-05-04
Yikes. P2 400 is looking pretty low-end these days. I have heard reports of P3 800s working fine, but you're at least half that.

Perhaps unfortunately for you, there is no clear hardware upgrade from where you're at to a well-performing system. Anything of the right vintage to be classified as an upgrade for you is going to be ultra-expensive. You'd be much better served getting a whole new system, frankly. You can build a modern box from scratch for about $250.

---

### Post by nanotube on 2006-05-04
my guess is that the bottleneck in the ram, not the cpu.
install some more ram into that machine (about 512megs is a good number), and then you should be running ok.

---

### Post by wylfing on 2006-05-04
I respect your opinion from other threads, **nanotube**.

However, what you said is not unequivocably true. RAM isn't everything. I have seen many 512 MB systems where bus speed presented an ugly problem. They could launch, but not comfortably run, a Gnome desktop, despite having plenty of memory. Everything seemed to take ages to do.

The solution was to migrate to a larger bus bandwidth. Issue solved. What I am saying to the OP is that the ancient bus on a P2 400 is not economically worth upgrading. Just ditch the whole thing and build a new box. It will be less expensive that way.

---

### Post by nanotube on 2006-05-04
[QUOTE=wylfing]I respect your opinion from other threads, **nanotube**.

However, what you said is not unequivocably true. RAM isn't everything. I have seen many 512 MB systems where bus speed presented an ugly problem. They could launch, but not comfortably run, a Gnome desktop, despite having plenty of memory. Everything seemed to take ages to do.

The solution was to migrate to a larger bus bandwidth. Issue solved. What I am saying to the OP is that the ancient bus on a P2 400 is not economically worth upgrading. Just ditch the whole thing and build a new box. It will be less expensive that way.[/QUOTE]
what you say about upgrading to a new box certainly makes sense, considering that you can get a lowend desktop from dell for 300bucks nowadays. however, if the guy is strapped for cash, and its a choice between spending $300 for a new box, and $30 for a ram stick (or even ripping one out of some other box for free)... it's something to think about. ;)

my guess is that the p2 400 system has maybe 96-128 megs of ram, so the large part of the 'slowness' would be caused by caching to disk. certainly, with the p2 400 and the slow bus, even with a gig of ram it is not going to run *fast,* but once things are loaded into ram, they would run much faster.

so in essence - what you say is correct, my statement is not unequivocally true, and i was not implying it was. but it would have been the first thing *I* would have tried, to see if more ram would make it at least bearable. (the second would try xubuntu, then fvwm). but i guess my poor grad student mentality is starting to show here, so i will leave it at that. :)

thanks for your very sensible comment, wylfing.

---

### Post by wylfing on 2006-05-04
In general I would agree about this. I am all for squeezing the last drop out of every system. I had a Pentium 100 MHz as a server until quite recently. 

However, it is going to take 80 - 100 USD just to try a 512 MB memory footprint on the system under discussion, because PC100 memory (presumably that's what it is) is getting older and harder to find, and so it costs more. For scarcely more money, you can replace *everything* with modern components.

---

### Post by confused57 on 2006-05-04
The first computer I installed Breezy on was a 500 MHz(AMD K6), 256 mb ram, integrated graphics,  you get the picture.
It was pretty slow compared to my main computer(2.93 GHz, 1 Gb ram), but it was usable, especially after installing Automatix, from which I installed the newer version of Firefox(the Breezy default Firefox is pretty slow).  You may want to try epiphany browser(from synaptic package manager), it's faster.

If your ubuntu install is still too slow for you, you might consider doing a server install, then look into installing xubuntu-desktop.  If you have the initiative, you might want to just download the xubuntu dapper beta .iso and try installing that on your machine.  You'll have a lot of daily updates with the Xubuntu Dapper & will need a fast internet connection.  I don't know how much you know about Ubuntu, Linux, etc; but xubuntu may be a lighter OS option.  Hope this helps.

---

### Post by 3rdalbum on 2006-05-04
Discussion of RAM and system bus aside: On a 400 MHz machine it still shouldn't be taking MINUTES to respond to commands (unless you mean that it takes a long time to start up, which in your case would be normal).

Have you tried going:

```
sudo nano /etc/X11/xorg.conf

```

and putting a hash (#) before the line that says Load "DRI", then saving your changes and pressing Control-Alt-Delete to restart the X server?

DRI can sometimes make a computer run super-slow, so disabling it might speed up your machine.

---

### Post by Jussi Kukkonen on 2006-05-04
[QUOTE=wylfing]Yikes. P2 400 is looking pretty low-end these days. I have heard reports of P3 800s working fine, but you're at least half that.

Perhaps unfortunately for you, there is no clear hardware upgrade from where you're at to a well-performing system. Anything of the right vintage to be classified as an upgrade for you is going to be ultra-expensive. You'd be much better served getting a whole new system, frankly. You can build a modern box from scratch for about $250.[/QUOTE]

You're probably right, but as anecdotal evidence: I have several machines in that performance range (~400MHz) -- in fact I only have machines in that range -- and all of them function quite well. On two occasion I only had 128MB of memory, and that was clearly not enough for out-of-the-box ubuntu, but Xfce works fine even there. Adding memory has *always* helped in my experience.

---

### Post by bt224 on 2006-05-04
Sorry about the delay. I didn't have a chance to look at the specs before I ran out, but it does 128 ram. It ran W2K fine before, although you could time the boot up with a calendar, so "low-end" is a kind way of putting it. Maybe this gives you a couple of ideas on how slow it's running. When it first booted, it wanted to do 90 updates. I first went in and sent an e-mail, if for nothing else, just to play with it some. That took about 15 minutes, and I did a Gmail from the browser. I thought I would check some settings to see what was up. I move the pointer up towards the menus, and it's very sporadic (freezes then   appears somewhere else) like video freezes. Then I click Applications. I could have went into the kitchen and made a sandwich before the drop down actually occurred. I'm not exaggerating either. I know the machine will be pretty slow, but this smells like something else. Oh, and back to the updates. I started the install last night at about 10. At 7 this morning they were still running, and the machine isn't frozen, it is actually working.

---

### Post by mips on 2006-05-04
Install Window Maker or XFCE (or Xubuntu Desktop) and see if it improves the speed.

It does sound very slow though so it might be something else.

---

### Post by bt224 on 2006-05-04
Will do, but.......how? Sorry, but I'm a uber n00b.

---

### Post by bt224 on 2006-05-04
ok, found out how, will try tonight

Could this be a video card incompatibility issue?

---

### Post by mips on 2006-05-04
[QUOTE=bt224]ok, found out how, will try tonight

Could this be a video card incompatibility issue?[/QUOTE]

Nah, doubt it. Only thing that could really affect video card is 3d accelleration which is not needed/critical.

---

### Post by bt224 on 2006-05-04
Thanks all. here's the plan, I will install the Xfce desktop and see if that works. Should I still disable the DRI (whatever that is) ?

[http://www.mrbass.org/linux/ubuntu/](http://www.mrbass.org/linux/ubuntu/)

---

### Post by nanotube on 2006-05-04
[QUOTE=bt224]Thanks all. here's the plan, I will install the Xfce desktop and see if that works. Should I still disable the DRI (whatever that is) ?
[/QUOTE]
doesn't hurt to try. :)

---

### Post by bt224 on 2006-05-04
Will do, thanks!

---

