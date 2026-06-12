---
title: "Do I need a NIC driver?"
date: 2005-09-05
forum: Absolute Beginner Talk
---

### Post by Insignius on 2005-09-05
My Internet connection isn't working quite the way it should.  It's really slow. I finished installing Ubuntu last night, and I seemed to be working okay. I was up until 3:30 playing with the command line!   But, this morning I was so lucky to find my graphics card was fried—The power chord had wiggled itself loose and melted to the side of the card!

Anyway, after purchasing a new card, I had to install it and in doing so unplugged all of the cords/connections including the LAN line. 

I plugged everything back in and got an error message; the faulty card must have done something.  I figured since my Linux recovery skills are next to nil at this point, plus the new hardware and the fact that I didn't have anything saved, I'd just start over and re-install. (Hey, it was kinda fun.  Way more fun than doing a Windows re-install!) 

Okay, enough with the storytelling and onto the problem:

Once I got my reincarnated Linux box up and running, I found I was having a helluva time with the net.  It worked, but it was really slow.  It would literally take five minutes to open a page.  Also, when I tried gaim, I couldn't get it to connect.

The strange thing is, downloads went fine; both in the system updates and Synaptic downloads I was getting speeds in excess of 200kb/s.  

So what I did was download Konqueror and that worked better—but still not as fast as it should.  And, just to be sure I unplugged/reset the dsl modem and router.  And, my parent's computer was working fine. 

With Konqueror, I checked out “Ubuntu starter guide” and followed the “How to load Web site faster in Mozilla Firefox?” guide that seemed to help, but very little.  Plus, gaim still wasn't working.


So I thought maybe I needed a driver.  Didn't seem to last night, but it couldn't hurt.

My connection is an on-board Ethernet connection on an ABIT IC7-G (?) motherboard. I checked the Abit website, but the only drivers they had were for Windows.  Plus, I'm still not totally down with unpacking files (specifically drivers) in Linux. 

So, first of all is the driver my problem and if so, how do I solve it?  If not, have any ideas what the problem is?

---

### Post by brinebold on 2005-09-06
There are a ton of things that could cause slow speeds.

The easiest to fix would be:
cable/DSL modem needs rebooted (unplug for 1 minute then plug back in)
router needs restarted (use your router config interface{probably HTML} or just unplug it for 1 minute)
You need to disable a conflicting network device in system>admin>networking on the gnome menu.

The impossile to fix would be:
Your ISP just decided you aren't in a hurry today.

It is unlikely that you need a NIC card driver unless you are using a wireless card (I did and it took me my entire first day + a borrowed laptop to figure it out).  If you do, it is unlikely that your NIC manufacturer will have drivers for your card.  They never seem to anyway.  Try looking or asking around to find the *chipset* that your card uses and use the drivers from that manufacturer company.

---

### Post by Insignius on 2005-09-07
Okay, well Firefox seems to be running at okay speeds at this point, yet I still can't get gaim to connect.  I don't know if that's part of the same problem, or a different one.

---

