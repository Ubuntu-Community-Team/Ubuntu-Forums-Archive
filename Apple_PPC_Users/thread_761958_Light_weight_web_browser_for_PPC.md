---
title: "Light weight web browser for PPC"
date: 2008-04-21
forum: Apple PPC Users
---

### Post by employeeno5 on 2008-04-21
Hi.

I built my girlfriend an iBook G4 on the cheap out of old broken ibooks.

I had enough left over parts to put together a second ibook (a very slow G3), which I donated to a friend in need.

It's a 500Mghz and 500MB RAM.

Despite limitations with the PPC architecture and Linux, she enthusiastically embraced Xubuntu (PPC 7.04) on her new machine. I got everything she needed running easily enough.

Now, she's in town on a visit and I'm trying to do some tune-ups for her. Despite everything working correctly, Xubuntu still runs pretty darn slow on this machine. 

I decided to try using just fluxbox for her WM and got rid of the desktop. Now we're flying and she's very fond of the slick and minimal interface fluxbox provides.

We still have one problem though: Firefox. It runs so slow. Crazy slow. Nothing is broken with it, but checking a gmail account is an excruciating process.

Could someone recommend light-weight (but still graphical) web browsers that are compiled for PPC? They do not need to be feature rich in terms of things like tabbing and bookmarks and what not, just able to handle most of  the modern non-proprietary web. 

I've heard that Kazehakase is good for that but I haven't found any PPC availability if there is any.
Any other reccomendations? Even if it's not anythings super light weight, just anything better than Firefox 2. 

Many thanks for any ideas.

---

### Post by abtabt on 2008-04-21
try dillo (not like firefox but a lot off speed )



for WM i use icewm i like it

---

### Post by stream303 on 2008-04-21
Sure - try the Epiphany browser.  Very similar to Firefox, but much lighter in weight - uses the same Gecko engine for now...

If you install it, be sure to look for epiphany-browser, as there is another package with the same name of just epiphany that you probably don't want.

If she doesn't run a lot of firefox-specific extensions, you'll be good to go.

If the router isn't too adept at using ipv6, perhaps telling firefox (and epiphany-browser) to stick to ipv4 might also help - in the url bar, just type
```
about:config
```
and search for ipv6 in the filter bar.  Double-Click on "network.dns.disableIPv6" to change the boolean value from false to true, and restart the browser.

Update: Sorry to keep throwing these things at you, but after installation, have you used top, or my favorite HTOP, to see if anything is sucking up all your resources?  On my iBook, I found Network Manager eating up 100% of my cpu, and had to disable Network Manager, rather than remove it...

---

### Post by oswaldkelso on 2008-04-21
on my daughters imac 333 mhz with 256 mb running debian testing we have the browser with the hardest name in the world to remember. kazehakase

[http://kazehakase.sourceforge.jp/](http://kazehakase.sourceforge.jp/)

I'm pretty sure it's in the ubuntu repos

It's a nice browser that has some nice features it loads quikly on that low end machine.

Also there is a version of dillo with tabs ( I use it in dsl ) dillo is fast, fast, fast, but not feature rich when it comes to media but for your regular sites that you know work its nice. (search tabbed dillo )

---

### Post by phreakout on 2008-04-22
That japanese browser is bundled with fluxbuntu.

---

### Post by employeeno5 on 2008-04-22
I haven't had any luck compiling Kazehakase from source which as far as I can tell is the only way I can get it installed. If anyone knows a repository with it that would be great, but as far as I can tell it's not in the Feisty Xubuntu repositories. Kazehakase was my first choice originally though. 

Dillo installed fine but appears unable to open gmail and many other pages. Perhaps I installed an older version or need to add some extensions or some kind?

Epiphany! Jeez, thanks for the heads up on "epiphany-browser" because I had been doing exactly what you were warning me not to. I will make Epiphany the next attempt.  

I can't check up on the dns lookups (thanks for the advice though) or try too much else right now because my friend had to leave this morning. 
That's why I was finally posting about this yesterday; I'd been futzing around with her computer all week but I still hadn't gotten a faster web browsing experience going yet so I figured I'd better look for some help before time ran out.
We only got to hang out briefly last night and all of your great advice was inaccessible as updates to the site were going on.

My friend is a very clever though and I'm sure with a little direction she can do any of this on her own. She has no real background in computers, never mind Linux, but she's interested and picked-up on allot as I talked through all of the changes I was making this past week.

It was a good nerdy week. This is someone I grew up and lived with for years. We haven't hung out in a long time. We were out allot for food, drink and friends, but when we weren't out we were watching Battlestar Galactica and playing with Linux so it was proper nerdy time!  

For now everything is still working fine, web browsing is just slow. I'll have her try out some of your suggestions. I'm sure that if nothing else epiphany should install and run fine once I actually ask for the correct package (woops!). I'd love to see if I can get kazehakase running though, or would love to hear about any other ideas.

Thanks to everyone for the helpful responses!

---

### Post by employeeno5 on 2008-04-22
Oh yes, and regarding Fluxbuntu.
After seeing how fantastically Fluxbox was running on her machine compared to having xfce up and running, installing Fluxbuntu seemed like a great idea to try out.
However, there's not PPC installer compiled yet. 

If anyone knows of one, or could help me figure out how to compile one myself, that would be fantastic.

Thanks again!

---

### Post by oswaldkelso on 2008-04-22
There is a ppc version in the debian testing repo,s I'm not sure if you could hook up the that?

---

### Post by stream303 on 2008-05-07
I guess I'm late to the party regarding the future of the Epiphany browser - seems like it will be ensuring it's future by switching from the Gecko engine to the more recent WebKit.  Nice.

---

### Post by abtabt on 2008-05-07
the latest dillo is in 804 repos
a very good BROWSER with speed on older macs

 is OPERA with downloads links forUBUNTU from 
510 to 710 but 710 works in 804 to     
 
[http://www.opera.com/download/index.dml?platform=linux](http://www.opera.com/download/index.dml?platform=linux)

sometimes ivp6 slowsdown the speed check it

---

### Post by linear on 2008-05-08
That Opera is for i386 only.

---

### Post by abtabt on 2008-05-10
1. link is for Opera 9.27 for Linux PowerPC
 
2.  i use it on a ppc imac with 804

3. have you download it and try it ?????

---

### Post by Jammy4041 on 2008-06-09
I've tried Kazehakaze on my laptop. It runs very fast, and i think it is very good. When I get Xubuntu on my iMac, I will have a look at Dillo with tabs- that should be very interesting.

---

