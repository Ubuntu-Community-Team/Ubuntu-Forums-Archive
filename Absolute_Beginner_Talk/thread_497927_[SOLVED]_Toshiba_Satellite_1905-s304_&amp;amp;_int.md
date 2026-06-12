---
title: "[SOLVED] Toshiba Satellite 1905-s304 &amp;amp; internal modem"
date: 2007-07-10
forum: Absolute Beginner Talk
---

### Post by Mark_in_Hollywood on 2007-07-10
I've just installed feisty fawn on a Toshiba Satellite 1905-s304 laptop.

I have no 9-pin connector by which to attach an external modem. 

This laptop has an internal modem, which wvdialconf can't find. I'm 99% sure it's a winmodem.

Anybody know whether there is a driver for this sucker and how I would get it into the laptop, with no wired/wireless connection.

I only want the dial-up long enough to synaptic the ndiswrapper. 

All help much appreciated.

---

### Post by Bartender on 2007-07-11
Isn't ndiswrapper already there?
If not, the simplest thing for you would be to find some broadband somewhere - a friend's house, work, school, library, whatever, and plug their ethernet cable into your laptop.  Unplug their modem and router for a minute, then plug back in, then start your laptop.

I was going to suggest downloading ndiswrapper package from a Windows PC, but the results were confusing to me...

I went to ubuntu packages,
[http://packages.ubuntu.com/](http://packages.ubuntu.com/) 
made sure it was set to look for feisty packages, and typed in "ndiswrapper"
[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=ndiswrapper&searchon=names&subword=1&version=feisty&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=ndiswrapper&searchon=names&subword=1&version=feisty&release=all)
Funny thing is, none of these look like the ndiswrapper package to me; they all look like add-ons of some sort?  Was expecting to see a ndiswrapper package

---

### Post by Mark_in_Hollywood on 2007-07-11
Dear Bartender:

I'll have a boiler maker with a Bud back . . . noooooooo wait this is Ubuntu not my local . . .

If plugging in a Linksys WUSB11v4 adapter doesn't bring up an available wireless network "available" with a right click on the network icon in the panel, I can only assume ndiswrapper isn't installed, but I'm way tooo nooooooobie to really know.

Have you a way to search not for mere mention of the filename: ndiswrapper, but whether the software is installed, configured and operational?

Meanwhile, my public library has public ethernet, I think. it may be the solution.

 THNX!, BARTENDER.

---

### Post by Bartender on 2007-07-12
Problem is the library will probly be all wireless.  I called mine, saying I had a PC I wanted to bring in but it didn't have wireless and would it be possible to plug in physically to an ethernet cable?  They said "no".  I found another thread of yours, 
[http://ubuntuforums.org/showthread.php?t=498739&highlight=ndiswrapper](http://ubuntuforums.org/showthread.php?t=498739&highlight=ndiswrapper)
where you mention that you have an external serial modem.  Have read several posts where folks said they used a serial-to-USB adapter to successfully connect an external serial modem to a USB port.  Something to think about.

Reading some of the threads, it appears that ndiswrapper isn't installed with the original installation.  Sorry about that.

If you had broadband I'd suggest Mint Linux, which does include ndis right off the bat...

---

### Post by bme on 2007-07-12
purchase a Prolific USB to serial adapter cable to connect your external serial modem to your laptop....I use it on my present Dell Inspiron and a former Toshiba Tecra no problem....
When you get one and you have problems please post back and we will help you set it up...

---

### Post by Mark_in_Hollywood on 2007-07-12
After learning about the LOCATE command, as in 

james@maplewood: locate ndiswrapper

I know know that ndiswrapper did install from the canonical cd for feisty.

After much playing that hasn't proved fruitful. I need other packages, too.

My local library (Los Angeles) has wired access, but thanks.

The idea about the connector changer seems promising. I think I've discovered ways to get ndiswrapper working in the meantime

SUCCESS. Please close this thread.

---

