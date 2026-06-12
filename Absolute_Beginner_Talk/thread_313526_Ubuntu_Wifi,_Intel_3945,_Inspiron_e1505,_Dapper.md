---
title: "Ubuntu Wifi, Intel 3945, Inspiron e1505, Dapper"
date: 2006-12-06
forum: Absolute Beginner Talk
---

### Post by Taigrr on 2006-12-06
Alright, I got wireless to connect, finaly. It does work. When it connects, the wireless light on the laptop lights up and everything. But, it cuts out alot. The light will flicker, then completely shut off for a few seconds, then flickers and lights back up. But, when the light flickers, the laptop stops responding. The cursor will stick for a minute, even as I type this. Hit the key's, and it hangs for a second, then blam, there's the text all of a sudden.

I used an installation script written by Wheelspin, so now I guess is there anything else? I changed the excryption from Hexidecimal to Plain, nothing. So I changed it back,   and went from DHCP to Static. Same problem.

Does anyone have ANY other ideas? This is throwing me for a loop.

---

### Post by Taigrr on 2006-12-06
Don't mean to bump, but...

*bump*

I've been working on it all night, and can't even begin to find what's going on.

---

### Post by PiggyGirl on 2006-12-07
Did you make any progress? 

Does anyone have any ideas on this?  I am having a similar problem and really need some help, if at ALL possible

Thanks :)

---

### Post by Taigrr on 2006-12-08
So no one knows what's going on?

This card was supposed to work "Out of the box", and didn't. Apearently it doens't even work after you get it to work.


I un-protected the wireless on the router, I installed and tried on Edgy, I threw it, kicked it, smacked it. 

Come on, someone has to know -something-. Hell, i'll send any of you the laptop if you think you can do it. I'll even throw in fifty bucks.

---

### Post by Taigrr on 2006-12-09
Well, I tried using the card with NDISWrapper, and uninstalled network-manager-gnome. Still flickers around.

So is there something else I should look for? Come on. This card worked for other people, so there's gotta just be an odd config file somewhere, right?

---

### Post by Taigrr on 2006-12-20
Anyone have any ideas now?

Or can someone point me in the right direction?

---

### Post by NewDisciple on 2006-12-20
I have the same wireless module on a Dell E1705 and mine works out of the box.  What application are you using to configure your network connections and what settings did you use?

---

### Post by macogw on 2006-12-20
Mine worked OOTB :/  I don't know what's wrong with yours

---

### Post by Taigrr on 2006-12-21
My card doesn't work -at all- until I install network-manager-gnome. It didn't on the old laptop either, which was identicle, as this one replaced it.

By out of the box, you mean right after install, yeah? 'Cause mine isn't there...

---

### Post by macogw on 2006-12-21
If it cuts out a lot, did you try just moving it somewhere else?  You could be getting a crappy signal.  I know mine really hates connecting to anything < 50% and it'll cut out a bunch then.

---

### Post by NewDisciple on 2006-12-21
On mine I had to use Wi-Fi Radar to connect to the correct SSID as there was interference from other networks in the area.  Depending upon their proximity you may be attached to a different network which is giving you a weaker signal.

---

### Post by NewDisciple on 2006-12-21
On mine I also used wi-fi radar to get the correct SSID because of other networks in the area.  If you are connecting to another network and not your own it will give you a weak signal and cause the problems you have described.

---

### Post by NewDisciple on 2006-12-21
Sorry about that!  I didn't think the first one posted.

---

### Post by Taigrr on 2006-12-22
Works in theory. But unfortunately, the laptop has been sitting RIGHT next to the router. It's been in the libing room too. Also, at a few free wifi places, where it still does it. It always seems to take a few minutes before acting up, though.

---

### Post by NewDisciple on 2006-12-23
Around the first part of this year I had some problems and discovered that heat wasted my Belkin router.  (just an idea)  Also have you tried resetting your router?Beyond this I have no other ideas.

---

### Post by nicknn on 2006-12-30
> **Taigrr said:**
> Anyone have any ideas now?

Or can someone point me in the right direction?

Hi,
I have an intel 3945 on my dell inspiron 6400 running edgy
got it working following these instructions:
[http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html](http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html)

---

### Post by aquaxbat on 2007-01-01
Ok, so I am a dork, semi-newb, whatever the case may be. I ordered an Intel 3945ABG mini pci card for my laptop. I am running Edgy 6.10 64-bit (could not for the life of me get 32-bit to work) on a Mobile AMD Sempron 3500+ (1.8GHz/512KB). I don't see why an Intel wireless card would pose any problems with an AMD chipset.

I put the new card in and attempted to make it work but with no success. There are just too many places with too many ways to get it to work to really understand things.

SO, i reloaded Edgy back onto my laptop in hopes that it would recognize it but when i enter in: lspci ... i still seem the lameazz Broadcom ethernet controller. Now is this due to the fact that there is an RJ-45 connection?? I can get online with my laptop as long as it is wired.

Does anyone have a really good site or recommendation on this?? i.e. i am a dumbass :neutral: or here's something that might help or you're screwed put your old card back in.

I would just love to have my laptop wireless with linux, i can't stand windoze and i am never going back.

Oh i am going to attempt the link above to see how it works. Until then...

---

### Post by internlover on 2007-01-03
Sorry can't help mine worked oob with card in hp 5220. good luck.

---

### Post by bsgjunkie on 2007-01-05
> **Taigrr said:**
> Alright, I got wireless to connect, finaly. It does work. When it connects, the wireless light on the laptop lights up and everything. But, it cuts out alot. The light will flicker, then completely shut off for a few seconds, then flickers and lights back up. But, when the light flickers, the laptop stops responding. The cursor will stick for a minute, even as I type this. Hit the key's, and it hangs for a second, then blam, there's the text all of a sudden.

I used an installation script written by Wheelspin, so now I guess is there anything else? I changed the excryption from Hexidecimal to Plain, nothing. So I changed it back,   and went from DHCP to Static. Same problem.

Does anyone have ANY other ideas? This is throwing me for a loop.

Any progress on this? I have the exact same problem. I had the bug that a few others noted where the 3945 wasn't recognized OTB and installed the linux-restricted-modules-generic - its now recognized, but I have the EXACT same problem as you've posted above. Any help would be appreciated.

Junkie

---

### Post by bsgjunkie on 2007-01-05
I'm starting to wonder if its a bad card instead of an error within linux.

In windows my internet connection will continuously drop at times. When it drops, it reconnects quickly, but each time it produces the network problem pop up from the intel wifi manager. Some times the connections is perfectly fine, others it'll do it for my entire connection time. Some networks seems to be better then others, but its not one specific network.

Any help would  be appreciated.
Junkie

---

### Post by Taigrr on 2007-01-11
Well, I doubt it's a bad card. It did the same exact thing on the first identicle laptop which got sent back to be replaced. Also, it's nothing with the router. I've tried it here many times, plus, a coffee shop not far from here, a mall just down the highway, and a 24 hour resteraunt with free wifi.

Internet works fine, not a single problem, with Windows. But when I use Ubuntu, it starts screwing around.

Does anyone know if it could be something with another module, or program? Or interfeering with other drivers? Or.. Something? Maybe the program doing something, because it thinks you're turning off the wireless?

Someone's gotta know. I'd be willing to open up my laptop to a knowlegable party. Send it right to a developer to figure it out.

---

### Post by Taigrr on 2007-02-17
Just checking back. It's been a few months, so was wondering if anyone has come across a fix for this issue?

---

### Post by Taigrr on 2007-03-14
I'm not givin' up on this!

Come on, anyone? Any hint, push, nudge or general glance in the right direction?

---

### Post by jakev383 on 2007-04-04
I have an E1505 that had the 3945ABG card in it and was able to get it working about as well as yours is - it would drop from time to time. To get it that far I had to use a different version of the firmware for it than shipped with Edgy.
I ended up buying a Broadcom off of Ebay and installing that with ndiswrapper. Haven't had a problem since. There's been talk of it working better with the inclusion of proprietary drivers in Fawn.....

---

### Post by sstakes1 on 2007-04-04
I'm guessing you are using WiFi-Radar. You need to close the WiFi-Radar Gui as soon as you are connected. On my laptop I noticed that when this window is open, it tries to scout around for available networks and when it does so, the green wireless light flickers and your laptop is locked.


HTH

---

