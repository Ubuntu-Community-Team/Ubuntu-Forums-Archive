---
title: "Would this be a good alternative to Win 2003 Server?"
date: 2006-07-06
forum: Absolute Beginner Talk
---

### Post by dannieboiz on 2006-07-06
Just complete building a server for the company, about to throw down a few grand for Win 03 server, SQL and what not. Then I thought of Linux and found this. I'm an intermediate MS networking guy, played with linux many years back when I was in school. I can probably teach myself Linux again easier than others since I've touched and feel it for awhile b4 quiting it. 

Relatively small company of about 10, Everyone running either XP Home or XP Pro. Would like file sharing, printer sharing and run SQL for a CRM (saleslogix) 

possible that we'd want to link with our HQ using Win y2k server. 

If this is not the right choice, please point me to the right direction. Thanks

---

### Post by mssever on 2006-07-06
File and printer sharing work great in Linux nowadays. You'll need to install Samba. Samba works with Windows networking (network neighborhood, etc., not sure what it's called). Windows machines don't even know that you're using Linux. SQL should work fine unless your software uses Microsoft extensions or something. MySQL and PostgreSQL are the two most popular choices.

As far as linking with HQ goes, it all depends on what technologies are used, but sine Linux is a huge player in the server world, chances are that you can make it work.

Also, Linux has come a long way when it comes to user interface/configuration, so tasks will probably be easier for you now than they were the last time tou played with Linux. Welcome aboard!

---

### Post by adam.tropics on 2006-07-06
Have a read [here.]("http://www.howtoforge.com/perfect_setup_ubuntu_6.06")

---

### Post by nameiwantistaken on 2006-07-06
Given that it's for work and you know the MS setup, I'd go with that.  You'll be creating a lot of work for yourself and it very easily could turn into your linux choice being blamed in case anything goes wrong.

---

### Post by mssever on 2006-07-06
[QUOTE=nameiwantistaken]Given that it's for work and you know the MS setup, I'd go with that.  You'll be creating a lot of work for yourself and it very easily could turn into your linux choice being blamed in case anything goes wrong.[/QUOTE]

I disagree with the above comment.

I don't know that Linux is much more work than Windows, it's just a little different. And more stable. There might be a bit of a learning curve, but there are plenty of tutorials out there and lots of help available. And once you get everything working, you should be out of the woods, having just saved your company lots of money.

---

### Post by 3rdalbum on 2006-07-06
At my workplace, the computers use VNC to get a virtual desktop which I assume is coming from the head office. That computer is running Windows Server 2003.

The number of problems we have had with it definately prompts me to give you this advice: Use Linux for any server.

If your printer doesn't work natively with Linux, you may need to have that connected to a Windows computer, but otherwise things should be fairly simple. Just don't change your Ubuntu computer's hostname after installation :-)

Remember, Linux was originally designed to be used on the server, and that is still its most widespread role. Ubuntu comes with a program called Terminal Server Client, which can use VNC. You shouldn't have any problems, once it's up and running.

---

### Post by nameiwantistaken on 2006-07-06
Disagree all you want.  What you're forgetting is that you're some guy on a website giving advice and this is his career.  Want to play around and learn how to administer a Linux based OS?  Do it at home and know it before you go to the workplace.  The people where he works don't care about Linux and where it is used.  They will only care that something went wrong because the tech guy went with something that they'd never heard of and he'd never really used before.  

This is ABSOLUTE BEGINNER TALK and you're suggesting there that someone put their job on the line to play Ubuntu server at work.  It's irresponsible.  Buy a couple of cheap P3 machines and run them on a home network for a while.  Once you're an expert at things, and don't need AD, then you can think of going to Linux.  Until then, do the safe thing, collect your paycheck, feed your kids and be happy.

---

### Post by dannieboiz on 2006-07-06
thanks for all the advise so far, keep them coming.

Ironically, I'm not the company's IT guy. I was hired on board as a product manager. :rolleyes: 

Currently, we're on a peer to peer. Each WS have it's own IP address from the ISP. (Who ever set it up in the beginning was an idiot) 

We really don't need a server, but I recommended that we get a CRM for the sales and product management and got an ok on it. All of our other offices have it. Boss asked for recommendation on server, bought a crappy gateway server, decent specs but noisey fans and it was a whopping 2800 bucks. 

I told boss to screw it, I'll build them one and go an OK. Built a better server for just under 1k. :) Nothing like a dual xeon but enough to support at least 10-25 users. 

Why did I do this? Hmm well, I just increased my job security now that i've  became the unofficial IT guy. Wearing more than one hats always help. I've also open the door for a raise. Hiring a full time IT guy would be  40-60k/year and that would be pure expenses. Give me a small raise and they got themself a fulltime in house IT guy who's also generate revenue. :-k 


If I can save the company a few more grands by going with Ubuntu, I think I may just site @ my boss's desk. LOL 

I'm gonna go ahead and install another boot of Ubuntu on the server to see how it goes. At this point it's just connected to 1 other WS for testing.



So you're saying there's nothing like an AD for Linux?

---

### Post by MaximB on 2006-07-06
I really think you made the right choice....IF you can learn ubuntu server FAST.
cuz I'm learning MCSE and win2003 is a pure BIG !
and it cost A LOT of money...for every workstation you will have to pay.
and it time limited....thouse robbers

---

### Post by dannieboiz on 2006-07-06
I got the desktop Ubuntu on my laptop. Up and running, surfing the net less than 20 minutes of reading. :) Now the server side is a totally different story. I left the IT field about 5 years ago, I had to pretty much start from scratch when I installed Active Directory on the WIn 2003 server that I'm trying out. Since I'm already MS cert, why not learn Linux and expand my knowledge.

---

### Post by nameiwantistaken on 2006-07-06
There was a good post on hardforum.com recently about using AD with Linux.  It's probably a good read for you.  I can see how you want to save money, but just be sure you don't dig yourself in a hole in the process.  People don't get fired for buying Microsoft or IBM.  The same can't be said for Linux and home built hardware.  Just be sure to CYA.

---

### Post by dannieboiz on 2006-07-06
When I built the Server, I got a quote from our local supplier that we buy our WS from and based on their specs, I shopped for same components equipments and gave management side by side comparison and go approval before buying. Server was up and running within a few hours and right off the bat, was knocked off almost $1k for more of a server than quoted. So I guess I'm safe from being fired for equipment, chances are I won't be fired for using a free server OS. 

I'm gonng search up that thread you're talking about on howard. :)

But so far, I like the support of Ubuntu already. I never seems to get fast response from the MS tech forums.

---

### Post by dmann on 2006-07-06
The product you need to be comparing with Ubuntu is Microsoft Small Biz Server.  It's cheaper than buying each piece of software (like sql, exchange, etc) seperately for a small environment like yours.

Ask yourself a couple of tough questions:

How are you going to back up the linux server?

Who are you going to call when the server crashes and you can't figure out how to fix it? (in a timely manner)

What are you going to do when your boss tells you to load a new app on the server that requires MSDE, MS SQL, or ASP and your server is running Linux?  Believe me, it could happen.  It happens all the time to me...

Don't get me wrong, I feel for you.  It could work for you, possibly even work very well.  Just realize that you are going where most current admins don't go.

Not to start a flame war, but I discourage people all the time from doing white box servers.  It's a no brainer for me - a good HP server doesn't cost that much more at all for what you get.  And you get drivers and components that have been tested over and over again to work well together along with the ability to buy parts for a server that is 5 years old. Heck you even get System Insight Manager for free and that will email you when a server component (example: fan or a RAID controller battery) dies.

White box might work good for google, but for most small biz I'd say it's SAFER to buy a brand name.  Heck, if something goes wrong then there's somebody to go after - that makes the legal department happy :-)

On another note, you could get yourself VMWare Server Beta and play with all kinds of scenarios without buying a ton of hardware - and it's free.

I totally agree about the "never got fired for buying IBM" - It means "stick with what you know will work".

For any kind of production Linux server you should be looking at CentOS, RedHat, or Novell.  They focus on business.  This doesn't mean that Ubuntu can't do it, but it certainly doesn't yet have the maturity that the others do.

Dan

[QUOTE=dannieboiz]When I built the Server, I got a quote from our local supplier that we buy our WS from and based on their specs, I shopped for same components equipments and gave management side by side comparison and go approval before buying. Server was up and running within a few hours and right off the bat, was knocked off almost $1k for more of a server than quoted. So I guess I'm safe from being fired for equipment, chances are I won't be fired for using a free server OS. 

I'm gonng search up that thread you're talking about on howard. :)

But so far, I like the support of Ubuntu already. I never seems to get fast response from the MS tech forums.[/QUOTE]

---

### Post by dannieboiz on 2006-07-06
I just tried to install Ubuntu server, it seems much more complicated than the desktop version, I didnn't see a GUI or what ever. All command prompt. I'm going to setup a cheap 1ghz linux server @ home and play with it for awhile.

---

### Post by nameiwantistaken on 2006-07-07
You simply need to load Gnome on it.  This is what I did to have AMP running out of the box since you can't do a LAMP install with the desktop version (why I don't know).

---

### Post by mssever on 2006-07-07
> **nameiwantistaken said:**
> You simply need to load Gnome on it.  This is what I did to have AMP running out of the box since you can't do a LAMP install with the desktop version (why I don't know).

Actually, I've done a LAMP install with the desktop version. You simply install Apache, MySQL, and PHP using your favorite package management software (Synaptic, aptitude, etc.). There is no difference between the two versions other than what is installed be default.

---

### Post by dannieboiz on 2006-07-07
ok, this is looking real bad. :) how do you load Gnome?

---

### Post by raptros-v76 on 2006-07-07
well, gnome is the graphical thing at startup. if you got the server version, heres the command to install gnome:

```

sudo aptitude install ubuntu-desktop

```
then, once thats done
```

sudo /etc/init.d/gdm start

```

that should do the trick

---

### Post by dannieboiz on 2006-07-07
command works, but no packages was found for the install, I downloaded the server version from this site. I tried to install after booting from HDD, should I boot from CD?

---

