---
title: "ubuntu vs. xubuntu"
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by e6626550w on 2007-06-20
I've been using ubuntu for a few months now and I like it. Been reading however that the xubuntu version is optimized for older computers. I'm using an old celeron 1100 with 384 ram right now and ubuntu does okay, afaic. I downloaded the xubuntu version last night and ran it off the cd but it is hard to tell how it will perform until it's actually installed I'm told.My question is, is there much of performance increase normally between the two versions?  I guess I'm asking the people who may have actually done it. I'm sorta of  hesitant to bother if it doesn't speed things up noticeably. Thanks. 

eileen...

---

### Post by Sushubh on 2007-06-20
a question comes to mind. how smooth is your experience running it from liveCD?

---

### Post by e6626550w on 2007-06-20
Worked fine, didn't encounter any problems and seemed start the programs from the cd about as fast as the installed ubuntu did. 

eileen...

---

### Post by raul_ on 2007-06-20
XFCE itself is much faster and light, but it's all about the applications you use. 

Lightness aside, I find XFCE a superior DE when compared to Gnome, but that's my opinion :)

PS: xubuntu's default look isn't very nice, but if you spend some time trying to customize it, you'll be very satisfied

---

### Post by Sushubh on 2007-06-20
[http://ubuntuforums.org/showthread.php?p=2586164](http://ubuntuforums.org/showthread.php?p=2586164) cheers. :D

---

### Post by lazyart on 2007-06-20
you can try it by doing

sudo apt-get install xubuntu-desktop

---

### Post by carloslosgrande on 2007-06-20
My experience is that it lacks a lot of the functionality of Dapper, Feisty whatever, and it can be difficult if like me you aren't well versed in terminal usage.
To put it simply, I found it very difficult to setup to run as I wanted.
My ignorance being the cause.

---

### Post by lasch on 2007-06-20
I have tried gnome, xfce, icewm and fluxbox and I always seem to end up back with gnome. I wish gnome were a little faster but I personally did not feel that I got that big of a speed boost with the others. I am new to Linux and though I have learned a lot in the last month I just feel more comfortable with ubuntu and gnome for now.

---

### Post by Old Pink on 2007-06-20
> **lazyart said:**
> you can try it by doing

sudo apt-get install xubuntu-desktop

First, enable your Xubuntu CD as a repository in your Ubuntu setup, and you'll download it off the CD without having to wait for the internet. :)

---

### Post by rcsarver on 2007-06-20
as lazyart said, if you are running ubuntu already, install "xubuntu-desktop" and you can choose whether to run gnome or xfce at login.

---

### Post by nicedream on 2007-06-20
> **carloslosgrande said:**
> My experience is that it lacks a lot of the functionality of Dapper, Feisty whatever, and it can be difficult if like me you aren't well versed in terminal usage.
To put it simply, I found it very difficult to setup to run as I wanted.
My ignorance being the cause.

If I may ask, does Xubuntu lack some of the applications or config tools that are found in regular Ubuntu?  I wasn't sure if the only difference was the GUI or if there was more to it.

---

### Post by Sushubh on 2007-06-20
am pretty sure that most applications would run no matter what GUI u are using :|

---

### Post by nicedream on 2007-06-20
> **Sushubh said:**
> am pretty sure that most applications would run no matter what GUI u are using :|

I realize that...;)

I am talking about the default installation.  Do they strip any apps or config tools out of the base install in order to make it run leaner?

Or to put it another way, is there *any* difference between the two, aside from the Gnome/Xfce switch?

---

### Post by raul_ on 2007-06-20
Thunar instead of Nautilus, for example :) that's a plus. And yes, some applications are stripped down. Epiphany, Evolution, Gedit, are all gone, with other alternatives. I'm a suspect though, because i like Xfce better

---

### Post by nicedream on 2007-06-20
Thanks for your help Raul...Since my laptop has 2GB of memory, I'll probably go for regular Ubuntu!

---

### Post by raul_ on 2007-06-20
> **nicedream said:**
> Thanks for your help Raul...Since my laptop has 2GB of memory, I'll probably go for regular Ubuntu!

Yeap. You could try KDE too. In my opinion, if memory is not a problem, then KDE is the powerhouse of Desktop Environments. 

Ubuntu is a Gnome distribution though, and I think there is more documentation for Ubuntu, although documentation for Kubuntu is also very good ;)

---

### Post by nicedream on 2007-06-20
Thanks, but no thanks.  I have always hated the KDE look.  And I remember trying it when it was around version  0.01 :)

---

### Post by Sushubh on 2007-06-20
am waiting for kde 4. current one is just too messy for me too. :)

---

### Post by kspn on 2007-06-21
Hi,

I am buying a new PC and I am planning on installing either **Ubuntu** or **Xubuntu** and I was wondering if anyone could tell me of a comparison of the features and benefits of the two version of the system. I am planning on using the 64Bit version of the OS whichever one I decide on.

I am inclined towards **Xubuntu** but I was looking for some advice and help.

_**New System Specs**_
AMD X2 64bit Dual Core 4000+
2gb RAM
160GB Hard Drive

I don't think I will have any issues running the two versions. I am a moderately experienced Linux Geek and I have no issues with extra configuration of the system as required.

_**The core Apps I wish to use are**_
Thunderbird
OpenOffice
Firefox
Bittorrent client
Apache/Tomcat

I hope I have provided enough information for some informed advice on this.

_**Information I am hoping to get includes**_
Amount of Customization
Ease of Customization
Ease of App install
Ease of App Compiling from Source

Thanks
Karel Young

---

### Post by ugm6hr on 2007-06-21
@ kspn:

I think your hardware will run either without difficulty.  I personally use Xubuntu (i386 with 256-1024MB RAM systems), but for your purposes - the out-of-box GNOME experience will be easier.

Xubuntu does not have the following as standard (but can be easily added if you have ethernet/DSL internet access):
OpenOffice - I use 
BitTorrent Client - I use KTorrent, which is a KDE app (I had major probs with others - most people seem to prefer WINE/utorrent for GNOME - but I think Ubuntu has a couple pre-installed)
build-essential - required for compiling from source

As for ease of installing apps from Ubuntu repository - it's identical.  Source compiling should also be identical (after installing build-essential).
I haven't tried customizing GNOME, but I gather they are fairly similar with GUI experience.  XFCE is certainly readily customizable.  Panels are particularly useful for getting mail notifiers, laptop battery power, trashcan, volume controls etc.  As for looks - try these websites:
[http://www.xfce-look.org/](http://www.xfce-look.org/)
[http://www.gnome-look.org/](http://www.gnome-look.org/)

You could of course install Ubuntu from LiveCD, then xubuntu-desktop afterwards to ensure you have all the Ubuntu apps with the feel of XFCE.  And it would let you try both.

---

### Post by kspn on 2007-06-21
So from what you are Saying the Primary difference between the two versions is the XF86 Window Manager.

Beyond that they are basically identical?

BitTorrent: The Client i was looking at installing is _Torrentflux_ mainly because I can run that as a background APP whether I have logged into the box or not.

**Easy** is not one of the items that is high on my priority list :)

On that basis, I think I will try the Xubuntu64 Version. If I am not happy I can always install Ubuntu64 on the system.

Further advice is appreciated, you can never have too much information.

---

### Post by dptxp on 2007-06-21
> **Old Pink said:**
> First, enable your Xubuntu CD as a repository in your Ubuntu setup, and you'll download it off the CD without having to wait for the internet. :)

How do you enable your Xubuntu CD as a repository in your Ubuntu setup ?

---

### Post by gn2 on 2007-06-21
> **dptxp said:**
> How do you enable your Xubuntu CD as a repository in your Ubuntu setup ?

As a 7.04 user you may not have to, open Synaptic Package Manager > Settings > Repositories.
A box opens and says "To install from a CD-Rom or DVD, insert the medium in the drive."

---

### Post by RedSquirrel on 2007-06-22
**@e6626550w:**

Xubuntu is quite a bit lighter than the standard Ubuntu (with GNOME). If you find your GNOME-based Ubuntu is at all sluggish, I am of the opinion that you will find that Xubuntu is very responsive. A fair bit of the configuration is done via a GUI, so it isn't a big adjustment from GNOME as far as I'm concerned.


** @kspn:**

For compiling software, as mentioned above, you'll need the **build-essential** package. 

Depending on what you are planning to compile, you may need to install some development libraries since they are _not_ installed by default on Ubuntu. They are in the repositories and they end in "-dev".

If a package exists in the repositories, but you want to compile a more recent version, you can do:

```
sudo apt-get build-dep *package_name*
```which should install most (perhaps *all*) of the things you will need to do the compiling.

See the man page:

```
man apt-get
```Have a look at [checkinstall]("https://help.ubuntu.com/community/CheckInstall") as well.

Have fun! :D

---

### Post by kspn on 2007-06-26
I have found that the *build_essentials* had **most** of what I needed (I still needed to also get libncurses5-dev) but overall it is going well, and so *fast*

The main item I have run up against is compile failures on code that has worked in the past but I think that it may be the difference in the Kernel version (2.6.x vs 2.4.x)

I am enjoying my experience and I think I might be able to convince my parents to also use Xubuntu :D

Thanks for all the help.

---

