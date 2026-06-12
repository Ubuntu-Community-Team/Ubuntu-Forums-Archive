---
title: "Can someone explain it to me like I'm a 2 year old?"
date: 2006-11-07
forum: Absolute Beginner Talk
---

### Post by SFC on 2006-11-07
After receiving many issues of TUX magazine, I decided to try the world of Linux (I currently have been using windows for 20 years). I must admit I'm a big fan of the free and open source software concept. After reading an article in the latest Tux mag. I decided to use Kubuntu (edgy) as my linux system. The interface is nice and appears easy to use. 

Know to the point, it's been a week and I still cannot figure out how to install most software. The kdesu adpet_installer is easy for installing existing suites or packages already in the ubuntu archives, but when it comes to other Linux software it seems very confusing. 

First, is the Linux version thing, there are so many, is the software compatible? (ie. will something made for SuSi run on ubuntu). Anyways, I always down load software that states it's compatible with ubuntu just to be safe.

Second, is the file extension thing, .rpm .dev and so forth. I've read the article about installing software suggested on an beginner tread([http://www.psychocats.net/ubuntu/installingsoftware)](http://www.psychocats.net/ubuntu/installingsoftware)). It suggests going to the command line to run .rpm or .dev, (command line! are we back to DOS know?) After trying the command line thing, I find that I have to install additional features like "aptitude update" and "aptitude install alien" to try and get the software I want to run.

Why doesn't the software just come in an .exe format like windows? you click on it, it installs, done deal. I'm not here to bash Linux or any system, it just seems to me that if you want people to cross over it's got to be easier. If I’m missing the boat here can someone please explain it to me (in beginner terms).

Thanks if you read this.
Steve

---

### Post by happy-and-lost on 2006-11-07
I've not used KDE in years, but somewhere in the "start (or K) menu" there's a piece of software called "Synaptic Package Manager", which you can find just about any software you want on :)

---

### Post by steve.horsley on 2006-11-07
Firstly, you are probably used to trawling the web for software rather than checking synaptic first. Instead, you should always check synaptic for what you're looking for. Maybe it's adpet_installer in kubuntu instead of synaptic - I'm not that familiar with kubuntu. Anyway, make sure you enable the multiverse and universe repositories, and you should have easy access to almost any software you want. Trawling the web should **not** be your first recourse.

Secondly, if you decide to download packages that are not created for Ubuntu, then you should expect more trouble than if you download Ubuntu specific stuff. Often it's just a case of unzipping the stuff and putting it in a directory. Sometimes there's an installer script to run, which isn't too hard either - just make it executable and run it. Just remember that you often have to get root priviledge to change system settings and files. The worst is if you choose to download and compile source code. If you've never downloaded and compiled windows apps from source code, then you can't really complain that it's harder in Ubuntu. It's the fact that it's so much easier is the reason some software is only distributed that way.

What software are you trying to install? As I say, it's most likely in the repositories anyway. Always, always look there first. And then ask in this forum if you are not sure. This forum is generally fast and helpful, especially for questions that can be answered quickly.

---

### Post by CatKiller on 2006-11-07
[How to install ANYTHING in Ubuntu]("http://monkeyblog.org/ubuntu/installing/")
[ Installing Software in Ubuntu]("http://www.psychocats.net/ubuntu/installingsoftware")

---

### Post by MWAAAHAAA on 2006-11-07
> Know to the point, it's been a week and I still cannot figure out how to install most software. The kdesu adpet_installer is easy for installing existing suites or packages already in the ubuntu archives, but when it comes to other Linux software it seems very confusing. 

It is called 'adept' not 'adpet'.

Actually this is one of the nice features that Ubuntu inherited from Debian. You want a certain program, just install the package and anything it needs is installed with it. What confuses you? You should certainly not search the web for this 'linux program' you are trying to install. That is often a beginner's mistake when people are new to linux. There are just two programs I installed 'off the web' simply because the version in the repositories does not match my needs. (These are wine and mplayer BTW). So stick to the repositories, everything you need is in it.

> First, is the Linux version thing, there are so many, is the software compatible? (ie. will something made for SuSi run on ubuntu). Anyways, I always down load software that states it's compatible with ubuntu just to be safe.

SuSe, Ubuntu, Debian, Mandrake, RedHat, those are all just linux _distributions_. They give you a complete linux based system with a selection of additional software which makes it easy for you to use your system and be productive with it. As this concerns linux, most of the software is probably available in source code form, so you can compile and install it yourself if you have the proper libraries (DLLs) and deevlopment tools installed.
When it comes to binary packages, there are special tools available to convert from one to the other (e.g. alien). If the binaries in these packages have been compiled against libraries that are compatible or equivalent to the ones in your system, and if the binaries are compiled for your particular hardware, then it should not be a problem to install these packages.

> Second, is the file extension thing, .rpm .dev and so forth. I've read the article about installing software suggested on an beginner tread([http://www.psychocats.net/ubuntu/installingsoftware)](http://www.psychocats.net/ubuntu/installingsoftware)). It suggests going to the command line to run .rpm or .dev, 

AFAIK you do not 'run' a package. You give it to some other program to unpack it for you ('dpkg' for .deb)

>  (command line! are we back to DOS know?) 

So why is a CLI bad? It's simple, it's fast and offers functionality that a GUI simply cannot give you. Certain things can be done much more easily from the command line than from a GUI. Myself being a linux user for 7+ years, I prefer a CLI over a GUI for many things.

> After trying the command line thing, I find that I have to install additional features like "aptitude install alien" to try and get the software I want to run.

I installed the demo for Ghost Recond: Advanced War Fighter and they actually needed me to install Ageia PhysX drivers! This stuff has to be done in Windows as well or why do you think pretty much every modern game comes with a version of DirectX on the install CD, so what's your point?
If you want to run software, you need to have the prerequisites required to run that software.

> Why doesn't the software just come in an .exe format like windows? you click on it, it installs, done deal.

Personally I find it easier to do an 'apt-get install program'. It is just different than windows. .deb is really just the install.exe equivalent from Windows.

> I'm not here to bash Linux or any system, it just seems to me that if you want people to cross over it's got to be easier.

Linux is different. If you want to use an OS that behaves like Windows, then why do you not just use ... Windows?

> If I'm missing the boat here can someone please explain it to me (in beginner terms).

Why do you want to use linux? If you are looking for a Windows clone, I'd suggest you stick to Windows.

---

### Post by podunk on 2006-11-07
There is page after page of software in Adept, thousands of apps, tens of thousands. 

It installs with 2 clicks. <---period No where do you want to put this or that. No "Do you agree and  are you willing to abide bys..." No 30 day trials with nag ware or shutdowns.

When you uninstall it 2 clicks and it's gone. <---period. No registry to become corrupt, no disk defragmentation left behind.

Simple. Fast. Easy. 

Compact. In 5 months I've installed far more programs and applications in Linux than I've accumulated in Windows since 98 came out. 4 office suites. No telling how many CD burning programs, multimedia programs, file browsers and other utilities.

PIMs, C programmers and compilers FTP clients, download managers, firewalls email clients - hundreds of programs to pick and chose from.

Games. Doom Boom Quake bubbles card games Wesnoth

I've only compiled one program on this machine, all the rest came from the repositories.

/ is 33 gigs in size. That includes 4 3+ gig isos of *buntu *and the compressed data of my windows which I backed up with Kubuntu*

I've been thinking about this whole competition thing. Competition involves profit - and there is none in Linux.

Movements just are. They don't compete. They arise and exist as long as they are of service to the human race.

I think it was asyiu that said "Linux doesn't want you - do you want Linux?"

I do.:-)

---

### Post by Jussi Kukkonen on 2006-11-07
> Why doesn't the software just come in an .exe format like windows? you click on it, it installs, done deal.

Many consider the repository approach far superior to the Windows installer method -- me included.

Pros:
[LIST]
[*]it's easy:
[LIST]
[*]a single user interface for all installs/removals
[*]upgrading the whole distribution is possible
[/LIST]
[*] it's more secure: 
[LIST]
[*]no downloading from unknown sites
[*]repo admins can dictate rules that all software must follow
[*]*all* software is kept up-to-date
[/LIST]
[/LIST] 

Cons:
[LIST][*] If the program you want is not in the repos, there may be problems: Especially installing without using dpkg at all can really break the whole package management scheme.
[/LIST]

I strongly suggest not installing stuff from outside the repos. Ask at the forums, the software you seek or something similar might be available... If you really want to, installing stuff using a binary installer or a .deb-package is not difficult (a couple of clicks or two lines on the command line at most).

> 
First, is the Linux version thing, there are so many, is the software compatible? (ie. will something made for SuSi run on ubuntu). Anyways, I always down load software that states it's compatible with ubuntu just to be safe.
Generally, any linux software will work (but keep in mind what I mentioned about installing stuff from outside the repos). Badly written software might not, and there may be problems with e.g. Applications-menu items and such. Also this software will not be kept updated by the package management, etc.

> command line! are we back to DOS know?
the command line user interfaces have existed long before DOS had that pitiful excuse for a shell, and I believe they will exist for as long as we use keyboards. A command line is a powerful weapon -- don't use it if you don't like it, but you shouldn't underestimate it either...

> I'm not here to bash Linux or any system, it just seems to me that if you want people to cross over it's got to be easier.
...well, I don't actually (new linux users are nice, but personally I don't see it as a primary goal). I just want a system that is most usable for me and as easy to administer as possible. Currently I'd say Ubuntu and Debian are number one in that regard.

---

### Post by Marsolin on 2006-11-07
You've hit upon one of the strengths and weaknesses of Linux. The packaging a repository systems that Linux distributions are better than what is available on Windows because you can easily keep programs up to date and also have more visibility into what is actually being installed. This helps prevent all of the broken program issues that happen on Windows.

The problem with this approach is that every distribution does it differently. As you found out, this means that programs not included in the repository become more difficult to install. A project called [Autopackage]("http://www.linuxappfinder.com/package/autopackage") is trying to improve this, but it hasn't been widely adopted.

The first program you should get familiar with in Kubuntu is [Adept]("http://www.linuxappfinder.com/package/adept"). It is the package manager that Kubuntu installs by default. You can also try installing [Synaptic]("http://www.linuxappfinder.com/package/synaptic") to see which you like better.

The default package type for Kubuntu is .deb. I suggest sticking to programs that offer a package in this format unless absolutely necessary. If you don't find the app through Adept or Synaptic you may be able to find a .deb that you can download individually. Installing it is actually very easy. Right click on the file in [Konqueror]("http://www.linuxappfinder.com/package/konqueror") and look for the Kubuntu Package Menu listing. Click Install Package, enter your password, and it will take care of the rest.

.deb files contain references to the programs and libraries that they depend upon to function and will not install if those dependencies are unavailable, however, any found in the repository will be automatically installed.

---

### Post by aysiu on 2006-11-07
> **CatKiller said:**
> [How to install ANYTHING in Ubuntu]("http://monkeyblog.org/ubuntu/installing/")
[ Installing Software in Ubuntu]("http://www.psychocats.net/ubuntu/installingsoftware")
I second the motion. Read those two links. You won't regret it.

---

### Post by lazyart on 2006-11-07
In Windows you have .DLLs.  In Linux you have dependencies.  Have you ever tried to install something from Windows and found that you needed to install the .NET framework or Visual C runtimes?  Same idea.  Windows comes with hundreds of .dll files.  Some you will use, some you might never.  The Linux approach is to only ship with the dependencies that you need.  If the time comes that you need a specific library, then you install it.
By using aptitude/apt-get these things get resolved for you.  If you venture on to the web and find something you like, look in Synaptic and see if it's there.  If it is, install it and it takes care of itself.
When I look for software "out there" I do look for at least a .deb package.  You can download it and double click to install.  If you run into the dependency issue there, you drop to the command line and type:
sudo apt-get install -f
It will resolve the dependency and complete the installation for you.  Believe it or not, typing things out is quicker than pointing and clicking.  Once you've done it a while you remember it.  I've fiddled with my display settings and couldn't get into the desktop.
sudo dpkg-reconfigure xserver-xorg
Blast thru it, reboot and chances are my display is fixed.  I'm Certified on Windows but using Linux I find that I wish the command line there was as robust.
It's an alternate way of doing things.  Like I've said before-- things in this kitchen may be arranged differently, but you can still cook here.

---

### Post by SFC on 2006-11-07
Well, thank you all. This sheds some light for me to keep going!
The software I use most is CAD software, that's why I was browsing the web to it. I found QCAD and that loaded quite easily.
Again great support and thank you!

Steve

---

### Post by faithsnathan on 2006-11-07
>   After receiving many issues of TUX magazine, I decided to try the world of Linux (I currently have been using windows for 20 years). I must admit I'm a big fan of the free and open source software concept. After reading an article in the latest Tux mag. I decided to use Kubuntu (edgy) as my linux system. The interface is nice and appears easy to use. 

Welcome to Linux and the Ubuntu family!  I know that Dapper is more stable than edgy, so you might consider "down"grading to it (in my opinion, anyway).  I don't know much about Kubuntu (which uses the KDE environment instead of Gnome in Ubuntu or XFCE or something in Xubuntu), but it should be pretty simular to my experiences.

>   Know to the point, it's been a week and I still cannot figure out how to install most software. The kdesu adpet_installer is easy for installing existing suites or packages already in the ubuntu archives, but when it comes to other Linux software it seems very confusing. 

As TheWizzard points out in [this thread]("http://ubuntuforums.org/showthread.php?t=294969"), >   safety because of several default settings -> downloaded files not executable, users don't have administrator rights, etc  , you don't get .exe files because it's a lot safer that way.  There are, however, many programs or whatever that can/will aid you in installing/updating software:
[apt-get]("http://applications.linux.com/article.pl?sid=04/12/03/177243&tid=47&tid=49&tid=106&tid=126") (my personal favorite)  You'll want to know the file name first (I use these [Ubuntu Forums]("http://ubuntuforums.org/") and [Google ]("http://www.google.com/")to find out what I want)
[Synaptic]("http://www.nongnu.org/synaptic/")
[Add/Remove]("http://shots.osdir.com/slideshows/752/19.gif")
[Automatix]("http://www.getautomatix.com/") ...

>   First, is the Linux version thing, there are so many, is the software compatible? (ie. will something made for SuSi run on ubuntu). Anyways, I always down load software that states it's compatible with ubuntu just to be safe.  

What's compatible in one Linux distro is not *always *in another, though it generally is compatible.  I don't know if this is smart or not, but if something says it's compatible with Linux or Unix, I'll usually go ahead and try it out.

>   Second, is the file extension thing, .rpm .dev and so forth. I've read the article about installing software suggested on an beginner tread([http://www.psychocats.net/ubuntu/installingsoftware)]("http://www.psychocats.net/ubuntu/installingsoftware%29"). It suggests going to the command line to run .rpm or .dev, (command line! are we back to DOS know?) After trying the command line thing, I find that I have to install additional features like "aptitude update" and "aptitude install alien" to try and get the software I want to run.

Yeah, aysiu, who's article that is, is really smart and I'd trust his advice (in other words, definately follow what he says about installing software).

I hope this helps you, Steve.  If not, please post back or send me a personal message on here.  Either way, I or (I'm sure) the rest of the community here would be glad to help you out!

Nathan

---

### Post by RasutoIbuki on 2006-11-07
Being a Windows convert myself, I'd be happy to explain this in a bit more detail than others have here.

> 
First, is the Linux version thing, there are so many, is the software compatible? (ie. will something made for SuSi run on ubuntu). Anyways, I always down load software that states it's compatible with ubuntu just to be safe.

There are many different distributions of Linux, all of them are, essentially, the same. There is no difference between SUSE and Ubuntu other than the graphics and software that comes OOB (Out of the Box). Some have different installers, different ways of packaging programs, and different ways of handling various things, but, in the end, it's all the same. So, is the software compatible? Yes, it is, but each distro has it's own unique way of dealing with how to install it.

> 
Second, is the file extension thing, .rpm .dev and so forth. I've read the article about installing software suggested on an beginner tread([http://www.psychocats.net/ubuntu/installingsoftware)](http://www.psychocats.net/ubuntu/installingsoftware)). It suggests going to the command line to run .rpm or .dev, (command line! are we back to DOS know?) After trying the command line thing, I find that I have to install additional features like "aptitude update" and "aptitude install alien" to try and get the software I want to run.

It's important to realize that even on Windows when you install a program all it does is unpack the files (and sometimes add things to the registry), so installing a program is just putting files in their places.

Each file extension such as RPM and DEV only specify the different software used to unpack and 'install' the program you want. RPM uses a different system than DEV, however, all of the files inside are the same. That's where alien comes in, think of it like this: on Windows you get software from an EXE that unpacks the files and puts them in the right places, other times, it's a ZIP, you extract the files from the ZIP to the right place, or a RAR. So, Ubuntu uses DEV packages with it's distro, you find a program that came as an RPM, you use alien to convert the RPM into a DEV. Then you can use the package manager in Ubuntu that unpacks the DEV to where it needs to go. The only problem I've ever had with this is that different distros have their menus configured differently, so you don't get the nifty icon, but that can easily be made. 

> 
Why doesn't the software just come in an .exe format like windows? you click on it, it installs, done deal. I'm not here to bash Linux or any system, it just seems to me that if you want people to cross over it's got to be easier. If I’m missing the boat here can someone please explain it to me (in beginner terms).


Once again, you have to understand that when you double click that EXE it just -unpacks- the files to the correct places, if you found software on Windows that came in a ZIP you'd have to do that manually as well. There are many ways to do one thing, I sometimes feel that one of Linux's best points is also a downfall for new users, the diversity. It's very confusing at first and it's hard to understand and grasp which way works best for you, but, once you get used to it and keep trying your best at it, you'll find out that these things that confuse you now will turn into something you're thankful for.

One of the best features that Ubuntu has are it's package managers that use repositories. Repositories (they may be called something different for adept users) are a network accessible storage system that contains the software. You search for the software in the repository and if it's there the package manager retrieves the files for you and puts them in the correct place, this way, you don't have to deal with converting from RPM to DEV or that missing icon. There are many many repositories out there that you can add to your configuration files, this increases the range of software that is available to you and I'm sure many people here can help you out with that.

I hope that I helped you out at least somewhat, if you need anything, feel free to private message me, I'm perfectly happy to give out my googletalk/AIM screennames if you need to talk to me in real time as well.

---

