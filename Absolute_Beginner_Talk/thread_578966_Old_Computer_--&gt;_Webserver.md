---
title: "Old Computer --&gt; Webserver"
date: 2007-10-17
forum: Absolute Beginner Talk
---

### Post by PooingCavy on 2007-10-17
Hey, um, im looking into turning my old Wndows 98 with 5gb hard drive (2.5 gb free), 96MB ram,a nd about 400 or 600 megahurtz speed into a webserver for my not-high-load site LettuceandCarrots.com.

Ive been looking into getting 98 replaced with a free linux build made for servers. I am looking to find a distro that matches this criteria:

[install] Fits on a single 700mb CD
Allows the use to have a LAMP system (or variants)
Can be connect to my home cable thing and basically hosts a site.
Wont totally replace windows (I have some nostalgia I like to play with on there) (I already have a cleared out 2.5 gb partition)
MUST have PHP enabled.
Not all flashy, no Beryl or anything or screen savers, I just need something to use to host my site.
Be able to host a Vent server.

Thats pretty much it. I am a freshman in highschool, and as a result, I cant just drop down even 300 dollars for some new-ish computer with better specs, not can I get one of those stacking servers with like 8gb ram and such.

My dad is in IT, so he cold be able to help me, but I have experience with computers. Networking is not my thing yet, and I have only had like an hour of linux experience. I hope to replace my WIndows partition on my Macbook with Linux soon.

Thanks!

---

### Post by Sef on 2007-10-17
> [install] Fits on a single 700mb CD

Yes.

> Allows the use to have a LAMP system (or variants)

Yes.

> Can be connect to my home cable thing and basically hosts a site.

Yes, if your cable has DHCP, it will connect automatically.

> Wont totally replace windows (I have some nostalgia I like to play with on there) (I already have a cleared out 2.5 gb partition)

It should be enough for a server if you run it from the command line.

> MUST have PHP enabled.

Yes, it has.


> Not all flashy, no Beryl or anything or screen savers, I just need something to use to host my site.

Can be declined or turned off.


> Be able to host a Vent server.

Not sure.

---

### Post by PooingCavy on 2007-10-17
Um, sorry, I forgot to mention, I tried 6.06 LTS ubuntu server, but it isnt installing right. Also, sorry Ubuntu lovers, but all I see is Redhat and SuSE being the top ones, but I havent heard any lovefor Ubuntu.

---

### Post by Kilz on 2007-10-17
The amount of ram may be an issue. [You may want to look at at this page.]("https://help.ubuntu.com/community/Installation/LowMemorySystems")

---

### Post by PooingCavy on 2007-10-17
Thanks for the link, but the install issue I did not clarify. I meant there was somehting wrong witht he installer IE it didn't find some components. I think there is something wrong witht he ISOs. Anyways, it was installing nicely ont he machine until it ran into the missing commponents thing.

Im going to try the 7.04 disc.

Unfortunaly, live used up all my CD-Rs and I onyl have a CD-RW left. Ill try as many linux builds as I need.

Are there any other linux distros that would run well.

---

### Post by KCPokes on 2007-10-17
I'd recommend going with a pure CLI distro as you'll save a lot of resources by not running X or a desktop environment.  You are going to have a hard time running any full distro with only 96MB of RAM.  There are some good lightweight distros out there (search the forums) that you could try.  My personal choice, which I've said many times recently, is Arch LInux for those low powered machines.  By default it doesn't have an X server or desktop environment, which you can choose to install if you want (something like Fluxbox or Openbox would be a good lightweight choice if you did decide to go with one) or you can stick with just commandline.  Installing something like Webmin can help you with the configuration if you aren't comfortable with doing everything via a terminal window.

---

### Post by PooingCavy on 2007-10-17
CRAP! My drive won't recognize CD-RWS?!?

Is there osmehting that doesn't require any media, and I just download and install direct-to-drive

---

### Post by Lostincyberspace on 2007-10-22
for servers i use Cent Os it is red hat clone that is very dependable i host sites and vent on it

---

### Post by russell.h on 2007-10-22
Another thing, you may have DNS difficulties if you just have a regular cable connection. Most cable is dynamic IP, in which case you will want to use dyndns.org or the like, but that won't let you use your current domain name. I think it depends on your cable company, and possibly on your domain registrar although I'm not sure of that.

Ubuntu is based on debian, which is a **very** solid distro for servers and the like. What I'm not sure of is how well it will run on your computer. I have a computer that is similar in all respects except it has 256mb of RAM, and it ran Ubuntu server beautifully. Debian should be almost the same for server I would think.

---

### Post by cfaulkner on 2007-10-22
Don't mean no disrespect to the Ubuntu peeps, but Gentoo has a 2007.0 minimal (55mb) iso disc you can put on that pc.  Just follow the x86 howto install guide on their site [www.gentoo.org](www.gentoo.org) 

and load a minimal linux..  you might want to bump the ram up to at least 256mb ram

I have Mysql, php, apache2 and Teamspeak running on my 600mhz 256 mb ram box on gentoo 2007.0

---

### Post by LanDan on 2007-10-22
96MB should be fine, and any distro should be able to handle it. and any distro can run these packages

then what is the difference between all these distro's?
packagemanagement!!!!!

just see what you are comfortable with

i could also recomend you Debian or FreeBSD, but they all can do the same so the choice is yours, i would say do some reading and try 1 or 2 and see where you get a warm and fuzzy feeling ;)

---

