---
title: "Is arch the distro for me?"
date: 2009-02-04
forum: Arch and derivatives
---

### Post by AllRadioisDead on 2009-02-04
Hi,
I've been running ubuntu for a while, though I want to get to know how linux works more. Ubuntu is simple to use, but I have no idea what to do whenever something doesn't work, I want to get more experienced with linux itself. I want a distro that comes simple, and I can learn to build up myself.  I've read the sticky and I get the impression that it will be a good distro to learn with. I'm torrenting arch linux now, will I be satisfied with it? Is there another distro that may do me more good? Are there any sites to get me more comfortable with linux, or that I can use as a reference? Thanks!

---

### Post by diwas on 2009-02-04
I am actually doing the same thing..hehe.
Check out this link 
[http://ubuntuforums.org/showthread.php?t=1055784](http://ubuntuforums.org/showthread.php?t=1055784)

And to know if Arch is for you or not:
[http://wiki.archlinux.org/index.php/Beginners_Guide](http://wiki.archlinux.org/index.php/Beginners_Guide)

Cheers!

---

### Post by gjoellee on 2009-02-04
[www.archux.com](www.archux.com) helped me when I was new to Arch

---

### Post by AllRadioisDead on 2009-02-04
Thanks a lot, I'll check those out when I get home in the afternoon.
I never get tired of the amazing ubuntu community :)

---

### Post by Rumor on 2009-02-04
it is hard to say whether you'll be satisfied with Arch. Arch is not for everyone.

If you are a tinkerer, someone who likes to tweak things or take them apart to see what makes them work, then Arch is for you. If you don't mind doing your own reading and problem solving to gain an understanding of why or how things work, then Arch is for you.

Arch can teach you quite a bit, but you have to be willing to learn.

Arch is what you make it. Make yours great and enjoy the process!

---

### Post by diwas on 2009-02-04
> **Rumor said:**
> it is hard to say whether you'll be satisfied with Arch. Arch is not for everyone.

If you are a tinkerer, someone who likes to tweak things or take them apart to see what makes them work, then Arch is for you. If you don't mind doing your own reading and problem solving to gain an understanding of why or how things work, then Arch is for you.

Arch can teach you quite a bit, but you have to be willing to learn.

Arch is what you make it. Make yours great and enjoy the process!
Thats wat I am talkin about!! Damn I have a slow internet...(downloading Arch is taking forever...cant wait to use it hehe):(

---

### Post by crimesaucer on 2009-02-04
Follow the ArchWiki for all the newest info for the install:


..... another good site to look at is the OLD GUIDE that has 10 pages of instructions with pictures of what to expect with an Arch install using console: [http://www.raiden.net/?cat=2&aid=276](http://www.raiden.net/?cat=2&aid=276)


Just make sure to follow the ArchWiki guide since it is the most current version of the install process..... but you can check the guide that I linked you to so you can see what that step will look like:


like cfdisk: [http://www.raiden.net/?cat=2&aid=276&pid=3](http://www.raiden.net/?cat=2&aid=276&pid=3)
or editing scripts in nano (scroll down): [http://www.raiden.net/?cat=2&aid=276&pid=5](http://www.raiden.net/?cat=2&aid=276&pid=5)
and using the ncurses menu for install (I like the FTP install, scroll to 4th pic down): [http://www.raiden.net/?cat=2&aid=276&pid=2](http://www.raiden.net/?cat=2&aid=276&pid=2) 


The reason I like the FTP install is because it will automatically configure your network section with DHCP (and it will configure that section in the /etc/rc.conf for you). It will also connect you to the mirror of your choice to download from...... then when you install the base/dev packages it will download the newest versions of everything instead of the old version of base/dev that is on the ISO image...... this will save you from having to do the full system upgrade right after installing from CD. (since Arch is a rolling release)


If you already have a perfectly working eth0 connection or wlan0 connection with Ubuntu..... and your hardware is easily recognized..... then the FTP method is faster to use. 


If your eth0 or wlan0 wifi connection is difficult to configure or if you have a difficult to configure router..... than use the regular CD version.

---

### Post by dannytatom on 2009-02-04
Pacman takes a sec to get used to, but it's lovely once ya get it down. :)

---

### Post by AllRadioisDead on 2009-02-04
I would still be able to install synaptic and use the ubuntu repositories though right? I mean, there's a lot of great stuff in the ubuntu repositories, and I'm not sure how expansive the arch ones are. I've never tried arch, so I'm just curious.

---

### Post by Simian Man on 2009-02-04
> **ihermit said:**
> I would still be able to install synaptic and use the ubuntu reprositories though right?

No, it has its own repositories and package management.  If you want to stick with Ubuntu but start from scratch, you could try using the minimal install CD.  This will allow you to install only those things that you want.  Also try setting up your partitions yourself.

Personally I wouldn't recommend Arch to anyone.

---

### Post by Cenotaph on 2009-02-04
Arch is not deb based, there is no synaptic. But there are some GUI frontends for pacman, it's all in the wiki ;)

I've started using Arch today, this is the kind of distro i was looking for definitely, not sure i'll keep it since i don't really use my laptop anymore but it's great if you want a clean and simple system.

---

### Post by smartboyathome on 2009-02-04
> **ihermit said:**
> I would still be able to install synaptic and use the ubuntu repositories though right? I mean, there's a lot of great stuff in the ubuntu repositories, and I'm not sure how expansive the arch ones are. I've never tried arch, so I'm just curious.

If you include AUR, Arch's repository is just as expansive (or maybe even moreso since it is easy to update packages in AUR by yourself) than Ubuntu's.

---

### Post by doorknob60 on 2009-02-04
There's no Synaptic, but there's Shaman, which is a GUI pacman frontend, just as good, maybe even better, than Synaptic. ALso I like Pacman better than apt-get. And AUR makes less comon software much easier to install than Ubuntu. Trust me, you'll love it (use yaourt as a package manager to access AUR).

---

### Post by handy on 2009-02-04
Here are the most important links to get started:

*_[http://www.users.on.net/~thehands/arch_linux.html](http://www.users.on.net/~thehands/arch_linux.html)_*

I really should add these to the above page also:

*_[http://ubuntuforums.org/showpost.php?p=6283883&postcount=3](http://ubuntuforums.org/showpost.php?p=6283883&postcount=3)_*

This one is a long one, but you will certainly become informed enough on the topic to choose how you handle .conf.pacnew files.

Personally I use nano to look at the new & the old & usually delete the ***[Edit:]** new, sometimes there is important editing that needs to be done but it is very rare. /edit *

It can be a worthwhile to wait until you have had a successful reboot before deleting some of the .conf.pacnew files. :-)

*_[http://ubuntuforums.org/showthread.php?t=881270&highlight=pacnew](http://ubuntuforums.org/showthread.php?t=881270&highlight=pacnew)_*

In answer to your question, the only way to know is to try Arch & find out.  Some people really don't like the Arch way, others find it suits them perfectly.  I have found in 10+ months of using Arch that my appreciation for the Arch way & the enjoyment I experience from using Arch just keeps growing.  Which surely beats the boredom I have experienced from using OSX & other computer/human interfaces. :-)

---

### Post by AllRadioisDead on 2009-02-04
Would there be a better distro for me to step up to before arch? Something intermediate?

---

### Post by handy on 2009-02-04
> **ihermit said:**
> Would there be a better distro for me to step up to before arch? Something intermediate?

Give Arch a go, it is so much easier & quicker to work with than Gentoo.  The documentation on the Arch Wiki is superb.  Follow the Beginners Guide to the letter & the only thing that will get in your way is if you have a strange piece of hardware in your machine.

Some people have trouble due to wireless internet connection issues, you will get good support here regarding that, or any other Arch issue for that matter.  You will also get good support in the Arch forums, though I have found that it is worth posting both here & in the Arch forum, as you can get quicker responses here because of the difference in the number of users in each forum.

If you have no wireless internet problems, I expect that you will find that Arch is a whole lot easier than you think it is right now.

If Arch suits you, you will be so happy that you found it. :-D

---

### Post by AllRadioisDead on 2009-02-04
I'm considering trying [Charkra Linux]("http://chakra-project.org/") first.
It seems easier to start off with, and it's based on arch. Thoughts?

---

### Post by handy on 2009-02-04
It will give you a taste.

What you miss out on is the understanding of how Arch works, that is gained during the installation of Arch.

Arch is more simple than most, if not all, of the other distro's.  The installation process introduces you to this simplicity.

This knowledge is a great foundation for future configuration & problem solving.

---

### Post by kk0sse54 on 2009-02-04
> **ihermit said:**
> I'm considering trying [Charkra Linux]("http://chakra-project.org/") first.
It seems easier to start off with, and it's based on arch. Thoughts?

Arch is really not that hard at all. People seem to be intimidated by the fact that there's no GUI installer, you're required to actually edit some text files, and there's no default DE. However if you print out the beginners guide or just have it displayed next to you, Arch is really a piece of cake thanks to their fantastic documentation that really just requires that you are able to read. Besides while Chakra might be fun to play with it's still a very new project and I'd stick to the normal method of installing Arch.

---

### Post by smartboyathome on 2009-02-04
> **C!oud said:**
> Arch is really not that hard at all. People seem to be intimidated by the fact that there's no GUI installer, you're required to actually edit some text files, and there's no default DE. However if you print out the beginners guide or just have it displayed next to you **or have it up in another virtual terminal since it is included on the CD**, Arch is really a piece of cake thanks to their fantastic documentation that really just requires that you are able to read. Besides while Chakra might be fun to play with it's still a very new project and I'd stick to the normal method of installing Arch.

There, I corrected that for you. ;)

---

### Post by Grant A. on 2009-02-04
> **C!oud said:**
> Arch is really not that hard at all. People seem to be intimidated by the fact that there's no GUI installer, you're required to actually edit some text files, and there's no default DE. However if you print out the beginners guide or just have it displayed next to you, Arch is really a piece of cake thanks to their fantastic documentation that really just requires that you are able to read. Besides while Chakra might be fun to play with it's still a very new project and I'd stick to the normal method of installing Arch.

I concur with the documentation part, if you print out the beginners' guide and networking guides from their wiki beforehand, it is a VERY simple installation. Note: Arch tends to break if it is not up-to-date, so get the network installation CD.

---

### Post by kk0sse54 on 2009-02-04
> There, I corrected that for you. 
Good point however I know personally I prefer when possible to have a laptop handy for all my installs.

---

### Post by AllRadioisDead on 2009-02-04
I don't have a printer working right now, that's why I've been inching toward Chakra for my first install.

---

### Post by kk0sse54 on 2009-02-04
> or have it up in another virtual terminal since it is included on the CD;)

---

### Post by crimesaucer on 2009-02-04
> Is arch the distro for me?

I would have to say no. 


I'm not saying this because I'm rude or because I think I'm 1337..... I'm saying this because of your comment about you wanting the Ubuntu repositories, .debs, and Synaptic. And how you don't want to install Arch because of the console install..... so you chose Chakra.


To me all of that just says that you haven't wanted to try Arch for the correct reasons. (not that this matters because once you try it you will probably love it like the rest of us)


Most people interested in Arch "WANT" to use the pacman package manager and the newest available versions of Linux apps updated every day in the Arch repositiry: [http://www.archlinux.org/](http://www.archlinux.org/)


..... they also want the AUR/ABS repos with easy to use PKGBUILDS..... and they usually want to get away from the i386 architecture to use the i686 architecture: [http://wiki.archlinux.org/index.php/Arch_vs_Others#Source-Based](http://wiki.archlinux.org/index.php/Arch_vs_Others#Source-Based) (if you are using x86_64 for 64bit then the i686 thing doesn't really matter). 


Plus a minimal install is usually another reason that makes people want to use Arch.....


So, if you want a KDE desktop with the newest apps available and an easier install CD then definitely go with Chakra. But I guarantee that once you get use to pacman and the Arch repos that you will prefer it to "apt-get".

---

### Post by AllRadioisDead on 2009-02-05
> **crimesaucer said:**
> I would have to say no. 


I'm not saying this because I'm rude or because I think I'm 1337..... I'm saying this because of your comment about you wanting the Ubuntu repositories, .debs, and Synaptic. And how you don't want to install Arch because of the console install..... so you chose Chakra.


To me all of that just says that you haven't wanted to try Arch for the correct reasons. (not that this matters because once you try it you will probably love it like the rest of us)


Most people interested in Arch "WANT" to use the pacman package manager and the newest available versions of Linux apps updated every day in the Arch repositiry: [http://www.archlinux.org/](http://www.archlinux.org/)


..... they also want the AUR/ABS repos with easy to use PKGBUILDS..... and they usually want to get away from the i386 architecture to use the i686 architecture: [http://wiki.archlinux.org/index.php/Arch_vs_Others#Source-Based](http://wiki.archlinux.org/index.php/Arch_vs_Others#Source-Based) (if you are using x86_64 for 64bit then the i686 thing doesn't really matter). 


Plus a minimal install is usually another reason that makes people want to use Arch.....


So, if you want a KDE desktop with the newest apps available and an easier install CD then definitely go with Chakra. But I guarantee that once you get use to pacman and the Arch repos that you will prefer it to "apt-get".

Your comment makes sense to me, and I appreciate your feedback. What would you suggest for me? I'm looking for something in the "intermediate level", but a distro that I can build up on and learn from. Any suggestions?:p

---

### Post by smartboyathome on 2009-02-05
> **ihermit said:**
> Your comment makes sense to me, and I appreciate your feedback. What would you suggest for me? I'm looking for something in the "intermediate level", but a distro that I can build up on and learn from. Any suggestions?:p

Intermediate level conflicts with what you want. If you are really wanting something you can learn from, install Arch and suffer through the slight learning curve. Otherwise, I would recommend you go with a minimal install of Ubuntu and build up from there.

---

### Post by dannytatom on 2009-02-05
Just install Arch, if you don't like it install something else.  It's not hard once you get used to it, pacman is wonderful, and Shaman's a great GUI frontend (similar to Synaptic).  There's almost no reason for .debs as the AUR has an insane amount of packages, most all current versions. Just dooooo it. :)

Install took me maybe 40 minutes (a lot of that time was for downloading packages since I chose the FTP route) and I'm in no way a linux guru.

---

### Post by estyles on 2009-02-05
I like Arch, really I do, but the sticking points for me that keep me from using it as a main distro are, 1) The community really has that RTFM mentality.  And some of the forum regulars will really shove it in your face.  2) There are precious few GUI tools.  If you ask for a GUI tool, expect to be told that you are an infidel that doesn't know the "Arch Way".  

These aren't from personal experience - or, rather, I haven't had anyone jump down *my* throat, but from reading the Arch forums, I've seen it happen very often to others who had, I thought, legitimate questions.  I don't need a lot of hand-holding and am perfectly willing to use the CLI for a vast majority of tasks, but...  here's the thing about GUI tools - particularly GUI settings managers...  they tell you what your choices are.  

I'm happy with experimenting, happy to do some research, but with the CLI, you have to know what command to type in and what options there are that will fix your problem (I know, read man pages - I do...  sometimes that is very illuminating, and sometimes there are no examples to explain what they expect the input for certain options to look like, which again leads you to guess).  It seems like magic sometimes when someone tells you to input a particular command.  And when searching for how to fix a problem, it seems like similar magic when you finally find out that you need to edit one particular text file embedded 4 directories deep under /etc.  When you first got Ubuntu, which were you more likely to figure out how to do on your own: browse through synaptic and find programs you wanted to install, or type "apt-get install blah blah blah blah" and instantly get everything you needed?  I'm not *complaining* about having to modify text files or type commands - I have a transparent terminal on my desktop specifically for that purpose and definitely type commands when I know that it'll be faster that way than using a GUI.  I'm just saying that GUIs have their use and place.

And I understand that Arch doesn't have a lot of GUI tools because nobody has stepped forward to write them - it's not like I'm paying $100 for the privilege of using the OS and have any kind of legitimate gripe when it doesn't do every little thing I want it to, the way I want it to, *when* I want it to.  What I don't understand is the absolute disdain of a lot of the Arch crowd for GUI tools and for anyone that says they might prefer one.

---

### Post by AllRadioisDead on 2009-02-05
Alright, well I just went through the installation, and I think everything went fine. However, now when I boot my computer all I see is a screen that says:
```
GNU GRUB version 0.97 (639k lower/523200k upper memory

[Minimal BASH-like line editing is supported.
For the first word, TAB lists possible command
completions. Anywhere else TAB lists the possible
completion of a device/filename.]
grub>
```

---

### Post by RJARRRPCGP on 2009-02-05
> **ihermit said:**
> Hi,
I've been running ubuntu for a while, though I want to get to know how linux works more. Ubuntu is simple to use, but I have no idea what to do whenever something doesn't work, I want to get more experienced with linux itself. I want a distro that comes simple, and I can learn to build up myself.  I've read the sticky and I get the impression that it will be a good distro to learn with. I'm torrenting arch linux now, will I be satisfied with it? Is there another distro that may do me more good? Are there any sites to get me more comfortable with linux, or that I can use as a reference? Thanks!

Yes, if you don't mind reformatting and reinstalling at least about 10 times!:evil: 

They're appears to be package breakage and it seems to have just gotten worse within just some hours ago! :evil:

KDE, when it was usable about 24 hours ago, I cannot use KDE now, because it claims a missing file and when I click "OK", I'm back at the command line!

---

### Post by AllRadioisDead on 2009-02-05
> **RJARRRPCGP said:**
> Yes, if you don't mind reformatting and reinstalling at least about 10 times!:evil: 

They're appears to be package breakage and it seems to have just gotten worse within just some hours ago! :evil:

Eughhh, what kind of package breakage, because I'm getting stuck at a grub screen.

---

### Post by estyles on 2009-02-05
> **ihermit said:**
> Alright, well I just went through the installation, and I think everything went fine. However, now when I boot my computer all I see is a screen that says:
```
GNU GRUB version 0.97 (639k lower/523200k upper memory

[Minimal BASH-like line editing is supported.
For the first word, TAB lists possible command
completions. Anywhere else TAB lists the possible
completion of a device/filename.]
grub>
```

That's probably bad...

Do you recall which device you have your /boot on?  (It's either the root partition for Arch, or something else if you specifically made a boot partition.)

If not, grub should be able to find it:

```

grub> find /boot/grub/menu.lst
grub> root (hdx,y)
grub> setup (hdx)
grub> quit <or is it exit?  I always forget...>

```

Replace (hdx,y) above with whatever the first command tells you.  If you have more than one menu.lst, you might have to figure out which one is for arch.  Replace (hdx) with just the drive number, like (hd0) if you used (hd0,1) for the first part.

Then reboot and see if that works.

---

### Post by AllRadioisDead on 2009-02-05
> **estyles said:**
> That's probably bad...

Do you recall which device you have your /boot on?  (It's either the root partition for Arch, or something else if you specifically made a boot partition.)

If not, grub should be able to find it:

```

grub> find /boot/grub/menu.lst
grub> root (hdx,y)
grub> setup (hdx)
grub> quit <or is it exit?  I always forget...>

```

Replace (hdx,y) above with whatever the first command tells you.  If you have more than one menu.lst, you might have to figure out which one is for arch.  Replace (hdx) with just the drive number, like (hd0) if you used (hd0,1) for the first part.

Then reboot and see if that works.
Alright, I tried doing 
```
grub> setup (hd0)
```
and I get
```

Checking if "/boot/grub/stage1" exists...    no
Checking if "/boot/grub/stage1" exists...    no
Error 15 File not found

```

---

### Post by smartboyathome on 2009-02-05
> **ihermit said:**
> Alright, I tried doing 
```
grub> setup (hd0)
```
and I get
```

Checking if "/boot/grub/stage1" exists...    no
Checking if "/boot/grub/stage1" exists...    no
Error 15 File not found

```

That means you skipped the grub setup step in the installer.

---

### Post by AllRadioisDead on 2009-02-05
> **smartboyathome said:**
> That means you skipped the grub setup step in the installer.

Should I reinstall?

---

### Post by dannytatom on 2009-02-05
I'm not sure if this'll work, but you can try sticking the live CD in and running the "Install bootloader/Grub" option then restart.  Even if it doesn't work, won't hurt anything. :p

---

### Post by AllRadioisDead on 2009-02-05
> **dannytatom said:**
> I'm not sure if this'll work, but you can try sticking the live CD in and running the "Install bootloader/Grub" option then restart.  Even if it doesn't work, won't hurt anything. :p

Naw, didn't work. I think I'll just do a minimal install of ubuntu before diving into arch, thanks for your support everyone.

---

### Post by chucky chuckaluck on 2009-02-05
> **Rumor said:**
> iArch can teach you quite a bit, but you have to be willing to learn.

rumor's right. i don't care about learning and haven't learned all that much since switching to arch. i use it because i don't like having things i don't need installed on my machine. it was easier to just start with nothing and add what i want than to try to figure out what all that extra crap was before i removed it.

---

### Post by gjoellee on 2009-02-05
> **dannytatom said:**
> I'm not sure if this'll work, but you can try sticking the live CD in and running the "Install bootloader/Grub" option then restart.  Even if it doesn't work, won't hurt anything. :p

That does not work, becuase you you did not mount or chroot the partition installed! You just installed Arch on the Arch Live...(no harm done to the CD). I would go for a new install. Make sure to not skip any steps.

---

### Post by kk0sse54 on 2009-02-05
> **estyles said:**
> I like Arch, really I do, but the sticking points for me that keep me from using it as a main distro are, 1) The community really has that RTFM mentality.  And some of the forum regulars will really shove it in your face.  
I have never had any problems with the Arch community but there's definitely a smaller tolerance there towards questions that can be usually solved using a simple google search.
> 2) There are precious few GUI tools.  If you ask for a GUI tool, expect to be told that you are an infidel that doesn't know the "Arch Way". 
Arch provides a minimal base system without a GUI so that you can choose what you want. How could there be gui tools available? Instead it's up to the user if you want them to install them. For example if you're sick of using the tar command and would rather have a GUI archiver it's as simple as "sudo pacman -S squeeze" or xarchiver or whatever you want.

>  here's the thing about GUI tools - particularly GUI settings managers...  they tell you what your choices are. 
Perfectly understandable but on the other hand it's usually just a matter of man <something> or in most cases I prefer to use <whatever> --help when it's available. Although sometimes in some rare cases it involves searching the internet a bit for an example of the command.

>  I'm just saying that GUIs have their use and place.
I concur but they have to be the right tools

---

### Post by crimesaucer on 2009-02-05
> **ihermit said:**
> Your comment makes sense to me, and I appreciate your feedback. What would you suggest for me? I'm looking for something in the "intermediate level", but a distro that I can build up on and learn from. Any suggestions?:p

Disregard my earlier comment. Arch probably is the "intermediate level" you seek. You'll realize the best things about it once you start using it.


> **dannytatom said:**
> "Just install Arch, if you don't like it install something else.  It's not hard once you get used to it, pacman is wonderful....."  "......the AUR has an insane amount of packages, most all current versions. Just dooooo it. :)...."

".....Install took me maybe 40 minutes (a lot of that time was for downloading packages since I chose the FTP route) and I'm in no way a linux guru......"


I agree with all of this statement.


Now seriously, if you want to install Arch..... read this "OLD" 10 page guide with pictures of each important step: [http://www.raiden.net/?cat=2&aid=276](http://www.raiden.net/?cat=2&aid=276)


Then read the "NEW" ArchWiki Beginner guide: [http://wiki.archlinux.org/index.php/Beginners_Guide](http://wiki.archlinux.org/index.php/Beginners_Guide) and follow each step..... you will recognize 95% of the steps because most things have stayed the same.


The only differences are with pacman.d (only has one file to edit called "mirrorlist" now), pacman.conf and rc.conf are written a bit differently, and Installing/configuring "X/xorg.conf" from this part: [http://www.raiden.net/?cat=2&aid=276&pid=8](http://www.raiden.net/?cat=2&aid=276&pid=8) is better explained with the new ArchWiki sections here:

[http://wiki.archlinux.org/index.php/Beginners_Guide#Install_X](http://wiki.archlinux.org/index.php/Beginners_Guide#Install_X)
[http://wiki.archlinux.org/index.php/Beginners_Guide#Configure_X](http://wiki.archlinux.org/index.php/Beginners_Guide#Configure_X)
[http://wiki.archlinux.org/index.php/Beginners_Guide#What_is_the_xorg.conf_file.3F](http://wiki.archlinux.org/index.php/Beginners_Guide#What_is_the_xorg.conf_file.3F)
[http://wiki.archlinux.org/index.php/Beginners_Guide#Create_.2Fetc.2FX11.2Fxorg.conf](http://wiki.archlinux.org/index.php/Beginners_Guide#Create_.2Fetc.2FX11.2Fxorg.conf)
[http://wiki.archlinux.org/index.php/Beginners_Guide#Input_hotplugging](http://wiki.archlinux.org/index.php/Beginners_Guide#Input_hotplugging)
[http://wiki.archlinux.org/index.php/Beginners_Guide#Test_X](http://wiki.archlinux.org/index.php/Beginners_Guide#Test_X)
If You Have NVIDIA/ATI: [http://wiki.archlinux.org/index.php/Beginners_Guide#Using_a_proprietary_video_driver_.28NVIDIA.2C_ATI.29](http://wiki.archlinux.org/index.php/Beginners_Guide#Using_a_proprietary_video_driver_.28NVIDIA.2C_ATI.29)

---

### Post by MisfitI38 on 2009-02-05
> **RJARRRPCGP said:**
> Yes, if you don't mind reformatting and reinstalling at least about 10 times!:evil: 

They're appears to be package breakage and it seems to have just gotten worse within just some hours ago! :evil:

KDE, when it was usable about 24 hours ago, I cannot use KDE now, because it claims a missing file and when I click "OK", I'm back at the command line!

Your obvious instance of PEBKAC should not be stated as an absolute fact in this manner. It is irresponsible. 
I am using nVidia drivers and pacman -Syu regularly, and so are many thousands of others, all without any issues.
If reinstalling 10 times is really and truly accurate, then perhaps you may ask yourself if this is really the right distribution for you, rather than blaming your 'package breakage' on the distribution.
Arch is a rolling release.

---

### Post by MisfitI38 on 2009-02-05
> **estyles said:**
> I like Arch, really I do, but the sticking points for me that keep me from using it as a main distro are, 1) The community really has that RTFM mentality.  And some of the forum regulars will really shove it in your face.  2) There are precious few GUI tools.  If you ask for a GUI tool, expect to be told that you are an infidel that doesn't know the "Arch Way".  

These aren't from personal experience - or, rather, I haven't had anyone jump down *my* throat, but from reading the Arch forums, I've seen it happen very often to others who had, I thought, legitimate questions.  I don't need a lot of hand-holding and am perfectly willing to use the CLI for a vast majority of tasks, but...  here's the thing about GUI tools - particularly GUI settings managers...  they tell you what your choices are.  

I'm happy with experimenting, happy to do some research, but with the CLI, you have to know what command to type in and what options there are that will fix your problem (I know, read man pages - I do...  sometimes that is very illuminating, and sometimes there are no examples to explain what they expect the input for certain options to look like, which again leads you to guess).  It seems like magic sometimes when someone tells you to input a particular command.  And when searching for how to fix a problem, it seems like similar magic when you finally find out that you need to edit one particular text file embedded 4 directories deep under /etc.  When you first got Ubuntu, which were you more likely to figure out how to do on your own: browse through synaptic and find programs you wanted to install, or type "apt-get install blah blah blah blah" and instantly get everything you needed?  I'm not *complaining* about having to modify text files or type commands - I have a transparent terminal on my desktop specifically for that purpose and definitely type commands when I know that it'll be faster that way than using a GUI.  I'm just saying that GUIs have their use and place.

And I understand that Arch doesn't have a lot of GUI tools because nobody has stepped forward to write them - it's not like I'm paying $100 for the privilege of using the OS and have any kind of legitimate gripe when it doesn't do every little thing I want it to, the way I want it to, *when* I want it to.  What I don't understand is the absolute disdain of a lot of the Arch crowd for GUI tools and for anyone that says they might prefer one.

Arch is not for everyone, it says so in official documentation and descriptions everywhere. It is targeted at 'experienced' or 'competent' users.
If a given person is neither competent nor experienced by their own surmising, then they may not want to use Arch. 
Or, they may want to dive in and try it for themselves, for educational purposes, or whatever their reason.
Arch has some of the best documentation available and an excellent forum search feature. Both of which go largely unused *by the very people who should be consulting it in the first place!*
Many, many tens of thousands of hours have been donated freely toward the distro and wiki. And yet, still some 'help vampires' who feel they are 'entitled' to hand-holding via step-by-step instructions in encyclopedic detail come forward asking very elementary questions.
It is only statistical probability that a few get told to RTFM. (In fact, very few get told this, in my own experience.)  

The concept that some of the documentation is perhaps 'too good' has been put forth a few times on these forums. The premise being that the guides make it so straightforward to get the distribution installed and configured, that when an error or unforeseen occurrence materializes, the user immediately blames Arch for its 'instability'. 
This may have some merit, but ultimately, Arch is simply what *you* make it. 
It offers very little assistance, and does require human intervention especially when upstream changes come along.
I see people on the Arch forums constantly asking questions from day to day. 
On day #1 a person asks for help installing GNOME. On day #2 they may ask which WM they should try. Day #3, after trying GNOME, KDEMod, Openbox and LXDE, they are having configuration problems and permissions issues and complaining of 'instability'.
Meanwhile, you just *know* that a pacman -Q | wc -l on their system will probably show over a thousand packages on their system, many of which they don't even need.
Again, if one wants to use Arch, they must keep in mind that 'Arch is what you make it.'

As for GUI tools, there is an entire project dedicated to a GUI installer and pacman front end, if that is your cup of tea.

---

### Post by chucky chuckaluck on 2009-02-05
> **MisfitI38 said:**
> It is targeted at 'experienced' or **'competent'** users.

( uh-oh! :( )

---

### Post by mips on 2009-02-05
> **chucky chuckaluck said:**
> ( uh-oh! :( )

Lol, ya best you format and re-install something simpler :)

---

### Post by Rumor on 2009-02-05
> **estyles said:**
> I like Arch, really I do, but the sticking points for me that keep me from using it as a main distro are, 1) The community really has that RTFM mentality.  And some of the forum regulars will really shove it in your face.  2) There are precious few GUI tools.  If you ask for a GUI tool, expect to be told that you are an infidel that doesn't know the "Arch Way".  

These aren't from personal experience - or, rather, I haven't had anyone jump down *my* throat, but from reading the Arch forums, I've seen it happen very often to others who had, I thought, legitimate questions.  I don't need a lot of hand-holding and am perfectly willing to use the CLI for a vast majority of tasks, but...  here's the thing about GUI tools - particularly GUI settings managers...  they tell you what your choices are.  


I've been an active member of the Arch community for two and a half years, and I read the forums on a daily basis. I don't wholly agree with your spin on the community, though I can understand how you might come to some of your conclusions.

A great deal of the "rtfm" mentality seems to come about because people do not search the resources available before posting their question. I've seen instances where there will be three or four threads in a row, each addressing the same topic where it is obvious that none of the posters has bothered to read any of the other threads. Even the most patient person will get snarly when asked for the umpteenth time why 'klibc' errors are happening.

As to GUI settings tools, I find that the man pages detail the settings quite well for most packages, and usually go into much more detail than can be presented in a GUI manager. I understand why some people want to go clicky-clicky and be done. I am more of the type who wants to know *WHY* such and such a setting works the way it does. To each their own.

> **RJARRRPCGP said:**
> Yes, if you don't mind reformatting and reinstalling at least about 10 times!:evil: 

They're appears to be package breakage and it seems to have just gotten worse within just some hours ago! :evil:

KDE, when it was usable about 24 hours ago, I cannot use KDE now, because it claims a missing file and when I click "OK", I'm back at the command line!

I cannot think of any issue where you would have to do a complete reinstall of anything ten times. Starting your application from a terminal will give you a reason why it does not work. you can then search on that reason or determine what you need to do to fix it.

I've been using and upgrading the nVidia drivers regularly for years. Beyond the occasional need to regenerate an xorg.conf file, I've never experienced any breakage.

Most issues that crop up can be resolved by remaining calm and doing some simple diagnosis.

> **MisfitI38 said:**
> 
Arch has some of the best documentation available and an excellent forum search feature. Both of which go largely unused *by the very people who should be consulting it in the first place!*
Many, many tens of thousands of hours have been donated freely toward the distro and wiki. And yet, still some 'help vampires' who feel they are 'entitled' to hand-holding via step-by-step instructions in encyclopedic detail come forward asking very elementary questions.


QFT.

The past few days here in the Arch corner of the Ubuntu community has seen a flood of questions that are covered in the wiki or detailed in the forums. For the most part I think those questions have been answered in a polite and helpful way . . . mostly because I've kept my big mouth shut :p

Arch is what YOU make it. The responsibility for it is in your hands.

I don't at all mind helping someone who genuinely needs help, but help me out by giving me some detail. Tell me what errors you're getting, include .conf files, give me something more than "KDE is broked! Wat do I do!??!!?" Ask smart questions and you'll be a whole lot less frustrated by the responses you get.

---

### Post by MisfitI38 on 2009-02-05
> **chucky chuckaluck said:**
> ( uh-oh! :( )

Always. You always make me smile, chucky.
This time you made me laugh. ;)

---

### Post by Redrazor39 on 2009-02-06
I was an epic noob before I started using Arch, and I still am to some extent, but I have learned SO much.

Just remember, FOLLOW THE BEGINNERS GUIDE. If you can, print it all off like I did and follow it step by step. It will save you so much hassle.

---

### Post by AllRadioisDead on 2009-02-06
> **Redrazor39 said:**
> I was an epic noob before I started using Arch, and I still am to some extent, but I have learned SO much.

Just remember, FOLLOW THE BEGINNERS GUIDE. If you can, print it all off like I did and follow it step by step. It will save you so much hassle.
I suppose I'll have to get back to this when I can access a printer.

---

### Post by smartboyathome on 2009-02-06
> **ihermit said:**
> I suppose I'll have to get back to this when I can access a printer.

It is included on the CD so technically you don't need to print it out if you don't want to. ;)

---

### Post by fwojciec on 2009-02-07
> **estyles said:**
> The community really has that RTFM mentality

A community that prides itself on writing documentation (have a look through the wiki) is likely to encourage others to read it.  It's perfectly natural, and there is nothing wrong with it.  Remember -- Arch is a community driven distribution, not a business, so there is a perfectly healthy tendency to try and educate new users so that they can become, at the very least, self-sufficient, and so that they can hopefully contribute to the effort in the future.

The alternative is death by [Help Vampires](http://www.slash7.com/pages). ;)

---

### Post by dannytatom on 2009-02-07
As both Misfits(I think) and fwojciec have mentioned, it seems help vampires have started the RTFM mentality.  So many of the posts I see on the Arch forums are people asking for help with things that could easily be fixed with a quick google search.  One of the main "points" of Arch (as I see it) is doing it yourself from the ground up and not having your hand held in the process.  Arch is meant for people with an alright understanding of linux, anywho.

---

