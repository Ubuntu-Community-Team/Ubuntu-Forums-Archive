---
title: "Advice on dumping Radeon for nVidia please"
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by boyturtle on 2007-04-27
After alot of trouble, a friend finally got My Radeon to work with DVDs, wmvs, etc. He followed the instructions from [http://ubuntuforums.org/showthread.php?t=321766&highlight=ati+radeon+xpress+200m+edgy+fglrx](http://ubuntuforums.org/showthread.php?t=321766&highlight=ati+radeon+xpress+200m+edgy+fglrx) and the videos all worked fantastically (better picture quality than in XP)  but in doing so lost all the desktop effects, as "ATI DOES NOT SUPPORT COMPOSITE EXTENSION!! "

Shame really, as I had grown very attached to my wobbly screen in the 2 days that i had it running and missed it terribly; so I thought that I would change my card to an nVidia FX5200 or 7300GT/GS but was advised that I could get wobbly screens on Beryl. so I followed the instructions from here [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Beryl_.28ATI.29;](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Beryl_.28ATI.29;) (Go to 1.9.1) but without reinstalling the card drivers.

I have a regret in doing this as I have taken a step back; the video quality is not very good now -not as bad as when i first installed feisty but back to sub windows quality AND I have no wobbly screen!!!!! 

My thoughts are that I will back track and undo Beryl instructions and remove XGL and reinstall the ATI drivers, at least that way I will have video that works, if not all the goodies; unless someone out there knows how to make this all work??

As I like all the wobbly bits, I may just take the plunge and get me an nVidia card and flog this on on eBay - shame really, as I only just bought it, but there you go. Any advice on the nVidia choices; does the fx 5200 do everything really well, or should I stump up the extra £40 for the 7300? If the latter, should I go for the GS or GT?

All help and advice greatly received from this Linux/Ubuntu novice

---

### Post by Belathor on 2007-04-27
I had Compiz working on my Intel GMA 900 integrated graphics chip so I doubt the nVidia GeForce FX5200 would have any problems.

---

### Post by orb9220 on 2007-04-27
> does the fx 5200 do everything really well, or should I stump up the extra £40 for the 7300? If the latter, should I go for the GS or GT?

Well I have a fX5200 dual monitors with 1.3ghz 640mb ram and all things are working, I am using the latest svn 0.3.0 beryl with things like wallpaper and screensaver plugins. Which allows you to set a time then the screen cube rotates back and slowly turns with transparency kinda cool.

The only draw back is the 128mb is limited.
If I have Firefox,Term,Nautilus,Amarok open and then try to open like Google Earth then google earth will go all black on trying to resize to larger. Reason ran out of video ram on card.

Solution any FX series with 256mb wil do much better.

So If you don't open a whole lot of graphics apps at same time than anything FX5200 or > will work with 90% of beryl plugins. With things like water or snow effects than you need a video card with more power and ram.

---

### Post by starcraft.man on 2007-04-27
I run beryl on my nvidia 6800 GT no problem. I've had 3 or maybe 4 nvidia cards over the years and can't say I've ever had any problems with em. As to removing and putting back your drivers, maybe you should opt for a clean install and copy your /home folder to a separate partition. Never know if theres any files left over that might cause problems ><. So if your buying a new card, go with Nvidia.

---

