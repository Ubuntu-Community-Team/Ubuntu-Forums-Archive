---
title: "exposing a fresh install to the internet"
date: 2006-10-25
forum: Absolute Beginner Talk
---

### Post by bajetownrep on 2006-10-25
hello

are there any documents which outline the minimum steps one should take before exposing a fresh install of ubuntu to the internet

---

### Post by tubasoldier on 2006-10-25
> **bajetownrep said:**
> hello

are there any documents which outline the minimum steps one should take before exposing a fresh install of ubuntu to the internet

Well, unlike windows you dont need a virtual condom for you pc to play on the net. So I dont really think so. just update it when the little icon says there are updates.

---

### Post by ReaderRat on 2006-10-25
There **is** a firewall installed (iptables), but, if you want to control what it does, install firestarter, the GUI for iptables. 
```
sudo aptitude update
sudo aptitude install firestarter
```
And, as the man said, Be sure to update when prompted.

---

### Post by elchinovi on 2006-10-25
> **tubasoldier said:**
> Well, unlike windows you dont need a virtual condom for you pc to play on the net. So I dont really think so. just update it when the little icon says there are updates.

"Virtual Condom"
Hehehehe
:mrgreen: 

Like tubasoldier said, you are free to roam the internet as soon as you have your system installed!
No antivirus, antispyware, or firewall to install... (you can later install an antivirus (IE ClamAV) or a front end for Firestarter firewall, but only if you decide to do so)
So go ahed, roam free around the interner pairies!
:p 

Good Luck!

---

### Post by nickburns on 2006-10-25
Windows users are so used to having to protect themselves, it is hard to get comfortable with the ideas of the OS actually protects itself.  As a new user I was nervous about no antivirus/spyware too ... but you'll be ok.

---

### Post by elchinovi on 2006-10-25
Yeap!
No defrag to do either...
It will check the filesystem every 30 shutdowns, and that's about it!
Enjoy freedom!
=)

---

### Post by Anonii on 2006-10-25
> **tubasoldier said:**
> Well, unlike windows you dont need a virtual condom for you pc to play on the net. So I dont really think so. just update it when the little icon says there are updates.
*The post beneath this point, is Anonii's own opinion about how things work in our galaxy:*

As far as I know, Windows users dont need a "virtual condom" too. And if they are not paraplegics, porn-maniacs, or doing illegal things in any way, they can live alright without a "virtual condom". Trust me, I've done it. 
Probably, the Linux kernel is a little better security-wise than Windows's, and probably hackers dont bother with Linux, because it is troublesome, and because the average Linux user is more advanced than the Windows one (or because they dont give a shit about Linux, as many say), but still, if you want to surf and feel 99% safe, you need a firewall, like Window's users do.

---

### Post by skymt on 2006-10-25
> **Anonii said:**
> ...still, if you want to surf and feel 99% safe, you need a firewall, like Window's users do.

[Sigh](http://ubuntuforums.org/showthread.php?t=283776&page=2).

We really need a wiki page about this. Call it something like "WhyYouReallyHonestlyDontNeedAFirewall".

---

### Post by bajetownrep on 2006-10-25
well I was more wondering about services/daemons that should be turned off and so on. 

With regards to iptables I was wondering if I needed to futz around with them before exposing it to the internet.

Thnx again.

---

### Post by CatKiller on 2006-10-25
> **bajetownrep said:**
> are there any documents which outline the minimum steps one should take before exposing a fresh install of ubuntu to the internet

[Make a cup of tea]("http://www.bbc.co.uk/dna/h2g2/A61345").

---

### Post by skymt on 2006-10-25
> **bajetownrep said:**
> well I was more wondering about services/daemons that should be turned off and so on. 

With regards to iptables I was wondering if I needed to futz around with them before exposing it to the internet.

Thnx again.

You don't have to do anything. By default, Ubuntu has no services running that are accessible from the network side. Unless you're running something like Apache or SSH (which, again, are not running by default), and are directly connected to the Internet (rather than through a router), there's absolutely nothing to worry about.

---

### Post by dbd on 2006-10-25
> **Anonii said:**
> *The post beneath this point, is Anonii's own opinion about how things work in our galaxy:*
As far as I know, Windows users dont need a "virtual condom" too. And if they are not paraplegics, porn-maniacs, or doing illegal things in any way, they can live alright without a "virtual condom". Trust me, I've done it. 

I don't think that's correct, if you just install windows and then connect to the net you will very quickly get problems. The [BBC tried it]("http://news.bbc.co.uk/1/hi/technology/5414502.stm") and:
> and it was never longer than 15 minutes before the honeypot logged an attempt to subvert it.

Windows is dangerous!

---

### Post by Kurt` on 2006-10-25
> **Anonii said:**
> As far as I know, Windows users dont need a "virtual condom" too.
Within 5 minutes (and in some cases, the average was claimed to be under 3) of being directly exposed to the Internet, pre-SP1 Windows XP machines would be taken over by remote code-execution exploits. :P

There's always the possibility of a remote exploit, but on Linux (and other UNIX-based operating systems) they're extremely rare.

If you're really paranoid, you can set iptables to drop all incoming connections/packets EXCEPT for those that are part of a friendly connection e.g. when you request a web page, the data sent back from the server is allowed, but someone randomly port scanning your IP won't see anything open

---

### Post by tubasoldier on 2006-10-25
> 
Windows is dangerous!

Agreed. I had no issues with Windows until I used it without a router. Even with a firewall it is no match for the syphillus that exists for it. Windows could never keep itself safe by itself. Windows security is all about keeping the user in a valid, paid for, EULA.

---

### Post by ReaderRat on 2006-10-25
If you want other discussions about firewalls or firestarter, go to "Tags" at the top of the page and search for "firewall" or "firestarter" (without the quotes).

---

### Post by Crashmaxx on 2006-10-25
> **Anonii said:**
> 
As far as I know, Windows users dont need a "virtual condom" too. And if they are not paraplegics, porn-maniacs, or doing illegal things in any way, they can live alright without a "virtual condom". Trust me, I've done it. 


Must not have been connected to a broadband connection then. My virtual windows partition in vmware got trashed with less then a few hours of use. I wasn't even browsing the web with it. Spybot found over two thousand pieces of spyware!

When I set it up I thought "Its behind a router, and going through ubuntu, and most importantly, I won't browse the internet with it, it will be fine." But without antivirus, and antispyware on it, it quickly came to a crawl. Then I installed spybot to clean it, and it found a ton of crap.

So yes windows does need a "virtual condom" at all times. And I am thinking I will disable the internet connection for my virtual machine, rather then run all that stuff.

On the other hand, ubuntu has been running for over six months all day everyday with nothing more then a router and iptables protecting it. And not a single issue, still as good as the day I installed it. in fact, a lot better with my tuning of it.

---

