---
title: "Macbook Pro running hot"
date: 2007-04-25
forum: Apple Intel Users
---

### Post by thatswhatshesaid on 2007-04-25
I have one of the older mac book pros, the ones that ran really hot (like too hot for lap use sometimes).  In Mac OS X I could use programs like lobotomo or smc fan control to adjust the fan speeds to keep the laptop relatively cool.

I've installed feisty on my macbook pro (MBP) and I have noticed that it feels very hot like before especially when running VMware Server.  I have been searching around for a little while to find a solution to the problem.  I think that either there aren't many people with this issue (pretty unlikely) or that I just haven't been searching for the right things.

So far it looks like I can get the values for certain smc fan setting in the /sys/devices/platform/applesmc/ folder but it didn't seem that I could save the changes to the files using vi.  Also I saw a site that talked about recompiling the kernal with applesmc (is this what I have to do?).  

So has anyone else run into this before and could you point me in the right direction?  I'm probably not the most experienced user out there but I like to think that I can hold my own.  This is my first venture into linux on macs (I do have a laptop and a tower also running feisty though).

-Thanks

---

### Post by ronocdh on 2007-04-25
Well, first things first, I recommend you contribute to the [bug report]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/52852"). I assume any progress would be documented there first, then percolate through the rest of the community. If you do end up following the issue closely, please make sure to post back here!

Also, offhand I have to mention that I've heard the vi included in Ubuntu sucks, and a **sudo apt-get install vi** might help out better. I personally don't use vi, so I can't really say either way. =D

---

### Post by michaels on 2007-04-25
I've got this kind of problem before!!! Exactly the same!

However, I don't know I'm luck or not. My fan doesn't work well and the stupid mac engineer change the logic board of my macbook pro because they said they couldn't find the problem. After that, my mac doesn't get hot again! 

So, I think, the prolem is about your logic board. Even you find some program to handle this situation, just like in OS X, the problem will never be solved as you expect. The only way to work out is to talk to your mac reseller! Maybe they're willing to help you! because apple pays for your repairing not them!

Good luck!

---

### Post by Technoviking on 2007-04-26
If you use Feisty, you can do the following.
[http://www.jasonparekh.com/2006/macbook-fan-control-in-linux/](http://www.jasonparekh.com/2006/macbook-fan-control-in-linux/)
also check of this page.
[http://www.jasonparekh.com/?page_id=9](http://www.jasonparekh.com/?page_id=9)

---

### Post by mustang on 2007-04-27
> **thatswhatshesaid said:**
> I have one of the older mac book pros, the ones that ran really hot (like too hot for lap use sometimes).  In Mac OS X I could use programs like lobotomo or smc fan control to adjust the fan speeds to keep the laptop relatively cool.

I've installed feisty on my macbook pro (MBP) and I have noticed that it feels very hot like before especially when running VMware Server.  I have been searching around for a little while to find a solution to the problem.  I think that either there aren't many people with this issue (pretty unlikely) or that I just haven't been searching for the right things.

So far it looks like I can get the values for certain smc fan setting in the /sys/devices/platform/applesmc/ folder but it didn't seem that I could save the changes to the files using vi.  Also I saw a site that talked about recompiling the kernal with applesmc (is this what I have to do?).  

So has anyone else run into this before and could you point me in the right direction?  I'm probably not the most experienced user out there but I like to think that I can hold my own.  This is my first venture into linux on macs (I do have a laptop and a tower also running feisty though).

-Thanks

The problem is power management isn't fully there yet for linux on laptops much less for the macbooks in particular. There's some work being done and apparently the new 2.6.21 kernel has made some progress on power consumption but we'll see.

All linux macbook owners will get less battery life (and thus hotter laptops) than in OSX. What I usually do is set the minimum fan speed to 3000 like in the link provided above to mitigate the heat problem. There are no solutions for battery life just quite yet. We'll have to wait patiently for the kernel developers on that end.

Regarding applesmc:

> 
    1 This driver provides support for the Apple System Management Controller, which provides an accelerometer (Apple Sudden Motion Sensor), light sensors, temperature sensors, keyboard backlight control and fan control. Only Intel-based Apple's computers are supported (MacBook Pro, MacBook, MacMini). - 

So no, it's just for the sensors.

---

### Post by thatswhatshesaid on 2007-04-27
Thanks all for the advice.  After re-reading the links posted by Mike, I realized that I had forgotten to actually enable write permission on the devices before I tried to modify them. :oops: With that change made I can set the fan speed manually and the laptop is much cooler.

Thanks again, this was actually my first post to the forum but it has been indispensible in setting up my other ubuntu machines, it really is a great help.

---

