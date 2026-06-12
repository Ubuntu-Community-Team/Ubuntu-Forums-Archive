---
title: "Windows Home Server (WHS) Killer!"
date: 2007-12-11
forum: Absolute Beginner Talk
---

### Post by linuxbee on 2007-12-11
Here is the mission:

An Ubuntu Server installed with all possible graphical interfaces (for beginners like myself) functioning as a Home Server which can provide the following services:

- files sharing
- media files sharing (video/movies sharing without downloading to the client)
- printer sharing
- scanner/fax sharing

- email server
- proxy server
- database server
- website server - light traffic for sharing with family and friends

Additional functions/services that will be nice:
- webcam/security cam connection 
- file backup automated
 
If the above services/functions can be implemented and combined into one installation CD/DVD, then I think it can be a real Windows Home Server killer - assuming all these can be accessed through an GUI.

What I meant is a package of all the above combined into a CD/DVD that any ordinary person can just put it in their machine and have it installed and after its amazingly fast installation time (Ubuntu took about 15 - 25 minutes as I timed) faced with a nice GUI?  I am sure most (if not all) of the above functionalities are already out there available, implementable, they just need someone capable with a better marketing sense (or someone who really know the problems a common computer user is facing).

The reason I am posting this is because after a few days of trying to learn and install Ubuntu desktop and server, I think its still too much for ordinary users (including those who may buy and use WHS) to handle and manage to have this nice Linux favor to be up and running - especially when presented with the pure text screen after installing the Ubuntu server version (7.10).

I understand that by using GUI in a server will compromise the security and performance to an extend, but if the point is to have a WHS killer, GUI is the way and I think even with the compromised security/performance, the level Linux may provide is still better than Windows. 

---------------

Any suggestion for the above configurations will be appreciated - I really would rather spend a bit more time to learn about using linux (even though I have to learn some command line operations) than pay $170 for another Windows products.

---

### Post by tgalati4 on 2007-12-11
My Mint 4 installation took 18 minutes from disk to reboot to surf.

Let's call the project:  Obvious!

---

### Post by MetalMusicAddict on 2007-12-11
This is already being worked on, but seems to have stalled.

[http://www.ubuntuhomeserver.org](http://www.ubuntuhomeserver.org)

There's another project as well but I forget the name. Searching these forums will show many posts about this.

Theres also: [http://www.freenas.org](http://www.freenas.org)

---

### Post by jflaker on 2007-12-11
All that stuff is great, but the ability to PXE boot machines to install *Ubutu (all flavors if enough space exists).  

Once the clients are installed, I want to be able to manage those systems from the console....remote and silent software installs .......config restores, User security based on a security model stored on the server..........

Among other things......this should be fun to watch grow.

---

### Post by llamakc on 2007-12-11
It's an intriguing idea but not really fodder for the "Absolute Beginner" forum IMO.

---

### Post by linuxbee on 2007-12-11
Guys, thanks for the responses!

I'll put it this way, as a long-time Windows user and a know-nothing linux beginner, I don't mind paying a reasonable price for a "Ubuntu Home Server" which has a nice GUI and can do the functions needed for my home and my home-office (which WHS seems to be able to do most, but Windows is something I really want to avoid).

I think normal users wouldn't want to wait for another year or so when WHS has already taken over the market, I hope someone out there with enough technical knowledge (too bad I'm not 'the one') should quickly assembly a Home Server package (e.g. into one single CD) with the 'already available' GUIs with as much functionalities as possible.

The point is timing, spending too much time in developing a perfect (functional/technical-wise) package would mean nothing to the market. Any additional functions can be added later.

The time is now...

---

### Post by MetalMusicAddict on 2007-12-11
> **linuxbee said:**
> The time is now...

And money makes the world go round.

As a volunteer/community developer this is just the fact of the matter. As I see things our current volunteer developer community is stretched very thin. Users have grow at a huge rate where the developers have not.

I do think the time is now but there just doesnt seem to be anyone willing to do it for free. Id love to but between Ubuntu Studio and family life I dont have the time.

---

### Post by llamakc on 2007-12-11
All you need is one meta-package. That's it.

---

### Post by MetalMusicAddict on 2007-12-11
> **llamakc said:**
> All you need is one meta-package. That's it.

No. The functionality people want is much more than a collection of packages.

---

### Post by linuxbee on 2007-12-11
Good point. 

And I appreciate those who dedicate their time and energy in developing a nice favor of Linux like this one. That's why, as a user, I don't mind paying a reasonable price for a user-friendly (with GUIs) "Ubuntu Home Server", and I think there are plenty of my type out there... : )

And I think its economically sensible for those of you with the ability to assembly a package (with the ready-made GUIs/technologies - instead of further development/new functions additions) to make it happen NOW... I am assuming to "assembly" a package with the already-made applications is much faster/easier than developing a brand new version of another Linux server for this purpose.

Forgive me if I'm ignorant in how to "cash-in" from this type of package, but I assume if functional-wise, Linux can be a Home Server, and the suitable GUIs are out there, then the next sensible and marketable thing to do is to combine/assembly them into a user friendly CD/DVD, which can be sold for $50 - $100 each (considering MS is selling their OEM version of WHS for about $170).  Which, if viable, should be a way to help the volunteers for this great OS and continue their good works.

The reason I started this topic is that, after trying Ubuntu in the past few days, I believe Linux (like Ubuntu) is mature enough for the end-users, and the market for Home Server is also mature enough to "start the engine" (I think that's why MS has started to promote/sell them) now.

P.S. Just a though from a Linux beginner:

I think the technology behind "Home Server" is nothing really ground-breaking, its the concept (or the term itself) that really count - it fits the current market. 

Comparing Linux (and its different favors) to Windows, drivers for different hardware could be the problem, so something like file (and media files) sharing, database/proxy/email/web servers should be implemented in the Linux favor of the "Home Server" without losing too much to Windows, and actually those should be the strengths of Linux, afterall that is what the Internet host with.

---

### Post by MetalMusicAddict on 2007-12-12
I've actually just reached out to the [Ubuntu Home Server]("http://www.ubuntuhomeserver.org") guys to see if I can help move their project along. With my work in Ubuntu Studio, and their dedication, I'm sure I can give them a boost.

---

### Post by linuxbee on 2007-12-12
Great... good luck to you and to us who are waiting to see it happens.... I'll keep an eye on the Ubuntu HS pages...

If you guys need any pure-user (non-technical) input, let me know.. : )

---

### Post by MetalMusicAddict on 2007-12-12
Another is [E-box]("http://ebox-platform.com"). Which looks to be coming along quite well.

---

### Post by citybird on 2008-01-14
try PXE booting to a TFTP server and using a network install. The choices there are staggering!!

---

