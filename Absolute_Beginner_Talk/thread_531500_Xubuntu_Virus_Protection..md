---
title: "Xubuntu Virus Protection."
date: 2007-08-21
forum: Absolute Beginner Talk
---

### Post by Dionysus135 on 2007-08-21
Hi im starting to get used to xubuntu 7.04 fiesty fawn.Now im going to set up a network with my windows vista.My question is that do i need a antivirus program for xubuntu?If so what good free antivirus program do you guys recommend?Also do i need a anti spyware protection too?If so what are good free spyware protections  are there for xubuntu?

-Thank you for your help.

---

### Post by oilchangeguy on 2007-08-21
no anti-virus, or anti-spyware software is needed. and please space after a period.

---

### Post by misfitpierce on 2007-08-21
If you require it to make sure you dont get windows ones and pass to windows computer go to [http://avast.com](http://avast.com) and get linux deb package and install.. To run run avastgui from terminal or make a launcher with command avastgui.

---

### Post by RonP on 2007-08-21
> **oilchangeguy said:**
> no anti-virus, or anti-spyware software is needed. and please space after a period.

Thats pretty irresponsible of you. 

I am sure you'll find that pretection is always important. I am waiting find out the answer to what the best would be too.

---

### Post by bodhi.zazen on 2007-08-21
Linux security is different then windows security.

See this thread for info : [[color=black]Ubuntu Security[/color]](http://ubuntuforums.org/showthread.php?t=510812)

But, to answer your question, there are no know active Linux viruses so anti virus is not needed.

Furthermore, antivirus software is reactive not proactive, meaning it can not protect you against the next Linux virus.

Don't forget, viruses take advantage of hole in the code. So the solution in staying up to date, especially with security updates.

HTH

---

### Post by oilchangeguy on 2007-08-21
> **RonP said:**
> Thats pretty irresponsible of you. 

I am sure you'll find that pretection is always important. I am waiting find out the answer to what the best would be too.

the user state's they're getting used to ubuntu. so that should mean they've been running the os for a day, week , month. they don't say. but if this is the case just by using the os for an extended period, the question answers itself. and a previous poster indicates it's needed to protect ubuntu from windows viruses. this is not correct. an .exe file won't run in linux.

---

### Post by bodhi.zazen on 2007-08-21
> **oilchangeguy said:**
> no anti-virus, or anti-spyware software is needed. and please space after a period.

> **RonP said:**
> Thats pretty irresponsible of you. 

I am sure you'll find that pretection is always important. I am waiting find out the answer to what the best would be too.

Not really. Linux != Windows

At this time, oilchangeguy is correct. That is not to say security is a non-issue, it is however different from other OS. See the link above for basic Ubuntu security.

---

### Post by Kilz on 2007-08-21
> **RonP said:**
> Thats pretty irresponsible of you. 

I am sure you'll find that pretection is always important. I am waiting find out the answer to what the best would be too.

The fact is that there are a Whopping 0, yes thats right [COLOR="Red"]**0**[/COLOR] linux viruses. A linux user doesn't really need to run a anti-virus program if they run linux. People coming over from the windows world are programed by the rampant viruses on it to think anti-virus is a needed. When in fact it is a poor design that allows viruses in (can you say integrating a active x browser into your operating system?). Another bad idea from Windows is everyone runs as root.
Linux was designed to be safe and secure, that and there are lots of variations. This makes it hard to write viruses for it. Add the fact that they cant do anything real bad without the root password and you see why viruses have not found a home on linux.
Now if you have the habit of forwarding attachments you havent looked at th friends who run Windows, maybe there would be a reason to have some anti virus software. But for the most part Windows users dont open attachments any more.
All in all if you feel you need anti-virus, please dont pay for it. In a few months you will learn that it isnt needed and it was a waste of money.

---

### Post by julian67 on 2007-08-21
> **Dionysus135 said:**
> Hi im starting to get used to xubuntu 7.04 fiesty fawn.Now im going to set up a network with my windows vista.My question is that do i need a antivirus program for xubuntu?If so what good free antivirus program do you guys recommend?Also do i need a anti spyware protection too?If so what are good free spyware protections  are there for xubuntu?

-Thank you for your help.

Like others have said you don't need AV to protect your Xubuntu system as it isn't vulnerable to viruses. It's possible to run AV to ensure you don't host/pass on viruses to Windows users but frankly it's their problem  and their own system's AV should take care of this. It really isn't your responsibility unless you run a mail server. 

You're also not vulnerable to typical spyware but of course whatever OS you run you are liable to annoyances like pop ups, unwanted advertising, cross site scripting and so on. You might want to check out [privoxy]("http://www.privoxy.org/") > Privoxy is a web proxy  with advanced filtering capabilities for protecting privacy, modifying web page data, managing cookies, controlling access, and removing ads, banners, pop-ups and other obnoxious Internet junk. 

It's available in the repos and easy to use, just google for a howto, will only take a couple of minutes to set up. It's available for Windows too and will really enhance your security on a Windows machine as well as making for a nicer browsing experience. 

If you're a Firefox user also have a look at the noscript extension. Again this will help a lot in keeping a Windows system clean.

If you want  anonymity (the ultimate anti-spyware strategy!) while browsing (at the cost of speed) you should also look at tor and the Firefox torbutton extension. Again it's in the repos, is usually used in conjunction with privoxy and there are lots of howtos to get you up and running in just a few minutes.

---

### Post by Tobster on 2007-08-21
To give you an idea of the chances your  Linux box getting a virus:

There are around 33 million Linux users  say Novell.

During 2006 there were 40 reported viruses worldwide.

So you got a 40 in a 33 million chance of getting a virus so in reality your Linux box is very safe indeed. :)

Thanks

Toby

---

### Post by Kilz on 2007-08-21
> **Tobster said:**
> To give you an idea of the chances your  Linux box getting a virus:

There are around 33 million Linux users  say Novell.

During 2006 there were 40 reported viruses worldwide.

So you got a 40 in a 33 million chance of getting a virus so in reality your Linux box is very safe indeed. :)

Thanks

Toby

Of those 40 reported, how many were actual viruses in the wild? Were they just proof of concept ? You know the kind that require you to run as root on a specific version of Red hat.   Secondly if they were supposedly real, who is doing the reporting and taking the reports. A salesman at Symantec Corp ?

---

### Post by ArtF10 on 2007-08-21
I read somewhere on here that Ubuntu ships without any open ports.

---

### Post by HermanAB on 2007-08-21
No open ports?  How about X for one...

If you run a mail server and serve Windoze machines, then you should run ClamAV and SpamAssassin, otherwise, don't worry about viruses.

---

### Post by bodhi.zazen on 2007-08-21
> **ArtF10 said:**
> I read somewhere on here that Ubuntu ships without any open ports.

That is true.

The "problem" is that "server software" will open ports. Sometimes this is obvious, such as openssh-server, but sometimes not.

---

### Post by mikey5555 on 2007-08-22
Dionysus135, 
While all the posts regarding your questions are correct, it is possible to pass on an infected file from your Ubuntu machine to your Winderz machine (happened to me twice   recently).  If you want a good **free** AntiVirus program, you might try **AVG Antivirus**.  It is one I have used for at least 3 years on all my Winderz machines, and is what I currently use on all mu Ubuntu systems.  This is only because all my systems are on the same in-house network, and I share files and folders among them all - 1dedicatec Ubuntu system, 2 "Dual Boot" Win-XP/Ubuntu-6.10 and Win-Vista/Ubuntu-7.04 machines, and last but not least, My laptop is dual boot Win-XP/Ubnutu-7.04.  You can find AVG Antivirus for Linux systems here...  [http://free.grisoft.com/doc/5390/us/frt/0?prd=afl](http://free.grisoft.com/doc/5390/us/frt/0?prd=afl)  Just check the list for your specific Unix version/flavor.  (NOTE: AVG is NOT free for Commercial use, ONLY to "home users").   Works great for me, and not difficult to install and config.

mikey5555

---

### Post by julian67 on 2007-08-22
> **mikey5555 said:**
> Dionysus135, 
While all the posts regarding your questions are correct, it is possible to pass on an infected file from your Ubuntu machine to your Winderz machine....................................

This has already been described by several other people. And anyway if a person runs AV Product A on all their machines, both Linux and Windows, what makes anyone think that Product A on Linux will detect and deal with virus any better than Product A on Windows???????????  It's obvious that the AV on the Linux PC is redundant, that is it serves no real purpose as it doesn't offer any protection that isn't available on the Windows machines and the computer is not vulnerable. 

btw I've had Windows viruses arrive on my Xubuntu laptop from a Mac that had collected them from a Windows machine, all of this while transferring files between computers using USB drives. Of course my machine wasn't vulnerable, it wasn't a big deal, the files were obvious and I deleted them. The Mac owner hadn't even been aware of them and anyway his machine wasn't vulnerable. The Windows user(s)? It's their problem It's up to them  to protect themselves, nobody can do it for them. That might sound harsh but while people are busy installing and sharing warez and cracks and using shareware and all kinds of closed source stuff of dubious origin then it's a lost cause anyway. They don't know it but they have more to worry about than the very rare Linux box unknowingly hosting a virus that will likely be caught by any functional AV.

---

### Post by Bakon Jarser on 2007-08-27
I'm new to linux but I read an article on slashdot just last week that says clam av is the best anti-virus program.  It is also free!

Edit:  found the link to the article.

[http://www.darkreading.com/document.asp?doc_id=131246&WT.svl=news1_1](http://www.darkreading.com/document.asp?doc_id=131246&WT.svl=news1_1)

---

### Post by julian67 on 2007-08-27
> **Bakon Jarser said:**
> I'm new to linux but I read an article on slashdot just last week that says clam av is the best anti-virus program.  It is also free!

Edit:  found the link to the article.

[http://www.darkreading.com/document.asp?doc_id=131246&WT.svl=news1_1](http://www.darkreading.com/document.asp?doc_id=131246&WT.svl=news1_1)

It might not be best for the typical Windows desktop as it is incredibly slow to scan and doesn't offer real time protection, only on-access.

---

### Post by liquidfunk on 2007-08-27
> **oilchangeguy said:**
> please space after a period.

 It's a full stop. A period is something a girl has.

---

### Post by ArtF10 on 2007-08-27
ok, here is the BEST Anti-Virus software BAR....NONE!!!!  And Guess what.....YOU'VE NOT HEARD OF IT!!!!!  Up until recently, I HADN'T.....

[http://www.eset.com/products/linux.php](http://www.eset.com/products/linux.php)

[http://www.av-comparatives.org/seiten/ergebnisse_2007_05.php](http://www.av-comparatives.org/seiten/ergebnisse_2007_05.php)

---

### Post by julian67 on 2007-08-27
> **ArtF10 said:**
> ok, here is the BEST Anti-Virus software BAR....NONE!!!!  And Guess what.....YOU'VE NOT HEARD OF IT!!!!!  Up until recently, I HADN'T.....

[http://www.eset.com/products/linux.php](http://www.eset.com/products/linux.php)

[http://www.av-comparatives.org/seiten/ergebnisse_2007_05.php](http://www.av-comparatives.org/seiten/ergebnisse_2007_05.php)

:rolleyes: it's been around for ages, it's popular, especially on p2p networks...it's on almost every new PC supplied with non genuine OS in SE Asia etc etc etc

---

### Post by ArtF10 on 2007-08-27
I see...well, over here in North America, its Norton or McAfee...pick your poison I guess.

---

### Post by Paulmd on 2007-08-27
> **Kilz said:**
> The fact is that there are a Whopping 0, yes thats right [COLOR="Red"]**0**[/COLOR] linux viruses. A linux user doesn't really need to run a anti-virus program if they run linux. People coming over from the windows world are programed by the rampant viruses on it to think anti-virus is a needed. When in fact it is a poor design that allows viruses in (can you say integrating a active x browser into your operating system?). Another bad idea from Windows is everyone runs as root.
Linux was designed to be safe and secure, that and there are lots of variations. This makes it hard to write viruses for it. Add the fact that they cant do anything real bad without the root password and you see why viruses have not found a home on linux.
Now if you have the habit of forwarding attachments you havent looked at th friends who run Windows, maybe there would be a reason to have some anti virus software. But for the most part Windows users dont open attachments any more.
All in all if you feel you need anti-virus, please dont pay for it. In a few months you will learn that it isnt needed and it was a waste of money.

More than 0 linux viruses. None active right now, though.

[http://en.wikipedia.org/wiki/List_of_Linux_computer_viruses](http://en.wikipedia.org/wiki/List_of_Linux_computer_viruses)


A linux (or indeed a Macintosh) machine can act like Typhoid Mary, though. By infecting downstream users via email. Mail servers are getting better about scanning email for viruses, though. And Windows users are getting better about the unknown attachments, but it's still a concern.

---

