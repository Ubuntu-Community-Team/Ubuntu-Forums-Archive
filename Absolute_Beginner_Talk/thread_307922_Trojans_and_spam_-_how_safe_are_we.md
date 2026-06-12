---
title: "Trojans and spam - how safe are we?"
date: 2006-11-27
forum: Absolute Beginner Talk
---

### Post by stig on 2006-11-27
How safe are we Ubuntu users from having our computers hijacked and used to send out spam?

I'm familiar with the arguments about the safety of Linux with regard to email viruses. I use a complex password to login. I download official updates quickly. I have a broadband connection with a hardware firewall. I take care with emails and never click on any links unless I trust the sender.

But there is so much news about trojans, robots, hijacked PCs sending out millions of emails etc that I still worry about this particular aspect. Is it possible for anyone to get control of my PC and use it in this way, given all the security I mentioned above? (I guess I'm going through a paranoid stage!)

Thanks

---

### Post by ReaderRat on 2006-11-27
[**AntiVirus For Ubuntu**](https://help.ubuntu.com/community/ClamAV)

---

### Post by Ben Sprinkle on 2006-11-27
No it's not possible. You would need root. Only way for a virus is if somehas has remotely connected to your computer with your permissions or if the person is right beside you.

---

### Post by darrenm on 2006-11-27
Don't install openssh-server unless you know what you are doing and nothing else can really harm you.

---

### Post by stig on 2006-11-27
Thanks for your quick - and comforting - replies. I got even more worried because there was a double-page spread in the British newspaper "The Times" on Saturday all about the trojan/spam problem. Incidentally, it also said one of the main people responsible for spam sent it via an ISP based in London but that the ISP disputes this. The newspaper would not reveal the name of the ISP for "legal" reasons. My ISP is based in London!

---

### Post by Ben Sprinkle on 2006-11-27
Lol, don't believe that rubbish. ;)

---

### Post by darrenm on 2006-11-27
Nah thats not right. The majority of spam comes from compromised Windows boxes direct to your ISP's mail server

---

### Post by drphilngood on 2006-11-27
I seem to remember the last study showing a Windows XP computer being compromised within ten minutes of being connected to the internet if it didn´t have all the malware protection, firewall and patches.
Does anyone remember or, better yet, have a link to this study for verification?  I no longer use Microsoft products but I´d enjoy the read if anyone can produce it.

edit:
This isn´t the one I had in mind but it´s interesting: [PCs Infected in 12 Minutes]("http://www.realtechnews.com/posts/1511")

---

### Post by Ben Sprinkle on 2006-11-27
Haha, it's true I have experimented this before by getting my neighborhood of 13 people to try to guess my ip and 'hack' into it, gaining control of access.

Worked within 20 minutes, about 13 or 14 I think. (Those people also knew what they were doing) :)

---

### Post by Oki on 2006-11-27
&#8220;You would need root. &#8220;
I have heard this one many times, but today you can read this regarding Mac; &#8220;this program could be silently installed to your User account and hooked to each application you use&#8230; and it doesn't require Administrator rights to do so.&#8221; Link; [http://www.f-secure.com/weblog/archives/archive-112006.html#00001030](http://www.f-secure.com/weblog/archives/archive-112006.html#00001030)

So, if this can happened to Mac OS X, then I dont understand why it cant happened to Linux &#8211; both normally requires password/sudo to install somthing?

And btw; I have a book about Ubuntu where they tell you how to install antispyware programs...

---

### Post by drphilngood on 2006-11-27
> **Goat Spirit said:**
> Haha, it's true I have experimented this before by getting my neighborhood of 13 people to try to guess my ip and 'hack' into it, gaining control of access.

Worked within 20 minutes, about 13 or 14 I think. (Those people also knew what they were doing) :)

I wouldn´t let a Windows machine near the internet but through a NAT router.

---

### Post by Ben Sprinkle on 2006-11-27
I forgot to mention I have a **cable** router, non wireless which makes it harder.

If you have a wifi or wireless area network then it's just plain retarded for people wishing not to be hacked.

I have this dumb person next door who has wireless, I can leech from him all the way across the court. :)

I could take over his router as well if he doesn't have a password. :)

---

### Post by jsilve1 on 2006-11-27
> **stig said:**
> How safe are we Ubuntu users from having our computers hijacked and used to send out spam?
<snip!>
But there is so much news about trojans, robots, hijacked PCs sending out millions of emails etc that I still worry about this particular aspect. Is it possible for anyone to get control of my PC and use it in this way, given all the security I mentioned above? (I guess I'm going through a paranoid stage!)

Thanks

First of all, suffice it to say that by using Ubuntu you are  completely safe from the typical Trojan, Virus, or Malware problems associated with using Windows. This point is important: YOU ARE COMPLETELY SAFE FROM VIRUSES. Don't believe anyone who says otherwise.

HOWEVER that does not mean you are completely safe from any kind of harmful or unwanted intrusion.

Ubuntu is Pretty Safe(TM) in its default configuration, and does not have too many Internet services enabled that can open cracks into a system.

That said, there are some tools, servers, and applications that you can install later than can reduce the potential integrity of the system.  If you don't need, for example, a Web Server (such as Apache), then DON'T INSTALL IT. That alone will keep your system safer.

Your Ubuntu computer is safe from Viruses. Period. There is effectively no Virus that can harm you. Don't believe Windows admins or the media when they say things like "Windows is targeted because it has such large user base, and its only a matter of time for Linux to be affected by Viruses." That is FUD, plain and simple, and as such is simply untrue.

(Trojans, however, are another story.  Although you are Quite Extremely Safe(TM) from Trojans as well.)

Please use Wikipedia and/or Google to read up on the difference between Viruses (which technically require no human intervention to propagate) and Trojans (which are basically socailly engieered tricks to get bad code running on your computer).

I guess all of this can go into the category of "Malware". But your Ubuntu box is basically immune to run-of-the-mill Windows Malware. To quote my Wife (on receiving fifty bazillion spam emails) "I am so glad I don't use Windows and don't have to worry about clciking on these emails".  That is essentially 100% true.

To *really* be safe, do (or don't as appropriate) do the following:

1) High bandwidth connection? (DSL, Cable, etc.) Run your computer behind a stand-alone firewall/router.  For example the Linksys BEFW series.

2) Don't install anything you won't use or don't need.  For example, don't install Apache if you do not need a webserver.


3) (for the really paranoid) *UNinstall* things that you never use. This is a bit harder to figure out, because some things that are "never used" are, in fact, used quite a bit by the system itself.  One example here, though, is "wget". This very useful tool is also used by crackers as a stage-two downloader once they have opened a tiny crack in your system. No wget? No way for them to get stuff onto your system.

4) (For the fairly paranoid) Install and configure a local Firewall tool.  Ubuntu (and Linux in general) comes with Iptables, a firewalling tool. But this thing is hard to configure. There are several excellent GUI firewall config tools such as Firestarter and Guarddog. Use one of those.

5) Set unused services to not start automatically. SSH, for example, comes with Ubuntu by default, but it is not turned on! That is a Good Thing(TM) as far as security goes. Do the same with any other service you don't use. System->Administration->Services (not that this tool is broken in Dapper (6.06) but works in Edgy (6.10))

6) Use GOOD PASSWORDS. Do not use your wife's, husband's, or kid's name, birth date, or own first name as a password. DON'T USE THE WORD "password".

7) Don't *run* binary attachments sent from untrusted sources. You won't get too many of these, but it is conceivably possible to get an executable script or binary program that is designed to Do Something Bad(TM).  The thing is, it won't be runnable. This is where the real difference between Windows and Linux is. Say I send a Windows bianry to somwone that is designed to delete everything on their C drive. All I have to do is give the file the extension ".exe" or ".bat" and double-clicking on the file, once saved, or even just downloading the file (depending on mail client settings), and Windows will run it!  In Linux, the equivalent just will not happen.  I can have a small Linux executable or shell script but it just will not run unless I manually save it, change the file executable bit to "yes", and then try to run it. It is the second step which is the doozy, and is the reason why Malware of the sort that plagues Windows does not exist for Linux. I have to *manually* set the execute permissions!

Well, I can't think of anything else for now.... Just trying to build up my "number of cups of Ubuntu"

later...

---

### Post by drphilngood on 2006-11-27
I set my IP range to allow enough for my connected machines only and then use Mac addressing to asign them.;) Every little bit helps...

---

### Post by Ben Sprinkle on 2006-11-27
You got any ideas how to clone mac addresses in linux? I need to know SOOOOO badly. :)

---

### Post by drphilngood on 2006-11-27
> **Goat Spirit said:**
> You got any ideas how to clone mac addresses in linux? I need to know SOOOOO badly. :)
haven´t got a clue:twisted:

---

### Post by Shuja on 2006-11-27
I can't remember where I read it but someone used wine to try and run windows viruses.  It was a rather amusing article.

---

### Post by bodhi.zazen on 2006-11-27
> **Shuja said:**
> I can't remember where I read it but someone used wine to try and run windows viruses.  It was a rather amusing article.

Here it is: [Running windows viruses with wine](http://os.newsforge.com/article.pl?sid=05/01/25/1430222&from=rss)

Other useful virus sites:

		[http://en.wikipedia.org/wiki/List_of_Linux_computer_viruses](http://en.wikipedia.org/wiki/List_of_Linux_computer_viruses)
		[http://librenix.com/?inode=21](http://librenix.com/?inode=21)
		[http://www.theregister.co.uk/2003/10/06/linux_vs_windows_viruses/](http://www.theregister.co.uk/2003/10/06/linux_vs_windows_viruses/)
		[http://math-www.uni-paderborn.de/~axel/bliss/](http://math-www.uni-paderborn.de/~axel/bliss/)
		[http://software.newsforge.com/article.pl?sid=06/04/18/1941251&tid=78](http://software.newsforge.com/article.pl?sid=06/04/18/1941251&tid=78)

As far as malware, yes it is possible for a Linux box to be hacked but it is rare and, because of open source these holes are rapidly fixed.

This links may be helpful:

[Linux Kernel Rootkits](http://www.la-samhna.de/library/rootkits/index.html)

[How to scan your (linux) computer for rootkits](http://www.howtoforge.com/faq/1_38_en.html)

---

### Post by drphilngood on 2006-11-27
Great post, bodhi.zazen, both interesting and useful!

---

### Post by bodhi.zazen on 2006-11-27
> **drphilngood said:**
> Great post, bodhi.zazen, both interesting and useful!

Thanks :p

If you want to see the process in action :

[chkrootkit results analysis help please](http://ubuntuforums.org/showthread.php?t=305367)

No solution to this one yet, but I am 99.9% sure his box was hacked (only root should have user ID =0 and he is finding interesting files.... :( )

---

### Post by tribaal on 2006-11-27
> You got any ideas how to clone mac addresses in linux? I need to know SOOOOO badly

Pretty easy:

```
ifconfig [interface name] hw ether [new MAC address]
```

Enjoy :)

- trib'

---

### Post by duality on 2006-11-27
You are very safe if you flollow these simple procedures:
1. Use firefox, install these extensions: adblock, adblock plus, fileset.G updater.

2. Install "firestarter", (firewall, frontend for iptables), or the hardcore way to learn and make your own iptables.

Thats pretty much it, and dismiss the antivirus for linux or any other such program for that matter, as it will only waste processing power for nothing.
When ubuntu is vulnerable to something, then you will get an automatic update pretty quickly to fix it...

---

### Post by Ben Sprinkle on 2006-11-27
> **tribaal said:**
> Pretty easy:

```
ifconfig [interface name] hw ether [new MAC address]
```

Enjoy :)

- trib'

Wholy!
[That's woah holy! :)]

---

### Post by stig on 2006-11-29
Coincidentally, I received a vnunet newsletter this morning with one story having the title "Adware penetrates OSX":

[http://mail.vnunet.com/cgi-bin1/flo/y/eybn0FTtk70V3L0DY860A7](http://mail.vnunet.com/cgi-bin1/flo/y/eybn0FTtk70V3L0DY860A7)

I know nothing about the inner workings of Linux - does it require user permission before it installs system libraries on the machine?

---

### Post by loell on 2006-11-29
yes, it requires root permission to install libraries,

trojans are possible in ubuntu, if i'm not mistaken debian packages can contain a script, you can use your imagination on how to launch that script  later, since deb package requires a root permession to be installed , 

a hypothetical situation could be..

a linux game has just been out, and its a cool game that everybody wants  to try , so now you see, the target audience is now large ,then a malicous packager/script writer , now volunteers to package and release it in the community , imagine hundreds or thousands could be downloading this game package :twisted:

viola, you've got an ubuntu zombie stations and worst it will broked your system later, when it has finished its purpose :twisted:

---

### Post by 3rdalbum on 2006-11-29
> **Oki said:**
> “You would need root. “
I have heard this one many times, but today you can read this regarding Mac; “this program could be silently installed to your User account and hooked to each application you use… and it doesn't require Administrator rights to do so.” Link; [http://www.f-secure.com/weblog/archives/archive-112006.html#00001030](http://www.f-secure.com/weblog/archives/archive-112006.html#00001030)

So, if this can happened to Mac OS X, then I dont understand why it cant happened to Linux – both normally requires password/sudo to install somthing?


That's the first mistake most people make when comparing the two operating systems - they assume that OS X is just pure FreeBSD with Quartz and Aqua on top. Linux has a fully-formed security system. OS X has bits and bobs of many BSDs in its kernel, but with only a shadow of a proper security system.

Programs can be installed into the filesystem on Mac OS X without a password. OS X runs its generic installer program as root (and any post-install scripts included with the package), without a password being needed. This is a ridiculous security flaw that Apple have acknowledged, but not considered fixing.

The same thing would not happen with Ubuntu. If something that had the same effect was found in Ubuntu, or any other Linux distribution, the vulnerability would be fixed straight away; not like those layabouts at 1 Infinite Loop.

---

### Post by bodhi.zazen on 2006-11-29
> **loell said:**
> yes, it requires root permission to install libraries,

trojans are possible in ubuntu, if i'm not mistaken debian packages can contain a script, you can use your imagination on how to launch that script  later, since deb package requires a root permession to be installed , 

a hypothetical situation could be..

a linux game has just been out, and its a cool game that everybody wants  to try , so now you see, the target audience is now large ,then a malicous packager/script writer , now volunteers to package and release it in the community , imagine hundreds or thousands could be downloading this game package :twisted:

viola, you've got an ubuntu zombie stations and worst it will broked your system later, when it has finished its purpose :twisted:

Thank you ! Yes, this is exactly how malware is spread, it is called "social engineering". and it is beyond viruses. All OS are vulnerable to this.

You should be cautions when installing anything outside of the official Ubuntu repositories or trusted sites.

---

### Post by loell on 2006-11-29
that is not to say  not to trust community packagers at all, i for one, package one or two bleeding edge softwares and released it to the community, both for testing and because there's demand. because of bleeding edge packaging, newbies are turned testers in an instant with little effort on their part, newbie feedbacks are very essential for the actual developers of those projects, in turn it speeds up development, its a benefecial solution for both users and project developement.

now, if we could just establish an indipendent community body, that can identify community packagers that is neither part of MOTU or official debian maintaners. atleast at some level  we can protect users from social engineering.

though we haven't seen this trend of threat yet, i think the time is nearing.

---

