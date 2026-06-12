---
title: "Absolute beginner guide for everything.[sc30317] n00b proof guide."
date: 2007-12-14
forum: Absolute Beginner Talk
---

### Post by sc30317 on 2007-12-14
**I've been a long time observer of Ubuntu forums, and now I feel as if I should put in my .02.**
***[I]UPDATED [12/14]*[/I]**
I know there are tons of new Ubuntu users, and I wish there was a good guide when I did my first install of the best way to get my computer up and running with all the cool stuff installed! ;)
**NOTE: THIS IF FOR GUTSY!**
If you are a new Ubuntu user, these may be the steps you are looking for to find an alternative OS solution!

**Initial install:**
1.  Download the Ubuntu desktop distribution - [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
You are most likely going to want to download the **X86 VERSION!**.  If you are new to Ubuntu, this will most likely be the distribution for you, as it is the most used version.  If you have more then 4GB of ram; however, you may want to look into the x86-64 version if you would like to utilize all of your RAM.  The x86_64 version may be difficult to set up for a new user, and you may have difficulties with java and flash, along with other programs.

After you have downloaded the x86 version (I know, around ~650MB, takes a long time, yada yada yada),   you will want to burn it to CD.   If you do not know how to burn an ISO to a CD, you will want to look at these sites:
1.)if you have a PC- download CDBurnerXPpro3- [http://cdburnerxp.se/download](http://cdburnerxp.se/download).  This is the best freeware for windows XP/Vista to burn an ISO.
2.) if you have a MAC -http://www.macosxhints.com/article.php?story=20060619181010389
3.) if you have some other funky os, PM me!  I will help you!

After you have the CD burned, save all the important stuff going on your computer.  Turn the actual computer off!  Put the Ubuntu CD in the drive as the computer is booting up.

The next part is tricky- every computer has different settings.  The bios (the area of the computer before you get to windows) is different for every computer.   Try pushing DEL, F12, or F10 to get into the bios, or look on the bootup screen to find out which button is necessary to push in order to get to the bios setup.  Again, if you have trouble with this portion, PM me.  I will try to help.

Once you get into this bios portion of your computer, you will mostly feel like a hacker.  There will be no pictures, and everything will be most likely black, white, blue,  and/or red.  Don't worry tho, everything will be fine.  You are trying the best OS in the world!  :guitar:

Look for the boot device.  Most likely, it will be the hard drive that boots first.  Make sure you change this boot device to the CD drive where you will put the ubuntu CD.  This is VERY IMPORTANT.  You want to make sure that you boot to the Ubuntu CD, or else that 650 MB downlaod was for nothing!

After you boot from the CD, you will have  a couple options.  You can check the CD for errors (exellent thing to do if you feel your CD didn't download/burn correctly), you can check your memory for errors, etc.  Personally, I feel there are only two important things on the Ubuntu LiveCD- the install mode (1st option) or the install in safe graphics mode (2nd option)  Find the model # of your computer.  Google it as such -  (Model #) Ubuntu.  If there are any search topics that are suggesting that you are going to have a difficult time installing Ubuntu, go for the safe graphics mode install.  Otherwise, choose the normal install.  

Once you pick your installation method of choice, the Ubuntu screen will start.  I remember the first time I saw an OS installation screen- very exciting!  All of the Ubuntu beginners will definitely enjoy this, and even computer veterans who are installing an alternate OS for the first time will definitely find this to be most interesting.  

After the splash screen takes over (the black screen with Ubuntu written on it and the orange status bar) finishes,  you will be logged into the Ubuntu environment.  Again, very exciting.

Some desktop icons should show up that will be of very much importance to you later will show up- most noticeably, the install Icon.  don't worry about this yet, we will get to that in a minute.  

After the desktop is booted up,  Feel free to play around with it for a while-  Go to **Applications .> settings** and check out the Text Editor- Gedit is really cool, and gives a good feel to Open Source text editing.  Check out Firefox (under the network menu), and check out totem (under the multimedia menu).  These are a few of the most important programs used in Ubuntu,  These three programs, along with the terminal, will make for a large part of your Ubuntu experience.

If after you look at these programs, and you say Hey, ubuntu is pretty cool, I would like to be able to use this all the time, then you will probably want to setup a dual boot.  If not-> well, then Linux captivated your interest for a while, and you can start to begin to understand the awesomeness of open source.

if you decide Ubuntu is for you, then you are ready to install!  One can use the installation icon to partition the disk; however, I would suggest using Gparted, an awesome disk partitioning tool that is available withing the Ubuntu live CD.  click on the **Applications ** menu, click **accessories**, and then click **terminal**.  A white box will show up on your desktop.  Don't be scared- this is the terminal, where most important compter stuff is preformed.  type **sudo gparted** in the terminal to open up gparted.  sudo is a command that allows one to access the system resources (any hardware, some specific software), and gparted is the graphica  partition editor that is included with Ubuntu.

Sudo is a command that is specific to Debian/Ubuntu based distributions.   It allows a normal user that knows the root password to have root access.  Root, or superuser, is the user in the computer that has access to everything, similar to an administrator for windows.  root access is needed for anything related to hardware, and some software things too!  Be careful using root/sudo commands; however, because they can cause damage to your system (not physical damage, they can just mess up this beautiful new OS you just installed!)

After you have done this, The gparted screen will show up.  It allows you to view the partitions that you have on the disks that are installed on your computer.  if you are running another OS (windows for example), it will show this partition.  To dual boot, you will have to make room for your ubuntu partition, possibly by resizing your window partition.  Use this website as a gudie [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning) 

Once you have your disk partitioned,  exit gparted and you are back to your Ubuntu LiveCD.
Even though you might be worried, that install icon on the desktop is looking pretty good.  Just man up and click it! XD

Run through the installation steps.  Everything is pretty self explanatory.  PM me if you have any questions about the installation process.   Follow this process-
[http://www.howtoforge.com/the_perfect_desktop_ubuntu_gutsy_gibbon](http://www.howtoforge.com/the_perfect_desktop_ubuntu_gutsy_gibbon)

After you have the perfect desktop installed, and have rebooted, and have the GRUB option, you are able to boot into Ubuntu from your Hard drive.  I would suggest doing that.

After you get into Ubuntu, there are many configuration changes that you will most likely want to make. 

First, you are going to want to update your sources.  Basically, this means you are going to want to make your computer able to install the best software available for ubuntu.  

Go to the terminal (Applications -> Accessories -> terminal) if you forgot;
type in ```
sudo gedit /etc/apt/sources.list
```

the gedit program you tested earlier will open up, but it will have all of this text in it that you dont understand.  This text consists of http sites.  These http sites are called **repositories**, and they hold all the important software you want to download.

once in /etc/apt/sources.list -> select all the text in the document, and delete it!  After this deletion, instert this group of text 

```
deb http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.

deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

##Universe

deb http://us.archive.ubuntu.com/ubuntu/ gutsy universe
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy universe
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## Multiverse

deb http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Backports

deb http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Canonical Partner Repository 

deb http://archive.canonical.com/ubuntu gutsy partner
deb-src http://archive.canonical.com/ubuntu gutsy partner
deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb http://security.ubuntu.com/ubuntu gutsy-security universe
deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://packages.medibuntu.org/ gutsy free non-free

```

Then, close gedit and save changes.

next, you are going  to need to add a gpg key for the medibuntu repository- easy as cake
TERMINAL -> wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add -
                     sudo apt-get update

After this,  you will be able to download all the important software for ubuntu.

First thing I would do is download the restricted-extra packages
```
sudo apt-get install ubuntu-restricted-extras 
```.  This will give you flash, java, and all the important things you need for your ubuntu.  

You also may want to look into installing the linux restricted modules package
```
sudo apt-get installlinux-restricted-modules
``` It has proprietary drivers (drivers in which a user does not have the source code for), but some of these drivers can make a system work (the Nvidia restricted driver, for instance, is fantastic).

Now, you have a good base for your ubuntu experimentation.  Ask all sorts of questions,  the people at ubuntuforums.org will love to answer any questions you have.  PM me if they don't want to answer your questions,  I will try :lolflag:


Other questions will most likely be answered on [Bhttp://www.ubuntuguide.org][/B] .  This site is EXTREMELY EXTENSIVE
Here is a link to commands for the command line [http://www.digilife.be/quickreferences/QRC/UNIX%20commands%20reference%20card.pdf](http://www.digilife.be/quickreferences/QRC/UNIX%20commands%20reference%20card.pdf)
Here is a list of linux software equivalents- [http://www.linux.ie/newusers/alternatives.php](http://www.linux.ie/newusers/alternatives.php)

Ubuntu is **AWESOME**.  It does some really cool stuff, and the best part is.-> its FREE!

Give it a try, I promise you wont be dissapointed.

sc30317

---

### Post by hyper_ch on 2007-12-14
Nice post but I have a few things:

(1) Why adding sources repos? Novice users won't be bothered with sources
(2) I'd concanate the list:

```

deb http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted universe multiverse
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted universe multiverse

deb http://archive.canonical.com/ubuntu gutsy partner
deb http://security.ubuntu.com/ubuntu gutsy-security main restricted universe multiverse

```

(3) I would not include the backports and medibuntu in there. For installation of the medibuntu repos I'd lead them here:  [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

(4) Regarding the 4gb barrier: I'd also tell that there might be a few minor issues with flash, java....

(5) > 
2.) if you have a MAC -http://www.macosxhints.com/article.

php?story=20060619181010389

that should be one link. I guess that's just a typo. Also good not to start the url with a dash (-) then it will be auto-translated to a link.

(6) I'd advive against this: 
> PM me if you have any questions about the installation process
The reason: One who has an issue is very likely not to be the only one. So when the problem is stated in public, others may profite from it also. Furthermore you can't be online all the time. So by posting it in the forums chances are good, that the person asking for help will get sooner an answer.

(7) Another type here
> 
[CODEsudo apt-get install ubuntu-restricted-extras [/code]


(8) Maybe you should create some headers and some kind of index in that post. That would also make it more structured and appealing

(9) I see you have linked to psychocats.net and howtoforge. Another essential page would be [http://www.ubuntuguide.org](http://www.ubuntuguide.org) (that one's really extensive). I'd add that also to your post.

Nevertheless, great work.

---

### Post by ingram on 2007-12-14
Great guide, I think this kind of guide would help many new people who are wanting to switch over to UBUNTU. 

The only problem I have with this guide is that there really is no way to get the potential users to read it. Most of the people that I talk to about switching over to linux are convinced it will be the most complicated thing in the world. I think that if they could read your guide it would go a long way to helping.

Great work though .

---

### Post by sc30317 on 2007-12-14
updated... more comments on making this perfect would be nice....

---

### Post by g7kse on 2007-12-14
I've installed and am happy with everything so far. If I want to tinker I know where to get advice.

What would be nice is a recommended list of linux alternatives in the package. The software may be in synaptic but if you don't know what its called or how to switch between autoCAD and it's linux equivalent for example then I can see th eless patient becoming frustrated.

Itss a bit of a tall ask I know but it may help us with less patience enjoy th eproduct more.

---

### Post by ingram on 2007-12-14
as for suggestions you might want to make mention of some of the restricted drivers that come with the disk. 

As for a list of alternatives to commonly used programs there are a few lists out there but most are not up to date and most are not very comprehensive.

I know in our guide you make mention of the sudo command but it might help to give a few warnings concerning it's use. Also cant remember if you put this in but some new users do not know that using sudo is similar to doing things in root.

Another addition would be some good places for them to search to get answers. I know that not everyone who is going to use linux wants to look for their own answers but it couldn't hurt for the people like me out there.  When I started I wanted to find the answers on my own  and I know a list of possible places to find those answers other than pouring through man pages would have been great. 

Though now that I think about it going through man pages isn't always such a bad thing.

---

### Post by lvleph on 2007-12-14
I have a concern with deleting the existing repositories. There is no mention that your list is specific to gutsy, and seeing that this is a beginner's guide that is a key fact that need be said.

A beginners guide on terminal commands would be useful too, I think. When someone asks for help, they are told all these things about the terminal, but nothing is ever explained. Now of course that is the fault of both the person asking and helping, but... Maybe a link to something like [this](http://www.digilife.be/quickreferences/QRC/UNIX%20commands%20reference%20card.pdf).

---

### Post by sc30317 on 2007-12-14
Anyone else have ideas for this thread?  I would like to make it sticky-capable ;)

---

### Post by Ralphie on 2007-12-14
great post, i am not so much a "n00b" anymore, but it certainly helps to have all this in one simple place for when I am setting up a new system, i am doing so as i type lol. 
You cant expect me to remember all these things each time i set up a computer :)

thanks!

Oh and a side note to the newbies... this guide wont solve everyones specific problems, (usually hardware / driver related), But it will get you started. Take each problem one at a time and i guarantee by the time you solve them all, you'll know your way around linux, and not want to use any other OS. 

What took me weeks to do while setting up my first linux system, now takes me 30 minutes max.

it gets easier. and then youve got a killer OS to show off and use

---

### Post by erfahren on 2007-12-14
pretty decent guide..

a couple of issues though. You suggest using CDBurnerXP, I've used that before and it's actually a lot more "program" (more features) than a person really needs to burn the ISO, and the correct .NET framework needs to be installed, etc.

For Windows I usually recommend ISO Recorder [http://isorecorder.alexfeinman.com/isorecorder.htm](http://isorecorder.alexfeinman.com/isorecorder.htm)
It's a small, light program, and easy to use - once it's installed all you have to do is stick a CD in and right-click on the .iso and select "Burn to CD".  You can adjust the burn speed (I've heard that it's best to burn at the lowest speed possible but I've never had trouble burning at the fastest, - it doesn't really take much more time burning slower though.)

I've seen some Ubuntu documentation that suggested [InfraRecoder](http://infrarecorder.sourceforge.net/) to burn it. (I looked for the page that said that but couldn't find it.) I've never tried it but, again though, it looks like a much more basic program to burn the ISO. It's really all someone needs.


The other issue is with the sources.list you provide. You say just to copy it, but the country code is US. The section of the wiki "How to add extra repositories" covers that. [http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Manual_Method](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Manual_Method)


The part about installing the linux-restricted-modules is really unnecessary. Once someone is connected to the internet all they really need to do is go to System > Administration > Restricted Drivers Manager and enable any driver that wasn't enabled by default. That does the downloading and installing of the driver. (The driver itself may need to be downloaded as well - at least that's the case with xorg-driver-fglrx - it's not a dependency of linux-restricted-modules.)

Also, you ever add anything about desktop effects, could you remind ATI card users that they also need to install xserver-xgl? The current ATI proprietary driver (fglrx) doesn't support desktop effects on its own at this time. (They need to install it and restart X - Ctrl+Alt+Backspace.)


I'll say one thing here, the existing documentation for Ubuntu definitley isn't lacking, but I think that there is so much of it now that it's becoming overwhelming. I find Ubuntu Community Documentation pages through Google searches sometimes that I never saw before while going through the [Ubuntu Documentation](https://help.ubuntu.com/) through the main site. (Maybe I just didn't look enough - lol !)

In any event, I think the Wiki is one of the best sources, if someone takes the time to look through all the contents: [http://ubuntuguide.org/wiki/Ubuntu:Gutsy](http://ubuntuguide.org/wiki/Ubuntu:Gutsy)

---

### Post by Rocket2DMn on 2007-12-14
Another thing: you should use "gksudo" for graphical applications instead of just "sudo".  See [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by Bruce M. on 2007-12-14
> **lvleph said:**
> I have a concern with deleting the existing repositories. There is no mention that your list is specific to gutsy, and seeing that this is a beginner's guide that is a key fact that need be said.

A beginners guide on terminal commands would be useful too, I think. When someone asks for help, they are told all these things about the terminal, but nothing is ever explained. Now of course that is the fault of both the person asking and helping, but... Maybe a link to something like [this](http://www.digilife.be/quickreferences/QRC/UNIX%20commands%20reference%20card.pdf).

What a great little reference card.  Thanks

I'm going to be upgrading to Gutsy soon, you can bet before I do, I'll come back to this thread (bookmarked) and reread everything again.  { well I haven't quite finished reading it all just yet }

---

### Post by Bruce M. on 2007-12-14
> **sc30317 said:**
> updated... more comments on making this perfect would be nice....

One thing I just noticed.  You don't mention that the guide is for the Ubuntu LiveCD until the 5th or 6th paragraph.  What if someone downloaded the AlternateCD? You should make mention about the LiveCD at the beginning.

Which brings me to something else.

At the beginning you have:

NOTE: THIS IF FOR GUTSY!

it should read:  NOTE: THIS **IS** FOR GUTSY!

and there you can add the fact it's the LiveCD

NOTE: THIS IS FOR GUTSY - LiveCD!

Hope this helps

---

