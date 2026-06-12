---
title: "Use Linex for Churches"
date: 2005-03-26
forum: Absolute Beginner Talk
---

### Post by derykddb on 2005-03-26
Hi,
I am new to Lynex. My interest in the operating system is that, because of what I have read, It would be an ideal system for use by churches etc. Transfers of programs and operating systems to sister organisations can be done without fear of working illegally.
However there seem to be some serious problems when changing from MS windows to lynex with desktop facilities.
For example, my understanding is:
One would need a VGA card of at least 8 megs, windows works happily on 4 megs
It seems that some sound cards because of conflicts cannot be used on lynex.
On the other hand the group that developed the church system say that the system was developed on a 486. I must be missing something somewhere! 
What I need to know is the minimum configuration that could have a desktop facility using lynex with a reasonable word processor,  spreadsheet and accounting package. Alternatively a reasonable user friendly arrangement that could be used by users who are not computer fundies.
The church system can be found on &#8220;infocentral.org&#8221; so the only stumbling block is what hardware to use, especially considering that most churches if they have computers at all are likely to have old p1 or equivalent.
Can any one help 
Deryk

---

### Post by az on 2005-03-26
Coming from an atheist, Happy easter!

Yes, we can help.  

I looked at the site and it seems to be some sort of database server.  You sould easily be able to run this under linux.  As well, since I do not think that you need to even have a monitor attached (since it is a server and other computers connect to it) it would  run faster on older hardware since linux is scalable (the graphical interface - mouse and cursor) is optional.  This would result in better performance.  From your description, I do not know if this is your setup.
Perhaps you are just using one computer running the server and connecting to it locally through your web browser.

Anyway,

"I am new to Lynex. My interest in the operating system is that, because of what I have read, It would be an ideal system for use by churches etc. Transfers of programs and operating systems to sister organisations can be done without fear of working illegally."

This is all correct with the exception of the spelling.  It's "linux'.  I point this out to facilitate your google searching.


"One would need a VGA card of at least 8 megs, windows works happily on 4 megs
It seems that some sound cards because of conflicts cannot be used on lynex."

No.  You do not even need a video card.  You can run a linux system headless (without monitor)  You can use pretty much any video card you want.  I have run it on pretty old hardware with as little video memory as 1 Meg.  Do not worry.

The same goes for sound.  I think that only very recent sound cards are not yet working completely properly.  Most other sound cards are fine.  Again, for your purpose, you would not really need a sound card anyway.


"On the other hand the group that developed the church system say that the system was developed on a 486"

486 computers are still useful.


"most churches if they have computers at all are likely to have old p1 or equivalent."

Ubuntu is scalable.  That means that you can run a full-blown desktop with all the bells and whistles or, if using old hardware, you can cut back on the stuff you run.  I personaly run linux on a 166 MHz Pentium I with 96 megs of ram.

The minimum requirements for installing Ubuntu linux are 32 megs of ram, however, It would not be very pleasing to work on such a system.  64 Megs or more is better.  You will need Greater than 2 Gigs of disk space for the full desktop install.  You can cut back, if space is short.
You can relatively easily install only the thin compenents that you need (Graphical environment, window manager and word processor and web browser)  You should be able to fit that in just under one Gig of hard drive space.  You will need more space to work with afterwards, though.

It is debatable what are the minimum requirements for the full-blown desktop.  In some areas, the less the people who will be installing this know about computers, the more the full desktop will be useful.   Let's say 128 megs of ram, 3.5 gigs of hard drive space and a 400 MHz processor.

For example, the full desktop will make it easy for you to install a new printer, while with the scaled down setup, you will need to install and confugre it by hand.

Please post any further questions.

---

### Post by az on 2005-03-26
I was thinking about your situation:

If you system is connected to the internet through broadband and you want to use it to service the parish community, have a look at:

[www.drupal.org](www.drupal.org)

This can run very well on old hardware.  It is quite impressive.  It can do a lot of things.  It is "community plumbing"



[http://wordpress.org/](http://wordpress.org/)

This simply for weblogging.  Drupal can do this, but if you want to keep it simple...  Weblogging would be useful for anouncements and the like.



[http://www.phpbb.com/](http://www.phpbb.com/)

This is simply a messageboard (forum).  Again, Drupal can do this, but this application can do it better.  It has more features but it only does forums.



Also, all this is scalable.  It depends on your needs.  You can host infocentral, drupal and phpbb all on the same machine, if you like.  Users would access them through the web.

If you are not connected to the web that way, you can always purchase web hosting.  For example I maintain a site that ran on an old computer, but due to bandwith restrictioin and other issues with my internet service provider, we moved the site to a commercial host.  It cost 15 dollars for the domain name and $9.99 per month for the hosting.
There are probably cheaper hosting companies, too.  I suppose that running an old pentium I 24/7 would cost a few dollars per month in electricity.  Maybe it would be worthwhile in your case.

---

### Post by robbydek on 2005-09-07
[CENTER]**Please help soon!!!!!!!!!!!!!**

I've installed Linux to my hard drive but know matter what range I put the screen at it says "out of range" It gives me the same messege with the Live CD too.  What do you suggest?  Anyway I've added it to a partition (since Windows XP is still on my computer) with the small screen size.  I have 10GB of hard devoted to the OS and I'm using version 4.10.

Thanks in advance for your help.
BB[/CENTER]

---

### Post by az on 2005-09-08
Your graphics card is misconfigured.  You canfix this.

Whne you beet, if you do not see the grub menu, you will see aprpompt to hit escape to get into the grub menu, so hit escape and get into the grub menu.

Select recover mode.

WHen you are in recovery mode type this:

dpkg-reconfigure xserver-xfree86

(this will ask you a bunch of questions about your video ard and mouse and stuff.  Take the default if you are unsure)  Whne it gets to the resolution section, only select 800x600 or less.  When it asks you for monitor configuration, select medium and pick 800x600@60Hz (or seomthing close to that)

To try it out, type:

init 2


If your monitor still goes blank, try hitting CTRL-ALT-F1 (Those three keys at the same time)  If that brings you back to the console you were just in, log in and type

init 1

and start over 

(dpkg-reconfigure xserver-xfree86)


You are going to have to work at it for a littte bit.  It may not work the first time, so keep reconfiguring it.  Try different options...  I cannot help you more since I do not know what hardware you have.

---

