---
title: "From The Number Of Samba Problems, one can see there are 1000's of hr's wasted."
date: 2006-05-18
forum: Absolute Beginner Talk
---

### Post by onehiq77024 on 2006-05-18
I am not the smartestgut in the world, but by  looking at the 1000's of hours being wasted on Samba problems, it seems to me that it is time to write a script to collect the relevent pc and Linux parms and write to the output to which ever of the 133 fstab files that should be updated to make permanent the shared directory.

Find below a perfeft example of a what Linux veteran went through, and he still may not have fixed the problem, and I quote; "10:00 - I'm starting not to dislike Ubuntu 5.10 as much as I did originally. At this point, I'm in the "I can live with it" stage, having just graduated the "grit my teeth and bear it" stage. Although I'd still prefer to be using Xandros, Xandros 3 won't run on my current hardware. Xandros 4 will support my new hardware, but isn't expected before June, about the time that Ubuntu/Kubuntu 6.06, also known as Dapper Drake, should be released.

By that time, it's possible I'll have "outgrown" Xandros. Xandros is extremely well integrated, and isolates new Linux users from the complexities of the OS. The price you pay for that is limited flexibility and choice. As long as you're willing to live with the choices that Xandros makes for you, everything just works. If you want to go beyond what Xandros offers, things can get ugly. Conversely, Ubuntu/Kubuntu is extremely flexible and offers unlimited choice, but at the expense of less hand-holding.

I'll probably install Xandros 4 and Kubuntu 6.06 and play with them extensively before I settle on one or the other. For my personal use, that is. I've installed Xandros OCE for several friends who are not computer people. I'll either leave them on Xandros 3 or upgrade them to Xandros 4, once the OCE version is available. Although some people sneer at Xandros as "Linux with training wheels", in my opinion it can't be beat for Windows refugees, particularly those who have no desire to learn a new OS.

[top]

Wednesday, 19 April 2006

[Daynotes Forums]    [Last Week]   [Mon]  [Tue]  [Wed]  [Thu]  [Fri]  [Sat]  [Sun]   [Next Week]    [HardwareGuys Forums]

09:17 - Here's an example of why I prefer Xandros to Ubuntu. Barbara's Xandros system, adelie, also functions as our ad hoc file server. I created four SMB (Windows) shares on that system: archive, barbara (her home directory), holding, and usr. I would like to map those SMB shares to subdirectories of my home directory on newton, my main desktop system. For example, the SMB share //adelie/archive should map to the local directory on newton /home/thompson/archive.

To accomplish this on Xandros, I simply fire up Xandros File Manager and choose Tools->Map Network Drive. XFM presents a list of available Windows shares. I click on, say, the share /archive on adelie. Xandros fills in a suggested mount point, /home/thompson/archive, which I can accept or override. When I click OK, Xandros takes care of everything automatically, and the new share shows up as just another directory in Xandros File Manager.

With Ubuntu, the process is a lot more complicated. Brian Bilbrey, a Linux guru, was kind enough to spend an hour on the phone with me last night getting Ubuntu set up. After some unsuccessful mucking about, it became clear that Ubuntu was going to let us mount the SMB shares, for which we'd already manually created directories in my home directory. After some head scratching, Brian said it sounded like I didn't have smbfs installed and suggested I run the following command:

sudo apt-get update && sudo apt-get install smbfs

That worked, although for the life of me I don't understand why Ubuntu didn't install smbfs by default. With smbfs installed, I was able as root to issue the command:

mount -t smbfs //adelie/archive /home/thompson/archive

which indeed worked. I'd already created the directory /home/thompson/archive, and when I clicked on that directory in Ubuntu's file manager, I indeed saw the subdirectories and files contained in that share on adelie. I noticed, though, that the icons associated with those files and directories made it clear that they didn't belong to me. Checking permissions, I found out that they were owned by root. That makes sense, since I did the mount command as root. So I used the command:

umount //adelie/archive

to unmount the SMB share. I then logged in as myself (rather than root) and issued the mount command. Alas, Ubuntu returned an error message, telling me I had to be root to mount something. Duh. That makes sense, but it left me with the permissions problem. Also, of course, I was issuing the mount commands at a command line, which means they wouldn't survive a reboot. Presumably, I can add a line like the following to fstab:

//adelie/archive /home/thompson/archive smbfs user 0 0

to mount the SMB shares automatically, but I haven't gotten around to doing that yet.


09:35 - And that did it. Thanks to email from Brian Bilbrey, I added the following lines to /etc/fstab.

//adelie/archive /home/thompson/archive smbfs rw,username=barbara,password=<barbara's-password>,uid=thompson,gid=thompson 0 0

//adelie/barbara /home/thompson/barbara smbfs rw,username=barbara,password=<barbara's-password>,uid=thompson,gid=thompson 0 0

//adelie/holding /home/thompson/holding smbfs rw,username=barbara,password=<barbara's-password>,uid=thompson,gid=thompson 0 0

//adelie/usr /home/thompson/usr smbfs rw,username=barbara,password=<barbara's-password>,uid=thompson,gid=thompson 0 0

And everything now works as it should. I've saved a copy of fstab in my never-delete directory.


12:13 - European consumer electronics giant Philips has filed a patent application worthy of Dogbert. If implemented, this technology would prohibit television viewers from changing the channel or muting the sound during commercials, both on live TV and on programs recorded to a DVR. This would be accomplished by inserting a signal to mark the beginning and end of commercial breaks.

It might surprise my readers to learn that I'm all in favor of this technology being implemented widely. Current automated methods of detecting and eliminating commercials, such as those used by MythTV, are only about 80% effective. Those methods depend on algorithms that detect anomalies in the program stream, such as the fade to black that occurs between a program segment and a commercial segment. Having unambiguous markers in the program flow would make it much easier to detect and eliminate commercials automatically.

Some years ago, I proposed a cooperative commercial-eliminating mechanism similar to CDDB, by which users of PVR applications such as MythTV could flag commercials manually and have the timing data uploaded automatically to a database, which later viewers could access automatically to flag their recordings to eliminate commercials. But having the networks do the flagging for us would be better still.

Of course, there are a few problems with this. Mainstream viewers are screwed, because they depend on commercial products, none of which will delete the commercials for them. Those of us with video capture cards and access to open-source apps like MythTV will benefit while most viewers will suffer.

Also, the networks may have a cunning plan: inserting flags in the midst of the actual program, which they hope our PVR software will automatically delete, believing that material to be a commercial, and thereby ruin the recording. But, as is always true of the cunning plans of the copyright pigs, this simply won't work. Our open-source PVR apps won't assume that everything flagged as a commercial is in fact a commercial, but merely (a) that all commercials are likely to be flagged as such, and (b) anything flagged is quite likely to be a commercial. In combination with the current algorithms for detecting commercials, this should boost accuracy from about 80% to more like 99.9%.

Thanks, Philips.



[top]

Thursday, 20 April 2006

[Daynotes Forums]    [Last Week]   [Mon]  [Tue]  [Wed]  [Thu]  [Fri]  [Sat]  [Sun]   [Next Week]    [HardwareGuys Forums]

09:51 - One of the annoying things about writing PC hardware books is that hardware and software comes and goes so quickly. For a while, Barbara and I had a running joke that our endorsement of a product was the kiss of death. It happened repeatedly. We'd recommend a product, such as the OnStream series of tape drives, only to find that the company had entered bankruptcy, often between the time we submitted the final manuscript draft and the time the book hit the stores.

I'm working on the media center PC for the new edition of Building the Perfect PC right now. I've been looking at various PVR applications, such as BeyondTV, Sage, MythTV, and so on. In the first edition of the book, we looked at MyHTPC. We found a lot to like, but concluded that it wasn't quite ready for prime time. In the time since then, there's been a lot of development on the software, and it was released as a commercial product from a company named Meedio. It looks a lot like Microsoft Windows Media Center Edition, but is more featureful, less encumbered by DRM, and much more configurable. We planned to recommend it (with several competing products) to people who wanted to run Windows on their media center boxes.

I'd done a nice write-up of Meedio Pro, with screen shots, details about its features, and so on. Then yesterday I went back to the Meedio site and found only an announcement that Meedio is no more. It's been bought by Yahoo, and the Meedio software is no longer available or supported. The electronic program guide stops working on 1 July, so anyone who's bought Meedio is screwed.

There's probably a lesson here. In one sense, the loss of Meedio is no big deal. Many competing products remain available, and some of them are quite good. At least one of the good ones, GB-PVR, is also free-as-in-beer, although not open source. But all of those products share a common drawback. If the company goes out of business or decides to discontinue the product, its users are stuck. It's quite possible they'll need to strip their systems down to bare metal and start again from scratch.

That doesn't happen with open-source applications like MythTV, at least projects that have a large and active community. If the original project leader abandons the project or gets run over by a truck, others will continue the project. If the original project leader starts taking the application in directions that the user base doesn't like, someone will fork the project. No matter what, the risk of users being abandoned is very small.

When we looked at MythTV in the first edition of the book, we concluded that it wasn't yet ready for prime-time. We haven't looked at MythTV lately, but we plan to do so. Just a quick perusal of the feature list tells us that things have changed a lot in the last couple years. And Linux is much, much easier to install and configure than it was a couple years ago, so it's quite possible that MythTV is a practical choice nowadays even for non-Linux folks. We'll have to see.


12:38 - This from Mark Huth:

From:    Huth Mark
To:      Robert Thompson
Subject: web pages
Date:    Thu, 20 Apr 2006 09:00:16 -0700  (12:00 EDT)

Bob,

This is an odd comment.  As you know, I’ve been reading your web pages for a long time and have never been critical of the pages themselves.  Now I find that the backgroup, the fine mottling you use as a background makes it difficult to read the pages.  Of interest, this doesn’t seem to have anything to do with my eyes, but may well have something to do with the use of high resolution LCD monitors!  I tried a little experiment, I looked at your web pages on my desk lcd’s and then went down the hall to use a much older and smaller CRT.  It seemed much less distracting and was much easier to read the text on the CRT.  I then got a couple of partners, one nurse, and two medical assistant to look at the pages (partners older, nurse and medical assistants MUCH younger).  All agreed that the text was very hard to read on the LCD and much easier on the CRT. 

Possible conclusions…..give up reading the web page, throw away the lcd?, ask Thompson to take a look at it and see if he can figure it you.

Grin,

mark 


That is interesting. I'm looking at my page right now on a 19" Samsung LCD, which has very high brightness and contrast, and the background is so unobtrusive it almost disappears. Years ago, I used a flat white background (255,255,255), but that seemed a bit glaring. I started using the background image to tone things down a bit. I'll ask my other readers what they think. Perhaps I should just drop the background image and return to using a pure white background.

So, what does everyone else think? Post your thoughts on the messageboard.


[top]

Friday, 21 April 2006

[Daynotes Forums]    [Last Week]   [Mon]  [Tue]  [Wed]  [Thu]  [Fri]  [Sat]  [Sun]   [Next Week]    [HardwareGuys Forums]

08:43 - Paul Thurrott, whom no one could accuse of being anti-Microsoft or anti-Windows, has just issued a scathing indictment of Microsoft and Vista. From the article:

"Since the euphoria of PDC 2003, Microsoft's handling of Windows Vista has been abysmal. Promises have been made and dismissed, again and again. Features have come and gone. Heck, the entire project was literally restarted from scratch after it became obvious that the initial code base was a teetering, technological house of cards. Windows Vista, in other words, has been an utter disaster. And it's not even out yet. What the heck went wrong?"


In fact, the situation is worse than even this article portrays. By the traditional definition, feature completeness, Vista is not yet even in alpha. The OS is fundamentally broken, primarily because the new DRM features that Microsoft has embedded so deeply in Vista simply do not work. Microsoft is pulling out all the stops to ship something--anything--it can call "Vista" by the currently-promised February 2007 release date, but I think it's very unlikely that it will meet that date. Summer 2007 is more likely, and even then I expect the first release of Vista to be disastrously bad.

Meanwhile, Linux just keeps chugging along.


[top]

Saturday, 22 April 2006

[Daynotes Forums]    [Last Week]   [Mon]  [Tue]  [Wed]  [Thu]  [Fri]  [Sat]  [Sun]   [Next Week]    [HardwareGuys Forums]

00:00 -



[top]

Sunday, 23 April 2006

[Daynotes Forums]    [Last Week]   [Mon]  [Tue]  [Wed]  [Thu]  [Fri]  [Sat]  [Sun]   [Next Week]    [HardwareGuys Forums]

00:00 -



[top]

Copyright © 1998, 1999, 2000, 2001, 2002, 2003, 2004, 2005, 2006 by Robert Bruce Thompson. All Rights Reserved.".

I have fought this problem too long and need real help for not only myself, but for the rest of the folks going through this problem!

If any is ready to solve the problem, I would greatly appreciate it.

Stan R. McLaughlin
[email]one_hiq@yahoo.com[/email]
713-464-3801
[http://off-site.selfip.com](http://off-site.selfip.com)

Thanks!

---

### Post by macdo on 2006-05-18
Please tell me you overquoted by accident :-D

macdo

---

### Post by nalmeth on 2006-05-18
I've wasted not even a matter of minutes with samba configuration.

The only problem I've had with samba is to blame on my setup with multiple routers, samba not being able to see shares on the other router.

---

### Post by Mr Fat Bat on 2006-05-18
I remeber when it used to take hours to get Samba working but with Breezy and Dapper i've spent almost zero time getting it to work.

---

### Post by rahelvey on 2006-05-18
actually samba detected and I share files no hassel at all.

---

### Post by joshrobinson on 2006-05-18
[QUOTE=rahelvey]actually samba detected and I share files no hassel at all.[/QUOTE]

i did no configuring whatsoever.. execpt to add smbusers for my windows laptop (that someone uses to listen to music through my ubuntu server box)

before when i used suse i was editing config files all day to get things to work

---

