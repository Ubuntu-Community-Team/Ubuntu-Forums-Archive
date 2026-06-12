---
title: "gtk-gnutella not working well... need some pointers"
date: 2006-09-30
forum: Absolute Beginner Talk
---

### Post by baylorbear on 2006-09-30
I'm running gtk-gnutella and not having much luck with it... 
my search results aren't as quantifiable as I'd expect on the gnutella network... 

And I also have this little red icon in the upper right hand corner of the screen that reads:  "You appear to be firewalled, both TCP-wise and UDP-wise."

I have no idea how to fix that... and I'm wondering if maybe that has something to do with my not getting many results...

Any advice on how to go about solving this little problem?

Thank you!!

---

### Post by baylorbear on 2006-10-01
bump

---

### Post by raul_ on 2006-10-21
just stumbled on your post. 
[http://www.portforward.com]("http://www.portforward.com")

---

### Post by DrMilo on 2006-10-21
You also have do some configuring in the search filters to get good results. Go into edit filters and under bultir>global (pre) start adding filters to eliminate unwanted file types. I would suggest adding a number of rules about file extensions, eg files that end with ram. You don't need the (.) just the letters in the extension (doc, mov). Don't skip clicking on the New/Replace button or the rule won't be added! I have them set up as individual rules so that I can easily remove one when I'm actually looking for that file type. I haven't found an easier way. Once it's done this is the best P2P ever!

---

### Post by hotani on 2007-04-28
I'm having the same problem with this app. I have had it running in the past, now it claims to be firewalled. I don't see how this is possible since my machine is in DMZ, and the port gtk-gnutella uses is open with firestarter.

Searches return nothing, and none of the connections are successful. All other network functions are fine.

---

### Post by nick p on 2007-05-26
> **hotani said:**
> I'm having the same problem with this app. I have had it running in the past, now it claims to be firewalled. I don't see how this is possible since my machine is in DMZ, and the port gtk-gnutella uses is open with firestarter.

Searches return nothing, and none of the connections are successful. All other network functions are fine.


I have the same problem as well. In the past all I had to do was open the port for gtk-gnutella in Guarddog. That doesn't work anymore and no one seems to know anything about this problem with the exception that they give vague references to port forwarding. All over the net people are having this problem and no one knows the answer. You get over a thousand google responses for this  problem and no one knows anything and they all give some hint about port forwarding which doesn't help anyone.

---

### Post by wastedfluid on 2007-05-26
If you are using a router, and you are NOT DMZ, have you opened that port on your router?

I never could get gtk-gnutella to download.  I could get it to search, but not download.  I always received really good search results - just it would never connect.  I setup port forwarding via my router, and configured my manual IP address.. it just would never work.  And I'm nto setting Ubuntu to my DMZ.. I'm not that brave. 

Anywhom,

Good luck.

---

### Post by nick p on 2007-07-02
It's been over a month now and I still haven't figured out why gnutella is a broken, worthless application.

---

### Post by moredhel on 2007-07-02
No it isn't you are just being un willing to sort out the problems, which will be for everyone who doesn't properly configure any software that needs open ports. try something like amule, it will be the same.

people are telling you about portforward because it gives walkthroughs for you to sort out the ports on your router.

---

### Post by nick p on 2007-07-03
Sorry. I tried amule but I have the same problem. I then bypassed my router and went directly from my modem to my computer but have the same problem. Someone mentioned that my ISP may block commonly used ports for p2p networks so I changed the ports around on amule and gnutella but I get the same problems. A lot, I mean a lot of other people get these same problems as well. A year or so ago I never had any problems with gtk-gnutella using Guarddog and a Linksys router. I opened up the ports in Guarddog and didn't even have to mess with my router at all. Now all of a sudden I, and many others are having this problem. I am going to try and install an older version of Gnutella and see if that works. If it does, I'll report back. Thanks.

---

### Post by cbiere on 2007-07-03
Many ISPs - especially or maybe exclusively in the US - do far more than just blocking P2P ports. They inspect packets and identify P2P protocols this way. You write that these P2P application stopped working for you all of a sudden albeit you had changed nothing and the applications hadn't changed either. I would assume that means the source of the problem is elsewhere. It doesn't have to be your ISP, for example, one's router might frequently crash and revert to a default configuration. Maybe you misunderstood something with respect to port forwarding. These home routers have often very confusing configuration interfaces and each vendor seems to use their own terminology. Typically, people might get two things wrong:

 * They enter their WAN address instead of the LAN address
 * They forward the wrong port

Port forwarding itself has nothing to do with P2P per se, you'd need that for any kind of server and it is easy to verify whether it works or not. tcpdump, for example, would show whether packets reach your machine or not. In other words, the first step is to make sure this works.

Actually, you don't need any port forwarding in order to use Gnutella. You only need this so that others can connect to your peer. This will improve things quite a lot because many  peers are behind a firewall/router and if both sides are, they cannot exchange any files at all. So at least one of them must be able to accept incoming connections. This affects search results too.

So basically, if you can connect to Gnutella but appear to be firewalled, that's sub-optimal but not a huge problem. If you, however, cannot connect to Gnutella at all that's a quite different issue and has nothing to do with port forwarding.

You shouldn't try to use any old version of gtk-gnutella. They are disfunctional. You should use version 0.96.3.

---

### Post by nick p on 2007-08-30
> **cbiere said:**
> Many ISPs - especially or maybe exclusively in the US - do far more than just blocking P2P ports. They inspect packets and identify P2P protocols this way. You write that these P2P application stopped working for you all of a sudden albeit you had changed nothing and the applications hadn't changed either. I would assume that means the source of the problem is elsewhere. It doesn't have to be your ISP, for example, one's router might frequently crash and revert to a default configuration. Maybe you misunderstood something with respect to port forwarding. These home routers have often very confusing configuration interfaces and each vendor seems to use their own terminology. Typically, people might get two things wrong:

 * They enter their WAN address instead of the LAN address
 * They forward the wrong port

Port forwarding itself has nothing to do with P2P per se, you'd need that for any kind of server and it is easy to verify whether it works or not. tcpdump, for example, would show whether packets reach your machine or not. In other words, the first step is to make sure this works.

Actually, you don't need any port forwarding in order to use Gnutella. You only need this so that others can connect to your peer. This will improve things quite a lot because many  peers are behind a firewall/router and if both sides are, they cannot exchange any files at all. So at least one of them must be able to accept incoming connections. This affects search results too.

So basically, if you can connect to Gnutella but appear to be firewalled, that's sub-optimal but not a huge problem. If you, however, cannot connect to Gnutella at all that's a quite different issue and has nothing to do with port forwarding.

You shouldn't try to use any old version of gtk-gnutella. They are disfunctional. You should use version 0.96.3.

Good info, thanks. I can connect to Gnutella but I appear to be firewalled. The problem doesn't have to do with my router because I tried coming directly from my modem, bypassing the router entirely. I'm assuming, as you mentioned was possible, that my ISP is inspecting packets, identifying P2P protocols and ruining my P2P experience. Perhaps I should dump AT&T.

---

### Post by asmoore82 on 2007-08-30
> **nick p said:**
> It's been over a month now and I still haven't figured out why gnutella is a broken, worthless application.

long ago, because of its light weight and extreme stability, the gtk-gnutella client
was widely used to distribute Win32 Viruses ...
these hacked gtk-gnutella clients would serve up an exact matching name to anything one searched for ...
maybe you, at one time, have search for a favorite $title and $artist and seen a tiny-sized result at the bottom
of the list ... something along the lines of "$artist - $title .exe" ~ hacked gtk-gnutella clients are most likely to blame

therefore, it has become extremely common practice for the "Crowd-pleaser" gnutella clients
to block and shun gtk-gnutella clients ...

long story short ~ you may want to switch to [Frostwire]("http://www.frostwire.com/").

---

### Post by cbiere on 2007-08-31
asmoore82, would you like to me enlighten about your motivation to claim such nonsense about gtk-gnutella? I almost suspect you have a vendetta against gtk-gnutella. While it is certainly used by spammers as well just like any other software out there, your claim "hacked gtk-gnutella clients are most likely to blame" is nothing but FUD. You are either horribly misinformed or a liar. Can you provide any pointers to information to backup your claims?

Anyone who has ever used Gnutella with whatever software will certainly agree with me that gtk-gnutella is completely negligible when it comes to spam. Most spammers use either LimeWire or Gnucleus-based software. The latter is getting outdated as the project is dead so spammers are slowly abandoning it. Shareaza is used by spammers too albeit just a few well-known ones, a certain gang you could say. LimeWire is the most "popular" software used by about 80% of all peers, thus it is extremely stupid to use anything else as a spammer because you stick out like a sore thumb. Further, vendor IDs can be faked just like almost anything else in Gnutella and often are. Unless you're  a developer or a very experienced user, you should not jump to conclusions.

If you need any proof just look at hostiles.txt provided by gtk-gnutella or let gtk-gnutella display spam results and inspect the spam origins all the way you want. You'll see that 99% of those spammers do not use gtk-gnutella. In fact, gtk-gnutella is probably the most aggressive and active spam fighting of all Gnutella software whereas LimeWire isn't going anywhere with their multi-million budget. So it would make some sense to badmouth gtk-gnutella from a spammer's point of view.

> therefore, it has become extremely common practice for the "Crowd-pleaser" gnutella clients to block and shun gtk-gnutella clients

Which exactly are these "crowd-pleaser" clients and which of them offer the option to ban clients by their vendor ID? Certainly neither LimeWire nor FrostWire. Could be BearShare or Shareaza maybe but once again I think you're just making things up because I've never heard of such a "common practice".

Switching to FrostWire? Freedom of choice is great but what has your "recommendation" to do with the problems the original poster experienced and what exactly is the advantage of FrostWire over gtk-gnutella? I'd recommend LimeWire over FrostWire any day because the latter is nothing but a slightly modded variant of LimeWire and usually a few versions behind. FrostWire is a pure win-win for LimeWire anyway. You're more likely to switch from FrostWire back to LimeWire than from a very different software like gtk-gnutella and since LimeWire writes the code they have 99% control over FrostWire and Gnutella anyway. You know that's why every big vendor does noname reselling or why Microsoft never really minded (actually appreciated) piracy. It's not as bad to loose some pennies than it is to loose marketshare to the competition.

---

### Post by cbiere on 2007-08-31
nick p,

have you tried this check? [http://www.canyouseeme.org/](http://www.canyouseeme.org/)
You could and should also double-check with netstat, that you're really checking the right port. Also you should stay away from "standard" ports 6346..6350 because even if your ISP is alright, the remote ISP might not be and block these ports. Then you're not "firewalled" but many people especially in the US cannot connect to you nonetheless making file transfers in either direction difficult or down-right impossible.

---

### Post by asmoore82 on 2007-08-31
> **cbiere said:**
> asmoore82, would you like to me enlighten about your motivation to claim such nonsense about gtk-gnutella? I almost suspect you have a vendetta against gtk-gnutella. While it is certainly used by spammers as well just like any other software out there, your claim "hacked gtk-gnutella clients are most likely to blame" is nothing but FUD. You are either horribly misinformed or a liar. Can you provide any pointers to information to backup your claims?

Personal experience from *_years_* ago ...
I used to run gtk-gnutella 24/7 in ULTRApeer mode *_years_* ago.
back then, the GUI *_always_* told you from which breed of client the search results came from;
it was one of the columns in the search results, so I *_know_* hacked gtk-gntulla clients
were being used to return "$artist - $title .exe" results.

[QUOTE="gtk-gnutella's HOMEPAGE"]Versions of gtk-gnutella more than one year old are **banned,** since they lack features that are
important to the rapidly evolving gnet's health and scalability.
In addition, unstable versions are **banned** after 90 days.[/QUOTE]

All I know for sure is, as time went on, gtk-gnutella returned fewer and fewer results,
and other clients on the same computer on the same network did not...

So I say, the starter of the thread should just *try* another breed of client
and see what happens. I would never recommend Limewire to anyone,
especially a Linux user; therefore my innocent suggestion for a client
to try out was Frostwire.

Then he can have the freedom to *choose* for himself.

---

### Post by cbiere on 2007-08-31
You "know". Yeah right. If your experience is so outdated why do you assume you can give any advise about the current situation?

I've been following Gnutella almost since day one back when "gnutella 0.56" was the most recent version and not just as user. Maybe I'm getting old but I don't recall any spam epidemic that was dominated by gtk-gnutella peers. Also you should know use the term "hacked" loosely. If this was gtk-gnutella at all, it was a modified version. Has nothing to do with "hacking". Open-source, free software, you know? Everything has its downsides. So every can modify any open-source software if he has the skills and everyone can share whatever he wants on Gnutella. Be it music or viruses. Not much you can do about except using filters.

I've already wrote in my first reply that everyone can fake pretty much everything on Gnutella including vendor IDs. So it is anything but clear that what you saw originated from gtk-gnutella at all. There have been Gnutella peers that echoed whatever vendor ID you used yourself. Pretty obvious if you connected manually multiple times with differing IDs especially if passed them a completely bogus ID.

I don't have the slightest clue why you are quoting this:
> Versions of gtk-gnutella more than one year old are banned, since they lack features that are
important to the rapidly evolving gnet's health and scalability.
In addition, unstable versions are banned after 90 days.

> All I know for sure is, as time went on, gtk-gnutella returned fewer and fewer results,
and other clients on the same computer on the same network did not...

Well, many bugs have been fixed *years ago*. Also most feedback I've read implies exactly the opposite. You get more results and less spam with gtk-gnutella. There's even a very obvious reason why you get more results with gtk-gnutella in any case but let's ignore that. Also LimeWire has been a bit back-stabbing. Just recently I had to find out that it drops all queries longer than 30 characters which is very little if you're searching for a full filename but if it not, you can easily hit this limit. LimeWire never said a single word about this to anyone. Pisses me off to no extend. Not to mention that LimeWire (just like FrostWire of course) don't support querying by hash unlike *any* other Gnutella software out there. For these two reasons alone, you'd be better off with anything else.

First of all, that's history and no longer true as of 0.96.4. Second this "banning" only applied to gtk-gnutella itself. LimeWire, BearShare, Shareaza, Gnucleus, Phex and whatever don't give a damn whether you use gtk-gnutella 0.92.1 or the latest. However, if you actually tried to understand what you quoted, you'd understand why you should update it once a while. If you used any other old software, say LimeWire 3.8, your experience would like-wise suck. There have been modifications to the protocol, there have been bugfixes to the software and numerous improvements. If that's no reason for you to update and you prefer bashing it, fine.

> I would never recommend Limewire to anyone, especially a Linux user; therefore my innocent suggestion for a client to try out was Frostwire.

No offense but what you say makes no sense at all and never stating any reasons doesn't help either. FrostWire *is* LimeWire with some minor modifications (basically just settings) and a different skin. Both are open-source and free in terms of the GPL. This has nothing to do with Linux.

If you have a problem with LimeWire, LLC you should clearly refrain from using either. It's not that I really have a problem with either but Gnutella has turned into a quasi-monopoly of LimeWire. This is not healthy, not at all. The missing competition will ruin Gnutella and FrostWire is no competition. That's just a bad cop/good cop game. It's pointless to avoid one in favour of another. Use either but don't be a hypocrite about it.

Last but not least, nobody here said people should not compare different software. You were just bashing gtk-gnutella with very dubious information and recommending FrostWire without providing a single reason. There are others too like Phex and if you like FrostWire, LimeWire will work just as well if not better. The freedom of choice includes the freedom to manipulate people of course.

I do encourage people to compare the latest releases of LimeWire, FrostWire, gtk-gnutella and Phex - just to mention software which is not dead or years behind the status quo. If you're not satisfied with the results, however, rather give feedback to the developers than spreading rumours and FUD just because you came across some spam or a bug.

---

### Post by Wolf_45 on 2007-11-25
"Late to the party", I admit but...

Same problem - gtk-gnutella 0.96.3 is reporting as "firewalled" on an "out of the box" feisty installation.  Not using port 6346, and it isn't bad forwarding unless feisty does some internal forwarding that I don't know about.  It can't be router problems, because the only thing between the 'puter and the wall is a phone cord (don't laugh, but dial-up serves my purposes just fine for the moment).

One thing I've noted is that the hostcache doesn't seem to be updating - everything (hits and misses) is showing 0.

Any pointers on direction to go from here?

---

### Post by blueglue on 2007-11-25
First off, alot of you guys are using software firewalls, do you really need them? are you distributing nation critical information? If no the NAT on you router is more than enough. I know alot of people would say that prevention is better than cure, but the security risk to a home user on ubuntu is real low. I gave up wearing waterwings to work incase of heavy rainfall along time ago! Try DMZ cool. If gnutella is not so good try the official Limewire for linux, it works a treat and supports bittorents too. PS i have a NAT on my router and Limewire works fine with no alteration from the manufacturers(belkin) defaults.

---

### Post by cbiere on 2007-11-25
gtk-gnutella 0.96.3 is over a year old. Therefore, it won't contact any bootstrap services anymore. This is usually not much of a problem if you run it every few days.

I've explained here how you can bootstrap it yourself manually:
[http://ubuntuforums.org/showthread.php?t=614989](http://ubuntuforums.org/showthread.php?t=614989)

Though the better option is to update to the current release 0.96.4, or even better to 0.96.5u from the SVN repository.

---

### Post by Wolf_45 on 2007-11-26
Thanks cbiere, I'll see about giving the manual bootstrap a shot.  As for using 0.96.3, I don't know what to say - that's what came down the pike when I used apt-get exactly a week ago!

blueglue, for a while I was running limewire on my RH 7.1 install.  To make a long story short, gtk-gnutella's always worked better for me.

---

### Post by Wolf_45 on 2007-11-27
> **cbiere said:**
> gtk-gnutella 0.96.3 is over a year old. Therefore, it won't contact any bootstrap services anymore. This is usually not much of a problem if you run it every few days.

I've explained here how you can bootstrap it yourself manually:
[http://ubuntuforums.org/showthread.php?t=614989](http://ubuntuforums.org/showthread.php?t=614989)

Though the better option is to update to the current release 0.96.4, or even better to 0.96.5u from the SVN repository.

cbiere, thought you'd like to know - bootstrapped manually, and everything works hunky-dokie!

<scratch yet another reason I "need" Win.....  Now if I can master GIMP, I won't ever have a reason to keep it!>

---

