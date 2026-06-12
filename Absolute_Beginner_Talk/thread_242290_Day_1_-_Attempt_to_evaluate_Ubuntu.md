---
title: "Day 1 - Attempt to evaluate Ubuntu"
date: 2006-08-23
forum: Absolute Beginner Talk
---

### Post by Kwales on 2006-08-23
Hi from another newbie ( To Ubuntu not computers )

I have only just in the last couple of days discovered this linux dist. And was very excited to actually boot my laptop this afternoon via the live CD.

First impressions I love it.

I spent a couple of hours downloading it from home ( thought a bit cheeky from work as our Net connection was already a tad slow )

During that time I did some googling on the OS and enjoyed what I found esp. the ch 4 news interview with Mark Shuttleworth giving me some insight into who was behind all of this.

[http://www.channel4.com/more4/news/news-opinion-feature.jsp?id=350](http://www.channel4.com/more4/news/news-opinion-feature.jsp?id=350)

My partner is S African and I was firstly totally drawn to the name of this os and its meaning and well ... after listening to the Nelson Mandella recording in the examples folder I was wowed.. and would realy like to be apart of this project. 

Good on you Mark !!! ( And the rest of the team )

But alas Im afraid Im back in WindowsXP land tonight writing this because I couldnt ( easily ) seem to work out how to get my WiFi connected up and get on the Net to try all the features out.

Im using a Dell inspiron 1150 with a USB D-Link router and usb antenna, with WPA encryption.

Ive read that I have to download some extra files to enable WPA so Im not asking for help here - Will read up some more when Im more awake  :o)

Just wanted to say Hi ! and give my first impressions.

Regards.

---

### Post by adds2one on 2006-08-23
Welcome to Ubuntu!

Not positive but I know with my Dell Latitude D600 I need to use something called ndiswrapper to get my wireless to work in Linux.

ndiswrapper lets you use the Windows driver for your wireless card. 

First you need to find out what wireless card you have. Type:```
lspci
```

note the first column such as 0000:00:0c.0

next type:```
lspci -n
```

to find out the PCI ID of the card. Find the PCI ID that corresponds to the first column of 'lspci' output you found above. The PCI ID is third column or fourth in some distributions and of the form '104c:8400'.

Follow the link below and first go to the "list of cards known to work."

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Main_Page](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Main_Page)
 
Now you need to get the Windows driver for this chipset. In the list, find out an entry for the same PCI ID, and download the driver corresponding to it. Unpack the Windows driver with unzip/cabextract/unshield tools, and find the INF file (.INF or .inf extension) and the SYS file (.SYS or .sys extension). If there are multiple INF/SYS files, you may look in the list if there are any hints about which of them should be used. Make sure the INF file, SYS file and any BIN files (For example, TI drivers use BIN firmware) files are all in one directory. 

Follow the instructions in the link above under "installation" and you should have no problems.

---

### Post by Kwales on 2006-08-23
Thank you very much for your reponse.

I will look into your info. in detail soon.

I hope that I can get all of my stuff working soon on Ubuntu.

But Im very interested in making this OS as easily installable ( if thats a word ) as possible.

I have already showed a few " Key " people in work tday links to Ubuntu and have already raised great interest, to certain staff some who are well into the UK education field of Computers / SW

And open source .

Again Thanks

---

### Post by steve.horsley on 2006-08-23
> **adds2one said:**
> Not positive but I know with my Dell Latitude D600 I need to use something called ndiswrapper to get my wireless to work in Linux.

That's odd. My D600 Just Worked (TM). It had a Centrino sticker on it, if that makes any difference.

---

### Post by Turgon on 2006-08-23
> **steve.horsley said:**
> That's odd. My D600 Just Worked (TM). It had a Centrino sticker on it, if that makes any difference.

Centrino makes all the difference. With Centrino you know that you have an intel wlan chip and intel has been very good with its drivers.

When it commes to thredstarters wlan problem:

You should get the ndisgtk package. To get it you need to get a wired connection, enable the univerce repository and then open a terminal and type:

sudo apt-get update

and then:

sudo apt-get install ndisgtk

Then you will get a nice gui program where you can insert your windows drivers.

For WPA you need the new networkmanager which you can download from the repositorys too. 

sudo apt-get install network-manager-gnome

And it will be inn.

To get network manager to find your card you need to type:

sudo gedit /etc/network/interfaces

and then erase all the text in the file. Save the file, and then restart.

I hope this helps! 

BTW, welcome to ubuntu!

---

### Post by Kwales on 2006-08-25
* UPDATE *

:(

Decided to go for the Ubuntu install last night, Installation looked great.

But me ole Dell Inspiron decided to give up the ghost toward the end.

Had a few problems trying to partition then thought ah what the hell format ! I have a recent enough full backup on an external drive.

Nasty errors, even when I tried to re-ghost with windows.

So no Ubuntu tnight. ( Or windows )

Looks like a hard disk failure - should have known I have had some warning signs over the last couple of months ie blue screening and having to re-ghost a few times.

Anyways - I have to admit Im sat here on a brand new Apple MacBook, up and running within about 30 mins. ( Managed to find one of two in south Wales this lunchtime )

And so far its Great.

OK I panicked this morning with no Pc, No Net access !!!!!!!

Im sure thats just a GeeK thing - but at least I admit it.

Anway - Just wanted to post again that Im still V V V interested on the whole Ubuntu community and hopefully be back soon with some trial feedback of the OS.

Regards

Kwales

p.s. If anyone has a spare Hard disk for a dell inspiron 1150 - pleas contact me !! :)

---

### Post by dca on 2006-08-25
I can't believe that many people around the world purchased that entry-level laptop (see below).  I use it as my work-horse to connect to servers when at work and basically as my overall "do" machine.  I, too, have a small problem w/ my WiFi.  I have an Intel ProWireless 2200B/G which funny enough worked the last time I had Ubuntu installed on this laptop right out of the box.  I re-partitioned and installed Fedora Core 5 to see the nuances between the two because some of the linux-boxes here where I work run it...  Well, I prefer Ubuntu, re-installed it and walah, wireless doesn't work...

---

### Post by Kwales on 2006-08-25
Hi,

This is what Im trying to find out about Ubuntu - I need to know how easy it is to install.

Yes I work in IT and can possibly get over these issues through Googling and Forums here but for the average user - If these problems are spread across too much hardware Im afraid its a no go.

Comments welcomed ??

regards

Kwales

---

### Post by dca on 2006-08-25
I use Linux at work, also.  My job is more the end result than adminning systems.  I know zealots here who swear by Fedora Core.  I built a server from spare parts, let the kid who'll support it put what distro he wants on it...  My laptop is Ubuntu, the storage servers I work with are Ubuntu, and the only useless advice I can give is out of the following distros:  Ubuntu, SuSE 10.1, Fedora Core 5, Gentoo, and some others I've d/l & installed in spare time Ubuntu was the best at auto-detecting all the crap on my laptop.  Sure, there was some tweaking that was needed.  A lot of people placate the fact that that is all Linux is.  When in fact, they install Windows and don't realize how much extra stuff they still need to do, I guess this just happen to know where to find it...

---

### Post by dca on 2006-08-25
...sorry, the last part didn't make any sense.  The point was users have to make tweaks after a WindowsXP or Windows Server install, they just know where to find...  No, that doesn't sound right either.  They know where stuff is in Windows because of exposure...  Maybe that's what I meant.
 
 
This forum is great, a great community, ignore some of the other distro enthusiasts referring to Ubuntu as a cult.  To me, there's only two types of user(s).  The ones that use Linux at their home and the user(s) who have no choice but to live with it because it's part of their job or livelyhood...  Let's face it, throwing a Linux distro like Ubuntu server on an old dual-PIII server w/ 4 drives equalling 400+GB space just so people can share files w/o mapping drives and turning off firewalls is a lot more cost effective than buying an Adaptec NAS server w/ the same amount of crap for $4500...

---

### Post by Kwales on 2006-08-25
Your lucky !

Ive recently found myself heavily governed by Network restrictions that will only allow Windows ( Very very restricted ) to government standard.

Its just crazy !!!

To use a Inferior product , less secure Just cos its " What is approved "

Mad ! I think

---

### Post by quarsan on 2006-08-25
Well I'm installing ubuntu right now. I tried the test CD for a few days and it picked up everything off the bat so I'm installing it. Currently it's downloading and installing 163 software updates...

---

### Post by Kwales on 2006-08-25
Exactly !!

Why are " Sensible  " businesses still paying for all those MS / Citrix licences when there are better " Freee " alternatives.

I guess its lack of support ?

Not once in my It life of work have I been asked to support linux.

why ??

Regards

Kwales

---

### Post by Kwales on 2006-08-25
Quarsan ! Well done please let me know how U get on.

regards

Kwales

---

### Post by dca on 2006-08-25
> **Kwales said:**
> Your lucky !

Ive recently found myself heavily governed by Network restrictions that will only allow Windows ( Very very restricted ) to government standard.

Its just crazy !!!

To use a Inferior product , less secure Just cos its " What is approved "

Mad ! I think

 
Incredible, they're not using Dell equipment are they?

---

### Post by Kwales on 2006-08-25
Yes so far Ive found 40 re-called batteries.

Why what manafacturer of laptops does your company use ?

---

### Post by quarsan on 2006-08-25
Why? I think inertia and time. Many people just feel that they are busy enough and don't have the time/inclination to learn another O/S. To be honest, I think they're right. The director, where I work, is run off his feet. He literally doesn't have time to answer his email - and I mean skimming through it, not replying to everyone.

If I suggest moving to open source, he will agree in principle, but he just doesn't have the time to learn how to use something different. This doesn't make him a bad person, just someone who uses machines as a tool to do his work.

There are some factors that made me move, at least on one machine, to linux:

1, I wanted to see what the fuss was about
2, Ubuntu has a lot of excellent documentation avaliable
3, I could do all my prep from studying this forum and a few links provided in the stickys. A wealth of good information and advice very clearly put.
4, The live CD allowed me to take a good look and see that it would, in principle, work on my system.

---

### Post by Kwales on 2006-08-25
Ok - Just one day my findings ( Not Ubuntu but leaving MS )

DLink WiFi router wouldnt let me add my MAC address - I guess badly designed web front end

Had to turn off Mac addie security ( for what its worth )

Took me ages to get MS messenger working ( OK Im MAC stupid )

But apart from that happy .

Regards 

Kwales

---

### Post by dca on 2006-08-25
> **Kwales said:**
> Yes so far Ive found 40 re-called batteries.

Why what manafacturer of laptops does your company use ?

 
All IBM/Lenovo...  They try to re-evaluate every now and then but it still goes to whatever is the latest-greatest IBM...  The workstations are simple clones P-IV 3GHz w/512MB RAM...   Now the servers are a meesh-mosh.  Tons of Linux.  :D

---

### Post by Kwales on 2006-08-25
A small percentage of Dells Mainly Latitude DC600 's

But seems like Dell recall is at least very easily managed - ie done a few online today

---

### Post by dca on 2006-08-25
It looks like a lot of the better laptop series from Dell were affected.  Not the entry-level ones (like I buy 'cuz I'm cheap) such as Inspiron 1150 as I use and the newer (I guess) B-series or what-ever...

---

### Post by Kwales on 2006-08-25
Yep My cheapo 1150

Even bought a new battery this year and neither were recalled.

I happen to like DELL - Just fed up of MS Windows

Hence my purchase tday of a MacBook


Regards

Kwales

---

### Post by trebor on 2006-08-26
Hi,

This is my first post here, though I am sure it will not be the last.  I got the free cd's from ubuntu played around with them here and there.  Working the hours I do it is somtimes hard to find the time. Now I got it installed on my home built computer (amd) and it running great.  I have installed the updates, added applications, I even found out how to change the kernal in this forum.  Now I can say with all sincerity, I think ubuntu is a great os.

---

### Post by Kwales on 2006-09-10
OK I feel a bit guilty here as this is not Ubuntu relatedt but !

Its taken me all weekend to transfer my ( very important data ) from my windows backup to my new MacBook.

Scary times - Leaving my data on just one hard disk ( Im a strong believer of having data in at least 2 places at al ! times )

So anyway this MacBook seems really ! great ! no probs so far, except some WMF file are asking for licenses and will not play ?

Any help here appreciated ..

So anyway !!


Now I have all my data back - I can get me ole Dell sorted with a new hard disk and really compare Ubuntu with other OS s

So anyway - How are you guys doing ?????


K

---

