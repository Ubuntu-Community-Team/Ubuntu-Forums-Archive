---
title: "Trying out Ubuntu for the first time..."
date: 2007-03-16
forum: Absolute Beginner Talk
---

### Post by Stickymaddness on 2007-03-16
Hello to everyone in the Ubuntu community! 

I'm Stickymaddness and I'm new to Ubuntu, but I'm not a complete linux n00b!! I've had a fair share of hardware/networking/internet/programming experience and I've run linux a few times. My first exposure to linux was a Redhat 6.2 disk that I was given. I tried it out, loved the fortune app and how sexy you could make the window managers, but ultimately reverted back to windows because I couldn't do what I wanted to. I later tried gentoo out, which I did enjoy, but ultimately I got tired of having to "fiddle" and ask the experts for help every time I wanted to do something.

I'd been thinking of giving linux another go for a long time, when a friend saw a youtube clip of Beryl and instantly wanted to try it out, which was the final nudge I needed to give it a go. A bit of reading up later, and Ubuntu really did sound like the way to go! 

I'm very excited about trying it out, and I would *Love* to have my pc 100% Microsoft free, I've always remained a huge fan of linux, I just haven't had the time to fiddle to get things to work. Which is my main concern...how much "fiddling" would I need for things to just work? And what about all my precious apps? I've heard there are better linux equivalents or there is ways to run the windows apps if there isn't, but how time consuming is this to get working?

As for what my precious apps are, I'd want to be able to run apps (or their equivalents) of :

[LIST]
[*]Photoshop cs 2
[*]The macromedia suite
[*]Nokia phone connectivity software
[*]Clonedvd
[*]Fruityloops
[*]Acid Music
[*]Uniform server
[*]A media player with support for all the codecs out there
[*]And of course, games!! What about directx10?
[/LIST]

**Thank you and apologies for the long post...**

---

### Post by oilchangeguy on 2007-03-16
try this
[http://www.linuxeq.com/](http://www.linuxeq.com/)

---

### Post by rennen01 on 2007-03-16
IMO, Ubuntu is one of the easiest flavors of Linux to install.  Good luck and welcome.

As far as the Apps, use wine after you are set up in Ubuntu and wine can run Windows Apps.  I can't guarantee it will run all of them, but there is great community support here.

---

### Post by Malta paul on 2007-03-16
Hi Welcome hope you enjoy Ubuntu :) 
You may like to take a look at [http://psychocats.net/ubuntu/index](http://psychocats.net/ubuntu/index)
good luck

---

### Post by jhenager on 2007-03-16
> **oilchangeguy said:**
> try this
[http://www.linuxeq.com/](http://www.linuxeq.com/)

LOL, looking through the list and seeing DVD Rip-o-Matic. :)

Although Gimp is a very excellent graphics package, with WAY more capabilities than I would ever use (I still don't know how to use layers, for example.) I do know that Creative Suite 2 is one of the most high end software packages out there. It doesn't cost thousands for no reason.
I will say this about that impressive list of required software - there is an equivalent for just about everything in Linux (I didn't see gnuCash listed as an equivalent for Microsoft Money or Quicken, btw).
Go for it. Dual boot if you have to. 
The last time I heard someone complain there was not enough software out there for Linux, I checked Synaptic.
There were over 18,000 entries, and the total cost? $0.

Looking again, I do see Quicken and gnuCash, just no entry for M$ Money.

---

### Post by Stickymaddness on 2007-03-16
Hi everyone,

=D> Thanks for the uberfast replies and the advice/resources you have pointed me to!! I will be installing ubuntu in a few days time and will let you all know how it goes. I will be temporarily dual booting, but I hope I will be doing a full conversion soon!!

I would love to be able to be one of the people who go "roflmao!! You run windows?!?!?"

---

### Post by honns on 2007-03-16
I am sad to report that DX10 will not be made for anything but Windows (Vista at that, no XP)  I had heard that the creators of wine will make a hacked version to run games, but because you will be running through an emulator you really wont be running the games optimally, although you will be able to play them.

About the other stuff, gimp is a photoshop clone.  A good media player? VLC - my favorite for windows and for linux, it plays almost all sound and video files.  I am truthfully not sure about the other stuff you mentioned, except I know there is support for DVD burning (tho i know nothing about it).  The rest you might be able to run with wine (Windows emulator stated above), good luck and welcome to the Linux world!

---

### Post by reacocard on 2007-03-16
> **Stickymaddness said:**
> A media player with support for all the codecs out there?

For music I recommend [Exaile]("http://www.exaile.org"). Extremely powerful, and easy-to-use. I have an Ubuntu Edgy repo for it even, so you can always stay up-to-date with the newest version. (see Exaile's Releases page, just after the packages.)

For videos, vlc, gxine and totem-xine all work very well. Totem-xine is best for gnome integration, but the other two offer a lot more options and features.

To get them to play everything:
```
sudo apt-get install gstreamer0.10-plugins-ffmpeg gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse libxine-extracodecs
```

You'll have to enable universe and multiverse for some of these.


As for games, there's Cedega for running windows games under linux, and of course there are all the games that are natively available for linux. Don't expect to be able to play everything though. If you really need certain games, I would say just dual-boot windows for now, until you've beaten those games, and only get new games that are linux/cedega-compatible.

Also, for PS CS2, I just found this thread: [http://ubuntuforums.org/showthread.php?t=275488](http://ubuntuforums.org/showthread.php?t=275488)

---

### Post by Stickymaddness on 2007-03-18
Well, I've just finishing installing Ubuntu and I have to say I'm majorly impressed! You'd have to be a complete mongoloid not to be able to install Ubuntu! Also being able to browse the net while I installed was pretty damn kewl too!!

Quick questions, how do I go about installing applications? I've seen that I can use something like 

```
# apt-get install appname
``` 

to install apps, but I receive an access denied error, which brings me to my next question, what is my root password? I tried to "su" but I don't know what password it wants....

---

### Post by reacocard on 2007-03-18
> **Stickymaddness said:**
> Well, I've just finishing installing Ubuntu and I have to say I'm majorly impressed! You'd have to be a complete mongoloid not to be able to install Ubuntu! Also being able to browse the net while I installed was pretty damn kewl too!!

Quick questions, how do I go about installing applications? I've seen that I can use something like 

```
# apt-get install appname
``` 

to install apps, but I receive an access denied error, which brings me to my next question, what is my root password? I tried to "su" but I don't know what password it wants....

You don't 'su' in Ubuntu, you 'sudo'. Sudo gives you root privileges for the command right after it, and you use your login password. So for apt-get, you would use:
```
sudo apt-get install appname
```
entering your login password when prompted.  To get the equivalent of su, use 'sudo -s -H'.

Also, there is Synaptic in the System->Administration menu if you prefer a GUI method of handling packages.

---

### Post by Stickymaddness on 2007-03-18
Found my problem!!!

I was running feisty faun! I was given a copy of it on cd to try out by a friend.

As I've found out, this is NOT a good idea! I was confused about how to install apps because Synaptics was missing from my installation!! System->Administration only had 4 items in it!! Also "sudo apt-get install appname" would exit and not do anything....

So suffice to say, I downloaded 6.10 and am installing it as I'm posting this!

Thanks for the help in any case!! 

Now that everything is up 100%, time to learn my new OS!!! :D 

*(Sorry about the double post!)*

---

### Post by Stickymaddness on 2007-03-19
Well I have to say I'm pretty damn impressed!

Linux has come A LONG way since I last ran it. Ubuntu is without a doubt the best distribution I have ever run, not to mention the best operating system I have ever run!! Simplicity combined with power! The install couldn't have been easier, and with minimal fiddling I have gotten everything I need so far up and running.

**Major shoutout to the Ubuntu and the open source community!! Keep up the good work!!**

---

### Post by Stickymaddness on 2007-03-19
> **reacocard said:**
> For music I recommend [Exaile]("http://www.exaile.org"). Extremely powerful, and easy-to-use. 


Thanks I got that working, but have to admit I still prefer xmms ;)

[QUOTE=reacocard;2307963]
To get them to play everything:
```
sudo apt-get install gstreamer0.10-plugins-ffmpeg gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse libxine-extracodecs
```

Had a little trouble here:

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package gstreamer0.10-plugins-ffmpeg

```

I have enabled universe and multiverse...

---

### Post by reacocard on 2007-03-19
> **Stickymaddness said:**
> Thanks I got that working, but have to admit I still prefer xmms ;)

[QUOTE=reacocard;2307963]
To get them to play everything:
```
sudo apt-get install gstreamer0.10-plugins-ffmpeg gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse libxine-extracodecs
```

Had a little trouble here:

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package gstreamer0.10-plugins-ffmpeg

```

I have enabled universe and multiverse...

My bad, the package name should be gstreamer0.10-ffmpeg

---

### Post by o0splitpaw0o on 2007-03-19
OK here's equivalents or  work aorunds to use the software:

**    * Nokia phone connectivity software - **
Click on Applications > Click on Add/Remove > type in **gnokii** check mark the software. >hit apply . type in your password> software will tell you where the icon is for it.
**    * Clonedvd**
Click on Applications > Click on Add/Remove > type in **Acidrip** check mark the software. >hit apply . type in your password> software will tell you where the icon is for it.
**    * Fruityloops**
Click on Applications > Click on Add/Remove > type in **Audacity** check mark the software. >hit apply . type in your password> software will tell you where the icon is for it.
    * Acid Music
Audacity does it all, no need
 **   * Uniform server**
Read the wiki on the linux client at [http://wiki.uniformserver.com/Main_Page](http://wiki.uniformserver.com/Main_Page) (not in the repositories)
    * A media player with support for all the codecs out there
  **  * And of course, games!! **
Click on Applications > Click on Add/Remove >click on games, checkmark all the games you want>hit apply . type in your password> software will tell you where the icon is for it.
**What about directx10?**
We need no stinkin' direct X we got OpenGL! - but you will need to setup your video card
[B]  * Photoshop cs 2
  * The macromedia suite[/B]
You can use Gimp for Photoshop, but if you like the plugins for photoshop, you need to install **wine**. This is the one I prefer to use directly from wine's website, because the new releases support icon directx, and directory support nicely. 
visit [http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html) and download the latest version based on what version of ubuntu you installed.

Click on it> Select "open with GDebi package installer" >click on install> type in your password>
DONE!

Now associate ".exe" files: Simple:

Put the CD in > **right click** on the "setup.exe" > click on properties> click on "open with"> click on Wine windows emulator if available ... if not > click on add > click on "use custom command > type in **wine** > click on add > click on close > now just click on the setup.exe and BAM! your on your way.

---

### Post by Stickymaddness on 2007-03-20
> **reacocard said:**
> My bad, the package name should be gstreamer0.10-ffmpeg

Excellent! Thank you! :popcorn: 

splitpaw, thank you for that list! I will have a look at those apps when I get a chance!

---

### Post by thefoolisme on 2007-03-20
Just to add my two cents, I've used Photoshop for years, and had Gimp installed at my office for occasional personal use.  If you are used to Photoshop, you won't like Gimp as much.  While it is a great program, and would be fine for most, there have been a few times where I've tried to do something in Gimp that I could do in Photoshop, and the option wasn't there.  Hard core PhotoShoppers will notice a difference.  In fact, Photoshop is the one reason I'll be attempting a Wine install myself, since I'm a newbie too.  But I do like Ubuntu so far.  I told my stepson that if he breaks his Windows one more time due to spyware, viruses, and crap, that I was putting Ubuntu on his computer too  :-)

---

### Post by Stickymaddness on 2007-03-22
Totally agree with you! I've tried to get by with gimp, it is a good app, but I need my photoshop!! I just _have_ to get my CS 2 running!!

---

### Post by MrCheese on 2007-03-22
I've been running linux for years (ever since PC Pro or whatever had Slackware on the cover and I had to cut 30-odd floppies to load it....)

From Slackware I went onto Redhat then I was a long-time SuSE user, tried FreeBSD, then Mandrake, experimented briefly again with RedHat & its cousins, then Debian & a few derivatives until one day I downloaded Ubuntu (Breezy Badger) and haven't looked at another distro since. Ubuntu does everything I want it to without doing stuff I dont want it to (ok, every distro has the odd rogue update which breaks something you rely on, but don't tell me Window$ doesn't as well).

Ubuntu gives me the right blend of usability, stabiity, maintainability and choice. I'm sure you'll soon be hooked when you get started.

As for apps, if there are Window$ apps you really can't live without, Wine may be the open-source answer but commercial solutions such as Crossover Office are affordable and more importantly, just work without fiddling. Many may flame me for this statement but if what you want is say, Office 2003 running on Ubuntu, who are we to argue? Actually, I have this on my desktop, trying to wean my wife away from the Dark Empire!......

---

### Post by Stickymaddness on 2007-03-22
> **MrCheese said:**
>  I had to cut 30-odd floppies to load it....)

Haha! I remember those days! Thank god we now have cd and dvd!!

> **MrCheese said:**
> Ubuntu gives me the right blend of usability, stabiity, maintainability and choice. I'm sure you'll soon be hooked when you get started.

I'm already hooked!! Ubuntu is definitely here to stay as far as my pc is concerned!!

> **MrCheese said:**
> Many may flame me for this statement but if what you want is say, Office 2003 running on Ubuntu, who are we to argue? Actually, I have this on my desktop, trying to wean my wife away from the Dark Empire!......

Personally I can't stand MS Office and have always used open office, but I get what your saying about still running the "essential"  windoze application....

---

### Post by hyper_ch on 2007-03-22
Regarding Win appz... if you can't run them in wine/crossover/cedega you still have an option to install vmware or virutalbox and have a virtual windows within your linux... however that is quite a ressource hog... I have 1 GB DDR ram and a 1.6 Ghz Athlon processor... it's ok... Civ 4 runs fine... but I notice that it's not near as "fast" was if it was WinXP alone...
However vmware allows me to run the last few windoze only programs :)

Regarding games: There you are probably better off having a Win install somewhere... not appz etc. loaded.. no firewall / antivirus (if you just use that windoze for gaming you don't need all that stuff...)

---

### Post by Stickymaddness on 2007-03-22
> **hyper_ch said:**
> 
Regarding games: There you are probably better off having a Win install somewhere... not appz etc. loaded.. no firewall / antivirus (if you just use that windoze for gaming you don't need all that stuff...)

I have an option in grub with the title "Games" Guess what that loads ;)

---

### Post by Arken on 2007-03-22
> **Stickymaddness said:**
> Hello to everyone in the Ubuntu community! 


[LIST]
[*]Photoshop cs 2 - The GIMP - pre-installed with Ubuntu
[*]The macromedia suite
[*]Nokia phone connectivity software
[*]Clonedvd
[*]Fruityloops
[*]Acid Music - There's a thing that works like iTunes pre-installed.
[*]Uniform server
[*]A media player with support for all the codecs out there
[*]And of course, games!! What about directx10?
[/LIST]

**Thank you and apologies for the long post...**

Hey, welcome to Linux! I am the noob of linux so far, and it boggles my brain cells. If you have wireless internet, I would advise keeping Windows on your system.

---

### Post by Stickymaddness on 2007-03-22
> **Arken said:**
> Hey, welcome to Linux! I am the noob of linux so far, and it boggles my brain cells. If you have wireless internet, I would advise keeping Windows on your system.

Greetings fellow newb!! :D Nope, I've had my internet up and running no problem since booted off the install cd!!

---

