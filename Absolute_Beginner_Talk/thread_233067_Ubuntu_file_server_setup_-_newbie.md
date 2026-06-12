---
title: "Ubuntu file server setup - newbie"
date: 2006-08-09
forum: Absolute Beginner Talk
---

### Post by riverman on 2006-08-09
Hi everyone :)  I'm interested in trying out some kind of Linux distro; Ubuntu has piqued my interest. I'm thinking of getting hold of a second-hand PC and using it to set up a home file server - nothing big, just somewhere to keep my growing collection of files. I'd like to be able to connect to my file server from my Apple iBook.

I'm looking for some advice on the following topics:

- what's the best flavour of unbuntu to go for? I was thinking of using the ubuntu server version.
- what should I look out for in my base PC? I don't think I'll be looking to use it as a fully blown desktop - no usb devices, no gaming, etc - but it would be nice to be able to hook up a display, a mouse, and a keyboard ;)  Forgive my ignorance, but I don't want to get hold of a PC and then not have it work with ubuntu. Most importantly, it's not going to be very high-spec (because it'll be old) so I need to know just how low spec I can go.
- is there anything else I should bare in mind in my project?

I'd be really grateful for some advice. I'm at home with computers (been using windows and then mac for nearly 20 years) but I'm totally new to any sort of Linux. Cheers in advance for any help.
:-D

---

### Post by kebes on 2006-08-09
This is my opinion. Everyone will have different advice on these topics, so take what we say with a grain of salt, and make up your own mind!

> **riverman said:**
> I'm interested in trying out some kind of Linux distro; Ubuntu has piqued my interest.
Ubuntu is a great place to start. It is a very well-polished and user-friendly Linux distribution. Good choice.

> I'm thinking of getting hold of a second-hand PC and using it to set up a home file server - nothing big, just somewhere to keep my growing collection of files.
Sounds like a good idea. Ubuntu is certainly up to the task of acting as a fileserver.

> what's the best flavour of unbuntu to go for? I was thinking of using the ubuntu server version.
I'm assuming this is your first Linux experience? If so, I would recommend just going with the standard Ubuntu install. This will be quite painless and give you a nice graphical environment to start with. You'll still be able to install all of the server packages, so nothing is lost. You can always uninstall the graphics stuff later if you really want to. The only reason I could see to deviate from the standard Ubuntu install would be if disk space is a big issue. Note that I personally prefer Kubuntu (the version that uses KDE as a desktop manager instead of GNOME), but both Ubuntu and Kubuntu are fantastic. The best way to start is to download the latest version install CD (Ubuntu 6.06 LTS, i.e. "Dapper Drake") and boot from that CD on your hardware. This "LiveCD" will let you test if your hardware is immediately detected, etc.


> what should I look out for in my base PC? I don't think I'll be looking to use it as a fully blown desktop - no usb devices, no gaming, etc - but it would be nice to be able to hook up a display, a mouse, and a keyboard ;)  Forgive my ignorance, but I don't want to get hold of a PC and then not have it work with ubuntu. Most importantly, it's not going to be very high-spec (because it'll be old) so I need to know just how low spec I can go.

The basic requirements are not too great. I have the newest Ubuntu running on a Pentium 3, 500 MHz with 768 Mb of RAM. A normal install will require about ~2 Gb of disk space and ~1 Gb for a swap space. A 10 Gb drive is enough for Linux to run happily (with plenty of software), but for a fileserver you'll probably want something bigger (depends how many files you are hosting!). Hard drive upgrades are not expensive.

Since this will be a 'headless' server (eventually) you don't need any sound card. Any graphics card will do fine, so you can really get the most basic one and Ubuntu will probably recognize it.

I imagine you could even run on lower-spec hardware than I described. (P3 300MHz?) A second-hand computer like what I described above will not cost very much (<100$).

> is there anything else I should bare in mind in my project?

The computer will need an ethernet card (obviously!). Wireless can be a pain sometimes in Linux, so stick with ethernet unless that's impossible. For a fileserver a decent sized hard-drive is crucial. The graphics card, on the other hand, doesn't matter (motherboard integrated graphics might be the best choice).

> I'm at home with computers (been using windows and then mac for nearly 20 years) but I'm totally new to any sort of Linux.

You shouldn't have too much trouble with Linux, then. It takes some getting used to, but the power is truly amazing once you get the hang of it. The Ubuntu forums have tons of good advice if you ever get stuck.

Post again if you need any further clarification, or have other questions.

---

### Post by riverman on 2006-08-12
Thanks for an excellent, detailed reply. Now that I've done a bit more research - and read your comment - I have a few more questions.

1) You say that I could install the standard version of Ubuntu and then install the 'sever stuff' later. How easy would it be to get LAMP up and running on Ubuntu Desktop? That's something I'd like to do at some point in the future. I noticed that Ubuntu server has LAMP pre-configured and ready to install; is this a good reason to go for the server edition (maybe with Gnome or KDE added on later), or is it just as easy to install and configure LAMP on the desktop edition, manually?

2) Hardware options sound good - I'm suprised at the relatively low spec required, which, when you're trying to get a PC for free like I am, can only be a good thing. But you say that Linux is patchy with wireless. Could you elaborate? I'd like to access the file server wirelessly if at all possible - rather than on ethernet - so I'm willing to work on it. I'd like to know what hardware is compatible before I buy anything.

3) Kubuntu vs Ubuntu: is the desktop environment the only difference? Just asking out if interest really.

Thanks again.

PS: I am new to Linux, but I've got some experience on UNIX in Mac OS X. So, I'd be happy messing around in the Linux terminal or command prompt to get things sorted out, as long as the Terminal procedures weren't too complex.

---

### Post by kebes on 2006-08-12
> **riverman said:**
> 1) You say that I could install the standard version of Ubuntu and then install the 'sever stuff' later. How easy would it be to get LAMP up and running on Ubuntu Desktop? That's something I'd like to do at some point in the future. I noticed that Ubuntu server has LAMP pre-configured and ready to install; is this a good reason to go for the server edition (maybe with Gnome or KDE added on later), or is it just as easy to install and configure LAMP on the desktop edition, manually?

Well it's one of those "six of one/half-dozen of the other" situations. You can install LAMP on the desktop version easily and you can install a desktop manager on the server version easily.

My advice: if you are new to Linux and don't know much about the unix command-line, then you should install the normal Ubuntu, play around a bit, and install your LAMP stack from there. You can install your server packages either using command-line arguments, or (if you get frustrated with that!) use a graphical package manager (called "Synaptic" on Ubuntu or "Adept" on Kubuntu). If this is your first Linux experience, it will be less 'painful' and an easier way to learn things about Linux. (Because, for instance, you'll have easy access to a GUI web-browser when you get stuck!)

If, on the other hand, you are quite comfortable with command-line work, and/or have some programming experience, then you could certainly start with the server version. That way you will have your web-server and all that installed without any effort. As you said, you can install a desktop manager should you desire.

In terms of "how easy," it's really amazingly easy once you get the hang of the "Linux way" of installing software: which is that everythign is automatically downloaded and installed from central repositories. Thus, after a basic dekstop install is done, it's really as easy as issuing these in a terminal:
$ sudo aptitude update
$ sudo aptitude install apache
$ sudo aptitude install mysql
$ sudo aptitude install php
...etc...
Alternately you can just pick the packages "Apache Webserver", "MySQL database server", "PHP 5 Environment" from the graphical package manager. Typically these installs proceed with no errors. Everything is downloaded, and installed for you, including any missing dependencies. You have to do some editing of configuration files afterwards, but nothing too complicated.

Conversely on the server version you can install a desktop environment easily:
$ sudo aptitude update
$ sudo aptitude install gnome-desktop

That's it, really. Personally, I've always done a "standard install" and then added the server packages, and it has always worked quite well. Of course the forums are available if you run into problems.

I'm sorry I can't give you a definitie "do it this way" kind of answer. Both will work and have pros/cons. Luckily a standard Ubuntu install is quite fast (assuming nothing strange happens). You can install it one way, play with it, and then install it the other way. No big deal.

>  2) Hardware options sound good - I'm suprised at the relatively low spec required, which, when you're trying to get a PC for free like I am, can only be a good thing.

Yes it's refreshing how optimized the Linux kernel really is. Like I said I'm running the newest Kubuntu on hardware that is 6 years old. It works perfectly as a server, acting simultaneously as a web-server, file-server, and mysql database. I must admit that the desktop environment is a little slower than I would like... but that's to be expected. It is certainly useable.

> But you say that Linux is patchy with wireless. Could you elaborate? I'd like to access the file server wirelessly if at all possible - rather than on ethernet - so I'm willing to work on it. I'd like to know what hardware is compatible before I buy anything.

Well there are of course many options. For instance what I do is have a wireless router that also has ethernet ports. The router is beside the Linux server and is connected via ethernet cable. So since I can access my wireless network, I do indeed have "wireless access" to my Linux server. This works great and was painless to install.

If however your configuration absolutely requires the Linux server to be using a wireless card, then this is a little more difficult. It's by no means impossible to get wireless working on Linux, it's just less straight-forward. If you're preparred to try a few things I'm sure you can get it to work. Also, if you are planning on buying a card then you should be okay--just buy a card that is known to work. I only issued the caution because most hardware is auto-detected and works perfectly using Linux... but wireless is one case where not all hardware will work.

Obviously the first thing to do is some online searches and see what cards have the best support under Linux. For many cards there is a stable open-source driver that will autodetect and make the card work immediately. For other cards you can use something called "ndiswrapper":
[http://ndiswrapper.sourceforge.net/](http://ndiswrapper.sourceforge.net/)
[http://en.wikipedia.org/wiki/NdisWrapper](http://en.wikipedia.org/wiki/NdisWrapper)

Which allows you to use the Windows driver supplied with the card in your Linux environment. I've been told that using ndiswrapper can require some effort.

This page:
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)
lists a wide range of different cards, and gives an idea about whether it typically "just works" out of the box. Pick a card that is supported and meets your needs and then do a search on the Ubuntu forums, to get an idea if people have generally met with success or failure with the card (of course people typically post when they have problems, not when everything works perfectly!).

I've never set up a wireless card in Linux, but I imagine if you pick a supported card it will be auto-detected like everything else.


> 3) Kubuntu vs Ubuntu: is the desktop environment the only difference? Just asking out if interest really.

Yes that's really the only difference! Ubuntu uses the GNOME desktop and Kubuntu uses the KDE desktop environment. You can change a Ubuntu install into a Kubuntu install by simply typing:
$ sudo aptitude install kubuntu-desktop
In fact you can have both GNOME and KDE on your system and switch between them, allowing you to try them both and find the one you prefer. The desktop environment doesn't change the "guts" of your Linux install, just the way you interact with it. Gnome is sometimes considered "more elegant" and KDE considered "more customizable"... both have pros and cons. (If you care, I prefer KDE, but Gnome is great too.)


> PS: I am new to Linux, but I've got some experience on UNIX in Mac OS X. So, I'd be happy messing around in the Linux terminal or command prompt to get things sorted out, as long as the Terminal procedures weren't too complex.

If you like the Mac OS X terminal then you'll be quite comfortable in Linux. All the unix commands are available. Linux is a little bit more "commandline-centric" than OS X. In OS X you can do everything without ever thinking of the terminal. In Linux, some things are much easier in the terminal, so getting used to it is a good thing. If you're going to be running a server it's obviously good to be comfortable with the commandline so that you can remotely login (SSH) into your machine and make changes.

I've only been using Linux for about two years now... but I love the power it affords. Ubuntu is really a great distro and I'm happily switching my machines over to it now! Hope it works out for you, too. If you have any more questions, feel free to post to this thread again or start another one!

---

### Post by riverman on 2006-08-14
> ...what I do is have a wireless router that also has ethernet ports. The router is beside the Linux server and is connected via ethernet cable. So since I can access my wireless network, I do indeed have "wireless access" to my Linux server. This works great and was painless to install.

Just after I'd submitted my last post, I realised I could do the same thing. I have a Netgear wireless router with a built-in moden and ethernet ports so hopefully I'll be able to get the whole set-up running without too many issues.

> I'm sorry I can't give you a definitie "do it this way" kind of answer. Both will work and have pros/cons. Luckily a standard Ubuntu install is quite fast (assuming nothing strange happens). You can install it one way, play with it, and then install it the other way. No big deal.

Again, I'd come to the same conclusion myself, but it's nice to hear it from someone with more experience. I think after working with Windows for so long, I'm still in the habit of thinking, "get it right the first time or I'll have to re-install *everything*". I'm coming over to Linux for just this reason. That, and the fact that it's free :D 

> on the server version you can install a desktop environment easily:
$ sudo aptitude update
$ sudo aptitude install gnome-desktop

I've read that using aptitude (rather than apt-get) makes it easier to un-install packages in the future. Any thoughts on this? It's something I may need to do, as space will probably be limited.

---

### Post by kebes on 2006-08-14
> **riverman said:**
> Just after I'd submitted my last post, I realised I could do the same thing. I have a Netgear wireless router with a built-in moden and ethernet ports so hopefully I'll be able to get the whole set-up running without too many issues.

You should be able to hook that up to Linux without any issues. Plus, if you already have the hardware, that's certainly cheaper!


> Again, I'd come to the same conclusion myself, but it's nice to hear it from someone with more experience. I think after working with Windows for so long, I'm still in the habit of thinking, "get it right the first time or I'll have to re-install *everything*". I'm coming over to Linux for just this reason. That, and the fact that it's free :D 

Indeed! There are lots of reasons why I love Linux! I'm sure you've heard all the usual ones (stability, power, freedom, etc.), and the fact is they really are true! It takes a bit of work, but the payback is great. Earlier today I set up a webserver on a friend's new Kubuntu install. We did the entire thing remotely (via SSH) and it literally took 10 seconds. Rather cool.


> I've read that using aptitude (rather than apt-get) makes it easier to un-install packages in the future. Any thoughts on this? It's something I may need to do, as space will probably be limited.

As far as I know there is no reason to ever use "apt-get"... always use "aptitude". Aptitude is a wrapper for apt-get (it calls apt-get in the background), but it does additional logging. As you said, this helps make removing packages easier. It's best to always use aptitude so that the records it keeps are up to date. I've never needed to use apt-get directly, since all of apt-get's command-line functions are available in aptitude.

Note, however, that occasionally you may have to invoke the "dpkg" command (which apt-get calls to actually do the packaging). It has some special modes (notably "dpkg --configure -a") that can be helpful in fixing problems.

---

### Post by riverman on 2006-08-15
> **kebes said:**
> As far as I know there is no reason to ever use "apt-get"... always use "aptitude".

Thanks, that's what I'll go for then. At the moment my plan is to get Ubuntu Desktop up and running on an old box, then do an re-install of just the LAMP Server once I've got used to the system. I like the idea of building the system up from scratch (I learn more that way) but I think I need a bit of a gentle intro on the Desktop version first. I'll probably add a desktop environment to the LAMP server (Gnome/KDE...oh, the choices! Never had this with windows :D ); I'll do this just so I can fall back on the GUI apps when I need to. What I really want to do, in the long term, is to learn to admin the whole thing remotely using ssh. That, though, will probably be the topic of another post!

Cheers for the help, kebes. This was my first post on the ubuntu forums and you've made me feel really welcome. Hopefully I'll be putting something back in the form of advice of my own when I've learnt something!

There's some other things that have come up while I've been looking into this, but I'll start some new threads once those thoughts mature a bit. For now, I think I've found out everything I need. Thanks!

---

