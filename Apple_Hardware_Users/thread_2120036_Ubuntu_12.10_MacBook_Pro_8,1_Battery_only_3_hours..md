---
title: "Ubuntu 12.10 MacBook Pro 8,1 Battery only 3 hours.."
date: 2013-02-25
forum: Apple Hardware Users
---

### Post by helios16v on 2013-02-25
Now that I have my desktop beast running I barely use my laptop any more so I decided to run this as my $1,500 facebook machine and use Ubuntu as the daily OS. The problem isn't that I'm getting about 3 hours of battery life (4 hours with the screen brightness on lowest, keyboard backlight off, and volume on mute) but it's that the guide I was using doesn't fully work as it says.

I used this guide and installed a compiled version of Ubuntu 12.10 for MacBook Pro 8,1
[https://help.ubuntu.com/community/MacBookPro8-2/Quantal](https://help.ubuntu.com/community/MacBookPro8-2/Quantal)

I used that guide and followed all the steps, I used an ethernet connection to do all of the updates and had to manually enable WiFi like it says further down that page. After enabling WiFi I went down futher to the battery section and there is a link that brought me here.
[http://ubuntuforums.org/showthread.php?t=1215928](http://ubuntuforums.org/showthread.php?t=1215928)

From there it says to do a number of things for the battery.
My battery reads 57.7wH however using the code```
cat /proc/acpi/battery/BAT0/info
``` won't work. I had to use a different code I googled.
To start up PowerTop the code supplied says
```
sudo powertop -d
``` however I had to use ```
sudo powertop --calibrate
``` which then shows that my watt hour usage is 21.7wH

I've tried the other codes further down the page and nothing seems to be working for me, I'm still only getting between 3 and 4 hours battery life when I should be getting between 8 and 12.

I would really like to start using this as my daily laptop again but this time with Ubuntu but this battery thing is killing me, I'm away from a charger for a lot longer then 3 to 4 hours a day. I would just barely make it though the day on a full battery running OS X so I need that battery life back to make this a feasible reality.

Thanks for any input, I looked into laptop-mode but that is apparently been disabled in 12.10.

---

### Post by nwalkey on 2013-02-25
That seems weird. I can get 2-3 hours on a much less efficient laptop... How many cycles are on your battery? Might be time for a new one. The macbook pro that I had went from getting 4-6 hours on a charge down to 1-2 hours after two years... It doesn't take time for their batteries to get less and less from a charge. Could also be the ubuntu set up. Do you have the right display drivers? Also what version of the macbook is it? (look up the year it should say something like macbook (8,1)

---

### Post by Chav on 2013-02-25
Does your machine have hybrid graphics?

---

### Post by helios16v on 2013-02-25
> **nwalkey said:**
> That seems weird. I can get 2-3 hours on a much less efficient laptop... How many cycles are on your battery? Might be time for a new one. The macbook pro that I had went from getting 4-6 hours on a charge down to 1-2 hours after two years... It doesn't take time for their batteries to get less and less from a charge. Could also be the ubuntu set up. Do you have the right display drivers? Also what version of the macbook is it? (look up the year it should say something like macbook (8,1)
My laptop is a 13" Mid 2010 MacBook Pro 8,1. I mentioned it above that my laptop is a MacBook Pro 8,1 and I used a guide specifically for the 8,1 8,2 8,3 etc so it would load the correct drivers for my laptop during install which is why I'm so thrown off by this battery problem.

Also, the afternoon before doing this I would get just over 11.5 hours of battery life on a full charge with the brightness at it's lowest, keyboard backlight off, and volume on mute but after installing Ubuntu 12.10 I get 4 hours on a full charge.

> **Chav said:**
> Does your machine have hybrid graphics?
I have integrated Intel HD Graphics 3000, comes standard on the 13" Mid 2010 MacBook Pro.

It just has something to do with the battery not being set properly. My battery reads as a 57.7wH battery, rather then Ubuntu running in between 9wH and 10wH on demand it's running it at 21.7wH so I need to lower that so it's between the regulated usage. I'm also assuming that draining my battery like this is not good for it at all.

So 57.7 watt hour battery divided by the 21.7 watt hours the laptop is using (21.7 watts per hour of use) drains the battery in 2.65 hours but since these laptops run "on demand" the watt hour changes as the computer needs more/less power so that's right around the 3 hour mark I'm getting with brightness, keyboard, and sound on full.

I just don't know how to change the way the OS sees my battery because it's reading it wrong thinking it requires 21.7wH when really it only needs about 9wH to 10wH

---

### Post by Chav on 2013-02-26
Have you tried setting all of powertop's tuneables to see if it is a power setting issue?

---

### Post by serpico007 on 2013-03-01
Even running OSX on my 17" model I barely got 3 - 4 hours from 2 new batteries. 8 - 12 hours is amazing.

---

### Post by yello_downunder on 2013-05-23
> **helios16v said:**
> 
Thanks for any input, I looked into laptop-mode but that is apparently been disabled in 12.10.

I have a 2011 Macbook Pro 8,1 (13"). When running powertop I see about 17-25W of power consumption, so with a ~60Wh battery that is about 3-4 hours of battery life. In OS X I get the advertised 7-8 hours. At one point I tested turning everything off (including X) and got it down to about 12W, but at that point the system is useless for web browsing.

I have other laptops as well, with the same effect.  Battery life seems to be about half as long as in OS X, or about 75% of Windows running time.  I think Windows is less efficient power-wise than OS X.

---

### Post by GhettoMrBob on 2013-05-25
There is a key piece of information incorrect about this post: you claim to have a mid-2010 13" MBP 8,1 with HD 3000 graphics. Either you have the 2011 8,1 model with HD 3000 graphics or you have a mid-2010 7,1 with Nvidia graphics. The information you've given is a combination of both.

That is just not possible. I work as an Apple technician and can tell you that model doesn't exist. I personally own the mid-2010 13" and it comes with Nvidia GeForce 320m graphics.

**IF** you do have the mid-2010 7,1 model, then I strongly advise installing the proprietary Nvidia drivers and enabling powermizer settings to either default or the next step up. This dramatically scales down the amount of power that the graphics draw and really help to extend the battery life. For example, my MBP is coming up on 3 years old and can still get a solid 4-5 hours on a charge while under OS X. My battery life has never been as good under Ubuntu but I can still squeeze at least 3.5-4 hours out of a charge, depending on the usage. Here's a useful link to enable the powermizer settings: linux.aldeby.org/post/nvidia-powermizer-powersaving.html
 
**IF** you have the 2011 model with HD 3000 graphics, I don't have much experience with this but I'd look to see if you can't downclock the graphics.

Also, you may want to look into installing tlp. A quick google search of tlp power ubuntu should bring that up.

---

