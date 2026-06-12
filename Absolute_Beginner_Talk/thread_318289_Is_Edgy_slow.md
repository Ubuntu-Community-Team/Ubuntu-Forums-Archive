---
title: "Is Edgy slow?"
date: 2006-12-13
forum: Absolute Beginner Talk
---

### Post by Otpadnik on 2006-12-13
Hi!
I've installed Ubuntu a few days ago and when it was running from CD it seemed slow, so I thought it would run faster when I install it. But, no?
It's A LOT slower than XP for now... I don't know if something needs to be reconfigured or...
Maybe it is cause my modem isn't installed, and my nvidia graphic card, but just now I've tryed Knoppix live CD and it was really fast so i just don't get it...
So please can somebody help me with this?
How to find out what more do I need to install? ](*,) 
And I have that damn Conexant HCF modem and don't have a clue how to install it...:confused: 
So, if anyone has an idea or a link plese post it!!!

Thanks

---

### Post by raul_ on 2006-12-13
What do u mean with slow?

What are your system specs?
Did u install edgy or dapper from the cd? =\ i didn't even know there was a cd for edgy. I read that u could only upgrade from dapper

---

### Post by AndyCooll on 2006-12-13
The simple answer to your question is ...no.

Edgy is much faster than XP. Must be something to do with your configuration.

:cool:

---

### Post by Otpadnik on 2006-12-13
Well.... It takes about three minutes to open terminal, and I downloaded CD form ubuntu.com desktop/download.... I didn't have any other linux before....
System specs?
Do you mean computer configuration?

---

### Post by raul_ on 2006-12-13
system specifications :) speed, ram, motherboard, blalablabla

Anyway, if u run XP fast u should run Edgy even faster (as here)

---

### Post by Otpadnik on 2006-12-13
Yes!
And I've been expecting speed and happines and a lot of fun and new expirience, but now I cannot Even read Linux for Dummies under Ubuntu, becaouse I will loose half of night to scrol one page :(
And I repeat Knoppix Live CD is faster than XP? :-k 
What's difference between these two? Maybe there is a solution???
Some auto-stuff that I should do manually?
HELP!!! :)

---

### Post by raul_ on 2006-12-13
U can always try System->Administrarion->System Monitor and see what's eating your CPU

---

### Post by Otpadnik on 2006-12-13
OK!
I'll try. But, beware, if I don't find anything I'll be back(probably also if I find it, there will be more troubles) :)

---

### Post by xabbott on 2006-12-13
> **Otpadnik said:**
> Maybe it is cause my modem isn't installed...

I've read a few post now that state Ubuntu or Gnome run slower without an internet connection.  If I recall you need to disable ipv6 and/or make sure you have /etc/hosts has proper localhost entries.

---

### Post by d3v1ant_0n3 on 2006-12-13
Install your graphics driver and things should liven up dramatically.

personally, I found Edgy notably faster than XP, even with Beryl turned on.

---

### Post by Fully216 on 2006-12-13
Make sure the system is up to date as well.

bootchart is a great tool that lets you visualize the boot process.  This will give you a general idea if something is going wrong when you start the computer.  For example, mine boot took a while because of a ndiswrapper problem.  I only realized it was there after running bootchart.

Personally, my ubuntu is wicked fast compared to Xp.  For example, my computer takes 4-5 minutes to start Xp, and 30 seconds in Ubuntu.  I tend to use less resources, the CPU hardly needs a fan in unbuntu, etc.

---

### Post by Ryba on 2006-12-13
> **d3v1ant_0n3 said:**
> Install your graphics driver and things should liven up dramatically.

personally, I found Edgy notably faster than XP, even with Beryl turned on.
Actually I find that edgy runs FASTER with beryl and 3d acceleration then it does without it. However, I also happen to have a GeForce 3 gaming graphics card as well so your millage may vary :)

---

### Post by felosi on 2006-12-14
ha ha now I hate to admit it but edgy is slow, and the boot and shutdown times are horrible. Nothing to do with configuration, a stock install of edgy is just plain slow. I started trying some different tweaks like prelink, using apt build for all packages, etc, Still slow. 

Im on dual core xeon 2.0 ghz machine and is still slow! Whats up with that?
I like ubuntu and all but edgy was a huge disappointment.
I hate windows, I use linux 24/7 but I say windows xp is twice as fast as edgy on all aspects. I seriously hope they fix this, I regret upgrading now

---

### Post by xabbott on 2006-12-14
I don't think you can say a stock install is slow. It is configuration or something concerning your hardware/software. Otherwise we'd all notice how slow it is. I'm not saying it isn't slow for you as I have noticed some have this problem. 

For me this is the fastest *booting* Linux I've used. I also feel it is as fast or faster than XP. I say that only because I didn't find XP to be slow and I don't find Edgy to be slow.

---

### Post by crimesaucer on 2006-12-15
I was about to write a huge essay on how my xubuntu edgy using xfce4.4 is faster then Windows Xp in boot-up time and Internet page loading time, but I'm just gonna recommend you install the xubuntu-desktop for edgy with the best configuration for your computer, and see how much faster xubuntu is then Xp for yourself.

And as for stock install, it takes half the time of Windows Xp which is 2 different CD's to install (plus 2 more CD installs for OfficeWorks and DVD), and that takes forever, Like 2.5 to 3 hours for Xp with service pack2, Office/Works, and DVD, compared to 1 hour with edgy. Then with Xp you have to update your Xp with all of the security updates from 2005 (65 security update), and that takes forever with reboots. Of course with edgy you do have to spend at least one hour or less with the wiki page and a terminal for all of your codecs, apps, and flash/java plugins if you don't want to use EasyUbuntu or Automatix2. And for an update/upgrade on the terminal, it takes about 1 minute.

also...to xabbott, about the ipv6, if you disable it in Firefox's about:config (network.dns.disable ipv6 true), doesn't that fix the problem or do you have to configure something in xubuntu/ubuntu as well?

**I did a test.** I timed the time it took from startup of grub to booting up and then starting 3 applications, Firefox 2.0 Thunderbird 1.5.8 and My Documents/My Music or thunar /home/me/music. I pressed time on the watch when I choose between xubuntu or Windows and pressed enter, and timed it from there until Firefox's homepage was fully loaded and Thunderbird was fully loaded and downloading email, and my file system was fully loaded and able to click to my choice of folder.

xubuntu won with a time of 1:32 seconds and loaded stable, and could of opened another 5 programs at the same time without breaking.
windows xp lost with a time of 2:46 seconds and felt like it was gonna never load Firefox or Thunderbird, and clicking on My Documents was barely working to get to the next folder.

I bet if other people timed this test that xubuntu/ubuntu would win by a whole minute every time.

---

### Post by felosi on 2006-12-16
i use xubuntu, using xfce most the time and icewm at other times. I started out with the dapper install cd and upgraded. Boot times are still slow, overall performance is disappointing,. Nothing to do with configuration and Ive seen it on 3 different computers the upgraded edgy. 
And for some reason I cannot get the ck kernel to work with it. I like ubuntu, dont get me wrong, but on a dual core xeon it should fly, it doesnt. Ive also seen it on p4 2.66 ghz -slow, 

I mean its not horrible to the point of being unusable but its by far NOT fast.

---

### Post by crimesaucer on 2006-12-16
On a crap computer it is much faster (1.6 GHz). I've timed it and compared it objectively. I am using a T1 cable connection so that also could factor in a bit.

With Windows Xp it takes about 3 full minutes for it to boot and load Firefox, Thunderbird, and My Documents, and the computer seems unstable opening three apps during the boot and start-up of Xp. Plus in Windows you have all of those annoying bubbles popping up (wifi, lan), and if your anti-virus (4th program to be fair) needs updates or your windows needs updates then that is more time also.

With xubuntu edgy, I was able to boot up, login, and open 8 fully working apps (Beryl, Firefox, Thunderbird, Listen musicplayer, GIMP, thunar, Grip, and Xterm) in 1:45 seconds.

Try that with Windows. Open FF, TB, GIMP, My Documents, WMP10/11, and Microsft Updates all at the same time and see how long it takes until all of your programs are fully working.

And for web pages like Surfline.com that usually takes for ever to load with Windows Xp, it loads twice as fast using xubuntu.

Maybe you don't see the difference with a strong computer, but having only a 1.6 GHz celeron m laptop, it is much faster using xubuntu.

---

### Post by derjames on 2006-12-16
I am running Ubuntu 6.10 using Vmware server in a core 2 duo T5600 laptop (1GB RAM), what I can say is that am very happy with the performance. It is really fast (don't know how to quatify this, it is just my impression...)

---

### Post by moshuptrail on 2006-12-16
You might not remember but earlier versions of Windows were real slow booting.  With XP, m$oft moved some of the boot process to AFTER you get your first screen and log in.  So you can get to the login screen and logged in pretty fast.  But then the disk churns and you can't do much for a while - especially while it's loading in your anti-virus program.  (oh, that reminds me, what's the time to load anti-virus in Linux?  zero!)

---

### Post by Old Pink on 2006-12-16
Took 7 minutes to install Dapper on this system, and under an hour to upgrade to Edgy (installation time, download time not included, it's not fair to judge Ubuntu's speed on my low quality internet) 

Both Edgy and Dapper are fast. Have you tried Dapper, is it any faster/slower? If they're equally slow, it's probably a problem with your hardware. Is the RAM in correctly? Do you have much RAM at all? 

I can't see how you could possibly find a fresh install slow, even Edgy running purely off the Live CD is faster than XP really. I found an old screenshot of my XP desktop floating around the internet a few weeks ago, and I had something like a total 14 malware removal tools on the desktop/taskbar, slowing it down even more so. 

I'm sure whatever your problem turns out to be we can work around it, please, post some more details. 

A screenshot of every tab in your System Monitor would be nice, for a start. (System > Administration > System Monitor) And then if you type "dmesg" into a terminal window and post the output, that'd be appreciated too. :)

---

### Post by LDRoamer on 2006-12-16
Like others have said you must have some kind of a configuration problem. I am running Edgy on an old laptop (compaq armada 1750). Its only a PII 366 but it does have a reasonable amount of ram (320mbs).  Edgy boots faster than windows but once loaded speed between the two is pretty comparable.

---

### Post by Fatec on 2006-12-16
> **d3v1ant_0n3 said:**
> Install your graphics driver and things should liven up dramatically.

personally, I found Edgy notably faster than XP, even with Beryl turned on.

Quite the opposite for me..i find edgy slower than xp, people who say its faster than xp need their head's checked (lol, this is a joke, dont take it seriously)...but yea, seriously i find xp alot faster than edgy.

---

### Post by phelixnyc on 2006-12-16
I am not sure what all of those replies are about Windows being slow on boot, if you tweak it enough it loads extremely fast. As for Edgy being slow I hade a similar experience with it when I installed it. I since have had a better experience with Dapper, so try different distro's see what works for you.

---

### Post by xpod on 2006-12-16
I aint had XP on a pc really since August\September but i`ve had about 4 or 5 xp machines come through my hands and not one of them was ever faster than Edgy or Dapper..
And these xp macines\laptops were all a lot newer than any of our older pc`s and had a bit more oomph in most cases.

Even after doing all the usual xp clean\tweak\exorcise procedures or even re-installing and having a fresh XP never got them even close to Ubu.[-( 
The boot up and shutdown times especially........once up & running though a fresh clean install of xp was probably not so far behind i suppose.:-k 

5 months into my ubuntu adventure they still run as fast as they did the day\s i installed them.Nothing i do put`s entries in startup folders without my knowlage,i dont have to do all that fragging lark and there will probably never be any viruses and spyware to slow me down either.

In xp i would constantly be scouring msconfig etc then defragging and running this scan,that scan  and the next scan just to keep XP running at a reasonable rate....

Good luck anyway...any problem you encounter is only something new you learn about:D

---

### Post by Fatec on 2006-12-16
> **phelixnyc said:**
> I am not sure what all of those replies are about Windows being slow on boot, if you tweak it enough it loads extremely fast. As for Edgy being slow I hade a similar experience with it when I installed it. I since have had a better experience with Dapper, so try different distro's see what works for you.

Agreed...i have my xp down to 9 seconds.

Edgy down to 37 seconds.

And im sorry people, but those of you on here who complain about xp being slow, i do ponder what sort of sites you visit and what apps you install as my XP is still running great, just as it was when i installed it waaaaaay back in the day, maintanence is the key people.

---

### Post by wh0rd on 2006-12-16
On a 512 MB of RAM I'm currently running an Antivirus, a rootkit detector, installing a printer and listening to MP3s with Banshee, browsing the internet, oh and also a reply to this post.

---

### Post by xpod on 2006-12-16
> And im sorry people, but those of you on here who complain about xp being slow, i do ponder what sort of sites you visit and what apps you install as my XP is still running great, just as it was when i installed it waaaaaay back in the day, maintanence is the key people.

Yeah...but  aint it a shame you have to spend sooooo much time doing maintanence.
I dont hate xp and aint out to do any shouting off about it and actually enjoy the messing about with it........when someone brings it for help

But what do all these normal untie\uncle\neighbour users do who barely know how to log on to their msn let alone do all the constant stuff that needs done to "maintain" xp......BAH HUMBUG!!!!

I`ve only done this stuff pc for 9 months  but every home user i know could`nt tell you what "msconfig" was let alone clean that or anything else out..
Yeah XP can run wonderfully IF you keep it maintained but i prefer a OS that i can install then learn how to USE instead of spending months learning what it takes just to keep the thing running ok.

I reckon you need to be more of a pc geek to keep XP running ok than what you do to keep Ubuntu running properly......

YUP......."maintanence" is the key all right!

---

### Post by Fatec on 2006-12-16
> **xpod said:**
> Yeah...but  aint it a shame you have to spend sooooo much time doing maintanence.
I dont hate xp and aint out to do any shouting off about it and actually enjoy the messing about with it........when someone brings it for help

But what do all these normal untie\uncle\neighbour users do who barely know how to log on to their msn let alone do all the constant stuff that needs done to "maintain" xp......BAH HUMBUG!!!!

I`ve only done this stuff pc for 9 months  but every home user i know could`nt tell you what "msconfig" was let alone clean that or anything else out..
Yeah XP can run wonderfully IF you keep it maintained but i prefer a OS that i can install then learn how to USE instead of spending months learning what it takes just to keep the thing running ok.

I reckon you need to be more of a pc geek to keep XP running ok than what you do to keep Ubuntu running properly......

YUP......."maintanence" is the key all right!

hehe

I've been using windows for years, perhaps i am a geek :P

But yes, xp runs great for me.

Edgy doesnt, dapper does...but still, its not faster than windows.

And to the post above, yes...i can multitask like that in windows without lag as well...

Then again, i get lag in ubuntu if i run torrents/music/net all at once heh.

---

### Post by xpod on 2006-12-16
> hehe

I've been using windows for years, perhaps i am a geek :P

But yes, xp runs great for me.

Edgy doesnt, dapper does...but still, its not faster than windows.

And to the post above, yes...i can multitask like that in windows without lag as well...

Then again, i get lag in ubuntu if i run torrents/music/net all at once heh.
Reply With Quote

XP can run great for anyone my friend but as has already been mentioned it`s all about "maintanence"....and knowing what it takes to carry out that maintanence.
Tell my MIL or my neighbour or my wifes pal the secretary how to "maintain" their pc`s
and you`ll still be getting a call a few weeks down the road....if not days](*,) 

If these dozen or so folks are an example of the bigger picture then i reckon theres an awful lot of really slow or even unusable xp machines sitting out there in ppl`s homes.

Not everyone has whizkid kids or someone they know who at least knows what "defrag" means.
I`ve seen peole on here ask what "defragging" is when told how to go about dualbooting so i can only begin to imagine the rest:-k ........£££££££££££££££££££££££££££££££:evil:

---

### Post by fiztlen on 2006-12-16
> **Otpadnik said:**
> Well.... It takes about three minutes to open terminal, and I downloaded CD form ubuntu.com desktop/download.... I didn't have any other linux before....
System specs?
Do you mean computer configuration?

I was just wondering about the super-slow launch times myself, and found [this thread]("http://ubuntuforums.org/showthread.php?t=296354").  I don't know if it applies (you on 32 or 64?) and haven't had a chance to try it on my machine, so ymmv, but check it out.

Lots of answers out there, keep plugging at it.

---

### Post by phelixnyc on 2006-12-16
As much as you bash it (Windows) most people use it (including myself). Yes Ubuntu is a great OS, yes it is  fast (not as fast as I have tweaked my xp to be), I want to continue to learn Linux better but have to agree after tweaking Ubuntu and XP, Xp is faster for me.

---

### Post by Old Pink on 2006-12-16
> **Fatec said:**
> And im sorry people, but those of you on here who complain about xp being slow, i do ponder what sort of sites you visit and what apps you install as my XP is still running great, just as it was when i installed it waaaaaay back in the day, maintanence is the key people.

Why should I spend ages maintaining a system in order to keep it running fast? It'd take the same amount of time to do things slowly. I'd rather use Linux: speed without the constant maintenance. :rolleyes:

---

### Post by crimesaucer on 2006-12-16
With Windows Xp properly defragged and the hard disk clean every week, with it having it's registry properly cleaned and rid of all broken keys using registry cleaning software, with having it optimized for speed and having all of the unnecessary applications turned off for the start-up, and with having the best free anti-virus and spyware installed (F-secure) and full computer scanned everyday to keep things running fast and using ccleaner, ad-aware, and spyware blaster and with having Firefox optimized for speed, it is still so much slower then xubuntu edgy.

So if you have Windows Xp down to 9 seconds for a boot screen (mine takes about 10 to 12 seconds), then how much more time does it actually take before you can actually do anything on it like browse Firefox or check your incoming email. Mine takes 2 minutes 46 seconds.

10 second boot, 2 minute and 30 second stall, before actually being able to use your computer compared to 1 minute 30 seconds on xubuntu running 8 programs fully working.  

Now if you tweaked your Xp to not have those annoying bubble messages, maybe that would save you a lot of time, but then you wouldn't get any important error messages or battery/wifi/virus warnings either.

I don't dis-like my Windows Xp. I have it as fast as it can be with a Vista shell pack (WindowsX) and an object dock with some nice png icons. It looks really good for Xp, and I use it with my utorrent that is TCPIP patched to 50(40) and configured to rip torrents as fast as possable with a TCP/ip set to 4000kbps. 

What Xp is better for:

1) My iRiver T30 device. 2) utorrent 3) having no problems playing quicktime/real videos. 4)WinRAR and FileZilla which both can be replaced with others or used with wine. 5) and I like how my laptop's mouse feels on Xp more. 6) Gnome is pretty ugly when it's default, but once you install Beryl (Beryl/Emerald is better looking then Xp) or a new GTK+2 theme it isn't a problem. 7) I prefer ctrl/alt/delete compared to xkill. xkill is better unless you can't type or use your mouse, then I start missing the ease of ctrl/alt/delete. 8.) some Firefox themes/extensions don't work with Linux.

What Xp is worse for: 

1) All around web performance and page loading time. 2) loading/using gmail or POP3 email (so slow in Windows). 3) Beryl/Emerald is so much better looking then Xp or and Xp/Blinds or vista shell. 4) not being able to be using my computer 1 minute after turning it on, instead, I have to wait for 3 minutes (Xp) while everything trys to load it's self. 5) all virus/spyware/registry/microsoft updates/disk clean/defrag issues and maintaining it's health turns into an everyday thing that is like treading water to keep from drowning. 6) always having to reboot after updates and certain installs and having to wait for another 3 minutes to get back to whatever I was doing. 7) and worst case scenario, booting/starting Xp 3 minutes, to find out you have microsoft updates, installing those for 5 minutes, re-booting and waiting another 3 minutes to finally be online.

xubuntu 1 minute to boot/start and open terminal and Firefox, terminal codes sudo apt-update, sudo apt-upgrade sudo apt-get dselect-upgrade, all upgrades added with out having to reboot AND being online on Firefox during the whole process with Firefox working faster and smoother then Xp ever has.

---

### Post by raul_ on 2006-12-16
> **crimesaucer said:**
> 
What Xp is better for:

1) My iRiver T30 device. 2) utorrent 3) having no problems playing quicktime/real videos. 4)WinRAR and FileZilla which both can be replaced with others or used with wine. 5) and I like how my laptop's mouse feels on Xp more. 6) Gnome is pretty ugly when it's default, but once you install Beryl (Beryl/Emerald is better looking then Xp) or a new GTK+2 theme it isn't a problem. 7) I prefer ctrl/alt/delete compared to xkill. xkill is better unless you can't type or use your mouse, then I start missing the ease of ctrl/alt/delete. 8.) some Firefox themes/extensions don't work with Linux.


You can use utorrent with wine.

I have no problems playing quicktime/real videos

U have compressing utilities installed natively in ubuntu that can handle any file

I think default XP is tacky (oh that green)

I have a script installed that shortcuts ctrl-alt-del to my Gnome System Monitor

As for the rest (how many are left? two?) i agree with you :)

---

### Post by Rackerz on 2006-12-16
You can also use Filezilla in Wine or use the native Linux version :).

---

### Post by felosi on 2006-12-16
well you are hearing this from an avid linux enthusiast such as myself xp is faster then edgy, plain and simple. May not be better but its for sure faster, EVERY aspect. Now lets compare ubuntu to other distros edgy = slower then slackware, slower then fedora, dont know about many others.

And what the hell is this still making everything for i386? What the hell is teh deal with that? I been using computers for 10 years now and I would say 386 is before my time. Hell look at the system requirements, I dont even think there is an 1386 pc with that. Really this day in age if you are truly running such old crap you need to get a job and buy something newer. Hell I have 2 computers in my closet from 2001 that are 686,  its not like its such new technology. And even if you are poor you can get a used pc from the pawn shop for around $100.

Anyway my point is ubuntu still making everything based on 1386 is stupid, I doubt 1% of ubuntu users are even on 386. And really how does ubuntu manage to patch some software and actually make it 2 timers slower, like firefox for example, it requires tweaking  right out of the box. I dont know Im disappointed with edgy, I cant even get the ck kernel to work with it and the "generic" kernel sucks, But instead of complaining I plan on trying another distro like gentoo that does in fact makes things for speed.

There is no excuse why ubuntu should be slow, Like I said before its not horribly slow but its noticeable, and why the hell would people abandon windows for a slower and more buggier system like ubuntu? Oh yes, buggy too but Ill not get started on that now. Keep in mind I am a 24/7 linux user, hate windows, never use it but I do have a dual boot I go on occasionally to do graphics stuff and its like night and day the speed and response time.

I think a lot of you are still gungho ubuntu and will support it no matter what even if it means denying the obvious. I just dont see how someone can sit and say its faster then windows, its not true. Like I said I get on windows from time to time and overall response time, boot time, EVERY Thing is like night and day. Things on windows open almost instantly as opposed to my xubuntu. Also on my xubuntu system this time I have built almost everything from source using apt-build. I dont see how ubuntu and debian developers do it but they can add their patches and what not and make a piece of software up to 2 times slower then it normally is.

---

### Post by raul_ on 2006-12-16
Nobody uses x386 processors? What world are you from? Besides, i have XP, it eats 2 times more RAM (yes, on it's own) than my ubuntu running beryl,firefox,amsn, listen music player and i just don't put nothing else on this list because i rarely use more than that (simultaneosly), because normally when i'm working im not browsing the web or listening to music. So anyway, it works differently with different persons.

As someone said: "Windows XP is great if you have nothing whatsoever installed"

---

### Post by crimesaucer on 2006-12-16
to raul: 

I haven't tried utorrent on wine because I was in utorrent's forums reading up on it, and everything I read about utorrent/wine made it seem like it would be more of a hassle then it's worth. Like stability and certain things not working. Plus, there didn't seem to be a lot of Linux support in those pages, maybe when they create that utorrent with a Linux port like they keep saying in digg.

Plus I have my utorrent configured perfectly to this "how-to" so as to work with a T1 LAN cable hook-up that can get 4000kbps and I'm still not sure if I would be able to configure it the same to be as fast when running under wine: [http://forum.utorrent.com/viewtopic.php?id=3912](http://forum.utorrent.com/viewtopic.php?id=3912)

Basically my torrents are very fast compared to when I used to run Azureus on Xp. And it's the only reason I haven't tried torrents on xubuntu (Azureus, Bittornado).

I have had problems with VLC and the media players at first. Now I have xine-ui and it works really good for basically everything, I guess it plays .avi ok, but I have had some .avi that wouldn't play on anything. As for Real, I wasn't able to get it from the edgy wiki page's repository and haven't tried to get it since. So I guess I listed #3 as objective filler that was more about "right out of the box" issues. I bet if I actually searched a bit, I could always find a repository that would install Real, I could just install automatix2 just to get their Real if I really wanted to, but I never see movies that use Real anyway. 

#4 was objective filler too, I don't need WinRAR if my torrents are on Xp anyway, and FireFTP is working really good. (I haven't tried to install FileZilla with wine yet because I was surprised at how good FireFTP worked, plus I can access it on my toolbar now and don't have to update FileZilla every week from Filehippo.com.)

Yes I agree with you, Xp is ugly, but so is Gnome's default panel and KDE's default panel. I do like the brown and sky blue "clear/human" window themes better then the default Xp colors, and the folders are better looking in human then in Xp. (when I use default Windows Xp I feel like I'm at the Library). 

Xp or XFCE/Gnome/KDE aren't as pretty as new Vista or new OS X Leopard. But after installing Beryl/Emerald, xubuntu/ubuntu wins hands down and even looks better then Vista/OS X. And some of the panel themes and window themes in Synaptic, xfce-looks, gnome-looks, KDE-looks, and other window managers look as good or better then the new Vista/OS X. I do think Xp with a shell theme can look good, but it does get a bit buggy, WindowsX 5.5 works pretty good on mine though.

I'm still learning linux a bit and haven't started making shell scripts or aliases yet, soon though, I guess that would be a good one to start with.

---

### Post by Old Pink on 2006-12-17
Hm. Alot of MS-fanboys here. :neutral:

*scared*

---

### Post by steve.horsley on 2006-12-17
Otpadnik - This thread seems to have gone off the rails. I suggest you start another one and make it clear that it takes 3 minutes to open a terminal - hopefully that will head off all the discussion about tweaks that make a few percent difference. Your choice of video card is clearly utterly irrelevant.

I can't imagine what could make such a dreadful delay, except possibly a bad shortage of RAM combined with no swap partition, but a live CD should have had the same problem. It may be worth reinstalling from scratch, I suppose.

---

### Post by Jasman on 2006-12-18
In my experience (running on an Asus Z70V laptop, Pentium M with 2G RAM and ATI x600) Ubuntu Edgy is slow out of the box, particularly the boot time. If I didn't want some particular features (for me, undervolting) and didn't have trouble installing my graphics driver on a non-stock kernel (I've done it, but it's always difficult, and I never know if I can reproduce it successfully), the simple solution would be to either recompile the stock kernel following one of many threads in this forum (all of which give you hints to worthwhile tweaks, including selecting your actual processor, instead of i386), or compiling a vanilla kernel with something like the ck patchset. I had recently installed the Gentoo-intended evolution-mission 2.6.18 patched kernel, and the boot time was under 30 seconds. This compares to a couple of minutes booting under the Edgy kernel, un-recompiled. I maintain, though, that even just recompiling the kernel from source with a few tweaks makes a lot of difference. So I guess I'm agreeing with another post here that rants against the use of one i386-optimized kernel. Although I think the Ubuntu developers have said this shouldn't be an issue with recent kernel developments.

---

### Post by jvc26 on 2006-12-18
I havent had any problems with the ubuntu edgy 'out of the box' install. I downloaded the ISO (having had a messy upgrade from dapper) and would say its running faster than dapper did, and definitely faster than my XP used to, even with beryl running and so forth. The only thing I can think of is it not being configured to your setup.

---

### Post by Otpadnik on 2006-12-18
Ok... I'm finally back in XP, to check my e-mail and stop playing with Ubuntu :)
When I wrote that I'll try what raul said I was sure this thread will die.
But it isn't.
Ok, it doesn't have anything to do with what I've asked but everyone are replying to thread name.
My bad. Sorry. 
After instaling modules for nvidia everithing is much better. I still don't have internet(Conexant winmoder ARGH), but I hope someone will give me external modem :)
My XP is really fast, but with A LOT of tweaking. My girlfriends and roomates computers are quite new and fast, but their XP is really slow.
And Ubuntu is "out of the box" as fast as my tweaked XP, so I guess it's score for Ubuntu. I'll format partitions with XP once I find modem :)

Nemanja

---

### Post by thingamahoojie on 2006-12-18
Is there a page on how to tweak Edgy so it boots faster? I'd like that. I have a fresh install, last 24hrs and it's pretty damn slow to get to the login. 

Once up and running though it feels as if it's as fast as XP or OS X for that matter.  :o

---

### Post by venik212 on 2006-12-20
> **xabbott said:**
> 6 and/or make sure you have /etc/hosts has proper localhost entries.

How do you do this last part?

---

### Post by SavageFreedom on 2006-12-20
Edgy works significantly faster than Win2000Pro, which is what I was previously using on this machine. It really blew me away.

Specs:
Dell Dimension B110
Intel Celeron D 2.66Ghz CPU
1024mb PC3200 RAM
160gb storage
NVidia GeForce FX 5500

---

### Post by SavageFreedom on 2006-12-20
Oh, sorry. Didn't see that you'd solved the problem.

---

