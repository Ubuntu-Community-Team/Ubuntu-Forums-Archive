---
title: "New to Linux"
date: 2007-07-10
forum: Absolute Beginner Talk
---

### Post by smgajg on 2007-07-10
Hello, I am brand new to linux and Ubuntu. I recently purchased an Acer Aspire Laptop model 5610z, it came preloaded with Vista which I immediatley new had to go because the performance was horrible. I decided to go the way of many of my coworkers and take the Linux plunge and decided on Ubuntu. It seemed like the least formiddable. I was able to easily download, image, and install on my new laptop the Fiesty Fawn version. My first feeling of success, however this was not to last.

Currently I am unable to get even the most of basic of functions to work, I dont know how to get information off of a cdrom, dvdrom or the like.

I cannot get my music to play since the all my files are MP3's and I have read that they must be converted.
I did however download Amarok in hopes I could give it a try but when I click on what looks to be the executable file I get an error, What am I doing wrong. 

I have no internet accessability.

I think I need some step by steps for many of these problems and I will be just fine. I have tried finding things to read but I seemingly get more confused. I dont understand why many of the available software plugins from my disk were not loaded, I get an message that says the manufacturer did not support my i86 mode or something like that.

Ok as i said before,I just need to get the bugs worked out and I am sure I will be as happy as everyone else seems to be with Ubuntu.

Thanks
A

---

### Post by swoll1980 on 2007-07-10
Open up synaptics package manager put restricted codecs in the search box and install them this will solve music problems

---

### Post by swoll1980 on 2007-07-10
system>admiastration>synaptics

---

### Post by swoll1980 on 2007-07-10
are you broadband or 56k?

---

### Post by sloggerkhan on 2007-07-10
Based on what you say, most likely you tried installing software from websites instead of using the repos. MP3s will play on linux. You should probably look at [https://help.ubuntu.com/](https://help.ubuntu.com/) and read through the categories.

---

### Post by Jem00 on 2007-07-10
Didn't you understand swoll1980 he has no internet accessibility.

Smgajg are you using a wireless or  wired connection??

---

### Post by regomodo on 2007-07-10
mp3s will play, unconverted, on linux (easily) assuming you have internet access. If not you'll have to install packages manually by downloading them externally and then installing them. A pita for a newb.

1st thing to do would be sort out the internet access. Makes life so much easier

your "media" folder contains all your drives

{edit} cheers for the post nalinde. I'm trying that as i speak. All that bandwidth going to waste. Might as well use it

---

### Post by swoll1980 on 2007-07-10
> **Jem00 said:**
> Didn't you understand swoll1980 he has no internet accessibility.

Smgajg are you using a wireless or  wired connection??

An important overlook on my part lol

---

### Post by ubuntu27 on 2007-07-10
**smgajg** _Ubuntu_ Linux is what I called a Internet based Linux Distribution. 
You need Internet Access (Broadband preferably) for many things. 

How did you post in this forum if you don't have Internet? 


Well, I guess you have two computers.

If you have Internet Access, simply follow this guide: [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

If you don't, you will have to use another computer that has Internet Acess and
Go to the following website, and download the needed packages. 

[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

Need packages is:

[ubuntu-restricted-extras]("http://packages.ubuntu.com/feisty/metapackages/ubuntu-restricted-extras")

---

### Post by nalinde on 2007-07-10
Hi smgajg and welcome to the community :-D

First of, there is a fatal thingy to take notice about, Ubuntu is not windows :-)

Unfortunately i don't know what you mean with your first question "Currently I am unable to get even the most of basic of functions to work, I dont know how to get information off of a cdrom, dvdrom or the like." please explain to be a littl

About the mp3:s. You absolutely don't have to convert your mp3:s to an other format as ogg. You can listen to them in ubuntu very easily.
UNFORTUNATELY, to be able to play mp3 and others you will have to download some packages (library's) to get it to work.

This packages ( and other programs) you download from something you call repository's. This repository's you will find in the program Synaptic. that requires an internet connection to work.

But if you got access to an internet connection elsewhere i would recommend this ["How to"]("http://ubuntuforums.org/showthread.php?t=352460") where you burn down  the repository to a DVD.

A other way is to download .deb files  (the Debian/Ubuntu .exe file). You can find this here [packages.ubuntu.com/]("http://packages.ubuntu.com/") and [www.getdeb.net]("http://www.getdeb.net"). (The repository's is a collection of .debs)

---

### Post by macogw on 2007-07-10
If there's somewhere that you can get access to the internet and a DVD burner, you can download all of the repositories to a set of 6 DVDs and then install from them whenever you want.  The .iso's are linked to on ubuntuguide.org

---

### Post by smgajg on 2007-07-10
Hi All, thanks for the quick responses. I didnt think I would get any so this is a very pleasant surprise. Seems like there are few questions you all had so I will try to answer to the best of my ability.

1. Yes I have an XP box that I am able to get online with but I do plan on "upgrading" that as well once I get comfortalble. However, my laptop is unable to connect to anything. I can go either wireless or dial up depending on where I am at.

2. Would love to hear more about the 6 dvds (10th poster) that contain all the images and how to get them and what have you.

3. I do realize that this is UNIX based and I am familliar with some UNIX commands so that dosnt scare me off, I am just really rusty on it as it has been years since I have fooled around with it. I work in a microsoft world so that is the bain of my existance :)

4. As far as not being able to do anything from the CD I guess the fact that Ubuntu is an internet based OS makes sense, so I am guessing the file types that most resemble .exe files are not and consequently not launchable from the desktop perse?

Thanks Again!!
A

---

### Post by macogw on 2007-07-11
The files that are like setup.exe (I wouldn't say they're like all .exe's as regular .exe's could launch anything) are .deb packages.  Each one installs one thing.  In the UNIX way of thinking, they each do one task, and do it well.  That means that instead of installing 50 of the same libraries with 2 different programs like you would on Windows, you install those 50 libraries once and they share them.  But that means you need to get all 50 of them.  The package manager handles that for you when you have an internet connection.  Without one, you're going to have to do it the more annoying way and install the libraries, making sure you install ones that the others depend on first.  If you have a deb sitting on your desktop, you can double click it and GDebi will come up and offer to install it.  If it says there's an unresolved dependency, you need to install that dependency first.  

Hmmm ubuntuguide.org doesn't have a DVD link set for Feisty.   A quick Google shows this [http://on-disk.com/product_info.php/products_id/278](http://on-disk.com/product_info.php/products_id/278) They're selling a set for Feisty for $30 on 5 DVDs.  Or you can download and burn a 4 DVD set from here [ftp://tuma.ui.edu/pub/ubuntu-repository/7.04/](ftp://tuma.ui.edu/pub/ubuntu-repository/7.04/) (assuming this is 32-bit, you'll need the i386 .isos 1-4  Don't worry about figuring out the Jigdo stuff.

---

### Post by Frak on 2007-07-11
> **smgajg said:**
> 1. Yes I have an XP box that I am able to get online with but I do plan on "upgrading" that as well once I get comfortalble. However, my laptop is unable to connect to anything. I can go either wireless or dial up depending on where I am at.

What brand is your wireless, what model, and is it internal or external?

> **smgajg said:**
> 3. I do realize that this is UNIX based and I am familliar with some UNIX commands so that dosnt scare me off, I am just really rusty on it as it has been years since I have fooled around with it. I work in a microsoft world so that is the bain of my existance :)

UNIX commands do help, but Linux is NOT UNIX or Windows, we just like to establish that early with new comers. As they can sometimes gripe at us because its "not a better windows", but most don't understand that Linux is NOT a Windows replacement, just an alternative.

> **smgajg said:**
> 4. As far as not being able to do anything from the CD I guess the fact that Ubuntu is an internet based OS makes sense, so I am guessing the file types that most resemble .exe files are not and consequently not launchable from the desktop perse?

.deb 's are the .exe 's of Ubuntu, and try as hard as you can not to mess with .tar.gz 's or .tgz 's.
.rpm 's can be installed via a program called Alien.

---

