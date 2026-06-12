---
title: "Internet safety"
date: 2005-06-06
forum: Absolute Beginner Talk
---

### Post by ~J~ on 2005-06-06
I've searched the forums for an answer after been told by a few people who've used linux for a number of months, and I simply must know if it's true what I've read and heard...

Is it true than you don't really need a virus protector and/or firewall when running linux?

I've shocked if this is true!  If it's not true, are there any decent virus protectors/firewalls that I should be using?

I used to use a Sun SPARC many years ago with something called Firewall 1 (a GUI kinda affair that was a nightmare to set-up) but we were strongly recommended having one because there were so many programs around that could run scripts so easily.

I do have Windows XP with Mcafee running on my win-partition, but I still feel a little exposed using the net on linux without any protection.

---

### Post by Sionide on 2005-06-06
The main linux based Firewall is called Firestarter and there are a few anti-virus packages out there too, but they're hardly needed. Most virii and trojans etc are written to attack Windows machines because they're so much easier to exploit. Linux is extremely secure on the Internet - try it out, run the Ubuntu Live CD, goto [http://grc.com/](http://grc.com/) and do a Shields Up test. You won't find any open ports.

---

### Post by somuchfortheafter on 2005-06-06
well personally the firewall is a good idea, firestarter is ok if you really need it however most consumer based routers have a more powerful firewall on them that doesnt sacrifice network usage for the end user. that is what i use for linux not a software package on my main system. also yes virii tend to be written for windows boxes with windows commands, same with spyware on the web, i do remember hearing about a guy online who actually got copies of the viruses and then installed them intentionally with wine but he ran into some issues that were pretty funny, yet he had to do alot of work to get that far.

---

### Post by Sionide on 2005-06-06
An ideal firewall is a hardware one obviously but I don't think that's what ~J~ meant. I mean [http://smoothwall.org](http://smoothwall.org) would be good for that kind of thing..

---

### Post by nocturn on 2005-06-07
[QUOTE=Sionide]An ideal firewall is a hardware one obviously but I don't think that's what ~J~ meant. I mean [http://smoothwall.org](http://smoothwall.org) would be good for that kind of thing..[/QUOTE]

I dumped smoothwall because the went of the GPL.
IpCop is very nice, it was based on Smoothwall at first, but it now dropped most of that code.

---

### Post by nocturn on 2005-06-07
[QUOTE=~J~]I've searched the forums for an answer after been told by a few people who've used linux for a number of months, and I simply must know if it's true what I've read and heard...

Is it true than you don't really need a virus protector and/or firewall when running linux?

I've shocked if this is true!  If it's not true, are there any decent virus protectors/firewalls that I should be using?
[/quote]

These are two questions with seperate answers.
No, you do not need virus protection on Linux.  There are virus scanners, but the primarily scan for Windows virusses (and can be plugged in to a mail server)

You may need a firewall depending on what you are running.  Ubuntu out of the box has no open ports, so there is little a firewall can protect (a default WinXP install has many things open).  
If you install software like Samba/NFS/... you may need a firewall, firestarter is supposed to be good, but it is way easier (and safer) to pay 50-90€ for a hardware box (either an old PC with IpCop or the likes or a Linksys/Netgear/SMC box).

---

### Post by tikal26 on 2005-06-07
[QUOTE=nocturn]These are two questions with seperate answers.
No, you do not need virus protection on Linux.  There are virus scanners, but the primarily scan for Windows virusses (and can be plugged in to a mail server)

You may need a firewall depending on what you are running.  Ubuntu out of the box has no open ports, so there is little a firewall can protect (a default WinXP install has many things open).  
If you install software like Samba/NFS/... you may need a firewall, firestarter is supposed to be good, but it is way easier (and safer) to pay 50-90€ for a hardware box (either an old PC with IpCop or the likes or a Linksys/Netgear/SMC box).[/QUOTE]
 J:
I  was new too and one reason I made the switch was the constant haseel with firewall and antivirus running on the background slowing things and since I am a student i just could not afford to pay in order to keep up. Now I run guardog and clamav in my machine and Ican run it so it checks my network cmputer that runs windows and it finds quiet alot of things, but in four months I never had a virus.

---

### Post by dewey on 2005-06-07
You don't need to worry about typical virii as much as you do malicious code.  For instance, if you downloaded a tampered with program, they could hide a simple "sudo rm -rf" command somewhere in the script, or even a backdoor/rootkit.  The virii scanners found on linux primarily scan for windows viruses, to prevent the spread of them on vulnerable machines.

Just install software from trusted sources(official repositories, official websites of the wanted program) and you'll be A-OK.

---

### Post by az on 2005-06-07
Virii is not a word.  You mean viruses.

Windows hosts viruses because of the way that it is put together.  Linux does give the viruses the same opportunities to grow.

That does not mean there are no security vulnerabilities.  Will a firewall protect you from vulnerabilities?  Probably not.

By nature, a firewall closes off your system and makes it unuseable.  Whenever you need to use something you open ports, punching holes into your firewall.

If you know what you are doing, or just stick to standard Ubuntu packages, your computer does not listen to any outside ports and is not at risk to fall prey to vulnerabilities.  So, yes, an ubuntu standard setup is more secure than a Microsoft company setup with a firewall and virus scanner.

Also, the linux kernel is the firewall.  All the firewall packages that are available are used to configure how the kernel handles packets.  That is what a firewall does:  It handles packets.

---

### Post by bastya_elvtars on 2005-06-10
[QUOTE=azz]Virii is not a word.  You mean viruses.[/QUOTE]

It is VIRI, as virus is a latin word, and its plural is viri, you are both wrong.

---

### Post by Jace on 2005-06-13
[http://www.m0n0.ch/wall/](http://www.m0n0.ch/wall/)

---

### Post by poofyhairguy on 2005-06-13
[QUOTE=~J~]
Is it true than you don't really need a virus protector and/or firewall when running linux?[/QUOTE]

Not like its needed in Windows, no. That is the reward you get for jumping on the Linux ship before the masses do.

---

### Post by ~J~ on 2005-06-13
Thanks for the feedback on this, I really appreciate it.

I've heard in the past about linux been pretty damn safe when it comes to virus and hacks, but one thing I have on my windows partition is McAfee internet security suite which has some great features.

For example I can block cookies, my 'navigation' on the net is via a proxy and of course I get warnings if Joe Hacker is trying to route FBI's traffic via my machine in a bid to capture the transactions from Parliment to Area51!

I already have a hardware firewall in my wireless router (a netgear DG834G) but of course coming from windows and all the trouble I've had, it's hard to believe and appreciate the robustness of linux.

Thanks again though, like I said I really appreciate it and hope someone else may have benefitted from your answers...

---

### Post by desdinova on 2005-06-13
J

I note by your location your also in Wales - you may want to join the South Wales Linux User Group at [www.swlug.org.uk](www.swlug.org.uk)

You can also block cookies etc with Privoxy - but a good firewall means you haven't got to worry about redirects etc. Privoxy is also a good ad blocking proxy

---

### Post by skoal on 2005-06-13
Strange, but in all the years I've run Win boxes I've never used a firewall or anti-virus software.  I've been running my computer "naked" to the world for over 12 years and have yet to get 1, yes 1, virus or trojan.  Sure, I get probed and port scanned all the time, but how's that any different from trying on clothes in a department store as customers peek at your naked legs under the wooden door in the fitting rooms.  Completely harmless, and quite exhilirating too.  If it works for Windows, surely, it works for Linux.

\\//_

---

### Post by ~J~ on 2005-06-13
@desdinova

Hey thanks for that, I might just pop along to one when I feel a little more confident in what I'm doing and I know the bar pretty well too!

@skoal - love the way you've described your vunerability!! lol

---

### Post by desdinova on 2005-06-13
[QUOTE=~J~]@desdinova

Hey thanks for that, I might just pop along to one when I feel a little more confident in what I'm doing and I know the bar pretty well too!

@skoal - love the way you've described your vunerability!! lol[/QUOTE]
 I'd join regardless - it always helps to know a local guru or two ;-)

---

### Post by Jace on 2005-06-14
What no remarks on the M0n0wall project? This is good stuff........

---

### Post by az on 2005-06-14
[QUOTE=bastya_elvtars]It is VIRI, as virus is a latin word, and its plural is viri, you are both wrong.[/QUOTE]
Virus is latin.  In the fourth declention (nominative, vocative and accusative), plural of virus is virus (that means whether is it a subject or a complement).  Viri is not in any english dictionary.

---

### Post by skoal on 2005-06-14
[QUOTE=azz]Virus is latin.[/QUOTE]
Didn't you mean, "latin is a Virus." I had 2 semesters of that way way back in high school, as nuns slapped my wrist for improper pronunCIAtion.  I couldn't escape that "plague" soon enough and get back to learnin' some good 'ole Texan Spanglish.

\\//_

---

