---
title: "Considering trying a Linux System"
date: 2007-12-01
forum: Absolute Beginner Talk
---

### Post by Z47isthenew42 on 2007-12-01
I currently run Microsoft Windows XP Professional Version 2002 Service Pack 2 on my Dell Dimension 2400 and am considering trying a Linux system.

When I View System Information, it displays my operating system, my computer brand and model obviously.  My processor is an Intel Pentium 4 and it displays this:

Intel Pentium 4 CPU 2.20 GHz CPU 2.19 GHz, 256 MB of RAM.

There is one program that I would be concerned about, and that  is SAS which I currently use for one of my classes and if I do go on to get a PhD, I will be taking the class to learn how to actually use it more than I figured out on my own since many state institutions and large companies use this program and want their employees to know how to use it.

I am wondering 1)  What system would be the best for this computer.  2)  Is there any way I can get SAS (I believe 9.1.3)  to run on a Linux distro.

Also, I would prefer to keep Windows on this computer while testing any Linux distro.

Thank you for your time.

---

### Post by jken146 on 2007-12-01
Your system meets the requirements for Ubuntu, but there are a lot of distros out there.  The easiest way to decide which you prefer (and discover if you have any hardware that isn't supported) is by trying out some live CDs.  distrowatch.com is all about linux distros.

If you do decide to install a linux distro then you will be able to dual boot it with Windows if you wish.  This is usually very simple.

---

### Post by annda on 2007-12-01
and our good friend [aysiu]("http://www.psychocats.net/ubuntu/") has a link to [videos]("http://video.google.com/videosearch?q=ubuntu+dual+boot") explaining how to set up a dual boot with windows and ubuntu.

p.s. i like a lot of linux distributions, but i always recommend ubuntu to newcomers.

---

### Post by laidback on 2007-12-01
With Ubuntu you can try it via the Live CD before installing. It doesn't touch your hard drive. You can also have a dual system, XP plus Linux/Ubuntu on the same hdd/system should you choose to install it.
I would suggest you get a total of 512Mb Ram, 256Mb is the minimum for Ubuntu. There is a version for lower spec machines, Xubuntu.
Search forum for Dell 2400 to see if there have been issues inthe past with this hardware.

Good luck.

---

### Post by jflaker on 2007-12-01
If you have the XP install disk, you can run VirtualBox with XP.  This way you still have Linux, but can run a virtual XP session and the specialized apps.  The only consideration is giving the XP installation enough virtual disk (meaning you need a sufficient disk drive)  and memory (get at least 2GB so you can give VirtualBox XP install about 1GB) to be efficient while giving ubuntu enough memory to do other things too.

I have a virtual XP install and can, if needed, do what I need for apps that refuse to run under WINE.....which, by the way, according to their site, SAS 9.x does not run.......reported for V6.10 ([This link]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=6700&iTestingId=8429")).  Not sure if 7.10 changed anything.

---

### Post by njparton on 2007-12-01
opensuse may be a good option if your a first timer - it has GUI's to configure most settings but the install and partitioning can be quite complex compared to ubuntu.

---

### Post by eolson on 2007-12-01
If it was me (and I know it ain't),  I'd upgrade the RAM with as much as the system will hold or you can comfortably afford  (even if you don't add Linux).  Then,  I'd set the system up to dual boot Windows and Ubuntu (extremely simple to do).

---

### Post by mellowd on 2007-12-01
What exactly is SAS? There might be a linux version avalible

---

### Post by Z47isthenew42 on 2007-12-01
> **mellowd said:**
> What exactly is SAS? There might be a linux version avalible

It's a program mainly used for evaluation and modeling of Statistical Data, and it is very important to learn for me either going onto a PhD or going and getting a job.

---

### Post by mellowd on 2007-12-01
> **Z47isthenew42 said:**
> It's a program mainly used for evaluation and modeling of Statistical Data, and it is very important to learn for me either going onto a PhD or going and getting a job.

Do you have a link to the website for this?


btw, have you ever seen Scibuntu? [http://scibuntu.sourceforge.net/](http://scibuntu.sourceforge.net/)

It adds a few applications to the base ubuntu system. I know there was also a dedicated science distro out there but can't seem to find it now.

---

### Post by mellowd on 2007-12-01
Ah, found it: [https://www.scientificlinux.org/](https://www.scientificlinux.org/)

---

### Post by houstonbofh on 2007-12-01
0) Your memory is light.  I am amazed that you can stand XP on that.  Memory is cheap...  I would tell you what kind you need, but support.dell.com seems to be down.  Check, but do not buy from Dell.  They change to much for memory.

1) If you upgrade the mory, anything will be fine.  If not, you may want a lighter distrubution.  That said, Ubuntu (with Gnome) is one of the easiest out there, and it does have the best community support by far.

2) You need to learn more about how to find information.  Search is your friend, and is often much faster than waiting for one of us to help you.  But once that fails, there are **a lot** of people who will bend over backwards to solve your problems, provided you have done the background stuff first.  In this case a simple Google of "SAS Linux" gave me a lot of info.  The best ones are...
[http://support.sas.com/documentation/installcenter/913/hosts/index.html#d](http://support.sas.com/documentation/installcenter/913/hosts/index.html#d)
[http://www.utexas.edu/its/products/sas/](http://www.utexas.edu/its/products/sas/)
[http://www.ats.ucla.edu/STAT/SAS/icu/install_linux.htm](http://www.ats.ucla.edu/STAT/SAS/icu/install_linux.htm)

So, yes it is available, but not free.  However, you may have a free or reduced cost option at your University.

---

### Post by mellowd on 2007-12-01
You university might even have it avalible for linux already

---

### Post by fenian on 2007-12-01
SAS is officially supported in Red Hat Fedora and SUSE so it may run under Ubuntu as well.
There is a guide [here ]("http://www.ats.ucla.edu/STAT/SAS/icu/install_linux.htm")for linux installation.

---

### Post by mali2297 on 2007-12-01
I have seen versions of SAS for Linux, you should check with your university if they can provide it.

I must mention [R]("http://www.r-project.org/"), it's a very good open source program for statistical computing .

---

### Post by SunnyRabbiera on 2007-12-01
> **fenian said:**
> SAS is officially supported in Red Hat Fedora and SUSE so it may run under Ubuntu as well.
There is a guide [here ]("http://www.ats.ucla.edu/STAT/SAS/icu/install_linux.htm")for linux installation.

yeh but it depends on the package... but gah those instructions are friggin ancient (it recommends a floppy for goodness sake!) and its possible that SAS no longer has a version for linux in development.
for most windows apps though there is wine, but its touch and go so a dual boot might be wise.

---

### Post by fatality_uk on 2007-12-01
> **annda said:**
> p.s. i like a lot of linux distributions, but i always recommend ubuntu to newcomers.

And very experienced users alike!! Trust me :) I've been working in the IT industry for over 25 years and have worked on everything from Amiga OS, AS400, BeOS, Good ol UNIX and right through ALL of the MS releases.

My current desktop is Ubuntu 7.10. Why, because it does all that I need it to do! It's pretty much an "Out of the box" or "straight from the .iso" more like, solution.

---

### Post by houstonbofh on 2007-12-02
> **SunnyRabbiera said:**
> and its possible that SAS no longer has a version for linux in development.
I guess you didn't look at my link to the SAS website.  Or the fact that his link you quoted was also in my list of links. ;)  Again, it should work, but it will take time, effort and money from someone...

---

### Post by Z47isthenew42 on 2007-12-03
> **mellowd said:**
> Do you have a link to the website for this?




[www.sas.com](www.sas.com)

[QUOTE=mali2297]  I must mention R, it's a very good open source program for statistical computing .[/QUOTE]

I already know about R and also (attempt to) use it.  The whole point of wanting SAS is that a lot of New York State agencies use SAS as well as large companies, and for the jobs I've found, a lot of them require Knowledge of how to use SAS.

Now it is possible that my university may have SAS available for Linux, but I would have to ask since their network is Windows and the University tends to be cheap.

Thanks for all the help.  By the way, I need to learn to search using the right search terms because I couldn't find stuff on the SAS website despite it being there.

---

