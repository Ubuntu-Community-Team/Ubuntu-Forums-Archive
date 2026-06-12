---
title: "So many problems!!!! help a poor n00b out?"
date: 2007-09-13
forum: Absolute Beginner Talk
---

### Post by buddhacub1120 on 2007-09-13
I have so many problems right now I don't know even where to begin. Should i start with how icons on my task bar or system tray or w/e it's called are not appearing and my programs such as GAIM are closing instead on minimizing? or should i start with no matter what  way i try to install flash and java, NOTHING WORKS! grrr i'm getting aggrivated. i'm very much so a n00b but have been having some non-n00b friends help me out but they only know so much...please help? 



:confused: ](*,)

---

### Post by Maestro23 on 2007-09-13
Step away from the keyboard and take a deep breath. It's going to be OK :smile:

Since you seem to have a multitude of issues, I suggest taking a look at:

Feisty Starter's Guide: [http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty)

Start working one issue at a time. Things will start to fall in place.

---

### Post by buddhacub1120 on 2007-09-13
ok so maybe im not as much as a n00b as a ithought. i have looked through the various and officals guides when i needed help or what not but there just seems to be so many kinks that as soon as i get one out, another one pops in. 


the biggest thing for me right now is gettin java and flash working. i need an older version on firfox apprently...can you point me in the right direction?

---

### Post by buddhacub1120 on 2007-09-13
and here's the other most annoying kink for me right now....firefox randomly not working. never had this problem before....

---

### Post by Perfect Storm on 2007-09-13
first:
Have you set up your sourcelist (enable universe,  multiverse and mediabuntu)

If you don't use all these flashy add-ons I also recommend epiphany browser (lihgtweight browser), instead.

---

### Post by ROUBOS on 2007-09-13
Hi there. I'm a noob too and my suggestion might not be a good one.
How about backing up your files and then re-install ubuntu. Then you can go through the guide and set things up properly from the beginning again.
That's what I'm about to do.
Maybe that's a windower$ approach but what can I say. Might be worth it since you trying to fix things up and more problems pop up.
Just a thought. 

Good luck.

---

### Post by NIT006.5 on 2007-09-13
Personally, to get flash and java going (among other things), I would recommend that you install Automatix and let it do all the work for you. The text below is an extract from another post on the forum somewhere, but I can't remember where or who posted it. I've used this on every installation I've ever done and I've never had any issues, so hope it helps:

echo "deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main" | sudo tee -a /etc/apt/sources.list

wget [http://www.getautomatix.com/keys/automatix2.key](http://www.getautomatix.com/keys/automatix2.key)

gpg --import automatix2.key

gpg --export --armor E23C5FC3 | sudo apt-key add -

sudo apt-get update

sudo apt-get install automatix2

Once automatix is installed, it can be found under Applications -> System Tools. Just select the apps, plugins and codecs that you want installed, and let it do everything for you. As I said, I've never had any problems doing it this way, so hope it works for you too. Good luck.

---

### Post by hyper_ch on 2007-09-13
Automatix is not recommended for installation.

There's a non-free flash plugin in some repos and java can also be installed through the repos. No need to use Automatix.

---

### Post by ROUBOS on 2007-09-13
just used Automatix just to check it out. I use 64bit version of ubuntu.
I had a problem with video and audio codecs. Videos like trailers from apple.com/trailers did not work properly. No sound and the video was like a negative film.
Now after automatix, they dont work at all :(

---

### Post by mlentink on 2007-09-13
[http://ubuntuforums.org/showthread.php?t=519872](http://ubuntuforums.org/showthread.php?t=519872)

...

---

### Post by Terl on 2007-09-13
> **buddhacub1120 said:**
> I have so many problems right now I don't know even where to begin. Should i start with how icons on my task bar or system tray or w/e it's called are not appearing and my programs such as GAIM are closing instead on minimizing? or should i start with no matter what  way i try to install flash and java, NOTHING WORKS! grrr i'm getting aggrivated. i'm very much so a n00b but have been having some non-n00b friends help me out but they only know so much...please help? 



:confused: ](*,)

To get Java, Flash, MS TTF, and MP3 plugins all at once type:

```
sudo apt-get install ubuntu-restricted-extras
```

Enter your password when prompted.  Follow along and respond to the prompts for information, all very easy.

Do not use automatix, it is not recommended; just check the forums for more info as to why.

---

### Post by Kitsun on 2007-09-13
Usage of Automatix seems to be an opinion.

Ive been using it for over a year, and haven't had any problems with it, I have used it less and less over time, but I still use it for installing Azureus because the repo version crashes at startup.

Ubuntu devs need to worry about things directly related to Ubuntu methinks.

---

### Post by ROUBOS on 2007-09-13
yes Azureus does seem to crash alot. Because of it I installed ktorrent

---

### Post by Perfect Storm on 2007-09-13
> **Kitsun said:**
> Usage of Automatix seems to be an opinion.

Ive been using it for over a year, and haven't had any problems with it, I have used it less and less over time, but I still use it for installing Azureus because the repo version crashes at startup.



Nope, it's a fact. It's actually been tested.

[http://mjg59.livejournal.com/77440.html](http://mjg59.livejournal.com/77440.html)

Also we don't support Automatix on the forums: 
[https://help.ubuntu.com/community/Automatix](https://help.ubuntu.com/community/Automatix)

Azureus have issues, please check in the tips'n'tricks forum for a guide. I know there's a couple. But get Deluge instead, it's highly recommendable.
[http://deluge-torrent.org/](http://deluge-torrent.org/), they have .deb packages ready.

> Ubuntu devs need to worry about things directly related to Ubuntu methinks.

As what? the Azureus thing. Azureus is part of the universe and therefore glitches happens.

[http://www.ubuntu.com/community/ubuntustory/components](http://www.ubuntu.com/community/ubuntustory/components)
> 
The universe component is a snapshot of the free, open source, and Linux world. In universe you can find almost every piece of open source software, and software available under a variety of less open licences, all built automatically from a variety of public sources. All of this software is compiled against the libraries and using the tools that form part of main, so it should install and work well with the software in main, but it comes with no guarantee of security fixes and support. The universe component includes thousands of pieces of software. Through universe, users are able to have the diversity and flexibility offered by the vast open source world on top of a stable Ubuntu core.

Canonical does not provide a guarantee of regular security updates for software found in universe but will provide these where they are made available by the community. Users should understand the risk inherent in using packages from the universe component.

Popular or well supported pieces of software will move from universe into main if they are backed by maintainers willing to meet the standards set for main by the Ubuntu team. 

---

### Post by buddhacub1120 on 2007-09-13
> **Terl said:**
> To get Java, Flash, MS TTF, and MP3 plugins all at once type:

```
sudo apt-get install ubuntu-restricted-extras
```

Enter your password when prompted.  Follow along and respond to the prompts for information, all very easy.

Do not use automatix, it is not recommended; just check the forums for more info as to why.

i did and nothing really happeend. something about 17 not upgraded

---

### Post by Perfect Storm on 2007-09-13
You have to enable universe and multiverse;

Try check synaptic - settings ---> repo...

or the manual way;

Exit synaptic, open the terminal;

```
sudo nano /etc/apt/sources.list
```

add;

[b]### Ubuntu community supported packages
### GPG key: 437D05B5
deb [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) feisty universe multiverse 
deb [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) feisty-updates universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe multiverse
deb-src [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) feisty universe multiverse
deb-src [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) feisty-updates universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe multiver[/b]

Save (ctrl)+(o) and exit (ctrl)+(x)

(you might want to change "dk" to your land code)

```
sudo aptitude update && sudo aptitude upgrade
sudo aptitude install ubuntu-restricted-extras
```

want to build a complete new sourcelist check here;
[http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)

---

### Post by por100pre1 on 2007-09-13
Follow this [how-to]("http://ubuntuforums.org/showthread.php?t=413624"). It worked nicely for me. :)

---

### Post by buddhacub1120 on 2007-09-13
i have the universe and multiverse repos on or w/e

---

### Post by buddhacub1120 on 2007-09-13
also i guess flash is telling me it can't support my structure. i'm runnin AMD64. i guess i need the 32-bit version of firefox...any help there?

---

### Post by Perfect Storm on 2007-09-13
If you're completly new to ubuntu or linux in general you should start off with 32-bit version on your 64-bit system to learn the basics first.

64 bit can still be a hassle...

---

### Post by buddhacub1120 on 2008-01-11
how can i swtich over to a 32 bitversion...and will i lose alot of my information?

---

### Post by Perfect Storm on 2008-01-11
Actually - If you upgrade to gutsy, there won't be any diffrent in difficulties between the two (32-bit and 64-bit).
The only thing that might be a little hassle will be java in browser.

Here's how you install flash on 64-bit: [http://ubuntuforums.org/showthread.php?t=476924](http://ubuntuforums.org/showthread.php?t=476924)

I myself have switch to 64bit now.

---

### Post by PmDematagoda on 2008-01-11
+1 on what Artificial Intelligence said. I began using 64 bit on Ubuntu 7.10 and it was really easy to get used to, it even worked very much like Ubuntu x86 and had pretty much the same applications. Java and Flash installation on Ubuntu 7.10 x64 is especially easy so you should have better luck with it. 

But as always, before upgrading the PC, you should backup all your important your data.

---

### Post by jonnywombat on 2008-01-11
Ok.. 

So if your using the 64 bit version then there is an easy solution for you..

Go to this post.. [http://ubuntuforums.org/showthread.php?t=202537&highlight=firefox+3in1+installer](http://ubuntuforums.org/showthread.php?t=202537&highlight=firefox+3in1+installer)

What this will do is lead you to script that allows you to install the 32 bit version of firefox, with full flash and java support.. You do this because although 64 bit support for java and flash is improving it is still a bit flakey.. much more stable to run the 32 bit version..

Also while you are there take a moment to look at swiftweasell.. this is an optimized version of firefox, and there is even a version optimized to run as 32 bit in the 64bit environment...it works a little quicker than firefox and i find it to be more stable.... You can use the 3 in one installer for swiftweasel too i think...

Once you have done this you might wanna make the appearance of firefox / swiftweasel more acceptable and do something about the ugly buttons..

visit [http://ubuntuforums.org/showthread.php?t=369596](http://ubuntuforums.org/showthread.php?t=369596) and grab the latest version of the firefox widget installer and then follow the instructions.. all will look pretty too..

Good luck

Jonny

---

### Post by buddhacub1120 on 2008-01-11
nothing you guys have given me i shelping =/ arrrg....

---

### Post by PmDematagoda on 2008-01-11
About your Java problem, could you post the result of:-
```
sudo update-alternatives --config java
```

---

### Post by billgoldberg on 2008-01-11
> **buddhacub1120 said:**
> I have so many problems right now I don't know even where to begin. Should i start with how icons on my task bar or system tray or w/e it's called are not appearing and my programs such as GAIM are closing instead on minimizing? or should i start with no matter what  way i try to install flash and java, NOTHING WORKS! grrr i'm getting aggrivated. i'm very much so a n00b but have been having some non-n00b friends help me out but they only know so much...please help? 



:confused: ](*,)

1. Maybe just a bad install I would just reinstall.

2 if thats not an option (i don't see why) you could try kopete or amsn for instant messaging

I can't help anymore

It just seems you had a bad install. (I however never heard of such problems on a fresh install)

---

### Post by buddhacub1120 on 2008-01-12
well this si actually my 3rd time installing. as far as amsn goes, that's only for msn msgr which is working fine. kpoete doesn't want to install properly either. i guess what im looking for is an AIM replacement that isn't gaim or pidgin.

---

