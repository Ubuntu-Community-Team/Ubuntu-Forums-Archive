---
title: "Is Ubuntu right for me?"
date: 2007-12-11
forum: Absolute Beginner Talk
---

### Post by Roquelaure on 2007-12-11
Sorry for the lame title.

I was always interested in Ubuntu after I saw it in action with Beryl at my school.  I've never used it beyond a bit of tinkering with a live CD, so I was wondering..

Is there a way to run Ubuntu with Windows XP at the same time?  I'm not looking to dual-boot, but have both OS running at the exact same time, so I could game with XP and surf the web or do some other task with Ubuntu.  I don't even know if this is possible at all, to be honest.

Is there software that can run on Ubuntu that can run Windows software, such as system .exes or open up .rar or .zip files?

How secure is Ubuntu?  I've heard stories of people who had Linux seasons running for upwards to a year without a single crash.  I also play heavy on my XP system and usually have to reset once every four or five hours.  I usually do things like multimedia editing or Dvd ripping (for legit use, not piracy), and playing around with desktop customization.

I'm also a bit of a minimalist, preferring as few icons as possible on my desktop.

So any advice or help you guys can offer me?  I'm curious to see how far I can play with Ubuntu and look forward to any suggestions and answers you can offer me. :)

---

### Post by FuturePilot on 2007-12-11
Yes you could run Ubuntu inside XP via a Virtual Machine. However you won't be able to use any of the desktop effects since they don't work in VMs.

You can get some Windows software to work in Ubuntu with Wine. Success however is kind of hit or miss. I would suggest looking for a native Linux equivalent to a program before using Wine. And yes Ubuntu can open .zip and .rar files among many others. You'll need to install a couple things for .rar files though.

Here's a good read on security
[http://www.psychocats.net/ubuntu/security]("http://www.psychocats.net/ubuntu/security") 
Stability wise, it's very stable. In the somewhat rare event of an app crashing, it won't take the rest of the OS with it.

No icons on your desktop you say? Well you'll be happy to know the default install doesn't have a single icon on the desktop :D

Also have a look here
[Is Ubuntu for You?]("http://ubuntuforums.org/showthread.php?t=63315")

---

### Post by PeterJS on 2007-12-11
> **Roquelaure said:**
> Sorry for the lame title.

I was always interested in Ubuntu after I saw it in action with Beryl at my school.  I've never used it beyond a bit of tinkering with a live CD, so I was wondering..

Is there a way to run Ubuntu with Windows XP at the same time?  I'm not looking to dual-boot, but have both OS running at the exact same time, so I could game with XP and surf the web or do some other task with Ubuntu.  I don't even know if this is possible at all, to be honest.

Yes, this is possible, I've seen some impressive hackery done with virtual box, BUT it's not going to do you any good as windows running under Virtual Box has none to terrible 3d support so it's no good for gaming.

You didn't mention specific games, but Source games and WoW are running  very well under wine these days. 

> 
Is there software that can run on Ubuntu that can run Windows software, such as system .exes or open up .rar or .zip files?
Wine will run windows exes... kinda, it's hit or miss some things work, some require lots of tinkering, and some just don't. Which is pretty impressive given that neither system was designed to work that way. As for zips and rars there are absolutely archive tools for both the KDE and Gnome desktop (but don't ask me what the Gnome ones are).

> 
How secure is Ubuntu?Alcatraz has nothing on Ubuntu. The default settings are to having nothing open to in coming network connections, there's no need to have a firewall if there's nothing to protect. There are viruses, but they are far fewer, can't remember the last time I heard about one in the wild. The security model of good separation of user and admin rights makes it hard for nasty software to really make a mess of things. And if you really want to go all out there's Bastille and SELinux (ie the stuff the NSA uses).

> 
I've heard stories of people who had Linux seasons running for upwards to a year without a single crash.
My space heater/irc box has been running strong for 75 days now, and shows every sign of slowing down.

> 
I usually do things like multimedia editing or Dvd ripping (for legit use, not piracy), and playing around with desktop customization.Then let me point you to dvd::rip as far I've heard the only thing it doesn't do is rub your feet while it's working.

And for customization and eye candy nothing beats Compiz. There's more themes, icons, window borders, sounds, and who knows what else over at gnome-look.org than you can shake a stick at.

> 
I'm also a bit of a minimalist, preferring as few icons as possible on my desktop.
Might I suggest looking in to XFCE? That's what I'm running I have no icons on my desktop, and just a system tray in the corner, and someday I'll find a way to make it disappear too with out loosing the functionality of having a system tray. This is way cut down from the baseline desktop but if you're looking to slim down XFCE is a good place to start. And if you want to go the other direction you might want to look in to flux box and building up.

> 
So any advice or help you guys can offer me?  I'm curious to see how far I can play with Ubuntu and look forward to any suggestions and answers you can offer me. :)I'm here to answer questions, see my sig, and don't be afraid to flag me down to come look at a thread.

---

### Post by kpkeerthi on 2007-12-11
> 
I usually do things like multimedia editing or Dvd ripping (for legit use, not piracy), and playing around with desktop customization.

[www.ubuntustudio.com](www.ubuntustudio.com)

---

### Post by discoade on 2007-12-11
>                               I'm also a bit of a minimalist, preferring as few icons as possible on my desktop.You can set your top and bottom panels to auto hide so you have absolutely nothing showing on your desktop! (gnome)

---

