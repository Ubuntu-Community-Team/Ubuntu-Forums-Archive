---
title: "Dual Boot XP after installing Ubuntu?"
date: 2007-11-12
forum: Absolute Beginner Talk
---

### Post by Difranco1911 on 2007-11-12
Well I purchased a barebones system and installed Ubuntu Gutsy from the get go.   I have everything in Gnome setup and have learned a ton about using linux.  Anyway there are certain hurdles that have yet to overcome, so I need to install Windows XP for Dual Boot. 

The reasons for needing XP:
Windows CE & ActiveSync 4.5
Cachemate for my PDA
Garmin GPSMAP 60CSx
GSAK (Geocaching Swiss Army Knife)

So how can I do this without wiping out my entire system to get XP Pro booting.  I really wish this were wasn't the case but I need to boot XP.    How about some VM app that would allow me to boot XP within Ubuntu?

Thanks in Advance,
Difranco

---

### Post by Hospadar on 2007-11-12
I'd first try using wine to see if you can run these apps.  I think the last time I tried to run the garmin map software with wine it didn't work quite right (I was using it with an etrex).  I know there are some native gps apps for linux that you might want to look into (gpsdrive).

As for GSAK and cachemate, I'm not sure if those could be run through wine, but you can always try first, some things run great right out of the box.  You might have a look into geotoad (installable from System->Administration->Synaptic, search for geotoad) and also if you search Add/Remove Programs under Applications for "palm" there's a whole bunch of stuff for syncing to palms.  Also I bet if you googled "palm linux" you'd find all kinds of stuff.

That said, if you can't get stuff working the way you want, either through native linux apps or running stuff under wine, you'll want to use gparted (installable through synaptic) to resize (make smaller) your main hard drive partition, and then use a windows install CD to install windows into this free space.  windows may overwrite the master boot record (where grub is, such that you couldn't boot into linux) at which point you would have to re-install grub (with a livecd from their website probably)

You may want to read up in the ubuntu community docs about dual booting, or do a quick forum or google search on the topic, you'll find tons of stuff.

Also note, that if you can't run things with wine or natively on linux with aforementioned tools, I would suggest a dual boot as opposed to a virtualized solution, as these can be difficult to set up, though if you're willing to stick through the setup, it will probably work just fine.

Some links for you:
[wine]("http://www.winehq.org/")
[geo tools for linux]("http://kitenet.net/%7Ejoey/blog/entry/linux_tools_for_geocaching/")

---

### Post by SpiritIsReality on 2007-11-13
howdy
I boot a few too, because I don't think a PIII can handle too much in the way of virtualization, but hopefully, the winter project is to get or put a dual core together. At least a P4 I hope.
Probably AMD. But back to your question. The reason I multi-boot is cause that's the way to run a PIII I reckon. It works.
3or4links
Unified documentation site - I need your input [http://ubuntuforums.org/showthread.php?t=579726](http://ubuntuforums.org/showthread.php?t=579726)
Documentation of Ubuntu [http://ubuntuforums.org/showthread.php?t=602668](http://ubuntuforums.org/showthread.php?t=602668)
Networking And Wireless Documentation Links [http://ubuntuforums.org/showthread.php?t=608751&highlight=documentation](http://ubuntuforums.org/showthread.php?t=608751&highlight=documentation)
LTSP Documentation Links [http://ubuntuforums.org/showthread.php?t=608744&highlight=documentation](http://ubuntuforums.org/showthread.php?t=608744&highlight=documentation)
I know there's multiboot at some of those places. But to be honest with you I'll have to check if the one I want to link you to is there. So just in case,
[http://www.google.ca/search?hl=en&q=grub+menu+boot+100&btnG=Google+Search&meta=](http://www.google.ca/search?hl=en&q=grub+menu+boot+100&btnG=Google+Search&meta=)
[http://www.justlinux.com/forum/showthread.php?threadid=143973](http://www.justlinux.com/forum/showthread.php?threadid=143973)

trails

---

### Post by Difranco1911 on 2007-11-13
I can sort of get GSAK to run in WINE.  However, my biggest problem is getting the information out of GSAK and into my GPSr and my PDA (Geocacching is all I have a PDA for).  Neither seems to work as they should in Linux and I have spent considerable time trying to work this out.    I don't really want to dual boot as it is a pain which I haven't done since I last toyed with Slackware back in '99/'00.

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-11-13
ya just install windows on a primary partion 
but windows is going to install its boot loader

then you have 2 options get windows boot loader to boot ubuntu or
reinstall the grub

---

### Post by ragadanga63 on 2007-11-13
Install XP on another partition.  Use Super Grub Disk to create GRUB bootloader.

---

### Post by SpiritIsReality on 2007-11-13
looks like that's so much for this thread, time to move on. way to go team!!!

---

