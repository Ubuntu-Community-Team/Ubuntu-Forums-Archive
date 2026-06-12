---
title: "Nexuiz, modern deathmatch on Linux PPC"
date: 2005-06-02
forum: Apple PPC Users
---

### Post by slux on 2005-06-02
I feel this warrants a little post on the PPC section here as well since the Linux x86 folks have had Doom 3, Enemy-territory, UT2004 etc. but until now the most advanced FPS you could play on Linux PPC was either Quake 2 or Cube.

Nexuiz is a huge leap forward as it is technically not from the yesterday of gaming although the advanced engine called DarkPlaces it uses does have it's roots in good old Quake 1.

And it's free. As in freedom. Everything including the maps, sounds, models and music is released under the GNU GPL, hoping to see it in many distributions including Ubuntu PPC.

Now It does have rather steep requirements and the best we ppc folk have is either the Radeon 9250 with r280 core and the DRI drivers or a r300-based card with the experimental r300 DRI drivers (Don't know how good those are). But I'm told it's been ran on an iBook with Linux PPC. I tried doing that myself but the Fedora install seems to have some issues with RAM so I was unsuccesful.

Anyone been able to run this? I know we won't be turning all effects on but I believe it should be playable.

Here's a link to the [Nexuiz thread in the gaming section](http://ubuntuforums.org/showthread.php?t=38615)

---

### Post by DJ_Max on 2005-06-05
Did you try to compile the glx or sdl version? I'm pretty sure the sdl version will run fine as long as you have the sdl packages. glx will take some tweaking.

---

### Post by slux on 2005-06-06
Tried both but I'm pretty sure there's something odd going on with that Fedora install since it's constantly running out of RAM even with desktop applications. I'm planning on replacing it with Ubuntu as soon as my Hoary CDs arrive.

Apparently this game is very CPU intensive (it's playable but I experience slowdowns on a AMD Duron 1,2GHz) but doesn't require too much from a video card. The 1GHz iBook I was planning on trying it on might be a bit slow...

---

### Post by DJ_Max on 2005-06-07
[QUOTE=slux]Tried both but I'm pretty sure there's something odd going on with that Fedora install since it's constantly running out of RAM even with desktop applications.[/QUOTE]
You might wanna read up on Linux a little more. This is how Linux works, it's been discussed numerous times. Don't worry about how much memory it uses, Linux will free it up as needed.

Some reference, 
[http://www.jonh.net/lppcfom-serve/cache/936.html](http://www.jonh.net/lppcfom-serve/cache/936.html)
[http://mail.nl.linux.org/linux-mm/2003-03/msg00077.html](http://mail.nl.linux.org/linux-mm/2003-03/msg00077.html)
> Memory Used - Amount of RAM in use by the computer. The kernel will attempt to use as much of this as possible through buffers and caching.
> Swap - It is possible to extend the memory space of the computer by using the hard drive as memory. This is called swap. Hard drives are typically several orders of magnitude slower than RAM so swap is only used when no RAM is available.

---

### Post by slux on 2005-06-07
[QUOTE=DJ_Max]You might wanna read up on Linux a little more. This is how Linux works, it's been discussed numerous times. Don't worry about how much memory it uses, Linux will free it up as needed.
[/QUOTE]

Heh, being a GNU/Linux user for now about 6 years straight, 5 of those exclusively and working as an admin I do very well know about that :)

Sorry, I wasn't very clear. Even a small number of apps tend to cause a lot of swapping on that machine and attempting to run Nexuiz sends it to an all-out swap hell with maybe 30 minutes of constant hd activity and no responsiveness from the machine. I've seen it experience similar things with a background compile going on while browsing the net.

I have no such problems on a 300MHz iBook G3 with a very similar amount of RAM. I've sometimes seen something similar but never as bad and constant as it is on that Fedora Core 3 prerelease PPC version.

---

### Post by DJ_Max on 2005-06-08
> **slux]Heh, being a GNU/Linux user for now about 6 years straight, 5 of those exclusively and working as an admin I do very well know about that :)
[/QUOTE]
Seems you have me beat.   said:**
> 
Sorry, I wasn't very clear. Even a small number of apps tend to cause a lot of swapping on that machine and attempting to run Nexuiz sends it to an all-out swap hell with maybe 30 minutes of constant hd activity and no responsiveness from the machine. I've seen it experience similar things with a background compile going on while browsing the net.

Oh, then you got yourself a problem when too much swap is used.  Your installation might be borked.

---

