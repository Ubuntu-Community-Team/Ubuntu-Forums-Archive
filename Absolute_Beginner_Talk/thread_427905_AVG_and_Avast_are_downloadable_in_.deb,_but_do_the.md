---
title: "AVG and Avast are downloadable in .deb, but do they work on Ubuntu feisty?"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by whee on 2007-04-29
AVG is downloadable in .deb, but does it work on Ubuntu(feisty) out of the box?
Or are there special tweaks nessecary to make it run on Ubuntu?

Link AVG: [http://free.grisoft.com/doc/5390/lng/us/tpl/v5#avg-anti-virus-free](http://free.grisoft.com/doc/5390/lng/us/tpl/v5#avg-anti-virus-free)

Link Avast: [http://www.avast.com/eng/download-avast-for-linux-edition.html](http://www.avast.com/eng/download-avast-for-linux-edition.html)


PS (edit): Hmmm i just noticed Avast requires a Licence key for which one must register.

---

### Post by starcraft.man on 2007-04-29
Just a note but if your running behind a NAT Router, I don't really see a reason for you to install AV software. I don't even know if there are that many viruses out there... likely a software like that would simply slow your pc down if it runs resident/actively and take up cycles when it did complete scans. I do like AVG though, used em for a few years on my XP.

---

### Post by whee on 2007-04-29
I also used AVG on XP, it seems to be one of the lightest virus scanners.
I think a virusscanner could be handy when a virus gets into the Wine directory.
There have been tests that some viruses for Windows run just as well under Wine.

---

### Post by 67GTA on 2007-04-29
I have Avast running on Feisty now, but just to check stuff I might migrate from my XP partition. Sometimes I will use it to check deb files if I get them from outside of the repositories. To make it easier I created an Avast menu entry with the menu editor. I just used "sudo avastgui" as the command.

---

### Post by starcraft.man on 2007-04-29
> **whee said:**
> I also used AVG on XP, it seems to be one of the lightest virus scanners.
I think a virusscanner could be handy when a virus gets into the Wine directory.
There have been tests that some viruses for Windows run just as wel under Wine.

This is true... but any windows specific virus would be limited entirely to your wine folder and couldn't get out of the visualization. EVEN in the odd chance it did, there is almost no chance it would have an effect on a linux distro given that Windows and Linux operate very differently...

So, if you got a virus in wine, you just delete folder and reinstall programs. Isn't that easier than worrying about removal? Besides, like I always have thought once a virus is in... you can't really ever be sure its completely gone >.<.

I mean I can see using it a bit, but in all likely hood you'll probably never be infected via wine less ur downloading illicit or bad files from bad places >.>

---

### Post by whee on 2007-04-29
> **starcraft.man said:**
> This is true... but any windows specific virus would be limited entirely to your wine folder and couldn't get out of the visualization. EVEN in the odd chance it did, there is almost no chance it would have an effect on a linux distro given that Windows and Linux operate very differently...


That's true, but that doesn't mean spyware or virusses wouldn't be able to send private data which resides in your Wine directory.

---

### Post by starcraft.man on 2007-04-29
> **whee said:**
> That's true, but that doesn't mean spyware or virusses wouldn't be able to send private data which resides in your Wine directory.

Ummm, well, if a spyware got installed having avg installed wouldn't do anything about that its mostly a virus checker... Not to mention, that is exactly why you don't store private data in the wine directory :).

Besides the point, IF spyware was installed in your wine directory. You'd probably not detect it until it had actually transmitted info about your data... unless your scanning constantly and that eats cpu.

The best prevention for such things is behaviour, don't do anything that would attract such things and you won't get them. and a Nat router is the best stopper you'll ever get.

---

### Post by oilchangeguy on 2007-04-29
read this: from this months issue of smart computing.



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







Want more information about a topic you found of interest while reading this article? Type a word or phrase that identifies the topic and click "Search" to find relevant articles from within our editorial database.

	Enter A Subject (key words or a phrase):
	
	ALL Words (&#8216;digital&#8217; AND &#8216;photography&#8217;)
	ANY Words (&#8216;digital&#8217; OR &#8216;photography&#8217;)
	Exact Match ('digital photography'- all words MUST appear together)




Home     Copyright & Legal Information     Privacy Policy     Site Map     Contact Us
Copyright © 2007 Sandhills Publishing Company U.S.A. All rights reserved.

---

### Post by whee on 2007-04-29
I also read though that root kits exist for Linux, wouldn't that be a reason to run a virusscanner for.(one that also detects root kits?)

Even though there might not be alot of virusses for Linux, wether it is a Windows or Linux virus/root-kit, i simply rather have a clean system.
Besides i dual-boot with Windows, not that that matters a whole lot, but it's a factor.

---

### Post by starcraft.man on 2007-04-29
> **whee said:**
> I also read though that root kits exist for Linux, wouldn't that be a reason to run a virusscanner for.(one that also detects root kits?)

Even though there might not be alot of virusses for Linux, wether it is a Windows or Linux virus/root-kit, i simply rather have a clean system.
Besides i dual-boot with Windows, not that that matters a whole lot, but it's a factor.

If a rootkit gets installed on your linux distro, your likely hosed, completely. A root kit, if it can get installed on your system, can do almost anything on your system I assume it would bypass your root pass... and would likely first off hide itself from your scanner. So if that happened, only way to trust your OS again is to reinstall it all after a complete format. Root kits are serioulsy dangerous. I mean I am sure it can hide itself, proabaly similar to how it hides itself in windows (goes down to the kernel level and unlinks itself from the chain of programs that run on your system, thus becoming invisible at the base level.

As for dual boot, that makes no impact whatsoever... the partitions are seperate, I don't believe the majority of those things jump partitions, and if they did you would likely already be hosed.

The bottom line is if you get something as bad as that on your pc, its hard to ever know if its really clean...

---

### Post by whee on 2007-04-29
But arguments like "if spyware is already on your system, the private data probably has already been sent" or "if a root-kit is on your system, then you're probably already hosed" are valid for all operating systems.
So following that logic one wouldn't need any security software on any OS.
Though for example virus scanners like Kaspersky do detect root-kits on Windows and can remove them.
Why not have a strategy like that as a Linux user?

---

### Post by starcraft.man on 2007-04-29
> **whee said:**
> But arguments like "if spyware is already on your system, the private data probably has already been sent" or "if a root-kit is on your system, then you're probably already hosed" are valid for all operating systems.
So following that logic one wouldn't need any security software on any OS.
Though for example virus scanners like Kaspersky do detect root-kits on Windows and can remove them.
Why not have a strategy like that as a Linux user?


You got my point perfectly. Almost all security software is after the fact and never guarantees a clean computer. In addition, all real time solutions that offer almost perfect protection do so at significant cost to your CPU and will slow down your pc (Norton, Mcaffee and Zonealarm are prime examples of this active zealotry that results in bloatware).

As a side note, I don't run any virus software on my XP partition either. I uninstalled my spyware cleaners and virus scanners. A NAT router is really all you need, it stealths you from the internet completely protecting you from anything actively trying to get on your computer. As such, the only way anything gets on your PC is because you installed it.

BTW, if you want further proof. Technology whizzes like Leo Laporte and Steve Gibson, run also without any spyware cleaners or virus scanners and they both use lots of copies of windows. The simple bottom line is behaviour is the ultimate deterrent to infection :).

PS: Not trying to be hostile, I just don't wanna see ya wasting any money or time on solutions that really can't guarantee your computer is clean.

---

### Post by whee on 2007-04-29
I understand that from the viewpoint of security experts.
But take for example someone i know, last time i visited i found 1000+ spyware entries on that persons pc(Windows) and it wasn't working very well anymore. The PC also didn't have a firewall.
I also found viruses and what not. It was a mess and the system had gotten slower.
I ran all sorts of anti-spyware software on that pc and also AVG, next to that i installed a simple non bloated firewall that atleast closed all ports.
After that the system functioned properly.

I know issues like that are less of a problem on Linux, but it's to illustrate why i think it sometimes can come in handy.

PS: I'm not interpreting your replies as hostile at all, it's good to get to know other people's point of view :)

---

### Post by whee on 2007-04-30
I'll bump the thread, because i don't have an answer to my original question yet.

---

### Post by 67GTA on 2007-04-30
Avast will run on Feisty. I have it running now.  I have not ran AVG on Feisty, but I'm sure it will work. I used AVG on Edgy. I like Avast better. The reg key is free.

---

### Post by whee on 2007-04-30
I've seen a thread on the forum though that the .deb for AVG was specifically for Debian, but that it could also run on Ubuntu with a few tweaks, but i was wondering if this had changed. If the .deb of AVG now works out of the box and doesn't need any tweaks/extra commands to make it work with Ubuntu.

---

### Post by mikewhatever on 2007-05-02
> **whee said:**
> I've seen a thread on the forum though that the .deb for AVG was specifically for Debian, but that it could also run on Ubuntu with a few tweaks, but i was wondering if this had changed. If the .deb of AVG now works out of the box and doesn't need any tweaks/extra commands to make it work with Ubuntu.

Why not install it and see for yourself. Here is a how-to [http://ubuntuforums.org/showthread.php?t=136064](http://ubuntuforums.org/showthread.php?t=136064)

---

### Post by gpilkay on 2007-05-03
I'm rather new as well, but I can say YES, they will both work on Feisty.  However, after trying both myself, I found that Avast works far better, and can even scan my XP drive while running Ubuntu.  Now for the odd part...Avast also detects several files that are not scanned because they have "no such device".  I don't know what that means, but it does NOT mistake them for viruses.  It just notes their existence.  I just close the window and look for the results.

Avast is by far the best of the two I used.  AVG, under Windows, I love.  But it had update issues, and caused some weird errors in Linux when shutting down.  No such issues with Avast.

Also, Avast was as easy to install as a Windows exe file, I just downloaded the .deb, double clicked it, gave it the code e-mailed to me, and it was done.  Nothign simpler.  And removal can be done in Synaptic, unlike AVG which was a huge command-lien mess to un-install (and I'm still not sure I did it all the way). 

You may also want to get the FIrestarter firewall GUI, it's small but it works.

---

### Post by bedlam on 2007-06-16
I couldn't find any information for running avast until I read you post.
I created the menu for avast and entered "sudo avastgui" but this does nothing, however take away the sudo and it runs from the menu.
I can run "sudo avastgui" from the command line where it asks for the password, once entered it also runs.
So I guess it's the password that leaves me with nothing when trying to run "sudo avastgui" from the menu.
Do you or anyone know how I can overcome this problem?
Thanks

---

