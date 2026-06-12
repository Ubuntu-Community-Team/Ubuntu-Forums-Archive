---
title: "Install software complicated"
date: 2007-01-14
forum: Absolute Beginner Talk
---

### Post by reabralop on 2007-01-14
Why is it such a chore to install things! I put 6.10 on a partition and am trying to use it. Surfing the web is making me aware of the shortcomings of the plugins. So I look on the forums and am noticing that you have to type in commands, copy files to a directory, or whatever else looks complicated. Why?

Is it the software developer? the OS? Both?

I can see why people are reluctant to use this! I am a fast learner but how am I supposed to enjoy my experience when I have to go into so much detail just to do something simple! 

I'm already disappointed. I see the potential but am turned off by the unnecessary complexity.

---

### Post by taurus on 2007-01-14
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

[http://www.getautomatix.com/](http://www.getautomatix.com/)

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by mykalreborn on 2007-01-14
when you think about it most of the times it's a lot easier than windows. because you don't have to spend a huge deal of time searching for the software on torrent sites and then for cracks and then see they have viruses or spyware or some silly old primitive thing we linux users haven't heard about in a long time. all you have to do is type
```
sudo apt-get *software*
```
and we're done. yes sometimes it can get a bit tricky, but there are tons of resources out there to help you in such a manner that all you have to do is copy those texts in your terminal and hit enter.

---

### Post by reabralop on 2007-01-14
I tried the Automatix program but most of the programs I clicked on came back as an error and didn't install. 

The psychocats site is informative but I'm thinking of an analogy; just because you can eat your dinner in the bathroom doesn't mean it's a good idea. Meaning just because you can use the command line that doesn't make it the best way to install things. Are the developers not making it as simple as OS X or Windows? Why are the consumers having to copy the correct file to the proper directory or the command to the line. 

Why is this the way we have to do it?

I'm not trying to get out of a little work, I'm just looking at something not streamlined or simple and asking why?

---

### Post by kebes on 2007-01-14
Well installing software in Linux is certainly different, but I actually find it much simpler and faster than in Windows or Mac OS X. You can just open up the Synaptic package manager (Applications > Add Application) and pick what you want off of a list. (Or use the commandline, which is even faster.) You have a centralized system for installing things you need, instead of searching all over the web or walking to a store. I consider this a very efficient system.

Sometimes the problem is that you won't know what the thing you want to install is called, or can't find it in the repository list. taurus gave you a link to "automatix" which is a neat add-on that will help you install the "most often requested" things in one quick operations (things like mp3 support, DVD support, etc.). That's a good place to start.

---

### Post by mykalreborn on 2007-01-14
there are files that you just double-click and they install automaticaly:
* .deb files that work in debain like distros
* .rpm files that work in red hat like distros
* .mo files that work in slackware like distros
the problem is that not every software provider makes a .deb, a .rpm and a .mo installer with every version as it would be pretty time consuming.
and plus... it's FREE. how can you even complain about anything. yes it need some work, but it's getting there. if people would just be patient. like the old saying goes: "good thinks come to those who wait" ;)

---

### Post by jd65pl on 2007-01-14
Why learn to read when there are plenty of picture books out there?

---

### Post by mykalreborn on 2007-01-14
> Why learn to read when there are plenty of picture books out there?
i take it you were sarcastic.:p if so well put :D

---

### Post by old_geekster on 2007-01-14
> **reabralop said:**
> Why is it such a chore to install things! I put 6.10 on a partition and am trying to use it. Surfing the web is making me aware of the shortcomings of the plugins. So I look on the forums and am noticing that you have to type in commands, copy files to a directory, or whatever else looks complicated. Why?

Is it the software developer? the OS? Both?

I can see why people are reluctant to use this! I am a fast learner but how am I supposed to enjoy my experience when I have to go into so much detail just to do something simple! 

I'm already disappointed. I see the potential but am turned off by the unnecessary complexity.
I began using "Ubuntu 6.10", yesterday evening.  I have installed numerous programs and have not typed a command to this point.

To install programs, go to System/Administration/Synaptic Package Manager/Log-in and that is it.  The packages that are installed have the "Ubuntu" logo next to them.  To install a new package, simple check the box next to it.  If there are dependencies (other necessary programs), it will install them, also.

As for surfing the web, using "Firefox 2.0.0.1" makes it a snap.  I have found one site that required another plug-in (Adobe Flash).  When asked if I wanted to install it, I clicked yes and it was accomplished without rebooting.

Some of my peripherals are working, but not all of the functions.  I know there is probably a way to improve the performance, but I am not to that point, yet.

Don't quit on it now.  The learning curve will be worth the effort.  Unless you are a gamer, there is not anything that you can't do as well as with Windows.  Even gaming is getting better with "Wine" from what I have read!   The best part --- it and 1000+ programs are FREE!

Good luck!

p.s. I am 61 years old.  Don't let an old_geekster out perform you.;)

---

### Post by Sef on 2007-01-14
> Well installing software in Linux is certainly different, but I actually find it much simpler and faster than in Windows or Mac OS X. You can just open up the Synaptic package manager (Applications > **Add Application**) and pick what you want off of a list.

In Edgy Eft, 6.10, it is called Add/Remove.

---

### Post by reabralop on 2007-01-14
For that matter why learn Linux when I already know OS X & Windows.





I'm not trying to be sarcastic. I'm trying to learn this and I have been running into many walls today (I installed it this morning after using the live CD for a few days). I think I've figured out the main problem for me. I am looking at the posts for the issues that I've had and am seeing explanations that, in theory, are very simple but the execution is difficult. 

For example I finally found the terminal (I hope that is the same as the aptitude, I don't know), and have tried to install many DIFFERENT things and I don't think they installed. 

Change; I don't want to go into all the problems I've run into today. I want to point out that even in the beginner's forum the answers aren't dumbed down enough. I'm intelligent but if there is a code spelled out somewhere as the fix to the problem and it doesn't explain anywhere where to put that code to make it work, then anyone will have trouble with it and get frustrated. That is only one example of the "power users" not remembering that they too were noobs and needed the dumbest questions answered. 

As for my tries to install I will keep looking to figure out why they aren't working.

---

### Post by old_geekster on 2007-01-14
Here is a link to the best guide that I have found on installing programs: 

[http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy)

I just installed "Google Earth" and it works perfectly.  I still haven't typed a command, because I simply copied and pasted the command given into the terminal.

How to find the "Terminal":  Applications/Accessories/Terminal.  Click on the "Terminal" and it will open.  I pasted the command at the cursor and accepted the Directory and it installed and opened.

I will learn the commands later, but for now I want to get up and running.

---

### Post by xpod on 2007-01-14
>  For that matter why learn Linux when I already know OS X & Windows.

To learn something new perhaps...something different?......something WORTH learning,not to mention being well worth the price:D 

Were you never stuck and frustrated the first days and weeks in a Windows pc???
Hell, im sure your still frustrated years later  with it hence the reason your here me thinks:-k 

Things are only easy when you know the answers m8 and as with anything that takes some time & patience me thinks.

Stick at it m8.......all becomes clear in time.
Well,mabey not "all" but certainly enough to get by.

---

### Post by nalmeth on 2007-01-14
Ubuntu is committed to software freedom, and as a result many of your regular plugins and codecs aren't on the installation disc.

See here for explanation:
[http://wiki.ubuntu.com/RestrictedFormats](http://wiki.ubuntu.com/RestrictedFormats)

Other distros are not so committed, and try to make those steps for you.
Linux Mint is ubuntu edgy with most all non-free codecs and plugins already installed. 

You might consider this distro if you don't want to do the work, but I recommend that you just do the work anyway. It will be a rewarding and educational experience. 

Installing software isn't difficult, just different. 
Here's another great guide about installing software in Ubuntu:

[Howto Install ANYTHING in Ubuntu]("http://monkeyblog.org/ubuntu/installing/")

---

### Post by aysiu on 2007-01-14
> **nalmeth said:**
> 
[Howto Install ANYTHING in Ubuntu]("http://monkeyblog.org/ubuntu/installing/") Unfortunately, that link is dead now and has been for over two weeks.

---

### Post by nalmeth on 2007-01-14
>  Unfortunately, that link is dead now and has been for over two weeks.
How sad, and how clumsy of me not to check. I've been wayward and not active for the last 2/3 weeks too, so thats my excuse.

---

### Post by riven0 on 2007-01-14
> **reabralop said:**
> For that matter why learn Linux when I already know OS X & Windows.


Well, that's the problem, isn't it? If you don't want to learn Linux, then don't?! No one is forcing you to. Windows or OS X works fine for a lot of people, so just use that. Why waste your time on something you obviously don't want to learn? :confused:

---

### Post by reabralop on 2007-01-14
Answer me this then, is there a resource, other than the forums, that explains how do do the simple things. Ex. I'm trying to install the drivers for my HP printer. I found the source using the forum. I went to that site, downloaded the driver, and tried to follow the instructions on the site ([http://hplip.sourceforge.net/downloads.html)](http://hplip.sourceforge.net/downloads.html)). In the instructions they mention "Open a console/terminal and cd to the download directory.". I know where the terminal is but don't know what they mean by "cd". I doubt it means compact disk. Not knowing what they mean by that I tried to make it work with what knowledge I have with no success.

I'm not necessarily looking for the answer to the cd question but am using that as an example of a term that I'm not familiar with. I am needing a resource that can explain the most basic things. As stated earlier I'm not dumb, I just don't know.

---

### Post by reabralop on 2007-01-14
Riven0, I was being a smarta## to an earlier comment, I do want to learn this because I don't want Windows as the main OS on this computer.

I will admit I have a new feature that didn't exist before. My scroll bars on the track pad didn't work with Firefox on Windows but they are scrolling perfectly in Linux and I didn't do a thing to make it work. Yes, that is a big deal for me. They have always been there but I've never been able to use them.

---

### Post by Hendrixski on 2007-01-14
> **old_geekster said:**
> I began using "Ubuntu 6.10", yesterday evening.  I have installed numerous programs and have not typed a command to this point.

To install programs, go to System/Administration/Synaptic Package Manager/Log-in and that is it.  The packages that are installed have the "Ubuntu" logo next to them.  To install a new package, simple check the box next to it.  If there are dependencies (other necessary programs), it will install them, also.

As for surfing the web, using "Firefox 2.0.0.1" makes it a snap.  I have found one site that required another plug-in (Adobe Flash).  When asked if I wanted to install it, I clicked yes and it was accomplished without rebooting.

Some of my peripherals are working, but not all of the functions.  I know there is probably a way to improve the performance, but I am not to that point, yet.

Don't quit on it now.  The learning curve will be worth the effort.  Unless you are a gamer, there is not anything that you can't do as well as with Windows.  Even gaming is getting better with "Wine" from what I have read!   The best part --- it and 1000+ programs are FREE!

Good luck!

p.s. I am 61 years old.  Don't let an old_geekster out perform you.;)


That's very inspirational thank you for sharing it.

I install Ubuntu for many people, some of whom are in a similar age group and they find the same thing to be true.  That all of the common functions are very easy to do,  easier than windows.

The more complicated things however are very hard.  But that too will change soon.   Canonical has done a great job.

---

### Post by Sef on 2007-01-14
>  Originally Posted by nalmeth  View Post
Howto Install ANYTHING in Ubuntu

Aysiu's reply: Unfortunately, that link is dead now and has been for over two weeks.

Only way I have been able to look at it using google is to wait for it to time out and click on archive.

---

### Post by Hendrixski on 2007-01-14
> **reabralop said:**
> Answer me this then, is there a resource, other than the forums, that explains how do do the simple things. Ex. I'm trying to install the drivers for my HP printer. I found the source using the forum. I went to that site, downloaded the driver, and tried to follow the instructions on the site ([http://hplip.sourceforge.net/downloads.html)](http://hplip.sourceforge.net/downloads.html)). In the instructions they mention "Open a console/terminal and cd to the download directory.". I know where the terminal is but don't know what they mean by "cd". I doubt it means compact disk. Not knowing what they mean by that I tried to make it work with what knowledge I have with no success.

I'm not necessarily looking for the answer to the cd question but am using that as an example of a term that I'm not familiar with. I am needing a resource that can explain the most basic things. As stated earlier I'm not dumb, I just don't know.

You will find that this is a very good resource to show you everything you need to know.  I don't know that it is easy for beginers though. [http://ubuntuguide.org/wiki/Ubuntu_Edgy#What_is_new_in_Ubuntu_6.10_Edgy_Eft](http://ubuntuguide.org/wiki/Ubuntu_Edgy#What_is_new_in_Ubuntu_6.10_Edgy_Eft)

I recomend you start with the section on "EASY UBUNTU"  it is a script that will install a bunch of multimedia stuff for you so that you can watch videos on the internet, and that you will be able to watch DVD's, and a bunch of other things that wouldn't fit onto the liveCD (for any reason, memory space, or legal).   :) hope that helps

---

### Post by jonny on 2007-01-14
99% of the time, installing software is far easier on Ubuntu than on Windows or OSX; and I use all three operating systems so I have no axe to grind.

If you follow the instructions in the Ubuntu wiki for enabling the universe, you'll find free software for almost any imaginable purpose by clicking on Add / Remove in the Applications menu.  And, by default, Ubuntu can cope with almost any hardware that you throw at it - I have five PCs including a laptop and a Mac with a variety of devices (motherboards, graphics cards, cameras, camcorder, printers, scanner, wireless cards, webcam, tuner cards, displays, input devices, etc) and every single device works perfectly out of the box with Edgy.  Unlike Windows, you rarely need to install driver with Ubuntu. Unlike OSX, you don't have to buy hardware from one manufacturer to be confident it'll work with Ubuntu.

So why are these forums full of complex software installation instructions?  It's because a typical Linux user is an incurable meddler who always wants to taste the forbidden fruit of unsupported software.  And many of the instructions assume that you've been hacking away at the command line for some time. That's fine if you know what you're doing, if you want to learn or if you just enjoy fiddling.  But if you want a quiet life, don't ever install anything that's not provided by Canonical.

You mention an HP printer and the hplip driver.  That software should be already installed if you're using the latest version of Ubuntu, 6.10 Edgy Eft.  Are you sure your printer doesn't work out of the box?  If it's not listed when you try to add a printer, try a similar model and see what happens.

---

### Post by aysiu on 2007-01-14
To put what jonny says a little more succinctly...

90% of the time, software and hardware are easier in Ubuntu, but that 10% can be a big pain in the butt otherwise...

---

### Post by 3rdalbum on 2007-01-14
> **reabralop said:**
> Answer me this then, is there a resource, other than the forums, that explains how do do the simple things. Ex. I'm trying to install the drivers for my HP printer. I found the source using the forum. I went to that site, downloaded the driver, and tried to follow the instructions on the site ([http://hplip.sourceforge.net/downloads.html)](http://hplip.sourceforge.net/downloads.html)). In the instructions they mention "Open a console/terminal and cd to the download directory.". I know where the terminal is but don't know what they mean by "cd". I doubt it means compact disk. Not knowing what they mean by that I tried to make it work with what knowledge I have with no success.


There's a great site which explains the terminal: [www.linuxcommand.org](www.linuxcommand.org).

People who've just come from Windows or Macintosh backgrounds typically have a lot of trouble installing software on Linux. Why? Because on those two platforms, the best way of installing software is to look for it on the web and download it.

On Linux, it is different. You should first look in your package manager (System > Administration > Synaptic Package Manager) for the program you want - then it's easier to install than on Windows or Mac.

If you look in Synaptic Package Manager and do a search for "HP printer", you will find "hplip", which contains pre-built drivers for your Ubuntu system.

Don't forget, some things in Windows still require the command-line. I was even fortunate enough to have to use it on my first time in Win XP :-)

---

### Post by jonny on 2007-01-14
> **aysiu said:**
> To put what jonny says a little more succinctly...

90% of the time, software and hardware are easier in Ubuntu, but that 10% can be a big pain in the butt otherwise...
I've installed every release of Ubuntu on multiple machines.  Back in the Warty Warthog days the pain the butt factor was more like 50% - hardly anything worked out of the box.  Two years further on, the only software I bother to install that's not in the Universe is libdvdcss and Quasar accounts.  Ubuntu meets my family's software needs with no fiddling.

---

### Post by riven0 on 2007-01-14
> **reabralop said:**
> Riven0, I was being a smarta## to an earlier comment, I do want to learn this because I don't want Windows as the main OS on this computer.


Ah, that explains it! Confused me for a minute there. :lol:

As for the printer, do what the other guys are saying. I've got an HP printer, and all I did was go to System >> Administration >> Printing

Then I double-clicked on Add New Printer and it detected and installed it for me. Should be the same for you.

---

### Post by reabralop on 2007-01-14
Thank you all for the insight. I will look into those. Unfortunately though I need to bring my Windows install back up to date. I formatted this morning and still need Windows for some of the software I run.

A large part of it was frustration with the commands not working. I'll look at that later now that I've calmed a little.

Again, thank you.

---

### Post by old_geekster on 2007-01-15
> **Hendrixski said:**
> That's very inspirational thank you for sharing it.

I install Ubuntu for many people, some of whom are in a similar age group and they find the same thing to be true.  That all of the common functions are very easy to do,  easier than windows.

The more complicated things however are very hard.  But that too will change soon.   Canonical has done a great job.
You are welcome!

I made this post for that exact reason.  Yes, I have had many years of working with computers, beginning with M$ DOS in the Eighties.  So, commands are not completely new to me.  However, there are some differences, while M$ DOS actually was based on UNIX , also.

Am I confused, absolutely,:confused:   I have never done anything for the first time that didn't confuse me a bit.  I simply put my head down and bull forward.](*,)

---

### Post by old_geekster on 2007-01-15
> **aysiu said:**
> To put what jonny says a little more succinctly...

90% of the time, software and hardware are easier in Ubuntu, but that 10% can be a big pain in the butt otherwise...
Amen to that, ayslu!:rolleyes:

---

### Post by old_geekster on 2007-01-15
> **reabralop said:**
> Thank you all for the insight. I will look into those. Unfortunately though I need to bring my Windows install back up to date. I formatted this morning and still need Windows for some of the software I run.

A large part of it was frustration with the commands not working. I'll look at that later now that I've calmed a little.

Again, thank you.
Good for you, reabralop!  Cooler heads always prevail.   Just be patient.

I spent approximately 300 hours learning M$ DOS commands.  I knew every one of them from memory.  So, I will get this down, also.

As one of the posters said, we all had major problems learning Windows, but we simply forget over time.

---

### Post by old_geekster on 2007-01-15
Here it is another day.

Well, I did a new complete install of "Ubuntu 6.10" last evening.  It went extremely well.

I went to update manager and added a few programs to the already voluminous updates that were already there.  It came to a total of 132.  It took almost an hour with DSL.  This included "KDE" which works great.  I simply log-out and chose the desktop that I want to install at startup.

I, however, wanted a better, easier, way to upgrade from other than Umbuntu sources.  So, I did a Goole search and came up with this site.  Here is the link:

[http://www.howtoforge.com/automatix_ubuntu](http://www.howtoforge.com/automatix_ubuntu)

I followed the guide precisely and the results were amazing.  Now, I have several lists of programs that I can use.  My first new install will be "Google Earth", using "Automatix".

I hope this will help you get further along in your learning curve, reabralop.  I know that it will certainly help me.

Hang in there.  We will someday give people help on the forum from our own experiences.

---

### Post by steve.horsley on 2007-01-15
> **aysiu said:**
> To put what jonny says a little more succinctly...

90% of the time, software and hardware are easier in Ubuntu, but that 10% can be a big pain in the butt otherwise...

Yes, but newcomers from windows do often seem determined to do things the wrong way and go straight for that 10%. I think that's because they can't concieve of the existence of the easy way that makes up 90%. They search the web before searcing Synaptic, and then end up trying to download and install often from source code. Oddly, downloading and compiling from source code for windows is sonething they would never consider, but they try to do it for Linux and then complain that it's hard.

Reabralop: I'm not having a pop at you, this is a general observation. You didn't say what printer you have or why the hplip that is installed by default is not making you happy. I wonder if you just didn't know how to install a printer. The install printer dialog has a box with a misleading button that looks as though it wants you to install a driver. In fact, it's just an option to override the existing driver which you probably already have, but it catches newcomers from windows out because installing drivers for every little thing is something that they expect to have to do. If you come back to Ubuntu, check here about the printer driver before trying to download a binary that may not have been built for Ubuntu.

---

### Post by reabralop on 2007-01-15
In terms of the print driver, I read in the forums that the one built in is old. The one I found online, described in the forum, says it will also give the ink levels as well as other things. I haven't found that in the built in driver.

As an update; the main problem I was having with the command line was that I was copying and pasting just as I was instructed but I was copying the whole command. Someone earlier said that I need to paste each line at a time. So far I have only done a single line command and it worked. I just need to figure out what it was I was doing with the multi line command to try it again.

I managed to get my mouse back buttons to work & play some (not all yet) streaming video. Those were the biggies I had trouble with yesterday. 

I'm still trying to figure out other ways to use this OS, as in non "personal computer" type scenarios. For instance I have long been trying to figure out how to build a touch screen media player with GUI for my truck. I hear all the time about non PC devices using Linux (even cell phones) so I figure I can make something happen.

---

### Post by MrKlean on 2007-01-15
Ummmmmm.....I've loaded all I needed for my small business..most of it thru synaptic or Automatix...Try loading Quickbooks sometime when you can't find you're serial numbers. Hey, try re-installing XP and having to call and get the install ID number after it's crashed a few times !!  Ubuntu is was easier than XP..all around ; )  IMHO ; )

---

### Post by riven0 on 2007-01-15
> **reabralop said:**
> As an update; the main problem I was having with the command line was that I was copying and pasting just as I was instructed but I was copying the whole command. Someone earlier said that I need to paste each line at a time. So far I have only done a single line command and it worked. I just need to figure out what it was I was doing with the multi line command to try it again.


You probably won't need this at the moment, but just something to keep in mind for the future: when combining multiple command lines, (for example, **sudo apt-get update** and **sudo apt-get dist-upgrade**), just use the && sign between. For example:
[B]
sudo apt-get update && sudo apt-get dist-upgrade[/B]

The only problem with the above approach is that if the first command fails, the second one will not execute. In order to execute the second command, even if the first one fails to go through:

> sudo apt-get update; sudo apt-get dist-upgrade

---

### Post by steve.horsley on 2007-01-17
> **reabralop said:**
> In terms of the print driver, I read in the forums that the one built in is old. The one I found online, described in the forum, says it will also give the ink levels as well as other things. I haven't found that in the built in driver.

The hplip that installs by default is able to do ink levels. Try this:
Right-click the Ubuntu logo and choose Edit Menus. 
Go to System->Preferences
enable HPLIP Toolbox
OK out of the editor and use System-Preferences->HPLIP to start the toolbox.
Not pretty, but functional.
> 
I'm still trying to figure out other ways to use this OS, as in non "personal computer" type scenarios. For instance I have long been trying to figure out how to build a touch screen media player with GUI for my truck. I hear all the time about non PC devices using Linux (even cell phones) so I figure I can make something happen.
That's really heavy stuff. You will need custom drivers for the touch screen. You would need to get really deep inside to do that kind of thing. It's beyond me, I think. Still, that's why people choose Linux - at least it's possible if you want to put the effort in.

---

### Post by reabralop on 2007-01-17
I followed those directions and I don't think it like it. When I selected system preferences and the HPLIP toolbox it responded;

PyQt/Qt initialization error. Please check install of PyQt/Qt and try again (the python-qt3 package must be installed for this program to work).

I don't know what any of that means. I printed a test page so something works.

---

### Post by riven0 on 2007-01-17
So did you try installing python-qt3 and see if that works?:
> 
sudo apt-get install python-qt3

---

### Post by reabralop on 2007-01-20
Yes, I am showing more info including ink levels but it won't print a test page. I will try other documents or the other window to see if something else works.

I'll let you know the outcome.

Thank you.

---

