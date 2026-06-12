---
title: "A few questions"
date: 2007-12-08
forum: Absolute Beginner Talk
---

### Post by Computerwiz1990 on 2007-12-08
Ok, my friend told me about Linux and how it was free, but i never knew it would be this easy to get.

Anyway ive decided to probably get the free cd thing.

Ok so when i reboot my computer with the cd in, the computer will boot in linux? Or supposed to?
Then i choose view or preview and it will go to like a temporary version of the OS. Right? Then some how from that preview i can choose to install it on the harddrive. I would have to make a new partition on the drive to do that right?
Then when it is installed, will i still be able to boot back in windows?

And what about my windows pre installed programs, will i be able to use them AT ALL? Or would i be able to reinstall them useing/in the Linux OS?

Yeah, iam wanting to try this OS out and i just need some starting help.

---

### Post by santiagoward2000 on 2007-12-09
Hi and welcome!
> **Computerwiz1990 said:**
> Ok so when i reboot my computer with the cd in, the computer will boot in linux? Or supposed to? Then i choose view or preview and it will go to like a temporary version of the OS. Right?
Yes! You'll get a screen with some options, if you choose **"Start or install Ubuntu"** you'll get the full system running from the CD. You can use it as if it were installed (maybe a little slower).
> **Computerwiz1990 said:**
> Then some how from that preview i can choose to install it on the harddrive. I would have to make a new partition on the drive to do that right?
Then when it is installed, will i still be able to boot back in windows?
Yes, on the desktop you'll see an **Install** icon. If you open it you'll be able to install it, and it will even guide you if you want to partition your drive, to keep Windows, and configure GRUB, which allows you to choose if you want to boot to Ubuntu or Windows.
> **Computerwiz1990 said:**
> And what about my windows pre installed programs, will i be able to use them AT ALL? Or would i be able to reinstall them useing/in the Linux OS?
What programs do you mean? There are Linux versions for most programs (or a similar alternative), or you could use something like WINE to run others...
If you have any other questions just ask!
I hope you enjoy Ubuntu!

---

### Post by sports fan Matt on 2007-12-09
Excellent Post, imho, Santiago

Who knows you may get a sticky out of it..if I had the capability to, I would just so the same questions/form of questions get asked over and over

---

### Post by santiagoward2000 on 2007-12-09
> **sox fan Matt said:**
> Excellent Post, imho, Santiago

Who knows you may get a sticky out of it..if I had the capability to, I would just so the same questions/form of questions get asked over and over

Well, thanks! You made me blush :oops:
I'm just happy to help.

---

### Post by aysiu on 2007-12-09
If you're scared about partitioning your drive, and you have at least 512 MB of RAM, consider a virtual installation: [http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)

---

### Post by Computerwiz1990 on 2007-12-09
Programs like the games i have. Guild Wars, Full TIlt Poker. Would i be able to use those being installed already with windows, or would i have to reinstall them under LInux?

---

### Post by Computerwiz1990 on 2007-12-09
And my Dialup program. Toast.

---

### Post by Myglaren on 2007-12-09
> **Computerwiz1990 said:**
> Programs like the games i have. Guild Wars, Full TIlt Poker. Would i be able to use those being installed already with windows, or would i have to reinstall them under LInux?

They won't work in Linux.  You could likely run them in Wine or dual boot with Windows and run them there, no need for a reinstall.

I would go for the dual-boot option until you have become familiar and comfortable with Ubuntu.  If you have insufficient free space on your hard drive - and you don't want to squeeze the Windows too tight or you will incur problems with Windows, chuck a second hard drive in and use that for Ubuntu.  Doesn't need to be huge, a second hand 40Gig one would do fine, at least to begin with.

---

### Post by Myglaren on 2007-12-09
> **Computerwiz1990 said:**
> And my Dialup program. Toast.

It is ages since I had dial-up but at the time I was using '98 and SuSE in a couple of dual-boot machines.  Never a problem, it just found the modem, installed and used it.

If you have a Winmodem (software modem for the most part) then you have problems.

A USB external modem may be a better option although I have never used one with any flavour of Linux.  Good luck trying to get hold of a hardware modem these days unless someone has a second hand one for you.

---

### Post by Computerwiz1990 on 2007-12-09
Ok, how does Wine work and how do i use it or initialize it? And what about all the drivers on Windows, will they still work or whats gonna happen there?

---

### Post by satx on 2007-12-09
One of the reasons I enjoy Ubuntu so much is the Ubuntu community- always willing to assist the new and even the more experienced users when they encounter difficulties. I have yet to have an issue in Ubuntu where I cannot simply post a thread and have an almost immediate response. 

What Microsoft fails to remember is who their customers are. There is no Microsoft community that I am aware of where the customers (users) are so willing to lend assistance. 

I have a dual boot WIN XP/Ubuntu 7.10 system, but I can assure you that 99% of my time is spent in Ubuntu. With the exception of FlightSim X, I really have no need to use WIN XP or the Microsoft Apps- I have found Linux versions of everything I really need. I am exploring FlightGear as a sub for FlightSim X. 

The inventory of Linux programs is astounding and free. Having my system now tuned, I can explore all the inventory....so many programs- so little time (what a problem!).

I am only a nano-GParted away from divorcing WIN XP!

SATX

---

### Post by Computerwiz1990 on 2007-12-09
Can someone answer my above question please.

---

### Post by AngryMallard on 2007-12-09
The install CD will find most, if not all, of the drivers you need to run all of your hard ware. If something goes amiss, you can usually find a solution online.

As far as WINE goes for video games, you might look into a program called Cedega. It's specially built to play most video games. Although I haven't gotten it to work playing older Win98 games like FF7 yet, it'll play HalfLife and Starcraft and probably anything else modern.

---

### Post by satx on 2007-12-09
Try:
[http://www.vmware.com]("http://www.vmware.com")
[http://www.winehq.org]("http://www.winehq.org")

As to your question, wine sets up a directory in your home folder, and you install your programs to it.  The needed drivers install from the software install. Not all programs will run, however.

My solution: I used VMWARE to setup up a virtual XP installation under Ubuntu. Then I can switch back and forth within Ubuntu if I need to run a windows app. Please note however, that all 3D features of your video card will not be supported under VMWARE, although I can run my virtual XP at 1280 X 1024.

For VMWARE info go to:

[http://www.vmware.com]("http://www.vmware.com")

SATX

---

### Post by sourcemorph on 2007-12-09
go to add/remove programs and install wine (this will install wine 0.9.46) .. the newest version however is 0.9.50, for that u need to add the wine repositories in the software sources. most games run fine on wine, even if they don't just google with game-name + wine and u'll get a link to a winehq page, it'll tell u how to make a game work if it isnt working. 

the games already installed on ur windows partition may or may not work on wine straightaway (especially those that make new registeries/ add files to the windows folder) , u can reinstall the game on wine or fix these things manually. 

and yeah my personal experience says that the newversion of wine is really good, and u shudnt feel the need to use a paid software such as cedega..

---

### Post by bsell on 2007-12-09
> **Computerwiz1990 said:**
> Ok, how does Wine work and how do i use it or initialize it? And what about all the drivers on Windows, will they still work or whats gonna happen there?

WINE is a binary compatibility layer that translates Windows system calls to Linux system calls. You have to install it from the repositories to use it and you have to configure it initially using the command line. If you are unfamiliar with a CLI, tinker with the command prompt on Windows to get an idea of working in a text environment.

If you are not comfortable with a CLI, I would suggest you use the Ubuntu Live CD for a while before installing or take aysiu's advice and set up a virtual box inside XP. I think Linux Basics has a generic VMWare player you can install any distribution on.

---

### Post by Tux.Ice on 2007-12-09
If you have a spare partition ubuntu and windozer will work together and grub will be able to choose between which one to boot. wine can make some windozer programs work but not all so you should get the free alternative.

---

