---
title: "Terminal Service ala Citrix: choice of server"
date: 2012-04-10
forum: Any Other OS
---

### Post by futura84 on 2012-04-10
I've set up a terminal-service like computer in my environment, using XRDP ( [http://www.xrdp.org/](http://www.xrdp.org/) , which uses a VNC-type of remote desktop rendering) and an Ubuntu derivative based on LXDE, Peppermint ([www.peppermintos.com]("http://www.peppermintos.com")). Simple thin-client pc's connect to this setup. This is all up and running in a satisfactory manner, however, I would like to move this installation to a proper server, preferably an Intel XEON or AMD Phenom based one. However, I have some questions, and although the requirements of my ideal setup fall somewhat in the middle of a true ubuntu server and an extended desktop environment, I think that some of you might be able to help me out. 
 
The issue is, that the server incorporates all user's desktop environments, preferably with the ability to run multiple desktop environments per user (i.e. each user holds his desktop-switch ability with 2, 3 or 4 desktops per login). I am unaware of the strain multiple desktops has on one's videocard abilities and performance, and seeing that most professional server's are not equipped with a high-end videocard, I would like to have some pointers as to which videocard you would deem appropriate for:
 
-allowing a maximum of 25 users render at least one desktop;
-possibly allow the same number of users render a desktop environment with desktop-switch capabilities. 
 
Again, I am unsure about the strain when allowing for the possibility of running 4 concurrent desktop screens per user, as one would normally  be able to do when logging in to a "fat" client environment (i.e. one user per cpu/videocard). I have been conservative with regards to this issue allready, I think, by incorporating the LXDE X11 environment. I would still very much appreciate any helpful tips and pointers with regards to installing an actual server environment.
 
A second but interrelated question: I've chosen PeppermintOS, which is a fork of Linux Mint, which in turn is a fork of Ubuntu, beceause it suits my environment. Am I, however, correct to assume that either of these OS's is suited in harnessing the potentional of professional server hardware, like an Intel XEON based platform, in terms of load balancing and using the full potential of multi-core cpu's? I would assume that these things are handled from within the Linux kernel itself, which is pretty similar across forks, but would appreciate confirmation on this issue. Thank you.

---

### Post by MG&amp;TL on 2012-04-10
> The issue is, that the server incorporates all user's desktop environments, preferably with the ability to run multiple desktop environments per user (i.e. each user holds his desktop-switch ability with 2, 3 or 4 desktops per login). I am unaware of the strain multiple desktops has on one's videocard abilities and performance, and seeing that most professional server's are not equipped with a high-end videocard, I would like to have some pointers as to which videocard you would deem appropriate for:

Not much-my videocard & CPU are fairly rubbish, but 8 virtual desktops running simultaneously does not put much of a dent in performance. 
 
 
> A second but interrelated question: I've chosen PeppermintOS, which is a fork of Linux Mint, which in turn is a fork of Ubuntu, beceause it suits my environment. Am I, however, correct to assume that either of these OS's is suited in harnessing the potentional of professional server hardware, like an Intel XEON based platform, in terms of load balancing and using the full potential of multi-core cpu's? I would assume that these things are handled from within the Linux kernel itself, which is pretty similar across forks, but would appreciate confirmation on this issue. Thank you.

All of Lubuntu (Ubuntu with LXDE), Mint LXDE, and Peppermint will manage absolutely fine. The difference is that Ubuntu will likely recieve upstream updates faster, as it is based on Debian, which actually does the packaging from upstream. Distributions "downstream" will take a little longer to receive updates.

Linux is one of the most popular operating systems for servers-I daresay it can manage the hardware. :)

As for the actual load requirements, I would suggest you measure the requirements on your current machine, and see what that can cope with, then multiply that by the specs of your proposed machine.

---

### Post by futura84 on 2012-04-10
This is valuable information, thank you. It raises the following question with me, however. I am currently looking at two main possibilities of installing a server environment. As we are on a little bit of a budget, and a new Xeon or Phenom server is a bit too steep atm at around 2000 usd, I would like to run the following options passed you:
 
- a second hand Xeon or Phenom server, at around 750-1000usd. Bear in mind that this will probably have been running at a company for some years already: I am a little unaware of the remaining lifespan of moving parts in these machines, such as the hard disks (many companies offer these second hand machines with the original SAS-scsci  drives, which ofcourse are quite impressive to work with, but if they have been  running for 3-5 years at 15000rpm, I'm a little concerned about their mileage). Mainboard, memory and cpu I am not afraid of. Biggest plus of this setup would be, that most servers are equipped with nice backup features, such as multiple PSU's, extensive hardware RAID possibilities, and a general purpose-built server quality.
 
- a brand new high performance desktop pc, installed as a server. Would also set me back around 750-1000usd, and would be equally well suited, however, I was always teached that consumer IT products are not particularly well suited for multiple concurrent sessions (not afraid of this issue), and suffer from the fact that they are not designed for running 24/7 for, say, 3-5 years on end (AM afraid of this!). If I recall correctly, the latter has to do with the electronic components themselves, which are of higher quality and can handle more strain on professional server equipment. 
 
Ofcourse, concerns about option one in terms of hard-disk mileage could be mitigated by opting for new drives; which makes the question boil down to: server grade equipment, be it second hand (partly) new, or not?

---

### Post by MG&amp;TL on 2012-04-10
I honestly couldn't tell you-not a hardware person I'm afraid. 

However, do remember that it is entirely possible to replace everything inside a server/computer, especially the moving parts. Disks, I imagine, should be no problem. I suppose it really depends on how much of a problem a failed disk would cause in your workplace. 

FWIW, on my desktop, which is also a server (LAMP, for mucking about with), I've had three failed hard disks, but nothing else has failed since I got it in 2004.

What sort of applications will your users run (for the benefit of those more experienced than I)?

---

### Post by futura84 on 2012-04-10
Absolutely nothing demanding; I guess LibreOffice would be the most resource intensive application, next to some applications running through Wine (again nothing demanding, as most of these programs are only frontends for the "real" applications, running on their dedicated servers in my network). 
 
The basic idea was/is to unify the desktop experience accross workplaces; I've recently switched to a "desk-less" working environment for my employees. They can roam around the office freely, and take a seat at any thin-client they like. Because I have both a front desk, for customers coming by, and a back-office, for general administrative functions, but all my employees both help customers as well as do these administrative tasks; and additionaly, because most of the programs I use use login credentials, so I can monitor which employee has done exactly which task (i.e. which records each one has added to SQL databases, which documents were appended etc.); I wanted to have the opportunity for each employee to have his own desktop "follow" him around the office, instead of using a fixed login/account on each specific pc; and which would facilitate me in always knowing who is logged onto the system, where, and with what specific applications running. 
 
I think what you are hinting at, in terms of HD choice, is: just get the biggest bang for your wallet's buck; and a new SSD would be that. Actually, all my employees store their files on a network fileserver, which is completely independent of the OS; I do not need an extensively big HD to accomodate their files. As a matter of fact, the server would be more of an application server in the traditional sense, just with the added ability of being capable of providing user desktops through a terminal-service-like protocol. Allowing for the occasional backup of that SSD on a regular Sata HD would be enough to allow for an easy hot-swap in case of system failure.
 
Thank you for sharing your thoughts on this matter with me, it reaffirms my idea that ultimately, opensource IS better :).

---

### Post by Perfect Storm on 2012-04-10
Moved to Other OS/Distro Talk.

---

### Post by MG&amp;TL on 2012-04-10
> **futura84 said:**
> Absolutely nothing demanding; I guess LibreOffice would be the most resource intensive application, next to some applications running through Wine (again nothing demanding, as most of these programs are only frontends for the "real" applications, running on their dedicated servers in my network). 
 
The basic idea was/is to unify the desktop experience accross workplaces; I've recently switched to a "desk-less" working environment for my employees. They can roam around the office freely, and take a seat at any thin-client they like. Because I have both a front desk, for customers coming by, and a back-office, for general administrative functions, but all my employees both help customers as well as do these administrative tasks; and additionaly, because most of the programs I use use login credentials, so I can monitor which employee has done exactly which task (i.e. which records each one has added to SQL databases, which documents were appended etc.); I wanted to have the opportunity for each employee to have his own desktop "follow" him around the office, instead of using a fixed login/account on each specific pc; and which would facilitate me in always knowing who is logged onto the system, where, and with what specific applications running. 
 
I think what you are hinting at, in terms of HD choice, is: just get the biggest bang for your wallet's buck; and a new SSD would be that. Actually, all my employees store their files on a network fileserver, which is completely independent of the OS; I do not need an extensively big HD to accomodate their files. As a matter of fact, the server would be more of an application server in the traditional sense, just with the added ability of being capable of providing user desktops through a terminal-service-like protocol. Allowing for the occasional backup of that SSD on a regular Sata HD would be enough to allow for an easy hot-swap in case of system failure.
 
Thank you for sharing your thoughts on this matter with me, it reaffirms my idea that ultimately, opensource IS better :).

I'm not going to open the HDD/SSD can of worms...;)

Well, I can't think a graphics card would be especially necessary, but a good CPU would be useful considering there's going to be a lot of users...that sounds like an epic workplace.

You seem to have your backup well-planned, so that worry's dealt with-I'm not an expert; but I think either choice will work well considering your (extensive) knowledge, although I personally might lean towards a good-quality second-hand server.

No problem, I hope I haven't made any mistakes. :)

---

