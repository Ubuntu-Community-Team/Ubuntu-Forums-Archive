---
title: "How to make use of a Powerbook G4 in 2017"
date: 2017-01-22
forum: Apple Hardware Users
---

### Post by CrisisCore on 2017-01-22
Hi there.

I recently got my hands on a top of the line PowerBook G4 1.67 GHz, 2GB of DDR2 RAM and an SSD, and it is slow in that the CPU bottlenecks everything. I want to use modern software on it, and being a Ubuntu/Linux fanboy, I decided to install Lubuntu on it. It now works reasonably well on the desktop, as long as I only do one thing, but all web browsers I tried are unusable. Even with just a single tab open the CPU sits at 100% load for every click I do, even on simple websites, scrolling is super choppy and everything takes forever to load. Does anyone use such a device actively and have any suggestions for performance in general and web browsing specifically, or is this device completely obsolete?

Regards,
Andreas

---

### Post by DuckHook on 2017-01-23
Welcome to the forums, CrisisCore,

Though I haven't seen a PowerBook in years, I work with a lot of older HW and many of the same principles apply, so I'll take a stab at answering your question.

This machine is still useful, especially now that you've got it working. It would be a shame to dispose of it if you can still get some use out of it.

Firstly, to your browser question:

There are many lighter browsers&#8213;especially in the Linux-sphere&#8213;that the general public are not aware of. They range from light to über-light. A couple of light browsers I would recommend trying are Midori and Epiphany. In the realm of the über-light is Links2. It should be obvious that as they get lighter, they also get more featureless. The tradeoff is always speed/overhead for features. In the case of Links2, it can't script at all, can't accept cookies, doesn't have tabs and is about as primitive as a browser can get while still being functional. It's basically a command-line browser with an ugly GUI slathered on top, but it runs like greased lightning and just nibbles at system resources. It cannot run AV, so it's just for reading content.

The other two browsers have much more functionality, but are also many times more resource hungry, though not as much as the mainstream browsers.

Now, on to the broader issue. How to make best use of it:

You may find that the best use for such a machine is as a server with no GUI at all. I've repositioned many such machines for both myself and my friends as backup servers, torrent servers, NTP servers, print servers, etc. If you get really ambitious, you could also use it as an owncloud, email, calendar or web server, although most such uses are a bit too complex for the average bear.

The point is that, once the GUI and GUI-type apps are eliminated, it's surprising what a new lease on life such old machines get. Since most people never back up their production machines, one of the best uses for an old clunker is often to attach an external USB HDD to the thing and rsync to it for a cheap-and-cheerful backup solution.

Hope the above gives you some food for thought at least.

---

### Post by ernsteiswuerfel on 2017-01-25
> **CrisisCore said:**
> Hi there.

I recently got my hands on a top of the line PowerBook G4 1.67 GHz, 2GB of DDR2 RAM and an SSD, and it is slow in that the CPU bottlenecks everything. [...] Does anyone use such a device actively and have any suggestions for performance in general and web browsing specifically, or is this device completely obsolete?

Regards,
Andreas

I am using a PowerBook 5,8, just like yours, as my main laptop. The best Linux experience I got with Ubuntu MATE 16.10. On versions before 16.10 2D/3D-acceleration is not working properly. The browser experience propably suffers a bit because of this. I hope the 16.10 drivers find their way into 16.04.2. The browser I found most usable was Qupzilla. Xombrero and Netsurf are fast, but don't display all pages correctly.

If your really want fast browsing experience you should try out Morphos. Browser used here is the Webkit-based OWB. [MorphOS]("http://www.morphos-team.net/") is generally much faster, but unfortunately has no good office suite ATM.

---

### Post by CrisisCore on 2017-01-27
Thanks for your tips. I was wondering about Hardware acceleration and how to get it to work in 16.04. I'll try installing MATE 16.10 to see if it helps, and I'll try different web browsers.

---

### Post by CrisisCore on 2017-01-28
I have a really pathetic problem. I'm using the german (Macintosh) keyboard layout. How do I type an @-sign???
Thanks for the Qupzilla tip by the way it works great! I installed MATE 16.10, and after removing the error reporting which clogged the CPU it runs quite well.

---

### Post by ernsteiswuerfel on 2017-01-28
> **CrisisCore said:**
> I'm using the german (Macintosh) keyboard layout. How do I type an @-sign???
Had the same annoying problem too, but I figured it out.

On my german keyboard the "@"-sign is on the 3rd keylevel of the "L"-Key. Then you only need to know how to reach the 3rd level. Go to the keyboard settings, press the "Optionen"-Button and then you get a list of possible settings. "Taste zum Wechsel in die dritte Tastaturebene" is your friend. I am using "Deutsch Deutsch (Macintosh)"-Layout, "Generische PC-Tastatur mit 105 Tasten (Intl)"-Model and "Rechte Windows Taste" for 3rd level. Works.

---

