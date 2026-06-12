---
title: "FreeBSD friendliness"
date: 2008-02-25
forum: BSD
---

### Post by HuBaghdadi on 2008-02-25
Hi.
Ubuntu came bundled with GNOME, FreeBSD has the option of installing GNOME too.
How both of them could be differ in terms of friendliness?
(yes I know, they are different OSs)
Thanks.

---

### Post by agim on 2008-02-25
From my experience with linux. Ubuntu seems to have the best hardware support. Since many people (myself included) consider hardware configuration to be the biggest pain in the a$$, I would say Ubuntu is much more beginner friendly.
I have heard that FreeBSD can be very hard to get completely up and running, especially on a laptop, so if that's what you are using, I would go with Ubuntu. If you really want to use FreeBSD, check out DesktopBSD or PCBSD. They are FreeBSD with a more noob friendly interface.

---

### Post by HuBaghdadi on 2008-02-25
DesktopBSD and PC-BSD both use KDE as the desktop manager, so Kubuntu do.
If both OS could use the same desktop manager, why Ubuntu is frienlier? 
Sorry, but I'm trying to know the difference.
Appreciate your help.

---

### Post by agim on 2008-02-25
Sure, no problem. FreeBSD is a little harder in part because the developers are much more interested in making a stable server than a stable desktop. They don't worry as much about things like laptop wireless compatibility, or a consistent hardware naming scheme, as Ubuntu does. 
In Ubuntu (linux in general) you're wireless card will me named wifi0. Whereas in FreeBSD it would be ath0 for an atheros card, and another name for another card, making it slightly less homogenous.
Another plus for Ubuntu is Synaptic and apt-get/aptitude. I have heard a lot of people say it is one of the easiest and most functional package managers out there, if note the easiest.
And finally, Ubuntu has a gigantic community, and a large, well-funded company behind it, all trying to make it the absolute best free desktop OS in the world.

As a beginner, I would suggest you have the Ubuntu base (gnome) desktop installed, you can install others as well, but most help (tutorials, previous posts) is geared toward the gnome version. I currently have Gnome, Kde-Core, Xfce, and Enlightenment set up, so don't be afraid to expiriment.

---

### Post by deepclutch on 2008-02-25
did anyone mentioned that bsd's wont install on anything other than primary partitions? ;) donno why,but logical partition support is called as an "ugly hack invented by intel" by bsd`ians.(dont ask me the source)

---

### Post by mips on 2008-02-26
> **deepclutch said:**
> did anyone mentioned that bsd's wont install on anything other than primary partitions? ;) donno why,but logical partition support is called as an "ugly hack invented by intel" by bsd`ians.(dont ask me the source)

Thats because they would only support a maximum of 4 primary partitions which in all honesty really is not much. BSD's need their own slice of the drive in which it creates it's own partitions without the restrictions of 4 primary partitions.

---

### Post by yabbadabbadont on 2008-02-26
Sounds pretty much like creating logical partitions within an extended partition...  oh wait, it is.  :D

(even if the partition ID number is not 5, functionally, it is the same)

---

### Post by justin whitaker on 2008-02-27
> **agim said:**
> Sure, no problem. FreeBSD is a little harder in part because the developers are much more interested in making a stable server than a stable desktop. They don't worry as much about things like laptop wireless compatibility, or a consistent hardware naming scheme, as Ubuntu does. 
In Ubuntu (linux in general) you're wireless card will me named wifi0. Whereas in FreeBSD it would be ath0 for an atheros card, and another name for another card, making it slightly less homogenous.
Another plus for Ubuntu is Synaptic and apt-get/aptitude. I have heard a lot of people say it is one of the easiest and most functional package managers out there, if note the easiest.
And finally, Ubuntu has a gigantic community, and a large, well-funded company behind it, all trying to make it the absolute best free desktop OS in the world.

As a beginner, I would suggest you have the Ubuntu base (gnome) desktop installed, you can install others as well, but most help (tutorials, previous posts) is geared toward the gnome version. I currently have Gnome, Kde-Core, Xfce, and Enlightenment set up, so don't be afraid to expiriment.

Take a look at this interview over at ONLamp:

[http://www.onlamp.com/pub/a/bsd/2008/02/26/whats-new-in-freebsd-70.html?page=1](http://www.onlamp.com/pub/a/bsd/2008/02/26/whats-new-in-freebsd-70.html?page=1)

Among other things, the FreeBSD devs have been working on wireless, the sound architecture, threading...overall, there are alot of improvements not only for the servers, but for desktops as well. 

As for community...well, the BSD community is large as well, and they aren't as fragmented as Linux-FreeBSD, OpenBSD, PC-BSD, are all flavors of the same basic code base, so there is a lot more compatibility between them. Try that with Ubuntu and SuSE, for example. 

Package management is not a competitive advantage. All package managers do the same thing, and some do it better than others. I agree that APT is pretty good, but there are arguments to be made for the Ports system as well. 

But getting FreeBSD running can be tricky, as others have noted. 

I don't disagree with you about Ubuntu vs. FreeBSD, but it's not as cut and dried as you make it out to be, particularly if you consider Ubuntu v. PC-BSD.

---

### Post by the8thstar on 2008-03-16
You may find some useful information here on FreeBSD.org in regards to hardware support and compatibility: [http://www.freebsd.org/releases/7.0R/announce.html]("http://www.freebsd.org/releases/7.0R/announce.html")

Just a thought. :)

---

### Post by ibutho on 2008-04-12
> **HuBaghdadi said:**
> Hi.
Ubuntu came bundled with GNOME, FreeBSD has the option of installing GNOME too.
How both of them could be differ in terms of friendliness?
(yes I know, they are different OSs)
Thanks.
I use FreeBSD as my main desktop OS and I personally don't believe that FreeBSD is hard. You just need a little patience to master it becuase the developers tend to leave most of the configuration to you the user and you don't get nifty GUI environments right from the start meaning that you should be comfortable working in the CLI or via an ncurses interface, during the installation and initial configuration of the system. This sometimes scares of some newbies, if they are used to being presented with a distro or OS with a pre-configured GUI environment and they don't work much in the CLI.

FreeBSD has more or less the same number of packages as Ubuntu (if not more in the ports collection) and you have the option of using their prebuilt packaging tools (which work in a similar way to apt/aptitude) or by building package from source in their ports collection. I have never really found hardware support to be much of an issue, but then again I don't always get the latest and greatest. Many wireless cards are supported and if they are not, you can use the Windows drivers via ndis which is similar in some way to ndiswrapper.

---

### Post by jnbek on 2008-04-12
I agree, FreeBSD isn't hard once you get the idea behind it. I can install and have a running FreeBSD desktop just as fast, if not faster, than Ubuntu. I am forever indebted to FreeBSD because I got to learn the inner workings of a UNIX system, not because I had to, but because the option to tweek everything with vim was there and available. All user installed config files go in /usr/local/etc/ so I could start there. In the years since I started using FreeBSD the versions have improved milestones in hardware detection, X setup, and overall portability. One of my favorite features if you will of FreeBSD, is, you can install any version from 5.3 and higher, then upgrade to whatever version is newest whether in your version tree or the latest, greatest, and hottest CURRENT tree. FreeBSD baby, It's the hidden treasure.

---

### Post by stream303 on 2008-04-18
When I first tried FreeBSD back in the 4.x days, what struck me as being friendly was finding that the "EE" editor was included in the stock installation for those of us who didn't know vi.  Although I knew vi somewhat at the time, it made it a great help when trying to get your friend's machine up and running - especially over the phone when they didn't know vi.  That small touch of thoughtfullness made me like FreeBSD from then on.

I also like the ncurses based sysinstall utility, which got used even after installation - it really helped me out when I was trying to grok the commandline.

Back then, all other distros, Linux included, seemed to force users to learn vi before they could get up and running as some sort of rite of passage.

If they thought enough about including the EE editor, I thought that surely they had the end-user in mind and so I was hooked forever more.

---

