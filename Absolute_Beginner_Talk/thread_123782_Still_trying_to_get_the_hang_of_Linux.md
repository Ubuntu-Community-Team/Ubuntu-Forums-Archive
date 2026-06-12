---
title: "Still trying to get the hang of Linux"
date: 2006-01-30
forum: Absolute Beginner Talk
---

### Post by Mishal on 2006-01-30
I have been using computers since 1995 when I started with 3x86 machine and handling Windows is a joke for me. I can do a little bit of work in DOS too. So I thought I will ultimately figure out how Linux works.

But though I have worked out how to mount hard drives and changing the look of the desktop and some other stuff, it is installing programs that's pissing me off.

I can understand that you either write apt-get in the terminal or use Synaptic to install software THAT IS ALREADY THERE with the Ubuntu package. But what completely baffles me is how to install software that I downloaded from the internet.

I have downloaded XAnim but I have no clue how to install it. And then what about DivX? Ultimately, I want to have the freedom of installing anything I like without being stuck within the boundaries of what's shown in Synaptic. So, somone please help :( 

Isn't there a standard way of installing all software? I hope I don't sound like a sissy but the 'Windows' way of pressing a few 'next' buttons was much easier to install stuff.

---

### Post by matthew on 2006-01-31
This will get you started...

[http://www.psychocats.net/linux/installingsoftware.php](http://www.psychocats.net/linux/installingsoftware.php)

---

### Post by aysiu on 2006-01-31
See the second link of my signature.
In other words, no.

The only "standard" apart from ```
sudo apt-get install blah
``` is ./configure make make install...

---

### Post by WindowsIsaPain on 2006-01-31
[QUOTE=Mishal]I have been using computers since 1995 when I started with 3x86 machine and handling Windows is a joke for me. I can do a little bit of work in DOS too. So I thought I will ultimately figure out how Linux works.

But though I have worked out how to mount hard drives and changing the look of the desktop and some other stuff, it is installing programs that's pissing me off.

I can understand that you either write apt-get in the terminal or use Synaptic to install software THAT IS ALREADY THERE with the Ubuntu package. But what completely baffles me is how to install software that I downloaded from the internet.

I have downloaded XAnim but I have no clue how to install it. And then what about DivX? Ultimately, I want to have the freedom of installing anything I like without being stuck within the boundaries of what's shown in Synaptic. So, somone please help :( 

Isn't there a standard way of installing all software? I hope I don't sound like a sissy but the 'Windows' way of pressing a few 'next' buttons was much easier to install stuff.[/QUOTE]

Hi,
This is my first post I would describe my knowledge as probably very much the same as yours. I found this page, [https://wiki.ubuntu.com/DebInstaller?highlight=%28deb%29](https://wiki.ubuntu.com/DebInstaller?highlight=%28deb%29)   but it seems to further add to my confusion. I wonder if my, unmountable floppy problem can be solved by either downloading a newer version of Ubuntu and going through the whole install again. There is no easily folowed directions. Can some one please point to a complete and easy to follow guide? How do you find out what the status is of the latest Ubuntu?
Kind regards

---

### Post by Mishal on 2006-01-31
> I can't think of a program off the top of my head that I ever needed to install from source
This is a quote from [http://www.psychocats.net/linux/installingsoftware.php](http://www.psychocats.net/linux/installingsoftware.php)

Unlike him, almost every software I want to install is not available in the Synaptic Manager. Xmms, Mplayer, d4x, Gnomebaker etc etc.

Most the readme files in within the tar file of the above software say that I have to "`cd' to the directory containing the package's source code and type
     `./configure' to configure the package for your system"

Okay, so when I do it, there is some sort of error or the other. And of course, there are hundreds of lines of code telling me what's gone wrong. But surely, there's an easier way out?

After all, Linux should aim to become more friendly towards people who are shifting from Windows. Trying to understand and write code in a terminal is hardly a red-carpet welcome, is it? :D

---

### Post by aysiu on 2006-01-31
Unfortunately, that's where it is.
There are basically three types of Linux users right now:

1. Low skills, low needs.
2. High skills, high needs.
3. Low/medium skills, high needs.

Luckily for me (I wrote that webpage, by the way), I'm in group #1, so Synaptic suits my needs. A lot of users in Ubuntu are in group #2.

Unfortunately, for now (this may change soon), you're in group #3. So you kind of have to decide whether you're going to dumb down your needs to be in #1 or pump up your skills to be in group #2. I'm willing to bet it's the latter.

> After all, Linux should aim to become more friendly towards people who are shifting from Windows. Trying to understand and write code in a terminal is hardly a red-carpet welcome, is it? By the way, not everyone believes Linux should **aim** to be friendly towards ex-Windows users. Linspire believes it. Xandros believes it. Mepis and PCLinuxOS believe it. Slackware and Linux from Scratch definitely don't. I'd say Ubuntu falls somewhere in the middle.

---

### Post by RavenOfOdin on 2006-01-31
[QUOTE=aysiu]See the second link of my signature.
In other words, no.

The only "standard" apart from ```
sudo apt-get install blah
``` is ./configure make make install...[/QUOTE]

What about ```
sudo dpkg -c blah
sudo dpkg -i blah 
```

?

Does that fall somewhere in the middle? :D

---

### Post by Mishal on 2006-01-31
[QUOTE=aysiu]Unfortunately, that's where it is.
There are basically three types of Linux users right now:

1. Low skills, low needs.
2. High skills, high needs.
3. Low/medium skills, high needs.

Luckily for me (I wrote that webpage, by the way), I'm in group #1, so Synaptic suits my needs. A lot of users in Ubuntu are in group #2.

Unfortunately, for now (this may change soon), you're in group #3. So you kind of have to decide whether you're going to dumb down your needs to be in #1 or pump up your skills to be in group #2. I'm willing to bet it's the latter.

 By the way, not everyone believes Linux should **aim** to be friendly towards ex-Windows users. Linspire believes it. Xandros believes it. Mepis and PCLinuxOS believe it. Slackware and Linux from Scratch definitely don't. I'd say Ubuntu falls somewhere in the middle.[/QUOTE]
Thanks for your reply. You understand my problem well. Unfortunately, the solution isn't around the corner.

Can anyone help me solve the problems listed in the following code?

```
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking for C++ compiler default output... configure: error: C++ compiler cannot create executablesSee `config.log' for more details.

```

Thanks :)

---

### Post by mstlyevil on 2006-01-31
[QUOTE=Mishal]This is a quote from [http://www.psychocats.net/linux/installingsoftware.php](http://www.psychocats.net/linux/installingsoftware.php)

Unlike him, almost every software I want to install is not available in the Synaptic Manager. Xmms, Mplayer, d4x, Gnomebaker etc etc.[/QUOTE]

If you want those software packages all you have to do is one of two things. 1. Edit your sources list. This is a how to on doing just that. [Enabling Extra Repositories]("http://www.psychocats.net/linux/sources.php") 2. Install and run Automatix. Automatix has all those packages plus it will edit your sources list for you to enable extra repositories. [Automatix]("http://ubuntuforums.org/showthread.php?t=66563") Of these two it is the the easiest way to install those packages plus your codecs, FF 1.5, OO.o 2.0, JR2E, Macromedia Flash, Realplayer and DVD playback. You can get all these things both ways but Automatix will do all of them at once without having to use the command line except to install Automatix itself. It will save you the hastle of searching synaptic for each package since the are all listed on the menu upon startup. I hope this helps.

---

### Post by midwinter on 2006-01-31
Yeah, just enable multiverse/universe and you'll be good to go.

[https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)

I'd recommend learning how to enable/disable your sources and install these things yourself rather than use Automatix or anything.  You'll learn something.

---

### Post by mstlyevil on 2006-01-31
[QUOTE=midwinter]Yeah, just enable multiverse/universe and you'll be good to go.

[https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)

I'd recommend learning how to enable/disable your sources and install these things yourself rather than use Automatix or anything.  You'll learn something.[/QUOTE]

I agree with this overall but if you do not have the time or the patience to do it all manually then I would just use Automatix.

---

### Post by Mishal on 2006-01-31
But Automatix is just for Breezy Badger, isn't it? I am using Hoary Hedgehog :(

---

### Post by mstlyevil on 2006-01-31
[QUOTE=Mishal]But Automatix is just for Breezy Badger, isn't it? I am using Hoary Hedgehog :([/QUOTE]

Ok, then follow the guide for editing your sources list. It has the list for hoary in it also. After you update the list you can follow this guide to install most of what you need. [www.ubuntuguide.org](www.ubuntuguide.org)

---

### Post by Mishal on 2006-01-31
You guys are really helpful (and quick in replying!). :)

I found the software I needed in Synaptic after updating the source list. But forgive me for complaining so much but using Synaptic to download and then intall new software is duplicative. That's because everytime I reinstall Linux, I will have to redownload those packages all over again.

In Windows, I download the installers I need and keep them in a separate folder.  Whenever I reinstall Windows, I just intall those software from that folder of installers. That way, I don't even have to have an internet connection to get myself back up to where I was before the Windows reinstall.

But in Linux, it seems that you have be connected to a fat bandwith Internet connection perpetually. Isn't there any way I can store these packages somewhere and direct Synaptic to use these rather than download them next time I install them?

Thanks again for your help.

---

### Post by midwinter on 2006-01-31
Well.. you could maybe look at this [https://wiki.ubuntu.com/AptMoveHowto](https://wiki.ubuntu.com/AptMoveHowto) - there are a few more other methods I think but don't have any experience with any of this.  Maybe try a few searches.

---

