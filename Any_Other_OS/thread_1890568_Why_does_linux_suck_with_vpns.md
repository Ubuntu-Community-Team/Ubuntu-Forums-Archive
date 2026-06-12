---
title: "Why does linux suck with vpns?"
date: 2011-12-03
forum: Any Other OS
---

### Post by jared8783 on 2011-12-03
I have linux mint 11 so i figured i would post here as well since mint is based on ubuntu

Ok so i have attempted to make linux mint 11 my primary OS.
The only thing I need it to really do well is the internet.
If I can't get it too then i will delete the entire OS.

I use a vpn service to browse the internet for privacy and securtiy.
purevpn.com to be exact
with linux the connection slows to unbearable speeds in ten minutes to an hour from initializing the connection.
i have to reset the connection to get a decent speed and often have to log out to do so

I have NONE of these problems in winows seven or xp
in windows i just connect once and forget its happy surfing from there

i really dont want to give up on linux
but if i cant fix this i will
so please gimme some advice

the connection type is pptp
unfortunately the company i have choosen doesnt offer an opnevpn
though they have many countries to choose from and a minimal logging policy, unlike hma and their two year logging bs

thanks
jared

---

### Post by sammiev on 2011-12-03
I use [Witopiawiki]("http://wiki.personalvpn.net/wiki/Main_Page") and find them very good. Should add, I use it for Linux.

---

### Post by bluexrider on 2011-12-03
> **jared8783 said:**
> I have linux mint 11 so i figured i would post here as well since mint is based on ubuntu

Ok so i have attempted to make linux mint 11 my primary OS.
The only thing I need it to really do well is the internet.
If I can't get it too then i will delete the entire OS.

I use a vpn service to browse the internet for privacy and securtiy.
purevpn.com to be exact
with linux the connection slows to unbearable speeds in ten minutes to an hour from initializing the connection.
i have to reset the connection to get a decent speed and often have to log out to do so

I have NONE of these problems in winows seven or xp
in windows i just connect once and forget its happy surfing from there

i really dont want to give up on linux
but if i cant fix this i will
so please gimme some advice

the connection type is pptp
unfortunately the company i have choosen doesnt offer an opnevpn
though they have many countries to choose from and a minimal logging policy, unlike hma and their two year logging bs

thanks
jared


I would think your question is rhetorical. 

I currently use a VPN that goes with my CISCO router and don't have any issues. 

the question may be why does openvpn suck?

do you know for a fact that this type of connection speed isn't an issue with your ISP or that a different box connects quicker? Just asking

as for as a LINUX Issue. Try a different distro see if you get a different answer

---

### Post by Perfect Storm on 2011-12-03
Moved to Other OS/Distro Talk.

---

### Post by BrokenKingpin on 2011-12-05
I use VPN from Ubuntu to get onto my work's network, and I have no speed or reliability issues what so ever.

I also have a friend that usees a VPN connection for safe browsing under Debian with no issues.

Maybe it is the VPN provider.

---

### Post by jared8783 on 2011-12-06
well then perhaps it is an issue with linux mint in particular
because it happens on mint on both my desktop and laptop
maybe a diff distro would work better

it is surely not an issue with purevpn 
as i stated in my op i have zero vpn issues in windows
and as i said in my op i am using pptp not openvpn

im still open to suggestion if anyone has any ideas cuz other than this i really like mint

---

### Post by SeijiSensei on 2011-12-06
Try enabling the [debug option for pptpd]("http://www.linux.org.au/~quozl/pptp/pptpd.conf.5.html") and see what it logs to /var/log/syslog.

---

