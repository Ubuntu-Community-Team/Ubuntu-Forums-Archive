---
title: "Ubuntu as Windows replacement"
date: 2007-05-06
forum: Absolute Beginner Talk
---

### Post by DrScum on 2007-05-06
today I  installed Ubuntu 7.04 on my Dell Laptop here a summary of my experiences.

the install stopped at the point where the hd partitioning should take place with an error message like partition blablabla could not be created on hda.

Tried all three options available in the installer no success.

Had to use GNOME partition editon 0.3 to manually create and format a primary and a swap partition

Other than that installation went smooth.

After install tried to configure the 3Com wireless card. No success, ergo no Internet connection.
Tried to run a DVD with totem, error message: can't run the DVD since the necessary plugins are not installed.

So much for Ubuntu being a desktop oriented OS aiming at the general Windows user with no deep computer knowledge and putting the user into a position to just run the install and use the system.

I would be glad if someone could help me to get at least the network card running.

It's a 3Com OfficeConnect Wireless 11a/b/g PC Card 3CRWE154A72 Version 1.0

---

### Post by srt4play on 2007-05-06
> So much for Ubuntu being a desktop oriented OS aiming at the general Windows user with no deep computer knowledge and putting the user into a position to just run the install and use the system.

Windows doesn't have to be configured at all?  That's news to me.  Despite this unnecessary comment of yours, you will find the folks here will look past it and still try to help you.

After some google.com/linux searching on 3CRWE154A72, it seems like it's going to take downloading the lastest madwifi drivers from sourceforge.net to get that card to work.

Good luck.

---

### Post by DrScum on 2007-05-06
Well, the comment may seem unnecessary to you but it's just the experience I had.

Regarding you driver advice. My problem is that I don't know how to install drivers in Unbuntu. I did try to solve the problem myself but I just don't know enough. I thought I was in the absolute beginners section of the forum and I thought somebody might have a hint.

But one needs to be put in place once in a while, it makes you humble.

Good luck to you too!

---

### Post by Nythain on 2007-05-06
i dont know what magical windows release you were/are using... but i havent gotten XP to recognize ANY wireless card out of the box... wich many distro's of linux have been able to do for me over the years... granted with any NEWER hardware you are gonna need to find the appropriate drivers for with any OS, thats just a fact of life.

As for the DVD playback and video/multimedia in generall... once again, windows has never quite gotten any of that right for me "out of the box" either... in fact the only way i play half my videos in windows is to pirate copies of media codec packs wich are usually virus infested and cause more crashes than play videos... 

Ubuntu doesnt support certain things "out of the box" for legal and FREE reasons... but thats all easily remedied with a little patience... much easier than than in windows usually. Ubuntu = sudo aptitude install w32codecs... windows = hunt down a decent codec pack, hope and pray it doesnt nuke my system, live with random crashes for the rest of my experience.

If dvd playback and mp3 playback are your main concerns, there are other debian based distro's that support this out of the box, like mint (i believe)

As for the driver issues... what are the instructions, and what are your complications, and we can help... im not familiar with your card exactly, but if you give us something to work with we can give you the advice/help you need

---

### Post by bobplano on 2007-05-06
you have to unpack it and then most likely use make. you'll need gcc, cpp, build-essentials, and linux-headers which you can get from [www.packages.ubuntu.com](www.packages.ubuntu.com) if you don't have internet for ubuntu. as for the windows replacement, nothing can really replace windows without being windows, so ubuntu isn't trying to do that, its just an OS that is stable and, for me, fun to use

---

### Post by ticopelp on 2007-05-06
I understand your frustration, but writing off the entire OS because one piece of hardware doesn't work out of the box is a pretty poor attitude to take, IMHO. 

It might also help to keep in mind that Ubuntu is not supported by a massive corporation, but by a community of users, and is provided free of charge to users. I think a certain amount of do-it-yourself is a fine trade-off for that, personally. 

Installing things using make is not that difficult -- many source code downloads include a readme file and instructions -- I'm a relative noob when it comes to compiling things, and I managed to get a program running from source a couple of days ago. It just takes some patience, as a user above said. And there are people here willing and able to help. Best of luck.

---

### Post by jfinkels on 2007-05-06
Welcome to Ubuntu!

It looks like you're going to need the madwifi drivers. If you need help with them, I would suggest making a new thread in the Wireless & Networking section. Also, try searching the forums to see if anyone else with your wireless card has already got it set up and working.

Here's a site that describes how to install anything on Ubuntu: [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

I think there are madwifi-tools in the Ubuntu repositories, so you may be able to install them like this (after enabling the "universe" repository in "System > Administration > Software Sources"):
```
sudo aptitude install madwifi-tools
```

Oh and here's a great site, the Ubuntu Document Storage Facility. [http://doc.gwos.org/](http://doc.gwos.org/) It has lots of info on hardware compatibility. I found this page which has some (outdated :P) information on the MadWifi driver [http://doc.gwos.org/index.php/MadwifiDriver](http://doc.gwos.org/index.php/MadwifiDriver)

---

### Post by ABCgang on 2007-05-06
I think part of the frustration with us new linux users is that we don't know what "unpack" or "make" means, or what gcc, cpp, build-essentials, and linux-headers mean, much less where to go to accomplish these things.  

We're asking these questions in the "absolutely beginner talk" forum, but some of the responses to our questions appear to zoom over our heads.  I own three computers, have installed/downloaded software, removed malware, replaced hardware and I still have a hard time understanding how to download or update something to ubuntu.  I only found out yesterday where to open a terminal - lol.  From where I'm coming from (and apparently a lot others in this forum asking for help), Windows XP is simple compared to ubuntu.  

With that said, I feel ubuntu could be a powerful OS, if I only understood it better. JMO

---

### Post by ticopelp on 2007-05-06
> **ABCgang said:**
> I think part of the frustration with us new linux users is that we don't know what "unpack" or "make" means, or what gcc, cpp, build-essentials, and linux-headers mean, much less where to go to accomplish these things.  

We're asking these questions in the "absolutely beginner talk" forum, but some of the responses to our questions appear to zoom over our heads.  I own three computers, have installed/downloaded software, removed malware, replaced hardware and I still have a hard time understanding how to download or update something to ubuntu.  I only found out yesterday where to open a terminal - lol.  From where I'm coming from (and apparently a lot others in this forum asking for help), Windows XP is simple compared to ubuntu.  

With that said, I feel ubuntu could be a powerful OS, if I only understood it better. JMO

I completely sympathize with you. I've been using Linux on and off for years, but always ended up going back to Windows because I couldn't get Linux to do what I wanted, felt the learning curve was too high for me, and just generally had a difficult time of things. 

For me, Ubuntu is a huge leap in usability and user-friendliness compared to any other Linux distro I've seen (the last ones I used were Mandrake 10 and Knoppix, which were OK, but still didn't feel "ready" to me). Ubuntu is incredibly user-friendly, but it is not Windows, and, no matter how friendly and helpful the user community, probably should not be held to the same expectations as Windows. I think it's too easy to get frustrated when you come into a new operating system expecting it to behave just like an old one.

There is definitely a learning curve involved with Ubuntu, and to be happy with it I think certain habits need to be broken. One enormous plus with Ubuntu is a fantastically helpful and thorough user community -- there hasn't been a single problem I've had that I haven't been able to solve within a few minutes of searching on these forums. 

I totally know where you're coming from in terms of a lot of this stuff seeming confusing -- but learning new things, and taking control of your computer (the way you often can't with Windows) can be a very fun thing. Think of it as building your own vehicle from scratch instead of taking the bus everywhere. Sure, there might be a lot to do, depending on what equipment you have at hand, but when it's done, it will be running the way YOU want it.

Again, I really hear what you're saying -- I was a complete dunce with Linux when I first started. Command line? Terminal? Ga-huh? It gets better, trust me. :)

---

### Post by jfinkels on 2007-05-06
> **ABCgang said:**
> I think part of the frustration with us new linux users is that we don't know what "unpack" or "make" means, or what gcc, cpp, build-essentials, and linux-headers mean, much less where to go to accomplish these things.  

We're asking these questions in the "absolutely beginner talk" forum, but some of the responses to our questions appear to zoom over our heads.  I own three computers, have installed/downloaded software, removed malware, replaced hardware and I still have a hard time understanding how to download or update something to ubuntu.  I only found out yesterday where to open a terminal - lol.  From where I'm coming from (and apparently a lot others in this forum asking for help), Windows XP is simple compared to ubuntu.  

With that said, I feel ubuntu could be a powerful OS, if I only understood it better. JMO

It's true, we can give advice that goes over new users' heads. To err is human. :\ Fortunately it's a team effort. :D Eric S. Raymond says, "With enough eyes, all bugs are shallow." The idea is a large community works better than just one person.

Here's something to think about, though. If you sat a hermit who had never used a computer before in front of a Windows computer, would it really be "simple", simpler than Ubuntu? As it turns out, we've just been brainwashed by living in a Windows-centric society!

Which is easier, typing "sudo aptitude install GIMP" or go to CompUSA, buy Adobe Photoshop, bring it home, put the disc in your computer, open Windows explorer, find the install.exe executable file, click through a bunch of licensing agreements, etc.?

btw, for lots of good information on how to efficiently get help, take a look at the link in my signature :D And as always, post in the forums if you need ANYTHING.

---

### Post by Mr.Beast on 2007-05-06
> **DrScum said:**
> today I  installed Ubuntu 7.04 on my Dell Laptop here a summary of my experiences.

the install stopped at the point where the hd partitioning should take place with an error message like partition blablabla could not be created on hda.

Tried all three options available in the installer no success.

Had to use GNOME partition editon 0.3 to manually create and format a primary and a swap partition

Other than that installation went smooth.

After install tried to configure the 3Com wireless card. No success, ergo no Internet connection.
Tried to run a DVD with totem, error message: can't run the DVD since the necessary plugins are not installed.

So much for Ubuntu being a desktop oriented OS aiming at the general Windows user with no deep computer knowledge and putting the user into a position to just run the install and use the system.

I would be glad if someone could help me to get at least the network card running.

It's a 3Com OfficeConnect Wireless 11a/b/g PC Card 3CRWE154A72 Version 1.0

Hi DrScum,  Welcome to Ubuntu.
I know where you are coming from.  I also feel that Ubuntu is touted as the distribution that is more like windows, or perhaps I should have said the linux distro for windows users.
Whilst I haven't gone out of my way to try other distro's of linux I would say that it certainly is the closest I have come across. However over the 15-20 years of Windows, pleople have just got used to working in a certain way, and doing things in a certain way.
Also manufacturers have got away with writing software to make their hardware work with just different versions of windows.
Until this last section changes it's alway going to be an uphil struggle to get some things working under any other operating system (In fact, Microsofts vista is so radically different in some areas that some manufacturers are struggling with this os as well!)
It's true that you dont just run setup.exe under ubuntu.  And there are qirks that you will come across that may have you fuming, but the same was said at each generation of MS's o/s so I think that this is more about change and what you are used to.
I'm afraid that I can't help on either of your issues, I just don't know enough yet about what may be the problem under the hood. But It sems to me that wireless is a big problem out the box.
Comparing this to windows, even XP would have this problem but the difference is that you know that on the CD you got with the hardware you can run setup.exe and everything will then work. 
What I would suggest (to anyone with a wireless problem) is how feasible is it to get ubuntu up and running with a wired connection.  Does your router have hard wired ports at the back, if so, then go for that as a temporary measure until you can get the wireless working.

I hope you keep on with ubuntu, as once it's up and running it does seem more stable, and certainly nippier than XP fully patched with the same protection level. (Vista, hah! don't even think about it until there are more device drivers out there and I'd probably say wait for SP1.)

---

### Post by Wiebelhaus on 2007-07-07
> **DrScum said:**
> Well, the comment may seem unnecessary to you but it's just the experience I had.

Regarding you driver advice. My problem is that I don't know how to install drivers in Unbuntu. I did try to solve the problem myself but I just don't know enough. I thought I was in the absolute beginners section of the forum and I thought somebody might have a hint.

But one needs to be put in place once in a while, it makes you humble.

Good luck to you too!


what the.....

you sound like a prick.

---

### Post by ukripper on 2007-07-07
> **DrScum said:**
> Well, the comment may seem unnecessary to you but it's just the experience I had.

Regarding you driver advice. My problem is that I don't know how to install drivers in Unbuntu. I did try to solve the problem myself but I just don't know enough. I thought I was in the absolute beginners section of the forum and I thought somebody might have a hint.

But one needs to be put in place once in a while, it makes you humble.

Good luck to you too!

Have you tried Ubuntu Guide ?

---

### Post by djvictor on 2007-07-07
you winblows users want everything done for you, quit bein lazy....

---

### Post by macogw on 2007-07-07
> **ABCgang said:**
> I think part of the frustration with us new linux users is that we don't know what "unpack" or "make" means, or what gcc, cpp, build-essentials, and linux-headers mean, much less where to go to accomplish these things.  

build-essential, linux-headers, gcc, etc aren't things you accomplish.  The person said to get them at packages.ubuntu.com, so do that.  When you click to download them, it'll ask if you want to use GDebi package installer to install them.  Tell it yes.

---

### Post by ugm6hr on 2007-07-07
> **DrScum said:**
> I would be glad if someone could help me to get at least the network card running.

It's a 3Com OfficeConnect Wireless 11a/b/g PC Card 3CRWE154A72 Version 1.0

I'll try and keep this simple.

This card should work in Ubuntu7.04, with a little nudge.

Check the result of this:
Open Terminal (Applications->Accessories->Terminal) and type:
```
lspci
```
I anticipate the reply should contain something like:
```
Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
```

If so, there are a multitude of potential solutions:
[http://ubuntuforums.org/showthread.php?p=2688436#post2688436](http://ubuntuforums.org/showthread.php?p=2688436#post2688436)
[http://ubuntuforums.org/showthread.php?t=38972](http://ubuntuforums.org/showthread.php?t=38972) (jaykay post)
[http://ubuntuforums.org/showthread.php?t=480778](http://ubuntuforums.org/showthread.php?t=480778)

If you don't have an ethernet connection to get online with Ubuntu, it might be a bit tricky.  Perhaps Wicd is the easiest option (but apparently not ideal):
[http://ubuntuforums.org/showthread.php?t=419348](http://ubuntuforums.org/showthread.php?t=419348) (start reading at post 9) 

PS: This forum is not staffed by Ubuntu / Canonical employees. We are users and give up our own time to help each other. If you want to complain about the product, please pay Canonical for the full support package, and complain to them.

---

### Post by ukripper on 2007-07-07
Don't know why some people are lazy and  want everything to be done for them. If you don't try you don't succeed.

---

### Post by Campingman on 2007-07-07
A bit harsh chaps, we have all been there frustrated and p*****d off.

I reckon he has sorted it now

[http://ubuntuforums.org/showthread.php?t=437226](http://ubuntuforums.org/showthread.php?t=437226)

---

### Post by Vague on 2007-07-07
> **DrScum said:**
> Tried to run a DVD with totem, error message: can't run the DVD since the necessary plugins are not installed.

So much for Ubuntu being a desktop oriented OS aiming at the general Windows user with no deep computer knowledge and putting the user into a position to just run the install and use the system.

I find it funny that this is brought up so much.  The "general Windows user with no deep computer knowledge" will probably find it easier to learn Ubuntu than a hardened Windows user, simply because they aren't as accustomed to doing things the Windows way.  My sister, who recently dumped Vista, has become almost as proficient in Ubuntu as she was in Windows in about a week.  It's really not that much harder, just different.  Also, I don't think I'm the only one who had plenty of trouble with DVDs in my fresh install of XP back in the day.

Anyway, I think this link might help with your DVD troubles:  [https://help.ubuntu.com/community/RestrictedFormats#head-e69e0c62de07b1e2b560c1ad6b68823328906067](https://help.ubuntu.com/community/RestrictedFormats#head-e69e0c62de07b1e2b560c1ad6b68823328906067)

Good luck in Ubuntu.  It can be hard at first, but it's easy once you get used to it.

---

