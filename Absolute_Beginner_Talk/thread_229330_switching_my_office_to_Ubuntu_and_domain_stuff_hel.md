---
title: "switching my office to Ubuntu and domain stuff help?"
date: 2006-08-04
forum: Absolute Beginner Talk
---

### Post by pap3rtiger on 2006-08-04
hey guys, im working for an Engeneering firm as the IT guy, and im lookinng at switching us to linux due to the cost and upkeep of windows, do you guys have any suggestions on making this as painless as possible and as a side note, were running AD off a windows 2003 server, how do i go about joining my domian?

---

### Post by benmoreassynt on 2006-08-04
I'd install Ubuntu on a single computer - one that does not matter too much - and then use it for a couple of months to see how you get on, and get really familiar with it. Like any OS it is going to take a while to get used to.

My own experience is that a lot of things are easier than Windows, and that it only gets tricky when you start dealing with hardware. You will need to look into the following:

Are the company's printers easily compatible with Linux? A lot are not.

Same goes for scanners and other peripherals.

Do you use wireless? In which case don't expect it to be headache free.

I don't know what you mean by AD (Apache deamon??? - sorry if that is a dumb question), but I think networking is where the real strengths of Linux lie, so whatever you have to do is pretty much going to be possible. That sounds a bit vague, but obviously Linux is used most as a server.

You might also want to consider paid support if you are using Ubuntu in an 'enterprise' environment. It runs from about $250 a year. That will save you getting in trouble with the boss when you run into problems.

---

### Post by pap3rtiger on 2006-08-04
ad stands for active directory, luckly we only use one plotter here in the office, which luckly has linux drivers and support. ive got ubuntu up and dual booting on my personal machine just to give it a go. i just need to get tied to my network to do some admin stuff. so far i can do most of the stuff i can in windows, i just need to be able to access client machines from nix. out side of the terminal server client

---

### Post by Wicca on 2006-08-04
As for Ubuntu and AD 2003 integration: it's not as easy as joining a XP-box. However, I managed to get it working using sadms: [http://sadms.sourceforge.net/]("http://sadms.sourceforge.net/")
I guess a painless switching from Windows to Linux depends on the software used at the moment. Are Linux equivalents needed? If so, users do not only have to switch from OS, but also from application(s), which can make it more painfull.

---

### Post by benmoreassynt on 2006-08-04
Sounds to me like you are savvy enough to make a go of it. Good luck. Like Wicca says - the real problem might be staff who resist moving from MS Word to Open Office (or whatever).

---

### Post by stormblue on 2006-08-04
This is what I would do:

1. switch over just one computer and see how well it works.

2. After things appear to be going well switch the staff over to gaim, thunderbird, and firebird, Open Office let them use this for a couple months

3. Have an early adopter opt-in switch over and then in 3 months make it mandatory.

---

### Post by Abhi Kalyan on 2006-10-25
Great Snakes, pap3rtiger
Dude We are doing the same.
The similarity
1. Shifting to UBUNTU completly from Windows server 2003
2. Running Internet share, File Share, VPN(etc.ect.etc.....)
We could join hands
Please Post back with the size and the current setup whihc you are running
My mail ID
[email]abhi.kalyan@gmail.com[/email]
Please keep posting.

---

### Post by Abhi Kalyan on 2006-10-25
Have been posting for a week now and the data that has gotten in is quite good,
As adviced in this page 
its best to migrate first to the office suites (open office) firefox, thunderbird (etc)
For CAD you should try Qcad, electrical cad-(avalable for linus- get into synaptic and open out all the repostories.)
Microsoft Project has a miniature alternative in Project Management(available in synaptic.
The best thing is to phase it out in batches, Creat A milestone for deployment over a setup.
One idea would be to invole every one in the conversion Project.
Cause mind Block will remain the hardest.
Ubuntu supports almost most of the modern harwares.
Ny ways waiting to see how it all happens.
all the best
sincerely
abhi kalyan.

---

### Post by Abhi Kalyan on 2006-10-26
Posting one message given to me by Mr.brentoboy.
1. Am pasting it here
2. Thread Name : "150 users in 45days + a server"

"
Here is what I would do:

First, go to the book store, here are the titles you want in order of importance:

Ubuntu Hacks

The Official Samba-3 HOWTO and Reference Guide

Linux Quick Fix Notebook

and Samba-3 By Example

------------------
If your project cant afford the books, you need to abort mission ASAP. You are in for a crazy ride, and even though these forums are helpful, you are going to need the advice from some really good books.

The last book up there (Samba by example) is the only one I would say is not absolutly necessary, I list it becuase it might give you a quicker start with samba, which will make the initial fealing as you get started give the project a euphoric lift -- that is always nice to have.

-------------------

Setup SAMBA first
Create 2 or 3 users, and 2 or 3 shares, and install ubuntu on 2 or three of the client computers. Get a "happy" little network going.

Once you like them, you can roll out the client PCs as quickly as you want.

This is a weekend project. When you are done, you will probably want to reformat all the PCs involved, and start over using the experience you gained doing it the first time.
----------------------

As far as all the other services go, add them one at a time, in order of importance. DHCP is probably necessary before you get too much farther.

The Official Samba-3 HOWTO book will sit by your desk for a few months, and you will need it every time someone calls and asks "Why does it..." "How do I..." (basically every day for a while)

The Ubuntu Hacks Book is the only book in the list that is specific to Ubuntu. It has loads of advice, it should sit on your toilet. Every time you "go" you should read a tip or two. As the administrator of this whole thing, you need to know what your options are. The book has lots of ideas that I would have never tried that are quite helpful.

The Linux Quick Fix Notebook is the one that will come in handy after you get past the samba hurdle. It will help you set up all the other stuff you want.

Dont even touch LDAP until you have a working network in place that people like. Then, (after your 45 day startup) when things settle down a touch, set up a new server with LDAP and add a handful of client boxes to that network until you really like what you have. Then, roll that out to all the other PCs.

------------

There is nothing inherantly difficult in what you want to do, and there are lots of guys out there who could just do it. But, if you want to do it yourself, and discover how at the same time, that takes time. And, you are going to do some things that will come back and give you a headache.

The number of client PCs on your network will amplify your headaches until you have things smooth, which is why I recommend adding one or two new things at a time until you have it doing all that you need. Starting with the most critical and moving on to the "luxuries."

---------------

The biggest reason that I can see that will cause you to NOT finish within 45 days is that you still dont have a concrete list of exactly what you are going to finish in 45 days.

So, not only can I not judge how easy it will be to do it, you cant focus on your target until you know what it is. And if you cant focus on a target, you will most certainly miss it.

-brent
_________________
- Brentoboy
"god is real (unless explicitly declared as int)" 

Also attaching a .odt file containing the same
Hope this helps.
Cheers

---

