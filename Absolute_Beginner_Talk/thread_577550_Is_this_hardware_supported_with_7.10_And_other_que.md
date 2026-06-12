---
title: "Is this hardware supported with 7.10? And other questions from a new (potential) user"
date: 2007-10-16
forum: Absolute Beginner Talk
---

### Post by Ulfursson on 2007-10-16
Long story short, I got a brand-new PC and laptop, and a friend of mine who is a rather enthusiastic Linux user convinced me to give it a try. She pointed me to this site, claiming Ubuntu is the most user-friendly one, and frankly, I've never used anything but Windows (95, 98, NT, XP, Vista) before, so I do care about user-friendliness a great deal. Now, here are the specs:

PC: 
Intel core 2 duo E6700
Geforce 8800GTX
2gb DDR2 ram

laptop:
Intel core 2 duo T7100
Geforce 8600M GT
Intel Wireless WiFi Link 4965AGN

I understand this more than meets the system requirements, but is all of the hardware supported?
Also, is it possible to run Vista and Ubuntu at the same time and how do you switch between them?
And another thing I'd like to know, what's the difference between the different Ubuntu versions (Ubuntu, Kubuntu etc)?


I hope I'm not too annoying with these questions, I'd just like to make sure this'll work like it should before I set off to download several CD images only to find out it won't.

Thanks in advance.

---

### Post by LowSky on 2007-10-16
Everything but the RAM will work...just kidding

to be serious try out a live CD and see if everything works
The worst thing you may have to do is get your wireless card working.

---

### Post by wolfen69 on 2007-10-16
wireless support for intel is very good. i dont see a problem with anything you have. but as lowsky said, try the live cd to make sure.

---

### Post by Dr Small on 2007-10-16
Like Lowsky said, run the livecd and see if it works. You may have to do some tweaking to get the wireless card to work. You can do a dualboot of Ubuntu and Vista, and to switch between the two, GRUB will be at the bootup screen, allowing you to change between the two operating systems of which you would wish to boot.

Dr Small

---

### Post by mikeyphi on 2007-10-16
Your systems will most probably work under Ubuntu - but why not give it a try without altering your current setup!!
I suggest you download 'Gutsy' from here: [http://www.ubuntu.com/news/ubuntu-7.10rc](http://www.ubuntu.com/news/ubuntu-7.10rc)
then burn the iso file onto a CD and boot from the new CD. Nothing will be changed on your system but you will be able to (almost completely) operate as though you have Ubuntu installed.
This will give you a good look at the OS and any contentions with your hardware.
To get the best look at Ubuntu with the 'LiveCD' it's best to have a wired connection to the internet, that way you can check if there's software support for your wireless card (not everything is included on the 'LiveCD')
Good luck!

---

### Post by LowSky on 2007-10-16
Forgot to mention that the Live CD runs much slower than a fully installed verison of Ubuntu.

---

### Post by az on 2007-10-16
> **Ulfursson said:**
> 
Also, is it possible to run Vista and Ubuntu at the same time and how do you switch between them?

Yes, this is known as dual-booting and it is very very common.

When you install Ubutu on a computer that already has an operating system, the installer should detect your cuurent OS and offer to shrink the disk partition on which it is installed.  This will make room for Ubuntu.  Once installed, the installer will create a bootloader which will run every time you boot your computer.  The bootloader will offer you a menu each time.  You can select which OS you want to run.

To switch to the other operating system, you simply reboot and pick the other OS.

> **Ulfursson said:**
> 
And another thing I'd like to know, what's the difference between the different Ubuntu versions (Ubuntu, Kubuntu etc)?


Ubuntu is free-libre open source software.  That means that anyone can contribute to development.  This means that you, the user, get lots more choice.

By default, Ubuntu uses Gnome.  Gnome is a desktop environment.  If you prefer a different desktop environment, there are plenty others to pick from.  Kubuntu is Ubuntu which runs KDE.  Which is better?  You choose.

---

### Post by Ulfursson on 2007-10-16
All right, I guess I'll try the rc liveCD. 

Which one should I choose? The link you provided lists Desktop, Server, Edubuntu, Kubuntu and Gobuntu. What's the difference?

---

### Post by LowSky on 2007-10-16
Desktop  -- Ubuntu 7.04 or 6.10 LTS is what you want

i suggest the x86 version, 64bit works but there is more support for x86

---

### Post by Dr Small on 2007-10-16
Desktop has the default installation of Gnome.
Server is Command Line Interface. (No GUI)
Edubuntu is for schools (has alot of school applications on it)
Kubuntu uses KDE desktop environment.
Gobuntu... I never heard of that one. O.o

Dr Small

---

### Post by LowSky on 2007-10-16
[http://en.wikipedia.org/wiki/Gobuntu]("http://en.wikipedia.org/wiki/Gobuntu")

> Gobuntu is an official derivative of the Ubuntu operating system, aiming to provide a distribution consisting entirely of free software.



---

### Post by Ulfursson on 2007-10-16
All right, I'm downloading the desktop version now. I'll post further questions as I attempt to abuse my laptop :biggrin:

---

### Post by Martje_001 on 2007-10-16
> **Ulfursson said:**
> All right, I'm downloading the desktop version now. I'll post further questions as I attempt to abuse my laptop :biggrin:
Maby you should wait 2 days, when Gutsy (version 7.10) is released. It has much better hardware support and it has Compiz enabled by default!

---

### Post by Ulfursson on 2007-10-16
> **Martje_001 said:**
> Maby you should wait 2 days, when Gutsy (version 7.10) is released. It has much better hardware support and it has Compiz enabled by default!

Not that bad an idea. I'd certainly rather have the final release than a test release candidate.

---

### Post by amlucent23 on 2007-10-16
> **LowSky said:**
> Desktop  -- Ubuntu 7.04 or 6.10 LTS is what you want

i suggest the x86 version, 64bit works but there is more support for x86


LTS is 6.06 Dapper, just to clarify. Also imo its plenty stable and a good OS just not as wonderful as feisty  (or even better gutsy). I would go with gutsy in 2 days.

---

### Post by Ulfursson on 2007-10-18
OK, I'm posting this from my laptop, running the 7.10 liveCD.

-Wired internet works, I don't have a wireless router at home to test that
-Sound doesn't work
-Everything is very slow, but I believe someone already mentioned that's because it runs off the CD
-How do I switch to Icelandic keyboard settings? It took me a while to find all the punctuation marks, and some special characters (á, ð, é, í, ó, ú, ý, þ, æ, ö) don't even appear to be present on the default keyboard setting
-The laptop's mouse pad works

---

### Post by Ulfursson on 2007-10-18
I've gotten this far with the installation. What do I do?
(I understand this has something to do with the hard disk, so I thought I'd ask here because I don't want to ruin my Vista installation with this)

Still looking for the answer on sound and keyboard settings, by the way.

[img]http://img152.imageshack.us/img152/4738/screenshotit0.png[/img]

---

### Post by Ulfursson on 2007-10-18
Anyone? :(

---

### Post by LowSky on 2007-10-18
hi Ulfursson, first to be safe go into Vista and Defragment your hard drive (should be an option under Programs>Accessories>System

then boot the Live CD again

setting up the keyboard options should be one of the first thing the installer asks you
the sound issue may need to be fixed once Ubuntu is installed

First pick the best option for Partitioning, How much of your hard drive do you want to give up
If it's half move the slider bar to 50% and click next.
If you want a certain amount or you want to partitions to be done by hand choose manual setting.

First resize your Windows Partition to however big you want it
Then create a new partition called ```
/
``` give this partition about 20GB
then create a home partition called ```
/home
``` as big as you like (this is where all your personal files will get stored (i reccomend 20-40GB)
Then create another partition called ```
swap
``` this should be from 512MB - 2GB


If this sounds too hard just use the automatic resize option and choose how much % you want to give to ubuntu

---

### Post by Ulfursson on 2007-10-18
How do I resize the Vista's partition?

*No offense, but congratulations on misspelling my username, btw :D*

---

### Post by LowSky on 2007-10-18
LOL, Sorry about that, I'm lucky if I spell my own name correctly.

look up at the picture you place in this thread, see the button that say edit partition?
Click that and shrink the size of the Hard drive from there

after that make new partions using my instructions from above

---

### Post by Ulfursson on 2007-10-18
As I've said, no offense.

How much smaller can I make the partition if there's 50gb of used space on it?

---

### Post by pelle.k on 2007-10-18
You forgot to mention *what* laptop you are using (brand/model etc). That sort of stuff is important people! :)

---

### Post by Ulfursson on 2007-10-18
> **pelle.k said:**
> You forgot to mention *what* laptop you are using (brand/model etc). That sort of stuff is important people! :)

It's a Compal FL91.

Oh, and I'm still having trouble with resizing my windows partition. Here's what happens when I click the "edit partition" button from the earlier-posted screenshot:

[IMG]http://img145.imageshack.us/img145/868/screenshotzm9.png[/IMG]

---

### Post by Ulfursson on 2007-10-18
bump.

---

### Post by mikeyphi on 2007-10-18
You might find answers to some of your questions about installing Ubuntu at this site: [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by Ulfursson on 2007-10-18
OK, playing around, I noticed the partition editor in the System->Administration menu, and I'm now resizing the partition. You'll have to excuse me for not noticing this earlier.

---

### Post by amlucent23 on 2007-10-20
> **Ulfursson said:**
> OK, playing around, I noticed the partition editor in the System->Administration menu, and I'm now resizing the partition. You'll have to excuse me for not noticing this earlier.

Did you ever get this installed?

I think if you have not, and your like most of us and process things visually, you should take a look at these free videos that explain step by step how to accomplish the install and other useful tasks.

[http://screencasts.ubuntu.com/MoS2007/09_Installing_Ubuntu_Part_1]("http://screencasts.ubuntu.com/MoS2007/09_Installing_Ubuntu_Part_1")

[http://screencasts.ubuntu.com/Installing_Ubuntu_with_Windows_Dual-Boot]("http://screencasts.ubuntu.com/Installing_Ubuntu_with_Windows_Dual-Boot")

These videos are fairly short and packed with instruction. If you still have questions please feel free to ask.

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-10-20
> **LowSky said:**
> Desktop  -- Ubuntu 7.04 or 6.10 LTS is what you want

i suggest the x86 version, 64bit works but there is more support for x86

YOU shut up about the 32-bit not haveing the same sapport as the 64-bit its just as sapported

---

### Post by bigboy_pdb on 2007-10-20
Regarding your laptop, you should create recovery discs for Vista if you haven't already done so.

---

### Post by Ulfursson on 2007-10-20
Thanks for all the advice, I got 7.10 installed now. 

If you can help me with getting sound working, write [[COLOR="DarkOrange"]here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=581812").

---

