---
title: "First time with Linux"
date: 2006-09-14
forum: Absolute Beginner Talk
---

### Post by Stone9 on 2006-09-14
Hi guys,

I'm brand new to Linux and am thinking about using ubuntu/kubuntu/xubuntu as my first distro. Does anyone have any recommendations as to which one?

I've downloaded all the LIVE CDs and have played around with them. Not sure which interface I like better, GNOME or KDE.

The machine I'd be installing on has the following specs:

Processor: PIII 800 MHz
RAM:       386MB SDRDAM
Video:     128MB Nvidia
HDD:       120GB 7200RPM 133ATA, but the installation would be on a 15GB partition

Thanks in advance guys!

---

### Post by kidders on 2006-09-14
I'm open to correction, but afaik the various Ubuntus are essentially all the same. You can pretty easily turn one into the other with a little tweaking.

Pick the one that seems like it fits you better ... if you make the wrong choice, it's not as if you'd have to start again from scratch or anything :-)

Unfortunately, your machine is a little low spec, so I wouldn't expect mind-blowing performance out of it though!

---

### Post by oedipuss on 2006-09-14
I think xubuntu might be much faster on your pc. It needs much less ram and resources than either gnome or kde.
I'm on gnome at this moment, with firefox and synaptic running, and little else, and it takes about 300-350 MB ram, so I suppose while 386 is technically enough, you'd be better off with a lighter environment.

---

### Post by Najand on 2006-09-14
Hmm, If you are looking for more tools, less speed and more GUI than text configuration, use KDE.
If you are looking for avarage  tools, a little more speed and a reasonable GUI configuration tools, use Gnome.
And If you are looking for a fast, steady graphical environment but less GUI tools, and more textbase configuration, use XFCE. (Recommended Specially for slow computers and computers with small RAM)

---

### Post by ciscosurfer on 2006-09-14
I primarily use Ubuntu (GNOME desktop; ubuntu-desktop metapackage) but occassionaly (very rarely) I switch over to KDE at my login screen (which is essentially is the kubuntu-desktop metapackage).  I also been known to run XFCE (xubuntu-desktop metapackage) and switch over to it easily on my login screen as well.  It just depends on the mood I'm in...
If you want something very light, but still usable, you can start with your xubuntu disc and them download the ubuntu-desktop metapackage and/or the kubuntu-desktop metapackage to give you GNOME and KDE, respectively.
I started out with Ubuntu and so I already had the ubuntu-desktop metapackage...I then downloaded kubuntu-desktop and that gave me KDE...and then I downloaded xubuntu-desktop to get XFCE

There are a whole slew of window managers out there!  Sometimes, I will switch over to Fluxbox.  You can find it in the repos I believe; can't remember though.

Have fun!

---

### Post by Najand on 2006-09-14
P.S. I usually recommend people to start with KDE. After achieving some knowledge about linux, migrating to Gnome and other graphical environment like  XFCE, Windowmaker, fluxbox is easier...

---

### Post by Stone9 on 2006-09-14
So, could I install Ubuntu, but then decide its too slow and load the x version instead?

Is there a version with all the GUI installed?

Thanks!

---

### Post by Najand on 2006-09-14
> **Stone9 said:**
> So, could I install Ubuntu, but then decide its too slow and load the x version instead?

Is there a version with all the GUI installed?

Thanks!

Different Projects of Ubuntu (official)
Ubuntu usues Gnome.
Kubuntu uses KDE.
Xubunutu uses XFCE.
Edubutnu is Ubuntu + Educational Resources (For Kids and teachers)

You can change to other environments easily by running this command in terminal (change project name with <PROJECT NAME>:
```

sudo apt-get install <PROJECT NAME>-desktop

```

---

### Post by Stone9 on 2006-09-14
The Ubuntu install comes with all three environment installed, but just with Gnome as its default? Or would I need to download the other environments separately?

Thanks!!!

---

### Post by Najand on 2006-09-14
The Ubuntu edition comes just with GNOME. You need to install KDE or XFCE using apt-get or  similar to be able to use them... If you want KDE from begining use KUBUNTU and if you want XFCE, use XUBUNTU.

---

### Post by M374llic4 on 2006-09-14
> **Najand said:**
> The Ubuntu edition comes just with GNOME. You need to install KDE or XFCE using apt-get or  similar to be able to use them... If you want KDE from begining use KUBUNTU and if you want XFCE, use XUBUNTU.

So if I want to go from GNOME to XFCE I type in the term

sudo apt-get install XUBUNTU-desktop or do you type 
sudo apt-get install XFCE-desktop  ?


And it gets and installs XFCE? If so, whats the command to switch between installed desktop software? How large is the file roughly?

---

### Post by Stone9 on 2006-09-14
Great! Thanks for all the replies guys!!!!

---

### Post by Najand on 2006-09-14
> **M374llic4 said:**
> So if I want to go from GNOME to XFCE I type in the term

sudo apt-get install XUBUNTU-desktop or do you type 
sudo apt-get install XFCE-desktop  ?


And it gets and installs XFCE? If so, whats the command to switch between installed desktop software? How large is the file roughly?

For full packages:
```
sudo apt-get install xubuntu-desktop
```
or
For XFCE only:
```
sudo apt-get install xfce 
```

It is possible to change  them in Gnome Desktop Manager.

---

### Post by ciscosurfer on 2006-09-14
> **Najand said:**
> For full packages:
```
sudo apt-get install xubuntu-desktop
``` or
For XFCE only:
```
sudo apt-get install xfce 
``` 
It is possible to change  them in Gnome Desktop Manager.

You can switch between desktop managers by logging out and then logging in again, making sure to switch to your new DM from within the sessions tab on your login screen.

---

### Post by Stone9 on 2006-09-14
Will that code go out to websites and download the pkgs needed or do you need to install them separately and use that code just switch between the environments?

- Thanks guys!

---

### Post by rocknrolf77 on 2006-09-14
Everything will download and install. You change the desktop in the login screen. Hit the session button and choose your desktop enviroment. :)

---

### Post by Najand on 2006-09-14
Anyway, why you just install one and if you found it not suitable for you install another one? Don't worry they  don't charge you fot reinstalling.

---

### Post by petri on 2006-09-15
You should NOT use apt-get when you  install a desktop. In fact you should not use it att all.

It is better to use [aptitude]("http://www.psychocats.net/ubuntu/aptitude") because it handles the depedencies much better. If you already have installed some of the desktop packages go to [aysius]("http://www.psychocats.net/ubuntu/index.php") site how you get ridd of them if you want to. There is also guides how to install these desktops and guides to other usefull things too.

---

### Post by Najand on 2006-09-15
Well, Aptitude for sure deals better with packages, but it just when you want to  remove packages and it is not generally very important. If you want to use [aysius]("http://www.psychocats.net/ubuntu/index.php") site to remove all the packages it is not a big difference by using apt-get and aptitude to install packages.

---

### Post by petri on 2006-09-15
Isn't it? With apt-get you have to include all the depedencies by yourself. If you instaled with aptitude and want to uninstall then all you need is the packagename. I think that's a big difference.

---

### Post by Najand on 2006-09-15
You  are not supposed to  add all dependencies by yourslef; it will select them all by itself... The only difference is, it will not remove all dependencies it installed automatically when you are trying to remove a package. That is becuase there might be a dependencies has been share with some other packages's dependencies. 
I repeat it again; aptitude is better than apt-get, but it does not mean there is something wrong with apt-get or you will be in trouble if you use apt-get.

---

### Post by ciscosurfer on 2006-09-15
You can run apt-get with switches to produce the exact same response as aptitude will produle without swithces.  Using apt-get over aptitude; using aptitude over apt-get; or using Synaptic over Adept; most are front-ends for apt and are a matter of preference.  Sometimes, when things go haywire, the use of dselect or dpkg is also necessary.  For those who are still brand-spankin' new to Linux and Ubuntu, I would recommend using Synaptic b/c it's very easy to learn, resolves dependencies cleanly, tells you when things get broken and how to fix them, etc.  I personally use Aptitude at the command line, but that's just me.  aysiu provides additional information about apt-get, saying: ...and you want to clean out some unused dependencies [after using apt-get to install], you can install and use *deborphan* or the graphical frontend *[gtkorphan]("http://www.marzocca.net/linux/goshots.html")* (now available in Dapper if you [enable extra repositories]("http://www.psychocats.net/ubuntu/sources.php")).

---

### Post by petri on 2006-09-15
No I meant like this: When you install with apt-get it takes care of the depedencies needed to the package but apt-get does not include all the depedencies when you want to **uninstall** the package. I see that I forgot that little piece of information.

**aptitude** includes a**pt-get** and **dselect** and some more so I can't see any reason why to recommend a**pt-get**. Using **apt-get** may not harm you or your pc but why keep files you don't need? Just in case? :biggrin:

Check out one link I googled [http://linux.derkeiler.com/Mailing-Lists/Debian/2004-04/3181.html](http://linux.derkeiler.com/Mailing-Lists/Debian/2004-04/3181.html) and there is more at /usr/share/aptitude

Why does people prefer do things difficult to themselves? Ego?

---

### Post by xpod on 2006-09-15
Using "aptitude" as apose to "apt-get" was probably the first command i learned to use 3 weeks ago.....

I now use it at all times i know what i want....I started out with add\remove but that left stuff behind....hence the reason i quickly discovered the pro`s and con`s of each and every one of the package managers......

..NOT that i recall WHAT i learned...but "aptitude" is all i need to know for now!

good luck and have fun

---

