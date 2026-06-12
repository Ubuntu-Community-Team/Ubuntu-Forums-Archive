---
title: "My experience so far - please help (long post)"
date: 2006-05-10
forum: Absolute Beginner Talk
---

### Post by matthewgoyke on 2006-05-10
Hello all, my first of many posts:

I've been reading about linux alot lately so I decided it's time to give it my best. I figured I would have a head start after using Unigraphics CAD systems on old SGI and HP Unix seats. I was wrong.

I am getting nowhere after 20+ hours. I will not give up, I am stubborn. I want to stick with Ubuntu. I have spent these 20 hours reading/searching on this forum and google for answers, with no luck. The most frustrating part is some of them are simple instructions and even those give error messages and don't work.

First off, I installed Ubuntu 5.1 on my Dell Inspiron 9300 laptop (at home) and an older (2-3 years) pc at work. They are both dual boot Ubuntu 5.1/Win XP Pro. Installations went very well, no problems. After that nothing. I can't do anything.

First off: Is it possible to do anything without an internet connection? Most of the tutorials say use apt-get. I can't do this without internet. I do have Win XP pcs that are on the internet at both work and home. I was hoping to download some programs/files I need, put them on my flash drive and onto the Ubuntu pc's.

I wanted to use Inkscape (Adobe Illistrator equiv) at work. I downloaded the inkscape tarball and tried to use alien to convert to deb...errors, it didn't work. I forgot to mention that I used Synaptec PM to install the alien and build essentials packages. Alien still created a directory for inkscape with a bunch of files in it, even though the error message. I was hoping to use the sudo make install or ./configure commands to get this to work, but still no luck. I downloaded the latest alien tarball and I can't do a sudo make install or a make or a ./configure to get the letest Alien working. At this point I am angry because a few different tutorials told me that those are the commands used to install the program. I did get my Blender to work though, (smile) The Blender tarball simply extracted to a directory structure with a blender icon. It just works. This makes me happy. So I am completely frustrated, how do I install rpm's if I can't even get alien to work?

My second issue is wireless for my laptop. After reading many posts, this is going to be a tough one. I got nowhere the first day. Last night I got the wireless icon to appear in the upper right corner, it says signal 100% strength, but no packets are sending/receiving. I used iwconfig, ifconfig, lspci, and many tutorials to find out what card I have, download and install drivers, install and set up ndiswrapper. At least I feel like I'm making progress with this one. So close, but so far. This is on a dell wireless router. Any ideas?

I think if I can get my wireless card going, apt-get will save my life, until then, I am banging my head against the wall. Please help.

Matt

---

### Post by christhemonkey on 2006-05-10
Ok, easier than compiling everything from source;
You can do what me and many other ubuntu users who are offline on their ubuntu boxes do, 
you can go onto [packages.ubuntu.com]("packages.ubuntu.com") and search for what you want, collect the dependencies, copy them all onto a usbstick (or the like),

Then copy them onto your ubuntu box and type,
```
sudo dpkg -i /path/to/file/you/downloaded/package.deb 
```

This will (hopefully) install the program you need.

This can get a bit tiring though, as a program has dependencies, which have dependencies, which have depen..... and then your in dependency hell!

But dont let me put you off, you can have a usable offline ubuntu box.

Oh and i know nothing about wireless sorry!

---

### Post by aysiu on 2006-05-10
[QUOTE=matthewgoyke]
I am getting nowhere after 20+ hours. I will not give up, I am stubborn. I want to stick with Ubuntu.[/quote] Can I ask that you consider something else...? You can be stubborn and stick with **Linux**. That doesn't mean you have to stick with Ubuntu. > First off: Is it possible to do anything without an internet connection? Most of the tutorials say use apt-get. I can't do this without internet. I do have Win XP pcs that are on the internet at both work and home. I was hoping to download some programs/files I need, put them on my flash drive and onto the Ubuntu pc's. Ah, here's reason #1. Ubuntu **sucks** without an internet connection. While some other Linux distros (like Fedora, Debian, and Mandriva) provide additional CDs with additional software (which you can download and burn on another computer that *has* internet, Ubuntu does not. > I wanted to use Inkscape (Adobe Illistrator equiv) at work. I downloaded the inkscape tarball and tried to use alien to convert to deb...errors, it didn't work. I forgot to mention that I used Synaptec PM to install the alien and build essentials packages. Alien still created a directory for inkscape with a bunch of files in it, even though the error message. I was hoping to use the sudo make install or ./configure commands to get this to work, but still no luck. I downloaded the latest alien tarball and I can't do a sudo make install or a make or a ./configure to get the letest Alien working. At this point I am angry because a few different tutorials told me that those are the commands used to install the program. I did get my Blender to work though, (smile) The Blender tarball simply extracted to a directory structure with a blender icon. It just works. This makes me happy. So I am completely frustrated, how do I install rpm's if I can't even get alien to work? Here's once again why Ubuntu stinks for you. Without internet, it's difficult to get alien, find dependencies, or even compile from source (the packages necessary to compile from source are not included in the default installation). > My second issue is wireless for my laptop. After reading many posts, this is going to be a tough one. I got nowhere the first day. Last night I got the wireless icon to appear in the upper right corner, it says signal 100% strength, but no packets are sending/receiving. I used iwconfig, ifconfig, lspci, and many tutorials to find out what card I have, download and install drivers, install and set up ndiswrapper. At least I feel like I'm making progress with this one. So close, but so far. This is on a dell wireless router. Any ideas? Another reason you should consider using another distro. I don't know why ([some people have offered explanations for this](http://www.ubuntuforums.org/showthread.php?t=170434)), but not all distros have the same hardware detection. While one distro will recognize your wireless card straightaway, another will not.

Bottom line: It's fine to be stubborn about trying out Linux, but Ubuntu may not be the distro for you. I would recommend the aforementioned: Mandriva, Fedora, and Debian.

---

### Post by Kvark on 2006-05-10
Ubuntu comes with a single CD. It has one program for each task preinstalled and expects you to install any additional programs you want from the internet with apt-get/synaptic. If you don't have broadband on your Linux box then it's a PITA to download programs for your Linux box with another computer.

A better way is to get another distro. Look for a distro that comes on a whole bunch of CDs. Those ones have 5 programs for each task preinstalled and have all other programs included on the CDs so you can install anything you want without having to download it.

---

### Post by DA_uf on 2006-05-10
You can select only CD repositories, but for new packages, I suppose they will be .deb so you will still need to get alien built for rpm's.

The folks over at the Programming Talk forum are helpful for your manual build questions [http://ubuntuforums.org/forumdisplay.php?f=39](http://ubuntuforums.org/forumdisplay.php?f=39)

---

### Post by RavenOfOdin on 2006-05-10
You could download via Windows and put what you need on a shared partition accessible from both systems, but without a broadband connection or some back up to do that with you're SOL on that one.

---

### Post by matthewgoyke on 2006-05-10
Thanks for the responses so far. I was hoping this was the distro for me. I checked a few out and I like the way this one looks and feels the best. I'm not giving up on it yet, but at least I won't feel bad if/when I do.

Matt

---

### Post by steve.horsley on 2006-05-10
It's a great distro, provided you have decent internet bandwidth. 0 bandwidth is a real problem. You might try Mandriva - it comes as about 3-5 CDs I think. I don't know about suse or Fedora. 

If wireless is the issue, give the Ubuntu Dapper Beta a whirl - it may be able to drive the wireless card out of the box.

---

### Post by matthewgoyke on 2006-05-10
actually i just installed dapper. i'm not connected, but it recognized everything. any suggestions on what's next? what is the gateway address?

---

