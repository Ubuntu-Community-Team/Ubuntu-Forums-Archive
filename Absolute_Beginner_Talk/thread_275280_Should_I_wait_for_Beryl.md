---
title: "Should I wait for Beryl?"
date: 2006-10-11
forum: Absolute Beginner Talk
---

### Post by dckirba on 2006-10-11
Hello all,

I've been trying to install either compiz or beryl on my computer at home : [http://www.ubuntuforums.org/showthread.php?t=274627](http://www.ubuntuforums.org/showthread.php?t=274627)
and have had no luck so far. Blank white screen. I know Beryl is far from finished software... should I just wait till a stable release is released?

I've followed every wiki I could find and every howto. Even tried mixing bits from one and the other :) 

I've heard Compiz is more stable at the moment, but I'm having trouble finding the latest packages. I have to download at work because my modem has gone cuckoo at home, so that is actually the majority of my problem.

So my major question is, how long till a stable beryl is out?

Cheers,
David K

---

### Post by PriceChild on 2006-10-11
I doubt you will have any problems if you follow the link i posted in the previous thread.

Edgy 0.1 has been released which is "stable"ish, however there are some very major bugs still out.

I do not advise that you install it on production machines. I do advise it as a tool to get your mates interested in linux though ;)

**[COLOR=Red]May i re-iterate that beryl is definately NOT a beginners subject.[/COLOR]**

---

### Post by smartalecks on 2006-10-11
The best guide I've come across for compiz is here:
[http://knowledge76.com/index.php/XGL/Compiz_Nvidia_32bit](http://knowledge76.com/index.php/XGL/Compiz_Nvidia_32bit)

The only thing I can say is to use the startup script in the "Discussion" tab instead of the one they suggest.

Once you get compiz running, switching to beryl is easy, although at the moment I reccomend Compiz because it 1) is more stable and 2) looks better atm.

---

### Post by dckirba on 2006-10-11
I asked the beryl forums for advice and I was told:

> Update your nvidia drivers and set up xorg properly not to use Xgl. This is not the bug but the configuration issue at your end.

I did follow the instructions on your link.

However, the one point I'm not too sure about is whether or not I have the latest Nvidia drivers. I installed the Nvidia driver from the install CD because it was avaialable and I didnt't have an internet connection at home and still don't :(

I assume they're not asking me to use the beta drivers.

I also thought Beryl could run on Xgl as well as Aiglx?

If I want to use Aiglx, do I have to update to Xorg7.1? Is this possible on Dapper?

Thanks again, sorry about all the questions, I don't know anything about this, just learning :)

Cheers,
David K

---

### Post by smartalecks on 2006-10-11
At the moment you are better off with XGL. Edgy is supposed to be released with Aiglx, and Beryl does or will (I am not sure, it definetly supports XGL atm however) support both.

I have the latest Nvidia drivers, I think:

nvidia-kernel-common: 20051028+1
nvidia-glx: 1.0.8762+2.6.5.11-5

---

### Post by PriceChild on 2006-10-11
The "latest" beta drivers are 9625 - beta

You do not need these, you will be fine with 8762, and more stable.

xorg7.1 is included in edgy and allows nvidia's latest drivers to run beryl, instead of the xgl work around. This is not possible in dapper and the general consencus is to remain using xgl with nvidia on dapper.

---

### Post by dckirba on 2006-10-12
Thankyou both :)

I am trying to hunt down a modem to use over this weekend at home and I should be able to update drivers and follow the howtos to the letter. I beleive that is what is causing most of my problems.

Thankyou again and I'll let you know on monday if it all worked :)

cheers,
david

---

