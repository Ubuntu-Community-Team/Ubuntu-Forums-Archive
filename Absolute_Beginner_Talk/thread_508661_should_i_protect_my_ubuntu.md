---
title: "should i protect my ubuntu???"
date: 2007-07-24
forum: Absolute Beginner Talk
---

### Post by akkad on 2007-07-24
hi,
actually am new with ubuntu and am happy with ubuntu performance and everything, and as i experienced slow performance with windows xp when i use anti viruses or any kind of protection, am really looking not to use them with ubuntu linux, first to keep the lovely performance and in addition as i heard that linux is hard for viruses or bugs free, so my question that do u think i really need a protection or ubuntu linux neednt ???

---

### Post by gn2 on 2007-07-24
You do not require an anti-virus program, you are perfectly safe without one.

Linux isn't Windows.

---

### Post by FleetAdmiral74 on 2007-07-24
Nope. Just don't do incredibly stupid things, and don't run as a root or admin account, and you will be fine from malware.

---

### Post by p_quarles on 2007-07-24
Linux is definitely safer than MS Windows, but it never hurts to take active security measures. 

First, if you use Firefox to browse the web, I strongly recommend getting the NoScript and AdBlock Plus extensions. This is an added layer of protection against web-based exploits.

You might also want to install Bastille Linux, as it offers some nice features that make remote attacks much more difficult. 
[https://help.ubuntu.com/community/BastilleLinux](https://help.ubuntu.com/community/BastilleLinux)

---

### Post by asmoore82 on 2007-07-24
if you run software to prevent security threats that aren't even coming and it affects performance I would say that "hurts."

---

### Post by PriceChild on 2007-07-24
I would second the noscripts/adblock extensions.

Ubuntu ships with no open ports as default... however if you install something like openssh-server... or apache or any other server apps then you will open yourself up to possible exploits. Very very doubtful they could be exploited but you should be aware :)

I would also ask you to ensure that you don't use "sudo" without thinking very hard. "Does this really need root access?", "Do I trust this application?", "Could this command make me lose some important files if I don't check it properly?" etc. etc.

Also you should never use untrusted 3rd party repositories.

---

### Post by p_quarles on 2007-07-24
> **asmoore82 said:**
> if you run software to prevent security threats that aren't even coming and it affects performance I would say that "hurts."
Actually, all of the software I recommended changes system configuration files to prevent bad things from happening. They use very few system resouces. In the case of things like NoScript, it will actually improve web browsing performance. 

And it's really not correct to think that security threats don't exist. In the Servers & Security forum, there's a new "I got hacked -- what did I do wrong" thread every few days. Admittedly, this is more likely when you're running services available via the internet, but it does happen.

---

### Post by FleetAdmiral74 on 2007-07-24
> **PriceChild said:**
> I would second the noscripts/adblock extensions.

Ubuntu ships with no open ports as default... however if you install something like openssh-server... or apache or any other server apps then you will open yourself up to possible exploits. Very very doubtful they could be exploited but you should be aware :)

I would also ask you to ensure that you don't use "sudo" without thinking very hard. "Does this really need root access?", "Do I trust this application?", "Could this command make me lose some important files if I don't check it properly?" etc. etc.

Also you should never use untrusted 3rd party repositories.

I third the noscript adblock extensions.

Oh, and kinda off topic...but I was always wondering, if Ubuntu ships with no open ports, how do you access the internet? doesnt that use port 80, in which case you would need to open that?

---

### Post by Orochi on 2007-07-24
NoScript is great, except when I forget I have it running and spend half an hour trying to figure out why javascript isn't working :P AdBlock is also nice, but I usually don't run it because ads are usually a websites main source of income and I don't want to take that away from them (and adblock isn't really necessary for security)

---

### Post by p_quarles on 2007-07-24
> **FleetAdmiral74 said:**
> I third the noscript adblock extensions.

Oh, and kinda off topic...but I was always wondering, if Ubuntu ships with no open ports, how do you access the internet? doesnt that use port 80, in which case you would need to open that?
The way I understand it, the ports aren't actually "closed" in the default installation, they're just not running any services, which means they're effectively closed. In any case, the default installation definitely doesn't block any outgoing traffic.

---

### Post by akkad on 2007-07-24
ok now i'll make up my mind, i will not install any protection, i believe in ubuntu 100%, but it seems i will install firefox add-on's which u all agreed to install them, thnx anyway.

---

### Post by lemonseed on 2007-07-24
I look at it this way, just because I have a gun in my house can I leave my windows and doors unlocked? Better safe than sorry.

---

### Post by Herman on 2007-07-24
Yes, and always make sure you md5sum your downloaded .iso file before you burn the CD to install Ubuntu in the first place too, that could be very important.

You'll see md5sum information some where around on the page where you start the download on most software sites, including Ubuntu, I hope everyone reads this,
> Learn how to verify that your CD download ok: [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
If you downloaded your .iso file from a reputable web site like Ubuntu's own site then probably it will be okay. You should still run the md5sun test on it to make sure it's genuine and intact.

Please refer to the secure [UbuntuHashes]("https://help.ubuntu.com/community/UbuntuHashes") page for the official list of Ubuntu MD5 hashes. 

You wouldn't trust food from the grocery store if the seal was broken on the package would you?
The same principle applies to software, and the md5sum is your way of checking the software hasn't been tampered with.
It is possible for people to 're-master' any .iso file for any software, and it's not really very difficult. 
Although I think it's unlikely, it is theoretically possible for someone to meddle with .iso files and then distribute the bad software through unauthorized sites.
Your protection is to run an md5sum check and make sure your .iso file is genuine. Everyone should use the md5sum tests , if your downloaded .iso file doesn't pass an md5sum test then it isn't Ubuntu or something went wrong with your download. Don't install it, throw it away and try again. More info: [Pre-install Page]("http://www.users.bigpond.net.au/hermanzone/p17.htm") 


Also, set a good password when you install,  [password tip]("http://users.bigpond.net.au/hermanzone/p2.htm#password_tip"), You can also refer to the official Ubuntu Wiki link about passwords, [link here]("https://wiki.ubuntu.com/StrongPasswords").

If you do those two things and what other posters have already mentioned above, (use safe repositories), you should be okay.

I use [SSH Network]("http://users.bigpond.net.au/hermanzone/p11.htm")ing in my LAN but I'm protected by another Linux firewall in my ADSL modem-router. Even if a cracker got through that they'd need to know my passwords, which are about as tough as I can make them.
I don't run any added firewall, I just leave my IPtables alone, unconfigured at the default settings. 
My Ubuntu installs pass firewall tests at these sites, [**'Shields Up!'**]("https://www.grc.com/x/ne.dll?bh0bkyd2")[COLOR=#666666] ,[/COLOR][Sygate Online Security]("http://scan.sygatetech.com/")[COLOR=#666666],[/COLOR] [AuditMyPc.com]("http://www.auditmypc.com/")[COLOR=#666666] .[/COLOR]
I also scan inside my LAN with Nessus and keep an eye on what's going on with  Wireshark.  Those and etherape are available in 'Applications'-->'Add/Remove Programs' in Ubuntu if you have the right repositories enabled,
I uninstalled one installation of Ubuntu which was running Samba. I think that was probably because I started Firewire in it to try that out, I'm just guessing. I like SSH and I wouldn't trust anything less. 

That's my opinion,
Regards, Herman :)

---

### Post by avik on 2007-07-24
> **FleetAdmiral74 said:**
> Oh, and kinda off topic...but I was always wondering, if Ubuntu ships with no open ports, how do you access the internet? doesnt that use port 80, in which case you would need to open that?

Unless you're running a web server, you're not using port 80 because you don't have any *incoming* connections on that port.  The outgoing connection goes straight to your ethernet/wireless card, I believe.

---

### Post by ushills on 2007-07-24
> **p_quarles said:**
> Linux is definitely safer than MS Windows, but it never hurts to take active security measures. 

First, if you use Firefox to browse the web, I strongly recommend getting the NoScript and AdBlock Plus extensions. This is an added layer of protection against web-based exploits.

You might also want to install Bastille Linux, as it offers some nice features that make remote attacks much more difficult. 
[https://help.ubuntu.com/community/BastilleLinux](https://help.ubuntu.com/community/BastilleLinux)

A lot of the security in Bastille is about restricting access to settings for root only, as Ubuntu only accesses root though the use of sudo what effect will Bastille have.  Will an admin user no longer be able to administer the system.

---

### Post by p_quarles on 2007-07-24
> **ushills said:**
> A lot of the security in Bastille is about restricting access to settings for root only, as Ubuntu only accesses root though the use of sudo what effect will Bastille have.  Will an admin user no longer be able to administer the system.
Bastille is perfectly compatible with sudo. Since the "sudo" command basically just gives you a fake root shell for fifteen minutes, there's no reason it shouldn't work with restrictions on root.

---

### Post by asmoore82 on 2007-07-24
only web servers use port 80 for communication... your web browser uses semi-randomized ports above 1024 ( probably even above 10000 ) for communication.

Also, in real world situations the server quickly moves transit over to another port so that it may accept more connections sooner on port 80 ... this is a part of the 3 step http "handshake"

1. Your Browser sends from port x to port 80 on Server to initiate "surfing"
2. Server sends back to port x on your computer and tells it to start sending to port y
 ... I'm actually unsure of whether or not the server uses port 80 or port y for this ...
3. Your Browser sends actual http requests from local port x to remote port y for the rest of the session.

after step 2 the server is already listening for more requests from other computers on port 80 ;)

EDIT: **note that the local machine doesn't do anything with local port 80

---

### Post by PsychedelicWonders on 2007-07-25
Fleet admiral – You said - Nope. Just don't do incredibly stupid things, and don't run as a root or admin account, and you will be fine from malware.

What does it mean to run as root or a admin accont? 

What is malware?

Pricechild – What is an open port?

And what is sudo, and why is It so bad that you want someone to really think before using it?  How would it cause you to lose files?

You guys said there are a lot bigger security risks when you run server programs, would there be any use in running server programs for home us?  Or it would be overkill for personal use?

P_quarles, you said all of the software I recommended changes system configuration files to prevent bad things from happening compared to the default setings – are you referring to your personal files becoming this “outgoing traffic” essentially?

What is noscript, and how does it help your web browsing?

And is Bastille Linux another version/alternative like Ubuntu?

Do you need to scan all programs you download with a md5sum check?

Sorry for all of the questions, I’m totally new to Linux and really want to learn so I can switch over.

---

### Post by intransit on 2007-07-25
So I was also wondering about this...

I just installed SAMBA for my networking to get the linux box to emulate a Workstation for my XP Workgroup network. There was a tip on security to disable wireless connections, which I did, for the moment. I will eventually want to enable wireless again for Uni (hopefully). That being said, what measures do I need to take to secure myself, and ensure I haven't opened any vulnerabilities/exploits myself?

Advice here is 1) install noscript, 2) install adblocker

Do I need to take anymore precautions when enabling wifi? Or does it just all boil down to the strength of my username/password ?

---

### Post by Pebbie on 2007-07-25
@ psychedelicwonder

1) root admin sort of mean the administrater for the window. with this right, u can mess your system up with no restriction. sort of like messing with system32 for window

2)malware sort of stand for malicious software (i think). well, just google for it. there's alot of it for window

3)about the port... cant really explain. sort of like a connector for you to connect with other computer. certain port have certain function. can google up the port number for its function

im not a ubuntu user.... yet. still downloading. so i can only answer this 3 question base on my knownledge. but most of the answer can be found by using google. seriously

---

### Post by sw1995 on 2007-07-25
Honestly, I am not trying to be "holier than thou" as I am new to Linux/Ubuntu myself, however after a couple of reinstalls, the only advice I have for you in regard to protecting yourself is to take it slow and not install everything and the kitchen sink. Other than that, crap, go hog wild. I teach online history classes and download endless streams of .doc and PowerPoint files and boy, oh boy, do I enjoy opening them fearlessly.

In retrospect I realize that upon first learning about the majesty that is "apt-get" that I viewed the terminal as a kind of magical well that all I needed to do was throw in these magical beans called "sudo apt-get" and out popped these slick, FREE programs. A few reinstalls later I learned that while Linux is "all about choice" and all of that line of thought, it is also FIRST AND FOREMOST about a kind of discipline.

-S

---

### Post by hyper_ch on 2007-07-25
well, basically you don't need any additional protection (addons to FF are recommended... wasn't there a password security flaw in FF a few days ago?)...

As long as you don't run any services you should be fine with the default settings of IPTables.

However, out of courtesy, you can install an antivirus program. The AVs in linux are mainly used to filter out windows viruses/worms/malware when the linux machine acts as file- or email-server. The effect is that the windows user doesn't have to deal with it...
I, however, don't do that courtesy... if someone approaches me that I sent a virus then I simply tell: "Oh, did I? I didn't notice anything... haven't had problems with viruses ever since I switched to linux..."

It's all up to you. The default install of Ubuntu is a lot safer than windows but also regular updates are required and there are a few things you have to remember: Only use software from trusted sources, preferrably only from repos...

---

### Post by ushills on 2007-07-25
> **p_quarles said:**
> Bastille is perfectly compatible with sudo. Since the "sudo" command basically just gives you a fake root shell for fifteen minutes, there's no reason it shouldn't work with restrictions on root.

I take it therefore that where bastille states that commands are locked down to root access only, sudo will still work.  I understand that sudo gives access to root but surely that is based on having some privileges associated with your user account, if those privileges are withdrawn why would sudo still work.

---

### Post by p_quarles on 2007-07-25
> **ushills said:**
> I take it therefore that where bastille states that commands are locked down to root access only, sudo will still work.  I understand that sudo gives access to root but surely that is based on having some privileges associated with your user account, if those privileges are withdrawn why would sudo still work.
It still works because those privileges are configured by /etc/sudoers, which isn't changed by Bastille. Anyway, you don't have to take my word that it works: the page I linked to is part of the Ubuntu wiki, and there would be no reason to have a page about it if the program made administrative access to your system impossible.

---

### Post by Orochi on 2007-07-25
> **intransit said:**
> Do I need to take anymore precautions when enabling wifi? Or does it just all boil down to the strength of my username/password ?

I would reccommend using WPA encryption for your wireless network, and to make sure you have a good password. Also, I suggest turning off SSID broadcast on your router if it has that option. Turning this off means that when computers search for wireless networks yours will not show up on the list. However, if you know the network is there and you know the network's name you can still manually enter the name to connect. It's just a bit of extra security (if people don't know your network is there, it's less likely they'll try to hack it).

---

### Post by hyper_ch on 2007-07-25
WPA can easily be hacked and hiding the SSID is not much use either... there are tools that let you easily detect even hidden wifis... go for WPA2 if it is possible.

---

### Post by Orochi on 2007-07-25
Also turn on MAC address filtering if your router has it.

I know there are tools that let you detect hidden networks, but the point is to make your network harder or more difficult to hack then other people around you, and hope that they go for them instead :D Really though, every little bit helps. Even if it is possible to hack WPA, it's certainly better than WEP (although WPA2 is better if it's available) and hiding SSID is surely more secure than broadcasting, even if some people can still discover it. WPA actually isn't that bad as long as you use a good password (more than 8 characters, try to make it as random as possible for best security).

---

### Post by fastpakr on 2007-07-25
> **hyper_ch said:**
> WPA can easily be hacked and hiding the SSID is not much use either... there are tools that let you easily detect even hidden wifis... go for WPA2 if it is possible.

Sorry - 'possible' is not even close to the same as 'easy'.  It is theoretically possible to crack WPA, but it isn't something that can be done in a reasonable amount of time with a decent key.  WEP is an entirely different story.

---

### Post by p_quarles on 2007-07-25
Actually, there are applications available that make it nearly as easy to crack WPA as it is to crack WEP. 
[http://www.informit.com/articles/article.asp?p=370636&rl=1](http://www.informit.com/articles/article.asp?p=370636&rl=1)
[http://docs.lucidinteractive.ca/index.php/Cracking_WEP_and_WPA_Wireless_Networks](http://docs.lucidinteractive.ca/index.php/Cracking_WEP_and_WPA_Wireless_Networks)

But, yes, WPA is okay if you use a really good key -- preferably at least thirty characters and no dictionary words.

---

### Post by Orochi on 2007-07-25
That WPA crack is just a brute force crack. If your password is long enough and doesn't contain dictionary words it's pretty secure. WPA much better than WEP where you can actually figure out what the key is from the packets being transmitted without brute forcing it. It's in no way "nearly as easy to crack" as WEP is.

---

### Post by ghope on 2007-07-25
A word of thanks to all those who asked and answered on this thread so far. I was also wondering about protection. On the WinXP side of my machine I am using Avast Home Edition for virus protection and have been very pleased with it. Even though the chances of receiving and passing a virus in Linux are much lower, I think I want to be a good citizen and run some  protection in Ubuntu. Would some experienced readers please reply with their suggestions/cautions about antivirus packages? My first thought is to use Avast Linux Home Edition, but I am open to alternatives. Many thanks to all for sharing your wisdom!

---

### Post by fastpakr on 2007-07-25
> **p_quarles said:**
> Actually, there are applications available that make it nearly as easy to crack WPA as it is to crack WEP. 
[http://www.informit.com/articles/article.asp?p=370636&rl=1](http://www.informit.com/articles/article.asp?p=370636&rl=1)
[http://docs.lucidinteractive.ca/index.php/Cracking_WEP_and_WPA_Wireless_Networks](http://docs.lucidinteractive.ca/index.php/Cracking_WEP_and_WPA_Wireless_Networks)

But, yes, WPA is okay if you use a really good key -- preferably at least thirty characters and no dictionary words.

They make the process easy, but not the physical brute force portion.  How quickly do you think you can pull it off?  If you're done in under a few weeks of solid crunching, I'd be impressed.

---

### Post by p_quarles on 2007-07-25
> **fastpakr said:**
> They make the process easy, but not the physical brute force portion.  How quickly do you think you can pull it off?  If you're done in under a few weeks of solid crunching, I'd be impressed.
Chill out. First, I responded to a post in which you chided someone for suggesting that the original poster should use WPA2 if it's available on your router and wifi card. That's good advice.

Second, the security of an encryption system has nothing whatsoever to do with whether or not I can crack it. Both of the articles I quoted suggest that WPA can be very secure, but only if it uses a password that is brute force resistant. The kind of argument you seem to want to get into belongs in Servers & Security, and not in Absolute Beginners.

---

### Post by gn2 on 2007-07-26
> **ghope said:**
>  Would some experienced readers please reply with their suggestions/cautions about antivirus packages?!

I have tried a few, my advice would be forget it, they're all a complete waste of time.

Let Windows protect itself.

---

### Post by hyper_ch on 2007-07-26
> **Orochi said:**
> That WPA crack is just a brute force crack. If your password is long enough and doesn't contain dictionary words it's pretty secure. WPA much better than WEP where you can actually figure out what the key is from the packets being transmitted without brute forcing it. It's in no way "nearly as easy to crack" as WEP is.

At the CeBit a guy demonstrated that WPA can also easily be cracked. The issue is that the handshake is not encrypted, only the (after handshake) connection. It is, of course, not as simple as WEP, but it still is a no brainer and it is reasonably fast...

---

### Post by hyper_ch on 2007-07-26
> **gn2 said:**
> I have tried a few, my advice would be forget it, they're all a complete waste of time.

Let Windows protect itself.

I second that... I haven't seen any reason to use antivirus software on linux yet... if windows machines get infected it's their fault... they should have secured their systems or use a different OS altogether...

---

### Post by elacerda on 2007-07-27
> **p_quarles said:**
> Bastille is perfectly compatible with sudo. Since the "sudo" command basically just gives you a fake root shell for fifteen minutes, there's no reason it shouldn't work with restrictions on root.
It is impossible to install Bastille in my PC. It simply takes 100% of my cpu usage and consumes 900MB of ram.
Are there any previous configurations that must be done before running Bastille ?

---

### Post by bodhi.zazen on 2007-07-27
> **ghope said:**
> A word of thanks to all those who asked and answered on this thread so far. I was also wondering about protection. On the WinXP side of my machine I am using Avast Home Edition for virus protection and have been very pleased with it. Even though the chances of receiving and passing a virus in Linux are much lower, I think I want to be a good citizen and run some  protection in Ubuntu. Would some experienced readers please reply with their suggestions/cautions about antivirus packages? My first thought is to use Avast Linux Home Edition, but I am open to alternatives. Many thanks to all for sharing your wisdom!

At this time there are no known active Linux viruses "in the wild" so there is nothing to scan/protect.

If a virus is developed, antivirus will not protect you any way as the virus definitions need to be updated first (anti virus scanners are reactive not proactive).

Last, if a virus is developed it needs to take advantage of a hole in the code. If this happens a security update will be issued. A security update is the fix to virus problems, not anti virus scanners. So ... keep your system up to date ;)

Linux != Windows

If you would like an overview of Ubuntu Security, take a look here :

[http://ubuntuforums.org/showthread.php?p=3088372](http://ubuntuforums.org/showthread.php?p=3088372)

---

### Post by Blutack on 2007-07-27
Course, you could use another *nix box between your internet and wireless access point.  Then ssh tunnel into it...WPA2 + SSH should be pretty secure I guess...

---

### Post by ghope on 2007-07-27
Thanks very much. Yes, indeed, I'm a refugee from Windows and it must show. I'll be reading your security primer carefully as I become better acquainted with Ubuntu and Linux. I'm really looking forward to working on my laptop with a perspective of awareness instead of vague fear and distrust. It will be a happy day when I can give up dual booting!


> **bodhi.zazen said:**
> At this time there are no known active Linux viruses "in the wild" so there is nothing to scan/protect.

If a virus is developed, antivirus will not protect you any way as the virus definitions need to be updated first (anti virus scanners are reactive not proactive).

Last, if a virus is developed it needs to take advantage of a hole in the code. If this happens a security update will be issued. A security update is the fix to virus problems, not anti virus scanners. So ... keep your system up to date ;)

Linux != Windows

If you would like an overview of Ubuntu Security, take a look here :

[http://ubuntuforums.org/showthread.php?p=3088372](http://ubuntuforums.org/showthread.php?p=3088372)

---

### Post by silent1643 on 2007-07-27
> **akkad said:**
> hi,
actually am new with ubuntu and am happy with ubuntu performance and everything, and as i experienced slow performance with windows xp when i use anti viruses or any kind of protection, am really looking not to use them with ubuntu linux, first to keep the lovely performance and in addition as i heard that linux is hard for viruses or bugs free, so my question that do u think i really need a protection or ubuntu linux neednt ???

[http://www.littleubuntu.com/v2/search.php?search=virus](http://www.littleubuntu.com/v2/search.php?search=virus)

---

### Post by bodhi.zazen on 2007-07-28
> **silent1643 said:**
> [http://www.littleubuntu.com/v2/search.php?search=virus](http://www.littleubuntu.com/v2/search.php?search=virus)

Interesting, but I would like to address those issues (including how to proceed) :

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

