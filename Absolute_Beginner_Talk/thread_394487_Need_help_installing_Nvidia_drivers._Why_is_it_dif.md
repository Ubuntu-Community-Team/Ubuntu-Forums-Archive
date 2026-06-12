---
title: "Need help installing Nvidia drivers. Why is it difficult?"
date: 2007-03-27
forum: Absolute Beginner Talk
---

### Post by linuxmonkey on 2007-03-27
I've been hearing about how Linux Desktop is making a comback, but I think Linux is way behind when it comes to ease of use. I'm a computer geek.  Everyone comes to me for computer questions and help.  I tried Ubuntu years ago, but didn't like it to much.  I wanted a little project this weekend, so I decided to give Ubuntu another try.  The install process went fine, zero problems. When the desktop came up, I noticed the resolution was pretty low. I checked the preferences, and my standard resolution for the Dell 2001FP is 1600x1200. That resolution wasn't an option.  I then went to Nvidias site, and saw they offered drivers for Geforce cards. I downloaded, tried to install, got unicode error message. I then did research on Ubuntus forum, and I had to printout 2 pages of terminal instructions to get the Nvidia drivers installed.

This is pretty sad. I managed to get them installed, resolution was how I wanted it. I then installed a few other programs, which was pretty easy using the built in installers. I rebooted my system to do some stuff in Windows.  Later, I rebooted into Ubuntu, and bam, got a "Failed to start the X Server" erorr. For some reason, my xorg.conf was bad.  I went back to the forums, and read up on how to fix this using sudo dpkg-reconfgure xserver-xorg.  I went thru the process keeping all of the defaults. I then started the gdm, and first thing I noticed was no sound.  Next thing was my resolution was incorrect.  Finally the graphics were very sluggish.

So, I'm back in WinXP.  I'm pretty disappointed about my experience so far.  This is alot of trouble trying to get something to work and its Way to much trouble for an average user.  

Any thoughts/suggestions on what I did wrong?  Why is installing standard Nvidia drivers so difficult?  What happen to my sound?

---

### Post by jinx099 on 2007-03-27
For your video drivers, why dont you try automatix?  Or you could also try Ubuntu 7.04 Beta.

Automatix is very easy to set up and will install your drivers, and other stuff without being a PITA.

---

### Post by linuxmonkey on 2007-03-27
> **jinx099 said:**
> For your video drivers, why dont you try automatix?  Or you could also try Ubuntu 7.04 Beta.

Automatix is very easy to set up and will install your drivers, and other stuff without being a PITA.

I plan on doing a reinstall tomorrow.  I'll give Automatix a try.  Why isn't this included in the standard installations?

---

### Post by Henry Rayker on 2007-03-27
I have no idea what happened to your sound (it may be muted...try using ```
alsamixer
``` in the terminal and changing the volumes of the Master and the PCM.) I know I've experienced situations where an app would just decide to mute one of my channels for one reason or another.

As far as the nVidia drivers goes...the issue is very complex. The drivers in question aren't open source and, as this is a Debian-based distro, that's kind of a no-no. If the manufacturers of hardware would actually support this sector of the market, things would be quite different. Imagine how you'd react if your hardware never came with drivers on the cd and you had to download them all in Windows...I find that more annoying than the "difficult" installation process. Honestly, after a while, it becomes second nature and installation is a breeze again.

All in all, I honestly believe Linux based distros (I'm using Fedora from now on, for the most part) to be MORE user friendly than M$ operating systems...I guess it's just my perspective, but I have far fewer issues with my machine (and when I have an issue, rather than it being a, "Well, nothing I can do there" sort of issue, it ALWAYS gets resolved.

---

### Post by ndube on 2007-03-27
> **linuxmonkey said:**
> I've been hearing about how Linux Desktop is making a comback, but I think Linux is way behind when it comes to ease of use. I'm a computer geek.  Everyone comes to me for computer questions and help.  I tried Ubuntu years ago, but didn't like it to much.  I wanted a little project this weekend, so I decided to give Ubuntu another try.  The install process went fine, zero problems. When the desktop came up, I noticed the resolution was pretty low. I checked the preferences, and my standard resolution for the Dell 2001FP is 1600x1200. That resolution wasn't an option.  I then went to Nvidias site, and saw they offered drivers for Geforce cards. I downloaded, tried to install, got unicode error message. I then did research on Ubuntus forum, and I had to printout 2 pages of terminal instructions to get the Nvidia drivers installed.

This is pretty sad. I managed to get them installed, resolution was how I wanted it. I then installed a few other programs, which was pretty easy using the built in installers. I rebooted my system to do some stuff in Windows.  Later, I rebooted into Ubuntu, and bam, got a "Failed to start the X Server" erorr. For some reason, my xorg.conf was bad.  I went back to the forums, and read up on how to fix this using sudo dpkg-reconfgure xserver-xorg.  I went thru the process keeping all of the defaults. I then started the gdm, and first thing I noticed was no sound.  Next thing was my resolution was incorrect.  Finally the graphics were very sluggish.

So, I'm back in WinXP.  I'm pretty disappointed about my experience so far.  This is alot of trouble trying to get something to work and its Way to much trouble for an average user.  

Any thoughts/suggestions on what I did wrong?  Why is installing standard Nvidia drivers so difficult?  What happen to my sound?

I'm not sure what happened to your sound but the following link should help you get your nvidia drivers to work correctly. It is a script that automatically downloads the latest nvidia drivers from nvidia's website (and any dependencies) and configures your xorg.conf.

[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

I would try reinstalling ubuntu, running the envy script to get the most recent drivers, and then using automatix to install codec's, google earth, etc. [http://www.getautomatix.com/](http://www.getautomatix.com/)

---

### Post by viergeame on 2007-03-27
It does take a bit of confusion sometimes with the set-up.  I'm sure all of us here have run into something that made us question our decision, but in the end if you stick with it it's completely worth it.  I remember installing Windows XP and having a ton of problems with it, and it taking a whole weekend to get it going.  I think that the big difference in a lot of cases is that Linux in general is just unfamiliar so it seems more difficult.  In my experience, limited though it may be, once you get down a few things it's far more user-friendly.  This may not be the case for you, but still I suggest working with it a bit more.

---

### Post by Toadmund on 2007-03-27
No, it's OK I suppose, I've had no problems.

Now I got a question, why the hell is it illegal to download codecs and drivers for hardware that we already purchased?
Do they not want us to be able to use their stuff?:confused: 

I think it's a Micro$haft conspiracy, I mean; it all works on Micro$hafts OS without it being illegal, is it part of the purchase price of M's OS?

I hate anti-trust monopolizers, which is why I use Ubuntu now.
Scumbag corporate Bast:x :x :x's

I DO NOT approve of this!!!
(nope, no way!)

---

### Post by zorkerz on 2007-03-27
First off welcome and glad your willing to keep giving new things a try periodically. If your looking for another project i think you may find success here with a new try.

> The install process went fine, zero problems.
Which version of ubuntu did you install?  and is it ubuntu using gnome or possibly a different gui like KDE (kubuntu)?

First off I would recommend doing a clean install as it is fast and it does not sound like you have many settings you will loose.  Otherwise you can attempt to fix your xorg.config file but this can be more work than its worth sometimes. If you do not wish to do a fresh install we could go through the xorg.conf file. It sounds as if your graphics driver section, monitor section, and sound section have been configured improperly by the reconfigure. There should be backups in /ect/X11/  you could copy the sounds section from an older one that worked. 

> I then went to Nvidias site, and saw they offered drivers for Geforce cards I will start here assuming a fresh install. I would recommend installing the drivers in a different way. Your method can work and does give you the absolutely newest version but as you saw the howto is not short or simple. [This page]("https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/graphics-cards.html")  gives you a great description of what to do. Essentially you will use synaptic or preferred installation method and select the appropriate nvidia package.

 > When the desktop came up, I noticed the resolution was pretty low.
With any luck this will be solved by installing the nvidia drivers from above.

Graphics drivers can be a huge pain i know ive run into trouble dealing with them before but power through this as I think you will find it well worth the trouble.
Best of luck write back with questions or how you found a solution.

---

### Post by zorkerz on 2007-03-27
wow i spent too long in my reply you all beat me to it!

---

### Post by linuxmonkey on 2007-03-27
> **zorkerz said:**
> 
 I will start here assuming a fresh install. I would recommend installing the drivers in a different way. Your method can work and does give you the absolutely newest version but as you saw the howto is not short or simple. [This page]("https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/graphics-cards.html")  gives you a great description of what to do. Essentially you will use synaptic or preferred installation method and select the appropriate nvidia package.


It looks like Envy from the link posted earlier would install the Nvidia drivers the easiest.  Do you not recommend that program?

[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

### Post by zorkerz on 2007-03-27
Ive never used it but i would trust tseliot on nvidia drivers.

---

### Post by Patrick K on 2007-03-27
I've used the Envy script and it works great.

---

### Post by Spalatum on 2007-03-27
You should definitely use the Envy script. It does all the work for you and works out of the box. I'm still new to Ubuntu and Linux in general and I must say that this script saved me a lot of trouble.  

You can get Envy here:

[Envy]("http://albertomilone.com/nvidia_scripts1.html")

---

### Post by the.unclean.cpp on 2007-03-27
I won't recommend you Ubuntu 7.0 (is still not for every day use), but I have to say I'm surprised of all the things you had to do to obtain your wanted resolution...It took me 5 minutes to install....You could've install the driver from the Add/Remove... Section
Anyway, I think Linux is more User Friendly than Linux :) The desktop is much more welcoming and everything is much faster and unchrashing on linux :guitar:

---

### Post by the.unclean.cpp on 2007-03-27
> **Spalatum said:**
> You should definitely use the Envy script. It does all the work for you and works out of the box. I'm still new to Ubuntu and Linux in general and I must say that this script saved me a lot of trouble.  

You can get Envy here:

[Envy]("http://albertomilone.com/nvidia_scripts1.html")

Aye...there....whatever are you doing, don't use Envy....it screwed up my X Server twice...

---

### Post by frodon on 2007-03-27
You are new to ubuntu, **why don't you just try to read the documentaion made for you** ;)
It will prevent you from all the side effect of external scripts (like automatix) and packages outside the repositories (like the nvidia drivers installed by envy) :
[https://help.ubuntu.com/](https://help.ubuntu.com/)

Read it all you want to know is there and all these instructions are approved and won't create you any problems.

---

### Post by msak007 on 2007-03-27
Feisty will attempt to fix the problems you had with your driver by making it easier to install the proprietary drivers from the repositories. As was already stated, they can't be installed by default because of their proprietary nature and would violate the principles of Ubuntu and Debian. But they can always be installed later:

[http://137.99.54.155/nv_not_good_enough.JPG](http://137.99.54.155/nv_not_good_enough.JPG)

I can't tell you yet how well this works yet because I have an Intel card on the laptop I'm testing Feisty on so those drivers are installed out of the box. I'll  be interested to see how well it works with my desktop which has an ATI card :rolleyes:.

---

### Post by Patrick K on 2007-03-27
> **the.unclean.cpp said:**
> Aye...there....whatever are you doing, don't use Envy....it screwed up my X Server twice...

I had a problem the first time I used the script. I now edit /etc/X11/xorg.conf from the "nv" driver to the 'nvidia" driver myself. Since doing this I've had no problems. Resolutions up to 1920x1200 are available for my old GF2mx card. 

What is nice about the script is it checks what card is installed and goes and gets the latest Nvidia driver from Nvidia's site for the card installed. No guessing as to which driver to use. A couple upgrades had hosed the video but running Envy fixed things perfectly.

---

### Post by zorkerz on 2007-03-27
In the future please separate you posts into multiple topics for everyones sake. It is difficult to give help when your os is being railed in the background and also difficult the have a serious comparison of os capabilities when we are also talking shop. Great to know its working now.

---

### Post by Zkupa on 2007-03-27
The first couple of times i installed the nvidia drivers it was a pain, but after i got used to it (have been using Ubuntu for 2 months or so) it got easier. I dont understand why you had to print out 2 pages to install them. 

All i do is :
sudo /etc/init.d/gdm stop (when in a black screen press ctrl+alt+f1 to come to a terminal window)
cd to directory with drivers in it (download folder)
sudo sh NVIDIA-(nameofdriver)
then just do what the screen tells you
When its done just do : sudo /etc/init.d/gdm restart

sure sometimes its not working, but after a little play-around with the xorg you should have a new shiny Nvidia-screen on startup.

You said somethin about installing some new programs using the installer, maby you got some updates for the kernel or the headers? Some say that would mess up the nvidia drivers and they should be reinstalled after this. Dont know about that one though.

Fell free to correct me if i am wrong, i am still not very experienced in the ubuntu/linux area :)

---

### Post by frodon on 2007-03-27
@zkupa
The easiest way is still to use the feisty GUI or type :
```
sudo apt-get install nvidia-glx
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
sudo nvidia-xconfig --no-composite
```Advanced explanations here :
[http://doc.gwos.org/index.php/Latest_Nvidia_Edgy](http://doc.gwos.org/index.php/Latest_Nvidia_Edgy)

---

### Post by brennydoogles on 2007-03-27
> **linuxmonkey said:**
> Any thoughts/suggestions on what I did wrong?  Why is installing standard Nvidia drivers so difficult?  What happen to my sound?

I've read so many threads recently about Nvidia drivers causeing serious problems with the system. I guess I was lucky (or poor) enough to have a super old card which was automatically recognized by Ubuntu. As for ease of use, Ubuntu is not windows (where the computer does the thinking for us), and sometimes we sacrifice ease of use for the ability to do whatever we want with our own computer (like edit important system files whenever we want). I miss super easy driver installation as well, but I don't think I would ever go back. I haven't booted my XP partition in weeks.

---

### Post by frodon on 2007-03-27
> **brennydoogles said:**
> I've read so many threads recently about Nvidia drivers causeing serious problems with the system. 4This concern only those who don't use the nvidia drivers of the official repositories mainly when a new kernel update come because when you install them outside the repository you have to install them again each kernel update (what you don't have to do if you use the package from the repo), if you use the version from the repositorie you won't have problems.

---

### Post by aysiu on 2007-03-27
> **zorkerz said:**
> In the future please separate you posts into multiple topics for everyones sake. It is difficult to give help when your os is being railed in the background and also difficult the have a serious comparison of os capabilities when we are also talking shop. Great to know its working now.
I've done it. I'm also retitling the thread, so it can actually get some support and not just arguments.

Arguments about Ubuntu/Linux being "user friendly" or not have moved [here](http://ubuntuforums.org/showthread.php?p=2359690#post2359690).

Arguments about the legality of Nvidia drivers have moved []here](http://ubuntuforums.org/showthread.php?t=394791).

---

### Post by linuxmonkey on 2007-03-27
First I would like to say thanks for all the comments.  I hope I didn't step on anyones toes.  I have re-thought some of my comments, and see that I may have been a little to hard on Linux.  I have to agree that the base Ubuntu install is easier then installing Windows (and its faster).   I am not giving up this time on Ubuntu.  I guess I had a bad experience and was venting.  So far I like what I see, once I got over the Nvidia driver issue solved.  I'm not sure if I can make Ubuntu my main OS, since I rely on a number of windows based programs day to day, but I hope to search for replacements.  I'm hoping to find a site with a table of windows apps to Linux apps replacements.

Sorry if I offended anyone, I hope to be able to contribute to the forum in the future.

---

### Post by aysiu on 2007-03-27
> **linuxmonkey said:**
> I'm not sure if I can make Ubuntu my main OS, since I rely on a number of windows based programs day to day, but I hope to search for replacements.  I'm hoping to find a site with a table of windows apps to Linux apps replacements. Here are a couple:
[http://www.linuxrsp.ru/win-lin-soft/table-eng.html#1](http://www.linuxrsp.ru/win-lin-soft/table-eng.html#1)
[http://linuxappfinder.com/windows](http://linuxappfinder.com/windows)

> 
Sorry if I offended anyone, I hope to be able to contribute to the forum in the future. I don't think you've offended anyone. People are constantly arguing about this stuff. The truth is somewhere in the middle. Desktop Linux gets an unnecessarily bad rap, but it still could use some GUI frontends for things (and the developers are constantly improving the interface and general user experience), and we all know this.

I'm glad you'll be contributing to the forum in the future. Don't be afraid to ask questions.

---

### Post by Toadmund on 2007-03-27
linuxmonkey said:
> I'm not sure if I can make Ubuntu my main OS, since I rely on a number of windows based programs day to day, but I hope to search for replacements.
That's one of the biggest things, re-learning linux versions of programs you already knew so well on windows.
For instance, I have my FTP (gFTP) all set up, but I have done no file transfering yet on it simply because I don't know it enough (I'm sure it's not that bad). It's just that sometimes I feel intimidated by the learning curve, and I wait for the moment when I feel right to dive in (da loinin' mood).
But there is nothing so bad that I feel I need to run back to Win OS.

After a short while windows will feel like Linux does now.:)

---

### Post by qamelian on 2007-03-27
> **linuxmonkey said:**
> I plan on doing a reinstall tomorrow.  I'll give Automatix a try.  Why isn't this included in the standard installations?

Because it has caused problems for some users by breaking their systems during upgrades between versions. It works great for some folks, not so great for others. Personally, I don't like it because it's a crutch. It's more to your advantage to learn to do things the right way. That said, if you need to get a system up quickly, utilities like Automatix and EasyUbuntu will certainly help you do it. Just be aware of the possible consequences when you are ready to upgrade to a newer version of Ubuntu.

---

### Post by qamelian on 2007-03-27
> **linuxmonkey said:**
> I'm hoping to find a site with a table of windows apps to Linux apps replacements.

[http://www.linuxeq.com/](http://www.linuxeq.com/)

---

### Post by Yumi on 2007-03-29
Just installed Feisty beta. No problems installing and all my Nvidia problems are gone! Google Earth works, Screen Resolution is 1280x1024. So far beta is stable.

---

