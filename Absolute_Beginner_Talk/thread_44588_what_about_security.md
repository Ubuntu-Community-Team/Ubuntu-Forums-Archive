---
title: "what about security"
date: 2005-06-26
forum: Absolute Beginner Talk
---

### Post by byen on 2005-06-26
hey fellas,
Ive been an Ubuntu user for over 2 months and have just one thing to say... AWESOME! everything works good (after a lil tweaking) but there are a few questions that I have which need to be answered. Please suggest.. Here goes....

No1: They say Ubuntu does not need a firewall since ubuntu has nothing listening. But what about controlling network traffic? what if some zombie program runs and tries to screw around? Does a firewall such as firestarter automatically secure ports?

No2:Ubuntu does not need an antivirus? I know there are not many viruses for linux out there..but seriously.... is this OS that safe? 

No3: Spyware. how do i check my PC for adware/spyware/malware? are there any tools to detect these.... i ask because i am under the impression that spyware/adware are browser dependent...so wont spyware effect ubuntu?

though for regular linux users these may sound silly but for a windoze user its hard to understand these issues. Please enlighten me....

thanks guys. Ubuntu rocks!

---

### Post by Seti on 2005-06-26
Hey byen! No you really don't have much to worry as far as virus/spyware problems where Ubuntu is concerned. Just be careful to avoid running services if you don't need them. That sort of thing. Spyware? You really shouldn't have to worry. The only thing to keep an eye out for is maybe the odd phishing scam, you know, someone sending you an email asking you to click a link and then validate an account password, that sort of thing. Also, just be careful to install packages from trusted sources only, keep your system up to date with apt and you should be A-OK!

---

### Post by cwaldbieser on 2005-06-26
This may help make it clear why your concerns are generally not a problem for desktop Ubuntu:

With regards to firewalls:  The reason why we need firewalls at all is because an attacker tries to get some sort of access to your computer remotely over a network.  Now there has to be two sides to the connection, just like a telephone call.  The attacker's side uses some sort of client, and your computer has to be the server.  Now by default, Ubuntu is not running *any* network servers-- no web server, no file shares, no ftp server, no ssh server, no telnet server, no mail server, etc.  So even if the attacker tries to connect to an unblocked port, there is no program listening that he or she can exploit.

Now as soon as you start enabling some services like samba file sharing or ssh, then you probably want some sort of firewall.  Firestarter has some good defaults.  I believe it does not allow any traffic that originates from the Internet by default.  So if you want to enable ssh from the Internet, you would have to explicitly unblock that port.

With regards to viruses-- there are many theories as to why there are no prominent viruses on GNU/Linux.  I don't know what attracts virus writers to other systems.  The fact remains that anti-virus software for GNU/Linux systems mostly just inspects samba file shares to make sure nothing bad gets passed on to Windows machines.  The GNU/Linux machines themselves are not affected.

Concerning malware-- if you stick to the repositories, you should be OK.  apt-get and synaptic automatically do a check against something called an md5sum when you get software from the official repositories, and that makes sure the software hasn't been tampered with.  If you get software from backports or the Internet, though, you will have to make sure you trust the source.  There is software for detecting rootkits and Trojan horses (chkrootkit is in the repositories).

---

### Post by poofyhairguy on 2005-06-27
[QUOTE=cwaldbieser]  If you get software from backports or the Internet, though, you will have to make sure you trust the source.  [/QUOTE]

If you follow this rule....you'll never have safety problems.

---

### Post by byen on 2005-06-27
thank you seti for the detailed explanation. you have no idea how happy i am for not having to run antivirus and antispyware all the time. but I still have one question that needs a little explanation.
Adware/spyware: I still do not understand this. Isnt spyware,adware and browser hijack software dependent on the browser as well.? and since we use firefox isnt there a chance that some browser hijack software/spyware could install itself during browsing?

I hate to sound so paranoid but as a windows user this is baffling that this OS is indeed this sweet and secure. But with this issue settled, my jump from Win to Lin would be complete!
thank you.

---

### Post by Kvark on 2005-06-27
I think the trojans that browser hijack software installs is OS specific too. But let's assume you could get some cross platform (java??) trojan through the browser.

You run firefox as yourself and not as root. So firefox (and any hijack software that firefox gets) can do only what you can do without root/sudo. Which means the only place it would mess up is your home directory, everything in there you should backup frequently anyway.

Besides, firefox seems to be very secure. It never got infected for me, even under windows, even on pages that got internet explorer infected with a whole zoo of trojans and viruses.

---

### Post by poofyhairguy on 2005-06-27
[QUOTE=byen]
Adware/spyware: I still do not understand this. Isnt spyware,adware and browser hijack software dependent on the browser as well.? and since we use firefox isnt there a chance that some browser hijack software/spyware could install itself during browsing?[/QUOTE]

There is a chance, but it low considering that:

A. I have never heard of an exploit like that in Firefox. Only IE has those problems because of Active X.

B. If that exploit did occur it would target Window's users I bet (they are the largest Firefox demographic)

C. The Firefox team works hard to prevent this

Also, even in the unlikely event that such an exploit was made, you are protected by the AWESOME multiuser system in Ubuntu (the thing Windows really lacks). Since the computer needs your password to install programs, if you a browsing the web and Firefox asks for your password you know that something is up! Firefox doesn't need a password for anything. So the malware can't sneak its way onto your system like it can in XP.

The elegant multiuser situation (and the fact that by default you don't run as an admin like in Windows) protects to a great level. The sudo system Ubuntu uses is the same Apple uses- its hammered out on the anvil of IT.


> I hate to sound so paranoid but as a windows user this is baffling that this OS is indeed this sweet and secure. But with this issue settled, my jump from Win to Lin would be complete!
thank you.


No problem. Questions are healthy.

---

### Post by byen on 2005-06-27
thank you kvark and poofy! case closed and another user converted! 100%!
Go Ubuntu! - where security isnt a big concern!

---

### Post by Mr. Electric Wizard on 2005-06-27
I'm thinking about setting up Apache2 tonight, is there anything I should do before I do any sort of port forwarding?

---

### Post by Kvark on 2005-06-27
[QUOTE=Mr. Electric Wizard]I'm thinking about setting up Apache2 tonight, is there anything I should do before I do any sort of port forwarding?[/QUOTE]

Just make sure the websites it serves don't allows anything you don't want to allow. Make sure outsiders can't use any web based admin control panels you put on the server, like phpmyadmin for example. If you write server side scripts, make sure you have read up on what security issues to keep in mind when working with the script language you're using.

---

### Post by flamarro on 2005-06-27
Just to say that i was a little like byen concerning spyware/adware.
It was a good tread to read, Thank you guys. fells much more safe and even more willing to keep using Ubuntu. 
As a newbie i'm using ubuntu since 4 june, so 23 days without XP and managing to do  the some things more or less, ones with more dificulties, other not, much more to learn though, but this FORUM's are just great, so many helpful guys, thanks again

I needed to say this.

By the way, sorry about my english.  :-P

---

### Post by Mr. Electric Wizard on 2005-06-28
I'll just be serving basic web sites, no Php or server side scripting or anything...
thanx :)

---

### Post by kabotage on 2007-08-23
informative... thanks :KS

---

### Post by cooltd825 on 2008-06-15
so.....could i get some clarification on an issue?

say some malware comes out on Java, non platform specific.  in theory, it could delete my whole home directory, right?  
and say i dual boot with Windows Vista.  would it be able to navigate into my /media folder and wipe out my sda1 drive?

sorry for reviving an old thread, but i couldn't find any more recent.

---

### Post by fidamehran on 2008-06-17
I have another query. This thread says that Viruses may not usually be encountered in Ubuntu. I read in another thread mentioning "What makes other OSs attractive to virus programmers"? It said as there is the question of money being involved, and need from Security Software companies to upgrade or make new Security Softwares, the virus programmers become inspired to make viruses. As Ubuntu is free and source code is open, Ubuntu Gurus remedy any security flaws within a short time.
Ok, now let me show you an article I found at Softpedia.com, titled: "14 Things that Microsoft Needs to Do with Windows 7 - No more failed &#8220;Wows&#8221;." By: Marius Oiaga, Technology News Editor. The link is: "[http://news.softpedia.com/news/14-Things-that-Microsoft-Needs-to-Do-with-Windows-7-88025.shtml]("http://news.softpedia.com/news/14-Things-that-Microsoft-Needs-to-Do-with-Windows-7-88025.shtml")"
It says: "Microsoft has to play dirty! It needs to jump at the jugular of Mac OS X, Linux, Windows XP and Windows Vista. It needs to sacrifice all Windows operating systems on the altar of Windows 7, and it needs to bury its competitors. No more extended support, no more feature-rich Service Packs, no more availability, no more lifecycle extensions... just Windows 7!

And, as for Mac OS X and Linux, Microsoft needs to bury them both. I don't care if half of the Windows 7 team starts building malicious code for OS X and Linux and then release it in the wild, and shuts down very Mac computer and all the machines powered by Linux that are connected to a network (except lawn mowers, of course; see #3). With Windows 7, Microsoft has to be at least as cutthroat as Apple or the open source community." If Microsoft takes this project to downsize the evergrowing Linux/Ubuntu community, what is going to happen?

Sorry for this big post. I guess the concern is not absolutely baseless... Right?

---

