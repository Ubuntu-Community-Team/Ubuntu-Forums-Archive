---
title: "linux anti virus software? why"
date: 2007-05-01
forum: Absolute Beginner Talk
---

### Post by silent1643 on 2007-05-01
if linux is suppose to be x1000 better at preventing viruses than windows, why are anti virus programs for linux still popular? is this a "just in case" cause? or simply for the paranoid?

---

### Post by oilchangeguy on 2007-05-01
read this, from the current issue of smart computing:   

The Tethered Goat
Is Linux Really More Secure Than Windows?

If you&#8217;ve heard about Linux, the alternative&#8212;and often free&#8212;OS (operating system) that competes with Windows and Apple&#8217;s Mac OS, one of the first things you were likely told is that it is far more secure than any version of Windows. Linux proponents are right and for a variety of reasons. It comes with many more integrated security tools than does Windows, for example, and new security measures can be easily applied without needing to patch core components of the operating system.

Linux is also open-source, meaning that the basic programming code is open for programmers to see and improve upon. Windows, by contrast, is closed source, meaning that only Microsoft can access and change the underlying code. The open-source nature of Linux has attracted a huge number of highly talented white hat hackers, who probe Linux for weaknesses the same way a black hat hacker would, but then fix the flaws before they can be exploited. By design, Windows doesn&#8217;t have this large community of supporters working in its favor, so the company is forced to respond to threats as they are revealed instead of proactively plugging security holes.

Linux also has the advantage of being highly compartmentalized compared to Windows, meaning that even if a malware program does somehow manage to break in, the damage it can do is often restricted to one area and the rest of the operating system is unaffected. Windows malware can gain access to a much broader range of the OS and can often bring down the entire computer or grant complete access to all of the operating system&#8217;s components.

Batten Down The Hatches

When it comes to the Internet, Linux is theoretically just as vulnerable to attack as Windows because both OSes use TCP/IP (Transmission Control Protocol/Internet Protocol) to let data in and out through various TCP ports. There are thousands of these ports, and each represents a door that a potential attacker can use to gain access to your computer. Port scanners are available that are designed to search for open ports. Hackers can use them to either flag unlocked ports for a future attack or to initiate an attack immediately.

Although Linux uses TCP/IP for transmitting and receiving Internet data, most versions of Linux (called distributions) are more secure than Windows out of the box because more TCP ports are locked down by default. Windows uses a lot of system utility programs called services that open up ports, effectively giving intruders more doors to work with.

Popularity Contest




SpywareBlaster differs from many antispyware programs in that it locks down your computer so attackers can&#8217;t get in instead of fighting them once they get there.

The SANS Internet Storm Center (isc.sans.org) claims that the average unprotected Windows XP PC connected to the Internet will be attacked in 10 minutes or less, on average. To test this, we connected a PC that had a fresh installation of Ubuntu Desktop (a Linux distribution) to the Internet and watched for attackers and then installed a fresh copy of WinXP SP2 (Service Pack 2) on the same machine and repeated the test. Both were actively probed by outsiders within 30 minutes, but after several days of testing, the Windows PC had a worm installed on it while the Linux machine was left untouched. The inherent security and compartmentalized structure of Linux are huge components of its resilience, but there are many contributing factors that make Windows more susceptible to attack.

People who program viruses, malware, and spyware targeted at home users want to do the most damage, gather the most information, or co-opt the largest number of computers possible, and Windows&#8217; 90%-plus market share makes it a perfect target. Home computers with Windows are also much more likely than home computers with Linux to contain valuable information. The slowly growing contingent of people who use Linux as their main operating system for home computing is hardly big enough to be worth a malware programmer&#8217;s time.

Anatomy Of An Attack

Let&#8217;s pretend we&#8217;re bad guys who want to perform a DoS (Denial of Service) attack on a corporate Web site. A DoS attack works by flooding a Web server with so many requests for information that the server becomes overwhelmed and locks up or even crashes. No single computer can generate enough requests to perform an effective DoS attack, and the attack could be traced back to you anyway; so the best form of attack would be to install a virus. The perfect DoS virus installs itself undetected on a computer, propagates to other computers via email or other means, and then erases its tracks and lies dormant until the precise time the DoS attack is scheduled to happen.

Even the most damaging viruses only infect a small overall percentage of PCs, so designing it for Linux is out of the question, because you&#8217;d never achieve the critical mass of computers needed to mount an effective DoS attack. The only OS that is installed on enough home computers is Windows, so that&#8217;s what malware programmers target.

Another popular type of attack exploits buffer overrun errors. Most programs that accept input from devices such as mice and keyboards have a memory buffer that temporarily stores input until the computer has a chance to process it. Programmers can take advantage of this to assume complete control of your computer. The most popular way to perform a buffer overrun attack is to load the data from a Web page when some unsuspecting soul visits a Web site, so let&#8217;s put our black hats back on and see how we can get maximum effectiveness out of our attack. We want to exploit the Web browser used by the largest number of people, which is Internet Explorer. Once we exploit the browser we want to make sure our malicious software will have the best chance to actually execute, so we design it for Windows. As you can see, going with a combination such as the Firefox browser and Linux operating system eliminates more than 90% of our potential victim pool, so why worry about anything other than Microsoft&#8217;s software?

Know Your Distributions

Just because Linux is an inherently safer and smaller target than Windows doesn&#8217;t mean you should let your guard down. There&#8217;s no such thing as a perfectly secure operating system. If you use Linux, make sure to read the documentation for your distribution carefully to see if there are any important security settings that are not enabled automatically, and use the same type of security programs you would use to lock down a Windows PC.

Root For The Underdogs

No matter what OS you use, it is possible to dramatically increase overall security by going against the flow when it comes to networking and Internet applications. Instead of Internet Explorer, consider using a browser that has less market share. Instead of Windows&#8217; built-in firewall, try a third-party application. There&#8217;s nothing you can do to avoid hackers who are specifically targeting you, but you can do a lot to avoid their attention in the first place.

by Tracy Baker


Best Defense


Aside from avoiding popular Internet-enabled software such as Internet Explorer, there are four main ways you can keep hackers and the malicious software they create at bay.

Firewalls. A firewall is your first line of defense because it examines all data entering or exiting the PC to make sure you personally requested it or sent it. Only use one firewall and make it a third-party one, such as Comodo Personal Firewall (free; [www.personalfirewall.comodo.com)](www.personalfirewall.comodo.com)).

Antispyware. Spyware lets programs communicate private data through the Internet without your permission, so be sure to use a product that locks down your computer. We recommend you try a product such as SpywareBlaster (free; [www.javacoolsoftware.com/spywareblaster.html](www.javacoolsoftware.com/spywareblaster.html)) along with one that eradicates spyware, such as Windows Defender (free; [www.microsoft.com/athome/security](www.microsoft.com/athome/security)
/spyware/software/default.mspx. You can use as many antispyware applications as you want to.

Antivirus. Antivirus software scans email and other incoming files to make sure they aren&#8217;t infected with known viruses, and they also take care of viruses that have somehow infiltrated the computer. Any brand-name tool will do the job, but never install more than one antivirus program on the computer at once.

Updates. Keep your operating system patched with the latest fixes at all times by using tools such as Windows Update (windowsupdate.microsoft.com). You also need to check for the latest antivirus and antispyware updates at least weekly and check to see if firewall updates are available at least monthly.

---

### Post by aidanr on 2007-05-01
if you are running a network with linux and windows boxes you don't want to be sending on viruses to the windows boxes over the network or by email

and afaik there are proof of concept viruses for linux and mac but i think they require you to enter you root password though

---

### Post by silent1643 on 2007-05-01
thanks, im not a paid subscriber so i can't really read the relevant part of that article, could you copy and paste?

---

### Post by silent1643 on 2007-05-01
> **aidanr said:**
> if you are running a network with linux and windows boxes you don't want to be sending on viruses to the windows boxes over the network or by email

good point... but on a stand alone linux system?

---

### Post by oilchangeguy on 2007-05-01
check out my previous post now.

---

### Post by silent1643 on 2007-05-01
great article, just what i wanted , thank you oilchangeguy

---

### Post by oilchangeguy on 2007-05-01
your're very welcome.

---

### Post by starcraft.man on 2007-05-01
I will make this brief, I already got into a very civil and nice discussion with Whee about this. [Here.]("http://ubuntuforums.org/showthread.php?t=427905") Bottom line, is that most Ubuntu users don't need an AV scanner at all. If you have a NAT router, you are protected from any passive attack the internet can send you. Behavior is most important, don't download bad files, don't open attachments, view email in plain text format, and you likely shouldn't fileshare from sources you don't trust (more people seeding like thousands, means thats a source you can likely trust).

Read my post if you want more info, and if you must I like AVG.

---

### Post by gamer91 on 2007-05-01
isn't it also for the same major reason as firefox - less people have creates less viruses for it.

---

### Post by mech7 on 2007-05-01
Does windows virusses also run under WINE ?

---

### Post by silent1643 on 2007-05-01
> **mech7 said:**
> Does windows virusses also run under WINE ?

good question i would also like to know this, i doubt it since you are still technically in linux

[QUOTE=starcraft.man]" Behavior is most important"[/QUOTE]

i agree 100%

---

### Post by Tomosaur on 2007-05-01
Anti virus programs are very often used on Linux to scan Windows hard drives for viruses. 

For those people who run anti-virus programs to protect their actual Linux system - it's usually a 'just-in-case' situation, yes. It's better to be safe than sorry. Servers, for example, absolutely cannot afford to suffer an attack, or downtime, so they may aswell run anti-virus software there.

---

### Post by orb9220 on 2007-05-01
I have seen a thread here about running windows virus's under wine and it can Fud your .wine folder. But leaking into Linux filesystem and creating Havoc? The thread stated it would just sit there not knowing what to do.

I imagine if A virus was written to exploit directlly using wine as the delivery package to a linux filesystem with linux specific commands than yes it could be done.

---

### Post by noerrorsfound on 2007-05-01
> **orb9220 said:**
> I imagine if A virus was written to exploit directlly using wine as the delivery package to a linux filesystem with linux specific commands than yes it could be done.
It couldn't damage your whole system though, unless you were running as root.
> **silent1643 said:**
> if linux is suppose to be x1000 better at preventing viruses than windows, why are anti virus programs for linux still popular? is this a "just in case" cause? or simply for the paranoid?
What leads you to believe that GNU/Linux antiviruses are popular? I think most home users of GNU/Linux don't bother downloading an antivirus as it is not really needed.

---

### Post by mech7 on 2007-05-01
> **orb9220 said:**
> I have seen a thread here about running windows virus's under wine and it can Fud your .wine folder. But leaking into Linux filesystem and creating Havoc? The thread stated it would just sit there not knowing what to do.

I imagine if A virus was written to exploit directlly using wine as the delivery package to a linux filesystem with linux specific commands than yes it could be done.

That is interesing.. and things like keyloggers and such are they blocked too ?

---

### Post by meman63 on 2007-05-01
Say you get a funny e-mail and decide to forward it to a buddy.Since you're running *nix,the virus it contains doesn't affect you,BUT when you forward it to him,VOILA!

Not too many people simply forward  e-mails anymore,though.Usually it's just a link to a web page.

Just my two cents worth.

  Regards,
           Monica

---

### Post by oilchangeguy on 2007-05-01
> **meman63 said:**
> Say you get a funny e-mail and decide to forward it to a buddy.Since you're running *nix,the virus it contains doesn't affect you,BUT when you forward it to him,VOILA!

Not too many people simply forward  e-mails anymore,though.Usually it's just a link to a web page.

Just my two cents worth.

  Regards,
           Monica
 
most isp's now scan emails for viruses. and if you get a forwarded email the smart thing would be to scan it yourself before opening it. (if you're using windows)

---

### Post by DrBair on 2007-05-03
OK, real reason for antivirus on linux is for servers!

I have a linux fileserver at my company, I want to make sure that none of the files on that server could be harmful to my Windows client computers. So I put antivirus on the server to protect the clients.

This is also a popular practice on email and ftp servers for the same reasons.

---

### Post by nobles_carl on 2007-05-03
I used "shorewall " (available as UBUNTU package) with the default configuration. Was scanned by " Shields UP " and they reported I was Invisible.
Carl

---

### Post by KingdomKid on 2007-05-06
> **mech7 said:**
> Does windows virusses also run under WINE ?

I found this article in another post, check it out.


[http://os.newsforge.com/article.pl?sid=05/01/25/1430222]("http://os.newsforge.com/article.pl?sid=05/01/25/1430222")

---

### Post by dpar on 2007-05-06
Here's the post I think a previous poster was talking about.

[http://ubuntuforums.org/showthread.php?t=72598](http://ubuntuforums.org/showthread.php?t=72598)

---

### Post by silent1643 on 2007-05-08
> **KingdomKid said:**
> I found this article in another post, check it out.


[http://os.newsforge.com/article.pl?sid=05/01/25/1430222]("http://os.newsforge.com/article.pl?sid=05/01/25/1430222")

Wednesday January 26, 2005 (06:12 PM GMT) is the article date, i wonder if this still applies..
if you have a windows virus on a linux box, how will the virus know what to do, its an entirley different system. Yes the virus will be on the machine, but it can't possibly do what it is suppose to do.

---

### Post by Barrius on 2007-05-23
I'm not sure about Linux or any variant, but I do know that OS/2 was pretty secure out of the box due to it's object-oriented approach.   An executable was such because it was created as an executable, not simply because of on extension.   "Opening" (actually executing) a file on MS Windows allows virii to propagate simply because of the way the OS processes it.    Vista attempts to correct this, but then one is faced with innumerable messages begging for permission.    

Give me Linux any day.

---

### Post by bodhi.zazen on 2007-07-28
I am not sure of the implications of this, it is something I have followed.

My comments are that if you find what you feel is a vulnerability, please report it to Launchpad :

[Launchpad](http://www.lauchpad.net)

The thread is quite old (Started in 10/05) and I am reporting the more recent activity this thread now and will post an update if one becomes available.



In the past there *HAVE* been holes in the wine code that allowed viruses to run on wine, but these have been patched. In reviewing that thread :

[list=number][*]The command to run the virus was initiated by the user, ie wine did *NOT* spontaneously run the code.
[*]It appears to my review that only the home directory was affected so unless you ran the virus as root the system does not appear to be compromised.
[*]The offending worm was "Some Fool" and from here : [http://os.newsforge.com/article.pl?sid=05/01/25/1430222](http://os.newsforge.com/article.pl?sid=05/01/25/1430222)

> **SomeFool**

The SomeFool first-generation worm (Netsky.D according to some folks) actually installs its winlogon.exe file under Wine, and, as an added bonus, seems to get stuck in an endless loop, thus really having a negative performance impact on my Linux machine! I'll give this one 4/5 penguins for not only running and sort of doing what it was supposed to, but actually doing mildly bad things to Linux -- at least until I hit Control-C in the terminal from which I was running Wine to stop it dead.
[*]The thread became "active" again with a similar report posted in 1/07.
[*]Some users on that thread discuss modifying the wine environment to allow viruses to run on wine by adding missing windows .dll IMO this is akin to saying "windows viruses run on windows code" which is very different then windows viruses running on wine code.
[*]So if you modify the code be sure you understand the security implications.[/list]

IMO this falls under social engineering and/or the caution about running code from untrusted sources ...

[indent]He he he ... including windows .dll[/indent]

---

### Post by oldos2er on 2007-07-28
> **Barrius said:**
> I'm not sure about Linux or any variant, but I do know that OS/2 was pretty secure out of the box due to it's object-oriented approach.   An executable was such because it was created as an executable, not simply because of on extension.  

 I know this is an older post, but I feel the urge to reply. <g>

 OS/2 was secure because, similar to Linux, its default was to have all ports closed (assuming we're talking about the single-user version of OS/2, not the server editions). Back in the day, it was never popular enough to attract the attention of virus creators and script kiddies, so it was relatively safe in that sense. IBM had created some OS/2-specific viruses "in the lab," but I never heard of any in the wild, and I was an OS/2 user for many years. IBM also sold an anti-virus program for OS/2, but, again similar to Linux, its main purpose was to scan for Win* virii to protect Win* users.

 I miss OS/2's object-orientedness--wish there was an OO window manager for Linux.

---

