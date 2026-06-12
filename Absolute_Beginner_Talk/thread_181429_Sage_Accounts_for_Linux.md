---
title: "Sage Accounts for Linux"
date: 2006-05-24
forum: Absolute Beginner Talk
---

### Post by ozPATT on 2006-05-24
Hi All, 

I'm not sure if this is the right place to post, but i couldnt see anything that looked more relevant... I am a newbie to linux, so here it is... 

does anyone know if there is any software out there for linux that will do the same as Sage Accounts? I am setting up a business and want to use linux for everything, I am using Ubuntu Breezy Badger (I think - how do I tell?)

thanks

Patrick

---

### Post by ProjectGod on 2006-05-24
you could perhaps use something called WINE to run windows apps on linux. good chance of success.

check the link below. 

[https://wiki.ubuntu.com/Wine?highlight=%28wine%29](https://wiki.ubuntu.com/Wine?highlight=%28wine%29)

check also [www.ubuntuguide.org](www.ubuntuguide.org) for adding repositories and everything else you need to get applications packages etc etc.

have fun!

PS tell us how you go! ubuntu is dying to be used in business.

---

### Post by ozPATT on 2006-05-24
well, i was hoping for a free program that has the same features as sage, not that money is the issue, but i am keen to demonstrate to some people I know that actually linux can offer the same as windows, without having to pay anything. 

so i may have to get sage and do as you suggest. I have seen another program that I am going to try to install, called MoneyDance, but not sure how it will compare with Sage... 

thanks for your advice. :)

---

### Post by bluenova on 2006-05-24
Sage have Linux versions no?

Quote Sage.co.uk:
Available for a choice of databases & environments
The solution can be deployed on multiple database platforms (DB2, MS.SQL, Pervasive.SQL and Oracle) and supports multiple environment platforms (Linux and Windows)

---

### Post by amanda on 2006-05-24
ozPATT, I'm not familiar with Sage Accounts: what does it do, and what do you use it for in your organization (what features/functionality is most significant?)

A caveat, as well: I'm not saying you'll never find a replacement for Sage Accounts that is Free and Open Source, but my experience has been that for specialized accounting and business process software, the process of converting to something free and trying to make it do what you need is also not cheap. Often it is still worth doing, but if you go into this thinking it will be free, you're in for a bit of a surprise.

That is my two cents--tell us about what you are using Sage Accounts for and someone may know of something suitable.

---

### Post by ProjectGod on 2006-05-24
as **bluenova ** said if Sage offer their software for linux go for it! although i guess one would still have to pay for it :).

if you want to test out other accounting software... search for packages using "Synaptic package manager" or use the terminal to find packages:

[B]sudo aptitude search accounting

sudo apt-get search accounting[/B]

... you can substitue any string into accounting. so ... **search account software **etc etc.

have fun!

---

### Post by ozPATT on 2006-05-24
wow cool thanks, i will have a look. :) 

i think that I will only need it for pretty basic stuff, income, expenditure, VAT, etc, I don't currently use anything. Just starting up, so I haven't really seen what Sage can do.. i just have been told it does everything you need it to do. If Sage is compatible with Linux then I probably will go for that actually... i didn't think of that. 

but i will still do a search or two as you have suggested. :) 

thanks for your help people :)

edit: i just checked sage.co.uk, and Sage Instant Accounts which is what I have been recommended, requires a Windows platform. :( oh well, i will have a look into your above suggestions. :)

---

### Post by costoa on 2006-05-24
Which Sage product are you talking about (like MAS90, MAS200, etc)? Also are there modules like cross-currency that you have to have? What's the network and user topography? Is it all in one office or do you need remote access via the net? Since Sage stuff can be found from one man shops to companies with tens of thousands of items and users what kind of shop are you aiming for?

---

### Post by ozPATT on 2006-05-24
hi there, just need to think small here... no massive network, not access via net etc, at this early stage of starting up, there will be me, and my computer and that's it. I will be doing freelance website programming, so initially, all i want to do is manage my accounts in a way that makes it easy for me to successfully put in a tax return at the end of the year. 

so very small, and very basic. :) being australian, i aim to have clients in oz and uk, so cross currency will probably be used.

the product i am looking for is [shop.sage.co.uk/instantaccounts.aspx]("http://shop.sage.co.uk/instantaccounts.aspx")

thanks

Patrick

---

### Post by ProjectGod on 2006-05-24
Excellent!

an aussie! i'm an aussie too! its quite late yeah? no worries i work from home!

since youre going to do web programming. i guess you'll need tools like cold fusion, dreamweaver, flash, etc etc

one package that can dock straight into linux is **Nvu** its an equivalent to dreamweaver... had a look at it myself... its quite alright. for the other window's native software packages. you may have to use wine or xwine...

---

### Post by ozPATT on 2006-05-24
haha, nope, I just have wScite, a text editor, and I have FireFTP which is an FTP extension for firefox. Along with GIMP, that's all the tools I need for the programming I do. :) ([www.aussiefreelancer.com](www.aussiefreelancer.com))

where are you from in australia? i am from Perth, but I am currently in the UK... reckon i will be here another couple of years yet, so hoping to get everything off the ground so that I can be earning english pounds when i return ;)

---

### Post by nanotube on 2006-05-24
since you say you are looking for small-time stuff, you can look into gnucash [http://www.gnucash.org/](http://www.gnucash.org/)

---

### Post by costoa on 2006-05-24
Yeah, I'm with nanotube on this: try gnucash. Sage stuff can work well but when it breaks it breaks hard. You could try a demo of Sage's Instant Account but I suspect it will freak under WINE.

---

### Post by ozPATT on 2006-05-24
cool thanks, i will try that. :)

---

### Post by jago25_98 on 2006-05-28
correct me if I'm wrong. 

- Sage accounts seems to be a bit of a standard in the UK, certainly amount small to mid size businesses. I see it advertised a lot in job ads.

- Only the more expensive line of Sage Accounts seems to be available for Linux (Sage Line 500?). This is probably because they expect the larger companies to use it.

- Thank goodness Gnucash is available from apt. LinuxFormat even said they prefer it to MoneyDance (pay for equivilent). It's a messive pain to install from source I found though. Gnucash seems a bit US centric?

Is there a free online accounts system like writely.com? That would be very handy.

---

