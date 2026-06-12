---
title: "Various Installation questions"
date: 2006-10-11
forum: Absolute Beginner Talk
---

### Post by jrz on 2006-10-11
We have a brand new (2day old) Compaq V3012AU notebook which we specifically requested a Linux OS rather than MS Windows. It uses an AMD Turion 64 X2 CPU, and when received and booted it displayed Ubuntu 6.06 as the OS they installed. How can I determine if it is the 64 bit OS for AMD or some other version such as i386 32 bit version? This may be important as we have not been able to get the Totem Movie Player v1.4.1 to play CD's, DVD's, divx avi, or mpg files and uncertain of what it can play, and searching for answers mentioned possibly having to install some additional CODECs and noted that Windows codec package cannot be used by the AMD64 version, so we don't know exactly what to install, and not understanding Linux are afraid to install many things not knowing where they will be placed so we wouldn't know how to remove them if they didn't work. Although I don't like MS Windows I have less fears using it as I have had so many bad experiences I have learned how to recover from mistakes. But Linux is new to me so I don't want to create a mess that might cause future problems, and am trying to do things correctly in the beginning. 

My primary question is: Is the Totem Movie Player which came installed capable of playing everything I might encounter, and if not should I first replace it or install an additional player. And in either case what codecs or additional installations would be necessary to eliminate having to search out and install something later. We would like to be sure we could play anything as we don't have easy internet access here.

One last question, as we live in Thailand, and travel around the world often purchasing CDs and DVDs from various areas we would like to assure that the region code doesn't get set in the DVD player as we already have DVDs from nearly every area possible. Can that be done in Linux? And if so is it simple?
Thanks for any help.

---

### Post by think13 on 2006-10-11
As for your version of Linux,
Open synaptic (system-administration-synaptic package manager)
Then search for 'linux-image' (w/o quotes)
Look for the one that is checked for you.
If it says something about 386, then you have the 32-bit version.
If it says something about 64, then you have 64-bit version
(pretty sure)  

hope that helps.

---

### Post by mediax on 2006-10-11
As a newbie myself, I've spent a lot of time playing with Totem, etc., attempting to get various video formats to play.

I think I've joined the majority who seem to consider Mplayer the best video player (although it took me ages to work out how to loop video clips in it! ](*,) )

Probably the most important thing for getting video to play well is to get the right codecs installed.  If you search for codecs in this forum, you'll find a number of guides on how to do this (I'd point you to one, but I don't have a link to one handy).  My personal advice is to install as many as possible - unless you have reservations about using non-open source software.

Good luck!

---

### Post by jrz on 2006-10-11
It looks like they installed the 32 bit 386 version. I don't know if that is good or bad, but it may simplify the codec problem according to another post I read.

---

### Post by PriceChild on 2006-10-11
Follow [http://wiki.ubuntu.com/RestrictedFormats](http://wiki.ubuntu.com/RestrictedFormats) for a good guide to install media formats.

---

### Post by az on 2006-10-11
> **PriceChild said:**
> Follow [http://wiki.ubuntu.com/RestrictedFormats](http://wiki.ubuntu.com/RestrictedFormats) for a good guide to install media formats.

That link also will lead you to a tool called regionset which will help you out with dvds from specific regions.

---

### Post by Fatjoint on 2006-10-11
I would download a copy of the Ubuntu Alternate Install before doing anything to make sure you have a way of re-installing.

Might also want to download the LIVE CD as well.

Once you have those things, you can play to your hearts content and try different things without worrying about it.  So what if you break it, reinstall.  

I blew my ubuntu up I think 3x in a two day period when I first started playing with it.  I knew very little of Linux then, but I discovered early on that if you create a /home partition to keep your stuff in, you're golden.  As long as you don't overwrite or format your /home partition you can install, reinstall, break by mistake, break on purpose, and still be cool.

---

### Post by bulldog on 2006-10-11
> **jrz said:**
> It looks like they installed the 32 bit 386 version. I don't know if that is good or bad, but it may simplify the codec problem according to another post I read.

The 32 bit version will do nicely :D I use it myself on a AMD X2.
You can take a look at Automatix to install a lot of usefull stuff at your choice.

[http://www.getautomatix.com/](http://www.getautomatix.com/)

---

### Post by PriceChild on 2006-10-11
> **azz said:**
> That link also will lead you to a tool called regionset which will help you out with dvds from specific regions.I bought some DVDs in New Zealand while i was there in the summer and the only thing they work on back home is my ubuntu box... i'm not complaining, just pleasantly surprised :)

---

### Post by gn2 on 2006-10-11
> **PriceChild said:**
> I bought some DVDs in New Zealand while i was there in the summer and the only thing they work on back home is my ubuntu box... i'm not complaining, just pleasantly surprised :)

Slysoft AnyDVD will sort you out for playing them in Windows and

DVD Shrink will let you back them up region-free.

---

