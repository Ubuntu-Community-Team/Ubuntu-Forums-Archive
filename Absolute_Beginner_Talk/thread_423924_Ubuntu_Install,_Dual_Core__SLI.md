---
title: "Ubuntu Install, Dual Core / SLI"
date: 2007-04-26
forum: Absolute Beginner Talk
---

### Post by OhioYJ on 2007-04-26
I've been having problems with all version of Ubuntu on my desktop PC. My Specs:

3800 AMD64 X2
Asus A8V-SLI Deluxe
1024 MB X 2 RAM
2 - 7800 BFG GTs in SLI
Main HD: 34 gig SATA Raptor Drive
2nd HD: IDE 250 GB
DVD Drive
Dual Monitors

I'm trying to install the 32-bit version of Ubuntu 6.10, to the SATA drive. When running the boot CD it always stops/freezes/crashes at the same point. As soon as the GUI for the install/live CD starts to appear (when the tan background shows up), and the sounds plays, I get a bunch of lines across the screen and everything stops. I know the CD is good as I used it on my AMD64 laptop.

---

### Post by Greg Knight on 2007-04-26
Hi.

I had similar problems when I first started with Ubuntu.  The problem seemed to be occurring because the x-server (the bit that running the GUI) couldn't deal with SLI.

Try disabling it.  I pulled my video cards out and set the mobo switch to single card, and then put just one of them back.  I could then boot the live cd all the way and install Ubuntu. 

Once every thing was fine, I just set the video cards back the way they were.

Sure Ubuntu is not making use of the SLI, but it doesn't really need to.

There may be an easier/less messy way to disable SLI temporarily, but I just stick to what I know.

Cheers!
Greg

---

### Post by OhioYJ on 2007-04-27
Ok tried removing the 2nd video card, and no luck. Even tried the "Safe Graphics" option for install. Still locks up/freezes in the same spot.

Any more suggestions would be greatly appreciated.

---

### Post by reidamd on 2007-04-27
I had a ton of issues with installing ubuntu, it turned out, it was just bad media on the CD I burned, are you using a CD-RW? I finally took mine out and realized that the metal was actually flaking of the CD-RW. Try burning the iso to brand new media and seeing if that helps. What point is the install freezing up at??

---

### Post by OhioYJ on 2007-04-27
> Try burning the iso to brand new media and seeing if that helps. What point is the install freezing up at??

No the CD I know is good, it was burned on quality brand name media, and I actually just got done using the CD on another laptop, not more than an hour ago, so it's definitely good. It always freezes at the same point, no matter which Ubuntu CD or DVD I use.

As soon as the GUI for the install/live CD starts to appear (when the tan background shows up), and the sounds plays, I get a bunch of lines across the screen and everything stops.

---

### Post by whee on 2007-04-27
Freezes can also be caused due to faulty videocards. I used to have Ubuntu freeze every 5 minutes after which i had to reboot. It was due to a nvidia 6600GT videocard which had manufacturing errors.(there was a whole batch that had manufacturing errors i wasn't the only one with such a card with the exact same manufacturing errors)
But boy was it frustrating, it took quite a while before i was sure it was due to the videocard, tried to isolate the problem and am happy i found out the faulty video card was causing it.
Finally i removed the faulty videocard and the freezes stopped completely.

Though i'm not saying that this is the problem you are having(doubt it), but i mentioned it in the case there is even a tiny possibility that this is the case.

---

### Post by OhioYJ on 2007-04-27
I hope theres nothing wrong with my video cards, they were both purchased new, and running in SLI, they don't have any problems running any of the 3DMark series, or running Windows. I don't have any other PCIExpress based video cards to test the theory though.

---

### Post by whee on 2007-04-27
> **OhioYJ said:**
> I hope theres nothing wrong with my video cards, they were both purchased new, and running in SLI, they don't have any problems running any of the 3DMark series, or running Windows. I don't have any other PCIExpress based video cards to test the theory though.

If you don't have any freezes, crashes or bluescreens in Windows then i wouldn't worry about your cards having manufacturing errors.(i guess)
I had problems both in Windows and Linux(not just Ubuntu) with that particular faulty card.

---

### Post by OhioYJ on 2007-04-27
Hey it was at least a suggestion, thats what I'm looking for, as I'd love to completely give Windows the boot in my house.

---

### Post by Ducati427 on 2007-04-27
You may need to install Fiesty in command mode, i had that issue when i was using the beta with my 7800gtx card it woudnlt' install, so i had a friend of mine help me and he get it running, that may be the isssue,   



Will G.

---

### Post by Greg Knight on 2007-04-28
> **OhioYJ said:**
> Ok tried removing the 2nd video card, and no luck. Even tried the "Safe Graphics" option for install. Still locks up/freezes in the same spot.

Any more suggestions would be greatly appreciated.

Did you switch the mobo over to single card mode? (their is a small circuit board half the size of a stick of RAM that sits under my cards, turned one way is for SLI the other for single card)??

If you did, or that still doesn't work, try putting the card in the other slot.

But above all else.  Don't give up!

---

### Post by kpel on 2007-04-28
I have a Core 2 Duo E6600 with a 'false' SLI (the 7950 GX2).  I get all sorts of graphical corruption and apparent freezing when I load the LiveCD for Feisty, but if I just let it run things eventually complete and everything works.

I'm just wondering if it really is freezing, or if it's just flaking out for a minute or two like mine does before it gets going again.

---

### Post by OhioYJ on 2007-04-28
> **OhioYJ said:**
> Hey it was at least a suggestion, thats what I'm looking for, as I'd love to completely give Windows the boot in my house.

Still open to more suggestions? Bump to the top.....

---

### Post by OhioYJ on 2007-04-28
> **kpel said:**
> I'm just wondering if it really is freezing, or if it's just flaking out for a minute or two like mine does before it gets going again.

No I had the same thought, but I've gone to the store and come back, and its still in the same spot, so I'd say its really freezing.

---

### Post by themusicwave on 2007-04-29
My friend had this problem and I did manage to fix it.  I don't understand why this worked, but I simply restarted gnome by pressing ctrl+alt+backspace when the screen with the lines came up.  

Gnome restarted and it magically worked, he has never had a problem since and is still using piggy-backed dual graphics cards.

I hope this helps.

---

### Post by OhioYJ on 2007-04-30
Bump... Still no luck.

---

### Post by OhioYJ on 2007-05-14
I think I might be getting somewhere. Using the 6.10 alternative install CD, 32-bit, I was able to go through and complete the text based install. Restart and got the login screen for Ubuntu. Unfortunately, I still get the same thing, as soon as type in my username and password and the desktop starts to load it freezes/locks up.

I'm starting to wonder if its something GNOME and not "ubuntu". I'm going to download the KDE version tonight to test my theory.

Still open to any suggestions. Bump to the top....

---

### Post by OhioYJ on 2007-05-14
Ok for anyone following along..... or having a similar problem.

I finally got the Kubuntu live CD to work in safe graphics mode. KDE wouldn't boot normally though. I'm running the install now, so we'll see if it actually works.

Keeping in mind I'm still a Linux newbie, can I install Ubuntu without a GUI, then install the Nvidia drivers, then install GNOME?  My thinking is that the graphics cards are giving me some sort of conflict perhaps it is because they are BFG overclocked cards?

---

### Post by OhioYJ on 2007-05-14
Ok, I'm running Kubuntu on the desktop right now, even posting this using it.... However..... I'm not really digging KDE, I think I'd prefer GNOME for a GUI, is there anyway to switch over now that I have it up and running?

Why does Kubuntu run on my system but Ubuntu/GNOME does not?

---

### Post by OhioYJ on 2007-05-14
Shazam..... Ubuntu and GNOME are up and running on my desktop, complete with my dual monitors....

[img]http://www.cdmfabrication.com/bbpics/desklinux.jpg[/img]

That completely eliminates all microsoft products in my house!

---

### Post by OhioYJ on 2007-10-23
Crap its been so long since I did this, I can't remember what I did to make it finally work.... And I have to reinstall it, so any ideas?

---

