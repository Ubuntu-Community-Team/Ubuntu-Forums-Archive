---
title: "Screen Brightness and Wireless LAN"
date: 2008-03-06
forum: Absolute Beginner Talk
---

### Post by Urufukiraa on 2008-03-06
Hello. I decided to finally scrap using Windows today, so I put in a CD I had ordered previously, and everything worked perfectly fine, until it came time to unplug my laptop's power cord.
My power was draining more than two times as fast (My battery had thirty minutes of battery time on Windows XP, but now only has about twelve minutes), after I did a little bit of research, I found out that it was the brightness was giving me the problem, and that the solution was to go into the Power Management properties, then hit "On Battery Power," to turn down the brightness.. 

To my dismay, the slider for that option was not there. So a friend who used Ubuntu for quite a while suggested that I updated (The CD I had was version 7.04),  because I likely had an extremely old version of the Power Management program. 
Well, I updated (It took almost three and a half hours due to my processor being old, so there is no way I will give up on getting it to work.) 
And, yet again, the Power Management center did not have the slider. 

I then noticed that my wireless card was not active on 2.6.22 (I believe that is the latest kernel?), so I hooked up to a wired connection and asked my friend how I to properly reinstall my drivers, he then told me to reboot into 2.6.20, which allowed me to connect to my wireless connection. 
Now, the answers to my questions here are probably painfully obvious, but I have been searching for almost eight hours now, and do not know where else to turn.
My questions are this, though:
How can I make my laptop's LCD dim so my battery lasts longer than twelve minutes? 
And, how would I go about getting and reinstalling my wireless drivers?

Thanks in advance.
 P.S I apologize if this post is too long.

Specs:
Toshiba Satellite A105-S101
• Intel® Celeron® M Processor 380
 o 1.60GHz, 1MB L2, 400MHz FSB
• ATI RADEON® XPRESS 200M Chipset
• Toshiba V.90 software modem
• 10/100 Base-TX Ethernet
• Atheros® 802.11b/g wireless-LAN

My current kernel is: Linux Toki-Laptop 2.6.20-15-generic #2 SMP Sun Apr 15 07:36:31 UTC 2007 i686 GNU/Linux

---

### Post by drascus on 2008-03-06
Most laptops screens can be dimmed or a brightend with a key board short cut. Its usually like Fn+F9 or something there will be a symbol on the F key that looks like a little sun with an up or down arrow. Hittin it while holding the Fn key should brighten or dim the screen. This isn't good for automatic mode but it will solve the problem.

---

### Post by incen on 2008-03-06
Yeah, you can usually dim your screen with some function key with your laptop keyboard. This is how I do when I try to tune the brightness. Also, you can add a new item on the panel to monitor your battery status. Right click on the panel -> add an item -> pick up the battery one.
However, I think the main problem is the life time of your battery. Neither 12 min nor 30 min sounds enough for a laptop. :(

---

### Post by Urufukiraa on 2008-03-06
Well, I just looked at my keyboard, F6, and F7 had the sun symbols, however, all F6 did with Fn/FnLock on was activate the tab key, and what F7 did with Fn/FnLock on was activate Caret mode. Thank you for the idea. [Edit:] Oh, and the battery has had problems since I got it, but best buy wouldn't exchange it even though I had paid a fee for a discount on a backup battery in the case of it malfunctioning. It also does not help that my father let it get wet while on charge.

---

### Post by Pobega on 2008-03-07
For your wireless card have you tried installing MadWiFi?

[http://madwifi.org/wiki/UserDocs/Distro/Ubuntu](http://madwifi.org/wiki/UserDocs/Distro/Ubuntu)

---

### Post by Urufukiraa on 2008-03-07
That fixed my wireless connection, it seems... However now my sound card is dead. Thank you for the help.

---

