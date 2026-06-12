---
title: "Is a firewall really needed?"
date: 2005-10-11
forum: Absolute Beginner Talk
---

### Post by Souljah on 2005-10-11
Hi guys. My installation is all done and finished. I even set up my internet connection. Now does ubuntu come with an inbuilt firewall or must I get one? Is it really needed?

For windows, I use Sygate firewall. I'm not too sure which is the best one for linux. You guys have any idea on that?

Ryan

---

### Post by aysiu on 2005-10-11
You might find the answer you need here:

[http://www.google.com/search?hl=en&q=site%3Aubuntuforums.org+need+firewall&btnG=Google+Search](http://www.google.com/search?hl=en&q=site%3Aubuntuforums.org+need+firewall&btnG=Google+Search)

---

### Post by Goober on 2005-10-11
(Short Answer - No, but you can get one (Firestarter), and an AntiVirus (ClamAV) if you really feel that you need it)

The first thing I did when I got Warty was to put on both a Firewall and an AntiVirus, since I thought it was like Windows, but you don't need either.

---

### Post by Souljah on 2005-10-11
So I don't really need a firewall for ubuntu? I am dual booting with WinXP however, is that still the case? I mean, in XP it's different you definitely would need a firewall. So can a hacker maybe go into my hard drive for XP and then somehow come into my linux. Quite interesting anyway.

---

### Post by bdash on 2005-10-11
Ubuntu comes with a Firefox in the Linux kernel, this is iptables. You may want to configure it in a paranoid way but it is safe for most users not to do it.

**

Explainations about what is a firewall (maybe it is not clear for everyone) : control the connections with the outside. It can prevent software that are on your computers to establish connection with the outside.

Windows users need one because they install applications that can not be trusted: stupid games they get by email, warez applications, patch to crack proprietary software... They also can get malicious applications from IE holes. And the firewall can tell them: "This application want to connect to the outside. Is it ok that MSOfficeCrack connects to a server located in Russia?" And they can say "no".

Using Ubuntu, if you install only applications from the official repository (multiverse excluded) you have the garantee that these applications are safe. So even if you don't know wether they connect to the outside world or not, is it usually when you want it. Synaptic fetching .deb packages is nothing wrong, but for a firewall like there are in the Windows world there is no difference between that and a malicious application calling home.

If you are paranoid:
[http://www.siliconvalleyccie.com/linux-hn/iptables-intro.htm](http://www.siliconvalleyccie.com/linux-hn/iptables-intro.htm)

---

### Post by Souljah on 2005-10-11
Well I will trust you guys on this one. I don't think I will need a firewall or an anti virus then. I will continue to use ubuntuu as you guys suggested. Thanks for the advice. :)

---

### Post by UbuWu on 2005-10-11
[QUOTE=bdash]
Using Ubuntu, if you install only applications from the official repository (multiverse excluded) you have the garantee that these applications are safe. 
[/QUOTE]

There is absolutely no garantee that applications from universe are safe. Only main is officially supported. For a lot of software you can install from the repositories (servers, network related stuff) it is certainly advisable to use a firewall.

---

### Post by frodon on 2005-10-11
Generally a firewall is needed when you run servives in order to have a better control, it's my case because i run FTP and samba servers and i want to be able to block some IPs really easily and the firewall help me to do that.
Therefore i don't run my firewall for security reasons, because linux kernel is enough strong except if you login in GNOME or KDE as root !!!!!!!

---

### Post by patrick295767 on 2005-10-19
[QUOTE=frodon]Generally a firewall is needed when you run servives in order to have a better control, it's my case because i run FTP and samba servers and i want to be able to block some IPs really easily and the firewall help me to do that.
Therefore i don't run my firewall for security reasons, because linux kernel is enough strong except if you login in GNOME or KDE as root !!!!!!![/QUOTE]

Since u use it, which firewall did you choose , are u using ?

thank you very much 

patrick

---

### Post by frodon on 2005-10-20
I use [firestarter,]("http://www.fs-security.com/") you can find it in synaptic.

---

### Post by nocturn on 2005-10-20
[QUOTE=Souljah]Well I will trust you guys on this one. I don't think I will need a firewall or an anti virus then. I will continue to use ubuntuu as you guys suggested. Thanks for the advice. :)[/QUOTE]

Don't take our word for it ;-)

If you install nmap, you can scan your system for open ports.
Try nmap against your Ubuntu, if you haven't explicitly installed any extra programs, there should be nothing listening.

Now, do the same scan against your Windows XP (firewall down).
You'll quickly see why it needs to be protected.

---

### Post by odin on 2005-10-20
[QUOTE=frodon]Generally a firewall is needed when you run servives in order to have a better control, it's my case because i run FTP and samba servers and i want to be able to block some IPs really easily and the firewall help me to do that.
Therefore i don't run my firewall for security reasons, because linux kernel is enough strong except if you login in GNOME or KDE as root !!!!!!![/QUOTE]

I always hear everyone saying that using root for everything is not something anyone should do but I still dont understand why and now even less...:rolleyes: Why is it so dangerous to login in Gnome or kde as root?

Thank's in advance :smile:

---

### Post by darkmatter on 2005-10-20
[QUOTE=odin]I always hear everyone saying that using root for everything is not something anyone should do but I still dont understand why and now even less...:rolleyes: Why is it so dangerous to login in Gnome or kde as root?

Thank's in advance :smile:[/QUOTE]

It is not so much dangerous as it is bad practice.

You wouldn't leave your car running, door unlocked and key in he ignition in the worst part of town now - would you???

Not running as root is just an additional layer of security to your system. Users, and any program run by a normal user have limited access to the system. Reducing the amount of damage that may occur should an attack succeed.

If you run as root, it is basically the same level of security as Windows, as the root account automatically allows full access to the system.

---

### Post by patrick295767 on 2005-10-20
[QUOTE=frodon]I use [firestarter,]("http://www.fs-security.com/") you can find it in synaptic.[/QUOTE]

Looks pretty good toool ... I'll install it !!
Thanks !!

Pat'

---

### Post by nocturn on 2005-10-20
[QUOTE=odin]I always hear everyone saying that using root for everything is not something anyone should do but I still dont understand why and now even less...:rolleyes: Why is it so dangerous to login in Gnome or kde as root?

Thank's in advance :smile:[/QUOTE]

Damage control.  Anything you do as root affects the whole system while a user can only touch his own files.  This is a big plus on Linux, even if you get E-mail viruses to work, if they do not have root access, they cannot damage your system, only your home directory (for which you should have backups).

The main principle is that of 'least privileges', if you do not need to have raw access to your harddisk, you should not have it.

---

### Post by Shiner on 2005-10-20
Re: firewalls...  If you have an always on internet connection and are connected through a NAT router and not running any servers, a software firewall is not needed.  If your PC is directly connected to the always on  modem, or you are running servers, you should run a software firewall, preferably a hardware firewall.
 
Re: root login...  I learned that using root for everything is inherently dangerous.  The root user is "god" on a Unix/Linux system.  What root says, system does.  A command submitted by the root user is not questioned in most cases.  One exception being file permissions: root can't save to a read only file in vi by simply using ":w", ":w!" must be used.  But "rm *" will go about it's merry way removing all files from the current directory without any qualms at all.  All this to say... The system assumes that the root user knows what they are doing, much like the Administrator user in Windows.

---

### Post by Captn on 2005-10-20
I tried installing Firestarter, but i get this. Can someone tell me why. Thank you in advance.

captn@ubuntu:~$ sudo apt-get install firestarter
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package firestarter


:confused:

---

### Post by odin on 2005-10-21
ok I can see now the root thing.Thank you both darkmatter and nocturn

---

### Post by Penguin Skinner on 2005-10-21
IMO the fact that Ubuntu does not, by default, come with a user-friendly iptables firewall configuration interface seems incongruous with other features and aspects of the distro -- especially the extremes to which they seem to have gone to discourage users from running as root.

From personal experience, I can tell you that running a firewall -- even when behind a NAT router, which I am -- is a sound and desirable practice, *especially* when running Linux.  Why, you may ask?  Because to the many hackers out there, a non-Windows box connected to the web has a much higher likelihood of being a server, and thus a more interesting target.

As regards running as root, doing so on a non-networked personal desktop system presents no unusual risk, even when connected full-time to the web.  As Peter van der Linden and others point out, this is so because that which is of greatest value, your personal data, may be just as easily lost while running as an ordinary user.  

Bottom line: understand the risks, understand your personal situation, priorities and needs, and decide wisely for yourself.

---

### Post by dalani on 2005-10-21
I asked myself the same question. I tested my security setup with ShieldsUp at [www.grc.com](www.grc.com) (click on shieldsup logo) this website will verify all ports of any computer connected to the net and show a PASS or FAIL with results.

I was surprised to know that my WIn98SE running ZONElabs firewall, stealths all my ports and makes my computer invisible to the net ab nd is airtight. Whereas Linux Ubuntu without firewall shows ports closed but actively responds to outside port requests and so on...

What does that mean? I don't know if Linux is airtight or not without a FW. Can spyware exist or download on Linux if it responds so eagerly to port probes?????

---

### Post by dbott67 on 2005-10-21
Firewalls prevent **unsolicited** traffic from entering your network or PC.Additionally, many firewalls run in a stealth mode, effectively making your computer "invisible" to drive-by hackers.  Without a firewall, a computer may be secure, but is "visible" to drive-by hackers, due to the fact that the ports respond as "closed".  Unfortunately, a "closed" response to a hacker means that there is a computer at that IP address.

Contrary to popular belief, Linux (in general) is not more secure than Windows XP (in general).  BTW, I'm not saying that Windows is more secure than Linux --- only that an improperly secured OS is vulnerable, whether it be Windows, Linux or OSX.  A somewhat older study from 2004 states that [Linux is the most hacked OS]("http://www.smh.com.au/articles/2004/03/01/1077989482304.html"):
> The group said it had analysed 17,074 successful digital attacks against online servers and networks in January 2004, with Linux accounting for 13,654 breaches, and Windows for 2005 followed by BSD and Mac OS X with 555 breaches worldwide .
Keep in mind that these are SERVERS, not desktop users but the overall point is valid.  Take a look at some of the major security vulnerabilities at [sans.org]("http://www.sans.org/top20/").  Most people get hacked because they fail to take the following measures:

**1. Keep their OS up-to-date (as well as applications)**  (i.e. run Windows update / Ubuntu update)
**2. Run a firewall** (this prevents the 'background radiation' of the internet --- worms like slammer and blaster and other automated scanners from detecting & infecting your computer).
**3. Turn off unneeded services** (this is a big one --- don't run a mail/web server unless you know what you're doing, as these services are regularly targeted)
**4. Run an antivirus and keep the definitions up-to-date **(at present, linux has a very low profile for viruses and spyware, but that is more likely due to the fact that there are far fewer linux-users than Windows-users, and it's easier to infect Windows because there are so many users that do not follow the above precautions).
**5. Don't run in admin/root mode**

Linux does have the benefit of having a better security model (in my opinion) for software installation than Windows, however, a buffer overflow of an unneeded or improperly configured service could grant root access to a hacker who could easily install a rootkit and 'own' your computer without your knowledge.  I would just hate to see someone get hacked because they practised 'security by obscurity'.  If you have an 'always on' connection, you should have a firewall (my personal preference would be a hardware NAT router, but software firewalls do offer a good level of protection.

Wireless laptop users that frequent public hotspots (or share their own with others) should run a software firewall, as well as be aware that if they are not using WEP/WPA their 'wireless' traffic is traveling in plain text and can be captured by anyone in the vicinity.

As the popularity of Linux continues to rise and it comes into the hands of the same inept users who can't run WindowsUpdate, or can't keep their AV up-to-date, or need to open every attachment that arrives in their inbox, hackers and malware writers will come up with new & interesting ways to infect users.

Major banks, credit card companies, NASA, Microsoft, the Defense Department, NYTimes and countless others have been hacked because they were all big targets.  Now, hackers are going after home users to infect their computers and turn them into a legion of zombies to do their dirty work.

My advice, turn on the firewall and don't eat yellow snow. :)

-Dave

---

### Post by Captn on 2005-10-21
[QUOTE=dbott67]Firewalls prevent **unsolicited** traffic from entering your network or PC.Additionally, many firewalls run in a stealth mode, effectively making your computer "invisible" to drive-by hackers.  Without a firewall, a computer may be secure, but is "visible" to drive-by hackers, due to the fact that the ports respond as "closed".  Unfortunately, a "closed" response to a hacker means that there is a computer at that IP address.

Contrary to popular belief, Linux (in general) is not more secure than Windows XP (in general).  BTW, I'm not saying that Windows is more secure than Linux --- only that an improperly secured OS is vulnerable, whether it be Windows, Linux or OSX.  A somewhat older study from 2004 states that [Linux is the most hacked OS]("http://www.smh.com.au/articles/2004/03/01/1077989482304.html"):

Keep in mind that these are SERVERS, not desktop users but the overall point is valid.  Take a look at some of the major security vulnerabilities at [sans.org]("http://www.sans.org/top20/").  Most people get hacked because they fail to take the following measures:

**1. Keep their OS up-to-date (as well as applications)**  (i.e. run Windows update / Ubuntu update)
**2. Run a firewall** (this prevents the 'background radiation' of the internet --- worms like slammer and blaster and other automated scanners from detecting & infecting your computer).
**3. Turn off unneeded services** (this is a big one --- don't run a mail/web server unless you know what you're doing, as these services are regularly targeted)
**4. Run an antivirus and keep the definitions up-to-date **(at present, linux has a very low profile for viruses and spyware, but that is more likely due to the fact that there are far fewer linux-users than Windows-users, and it's easier to infect Windows because there are so many users that do not follow the above precautions).
**5. Don't run in admin/root mode**

Linux does have the benefit of having a better security model (in my opinion) for software installation than Windows, however, a buffer overflow of an unneeded or improperly configured service could grant root access to a hacker who could easily install a rootkit and 'own' your computer without your knowledge.  I would just hate to see someone get hacked because they practised 'security by obscurity'.  If you have an 'always on' connection, you should have a firewall (my personal preference would be a hardware NAT router, but software firewalls do offer a good level of protection.

Wireless laptop users that frequent public hotspots (or share their own with others) should run a software firewall, as well as be aware that if they are not using WEP/WPA their 'wireless' traffic is traveling in plain text and can be captured by anyone in the vicinity.

As the popularity of Linux continues to rise and it comes into the hands of the same inept users who can't run WindowsUpdate, or can't keep their AV up-to-date, or need to open every attachment that arrives in their inbox, hackers and malware writers will come up with new & interesting ways to infect users.

Major banks, credit card companies, NASA, Microsoft, the Defense Department, NYTimes and countless others have been hacked because they were all big targets.  Now, hackers are going after home users to infect their computers and turn them into a legion of zombies to do their dirty work.

My advice, turn on the firewall and don't eat yellow snow. :)

-Dave[/QUOTE]


Awsome post Dave, thank you.

---

### Post by dalani on 2005-10-23
Dave that's the most concise and thourough explaination about the whole issue of securing one's computers (be it desktop or otherwise). 

It answered all my general questions concerning this issue.

---

### Post by dalani on 2005-10-23
The specifics in my case is to examine my default Ubuntu 5.04 installation and make sure (for speed and security) that I'm not running uneeded services.  Something tells me it is not (no apache or server install and ssh is disabled). As for a firewall, Firestarter might be the thing but previous post suggests it to be difficult to configure for a time challenged user like myself.

So I'll check with apt to see what there is available.

Point #5: I have to type in a root password for almost all or any system change or system related item including connecting to the internet. It seems like an obvious indication that I am NOT running in root mode. right?? Anyways I hope because, otherwise, how do I know for sure that my Ubuntu installed isn't in root mode?? (I boot in automatically as *user* with access only to home directory and FAT32 partitions with permissions.) Is there a quick way to check this??

---

### Post by dbott67 on 2005-10-23
The default installation of Ubuntu does not include any services such as mail, ftp, www, telnet, etc. so you should be relatively safe in that regards.

As for running in root mode, the Ubuntu installation actually disables the root account, forcing you to enter your user password to perform administrative tasks.  There is a way to enable the root account, but you must follow a set of instructions provided in the 'unofficial ubuntu guide' (see link below).

[http://www.ubuntuguide.org/#setchangeenablerootpassword](http://www.ubuntuguide.org/#setchangeenablerootpassword)

So, if you've never performed these instructions, root is still disabled.  If you want to double-check, just follow the instructions to disable (ie. **sudo passwd -l root**).

-Dave

---

### Post by dalani on 2005-10-23
I installed portsentry, a small program that detects stealth port scans. It was a fast download. The docs show this to be a simple utility. But by default, it does not block intrusions. To do so IT REQUIRES A CONF file with commands to block intrusions. Had to decipher the man pages and create a config file. I restarted portsentry but TEsting my ports show no effect. (4 ports are open eg.'finger port 79' and the rest closed). I want to block and stealth ALL my ports. The syntax below is either faulty and/or portsentry on startup does not 'read' the .conf file. 

any insight would be appreciated.

[CODE]#man /etc/portsentry.conf for details
ADVANCED_PORTS_TCP=5000
ADVANCED_PORTS_UDP=5000
SCAN_TRIGGER=0
BLOCK_UDP=0
BLOCK_TCP=0
BLOCKED_FILE="/home/../firewall-log.txt"
KILL_ROUTE="route !"[CODE]


-----------------------------------
DISREGARD PORTSENTRY QUESTION. 
Ill remember to google first before posting. Seems portsentry though small and unobstrusivly simple, actually isn't so good. Here is an exerpt from a comparison between SNORT and PORTSENTRY:

> Cons:
A port scan detector [portsentry] that binds to ports is a terrible idea. It advertises services (usually those that are known to be hackable, which is why Port Sentry binds them in the first place) that aren't there, making your server seem like a hackers goldmine. This forces you to use Port Sentry's counter measures (routing the port scanner to a blackhole or bringing up a firewall rule to blck the attacker)... 
see the rest at http://www.linux.ie/articles/portsentryandsnortcompared.php

---

