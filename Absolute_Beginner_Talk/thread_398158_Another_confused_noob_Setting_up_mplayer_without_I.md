---
title: "Another confused noob: Setting up mplayer without Internet connection"
date: 2007-03-31
forum: Absolute Beginner Talk
---

### Post by leecou on 2007-03-31
Hey everyone,

I'm a completely new Ubuntu user having spent all my life using Windows.

I have an old compaq P4 that I want to use as a media centre. all i want to do is play DVD's and avi files on it through my tv. The media PC has no internet access.

The nice people over at the Linux Forums gave me loads of info about setting up Linux and I have chosen Ubuntu and installed it(V6.06 from a live CD) on my computer. I've searched through the forums here and solved a few issues but there are a couple of bits that I could use some advice on.

I want to run the PC without a keyboard (space is an issue, I don't want to buy a wireless one and I really have no need for one with what I'm using the PC for). I've tried to get the on screen keyboard to work, but evertime I launch it nothing happens (double click, run - none of these get it to start up.

I also want to install Mplayer to play the avi files but I'm having a nightmare. 

I've downloaded the mplayer files (and the codec files) to a USB stick, but can't see either the USB or mplayer using the "add/remove" tool. I tried double clicking the mplayer folder but don't recognise anything in there (what's the Ubuntu version of a .exe file?).

I've also looked at the installation notes for installing via a command line. Just one problem - where do I find the command line????

Any and all help is really greatfully received. I've spent most of the day getting this far but am now stuck fast.

Cheers

L

---

### Post by useResa on 2007-03-31
You can find the "command line" by starting a terminal. This is done via the menu Applications --> Accessories --> Terminal.

Furthermore, if you like to install mplayer, this is available in the repositories of Ubuntu and thus you can install it using Synaptic or by issuing the following command```
sudo apt-get install mplayer
```

Hope this will help you move forward

---

### Post by leecou on 2007-03-31
useResa, you Sir (or madam) are a hero.

Ok tried that and got an error message E: Couldn't find package mplayer.

I've got the mplayer package on a memory stick. Can I point the command line to that for  the package install?

L

---

### Post by Zuuswa on 2007-03-31
useResa, he says he has no internet connection on that computer, so apt-get wont work like that.

As to the package, if it is a file with .deb at the end, then all you need to do is double click on it and it should install, although since you arent connected to the internet I am not sure if you will be able to get all the dependancies for it.

---

### Post by useResa on 2007-03-31
> **Zuuswa said:**
> useResa, he says he has no internet connection on that computer, so apt-get wont work like that.
I agree, my mistake. I missed out on this.

If I stick a memory stick into an USB slot, an additional "drive" is displayed on the desktop. Is this also the case in your situation?
Could you also indicate what the extension is of the package that you have for mplayer (is it .deb)?

BTW: I'm male, but you don't have to refer to me as sir (makes me feel so old) ;)
Regards.

---

### Post by leecou on 2007-03-31
Right then

When I dock the USB stick I can see it on the desktop. I downloaded mplayer from the mplayer website and downloaded this version

*MPlayer v1.0rc1 source*

I'm not sure what the extension is as there are loads of folders in the download (including a debian one) but there are no .deb files

Thanks for all your help guys

L

---

### Post by annda on 2007-03-31
sources need to be compiled first, and you don't need that, because somebody has done it for you first.

get your packages from

[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

they are already compiled and packaged for ubuntu, all dependencies are listed so make sure you download them too. and start double-clicking with dependent packages on the .deb's.

that's what it looks like for mplayer in dapper:
[http://packages.ubuntu.com/dapper/graphics/mplayer](http://packages.ubuntu.com/dapper/graphics/mplayer)

you probably have most of the dependencies installed by default, so there's no need downloading them. check system > administration > synaptic to see what you have.

p.s. using ubuntu without an internet connection can be troublesome but since it's not your main machine and you just need a few applications, your suffering will be short - until you get everything up and running.

---

### Post by leecou on 2007-03-31
Thanks for the help. I'll check these out in the morning.

I only need the machine to do two things - play avi files and have an onscreen keyboard. Once thats done there should be no reason to change it.

That probably won't stop me changing either my home pc or laptop to Linux at some point :)

---

### Post by leecou on 2007-03-31
I've had a quick go with the mplayer download.

Download went ok but I'm getting a dependancy message. Sorry annda, I think I'm being stupid but I can't see the dependancy that you mention at the link you supply.

I'll have another look in the morning

Thanks for all your help guys. Anyone got any ideas on the original keyboard questions?

Cheers

L

---

### Post by wj32 on 2007-03-31
If you get dependency errors, then look for those packages as well and install *them* first.

---

### Post by annda on 2007-03-31
dependencies are marked with a red dot.

as i said, no need to download them all. check synaptic first.

good night and good luck!

ps. tell us more about the on-screen keyboard trouble. i can't find it anywhere on my system, so how do you launch it?

ps. 2 a personal rant here:
> I think I'm being stupid
please don't call yourself stupid. i'm so tired of reading this. you are simply not experienced with linux/ubuntu, it doesn't make anyone stupid. i know it's just a figure of speech, but it hurts to read people calling themselves names.

---

### Post by leecou on 2007-04-16
Hey all,

I've managed to get some free time to get back to resolving my problem (I want to install and run mplayer on an on compaq box running Ubuntu 6.06 but without an internet connection).

So i downloaded (on another machine) the mplayer.deb file (thanks for helping me find it). double clicking it gives me a "dependency not satisfied" error for libartsc0. I then downloaded the .deb file for that and got a libc6 error. I downloaded the .deb file for that and got a tzdata error. I downloaded the .deb file for that and got a "Faled to install package" error mesage and a black box.

I'm now struggling.

Does anyone have any ideas (in simple words) what the hell I'm doing wrong? Any and all ideas greatly welcome

L

---

### Post by annda on 2007-04-16
you are doing it right. it's so tedious because you can't work with apt-get or aptitude because you don't have internet aceess.

try to download tzdata again.

---

### Post by Maestro23 on 2007-04-16
> **annda said:**
> you are doing it right. it's so tedious because you can't work with apt-get or aptitude because you don't have internet aceess.

try to download tzdata again.

Yeah.  Keep plugging away at it this way.  Since you have no access to the repositories.  I know it is painful.

Be thankful that the packages site is there though.

---

