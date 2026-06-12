---
title: "Wired Ethernet Connection Issues"
date: 2006-04-09
forum: Absolute Beginner Talk
---

### Post by Sylvester Ink on 2006-04-09
Hello all, I'm a rather new Ubuntu user (or rather, Kubuntu), and I thought I'd give this forum a try for some of my problems.  I'm still getting used to the environment, so be patient with me.  :) 

I'm running the Breezy 5.10 release of Kubuntu on my laptop and set up my wired network card (PCMCIA) when I was initially installing Kubuntu.  I did a manual setup, since my home network is static.  After setting it up this way, everything ran perfect and I had no problems accessing my internet connection.

However, I recently tried to pop in my wireless card and see if I could set that up so I could access my school network (dhcp).  I started to set it up (no major network changes, just poking around the "System Settings->Network Settings" section) but realized that I didn't have WPA Supplicant installed.  So I unplugged the wireless card and tried to access the internet through my wired card to download the tools I'd need.

Unfortunately, I think I may have inadvertantly changed some minor setting somewhere (or that it may have been changed automatically) and as a result, I now can't access the internet through my wired card.  I've tried browsing my local network, and it's showing up just fine.  (I can access my PC through Samba without any problems.)  So I suspect it may have something to do with my DNS settings or my gateway settings.

For the default gateway, no IP address is specified, and whenever I try to specify it, the settings are forgotten by the time I leave the System Settings.  (I don't even think they're applied at all.)  Also, the domain name servers I previously entered are still there, unchanged.

All of this is done through the GUI System Settings manager in Kubuntu.  (I've also tried using kcontrol, but that made no difference.)

Any advice you folks have for me would be more than welcome.



Also, on a side note, I come to Ubuntu/Kubuntu from Suse, which I used for a short time before.  One of the nice things that Suse's Yast tool had was a Hardware Profile Manager, which kept various versions of your resources and allowed you to switch between different configurations easily.  (It also allowed you to rescue yourself from problems like the one I'm currently having by saving a good profile and reloading it if you jacked anything up.)  I mainly used it to switch between my home network settings and my school network settings.  Is there any such software available for Ubuntu that I may want to look into?  (And what is that Network Profiles thing in the Network Settings area?  It didn't seem to do much in the way of saving my butt.  :p )

Let me know what you think.  (And sorry if I made the post a bit long . . .)

---

### Post by gazj on 2006-04-09
I know this isn't much of a fix, but when i used kubuntu, i had the same problems, the network manager is really pants, what i used to do is install the gnome network tools, but that may be a problem without out a connection to the net

anyway here is the command to get it

```
sudo apt-get install gnome-system-tools
```

you can the start it with

```
sudo network-admin
```

not ideal but will work

---

### Post by Sylvester Ink on 2006-04-10
Yeah, I did notice the networking tools were a bit nicer for Ubuntu.  (Hopefully they'll be tweaked in future Kubuntu releases.)

In any case, is there any way to edit the config files manually?  That would probably be the most direct way to fix it, I should think.  I'd just need to know what files to edit and what values to set.  Any ideas?

---

### Post by Sylvester Ink on 2006-04-10
Sorry to double-post, but I've fixed the problem.  It looks like somehow my default gateway settings were deleted/removed.  I fixed it through the command-line, following the instructions here:

[http://www.linuxheadquarters.com/howto/networking/networkconfig.shtml](http://www.linuxheadquarters.com/howto/networking/networkconfig.shtml)
(It's basically instructions on configuring your network through the command line.)

Hopefully anyone else with similar issues will find this of use.  :-D

---

### Post by gazj on 2006-04-10
Glad you got it sorted ;) next thing i was going to was going to say was try using command line with the ifconfig command, but thought you might like a gui way out first, anyway helpful page there :)

---

### Post by Sylvester Ink on 2006-04-15
I know it's been some time since I posted, but I've had a busy week.

Anyway, I found out that my fix is reset every time I reboot.  Probably some set values of the network manager that are overwriting my changes.  In any case, I was wondering if there was any way to make this change automatically happen at boot up (some sort of quick-n-dirty bootup script).  This will be a temporary fix for the next two months or so.

Fortunately, I took a look at the Dapper roadmap, and it looks like the fix for this networking bug has been acknowledged and implemented, so I need only to wait until June.  :-D

---

