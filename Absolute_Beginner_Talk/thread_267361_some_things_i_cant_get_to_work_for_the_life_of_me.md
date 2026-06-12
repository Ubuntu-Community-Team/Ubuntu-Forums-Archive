---
title: "some things i cant get to work for the life of me"
date: 2006-09-28
forum: Absolute Beginner Talk
---

### Post by tjjohnso on 2006-09-28
ok the system i have installed is kubuntu dapper drake 6.2.06.
on an HP Pavilion dv5000
Intel Centrino duo 1.83 GHz processor
NVidia GeForce Go 7400

first of all i cant get mic input to work, i dont know if im using OSS or ALSO, dont know how to find out, and when i open Kmix and look at the options for input all i have is a capture slider, no mic. also the capture slider does not have a green light, shaded or lit at the top. only a red one at the bottom. im trying to get it to work with skype... so if anyone knows how to get it at least working that would be great. also when i look at other peoples kmix screenshots online...it looks like they have some type of engine running, or maybe its the soundcard O_0;; and they also have like 6 different sliders for input.

next i can install cedega from tgz, i figured out that much. however, when it runs the tests for Open GL rendering and 3d acceleration, it fails. maybe an unsupported graphics card? or unrecognized? i dont know and i dont get any error messages so i dont know where to start on that either.
anyone know how to get Open GL and 3D acceleration running at full capacity?

next if someone can point me in the direction of a GOOD tutorial for installing compiz and the wobbly windows and the cube and such that would be grat. ive tried a couple and them i get lost when they start talking about certain filepaths they used to get it working.... that i apparently dont even have.

i want to run linux so bad but everything seems so broken with no answers i kinda wannna give up.

help is much appreciated.

---

### Post by happy-and-lost on 2006-09-28
[http://www.tectonic.co.za/view.php?id=1153](http://www.tectonic.co.za/view.php?id=1153)

What's your output for glxinfo?

---

### Post by tjjohnso on 2006-09-28
O_0;; glx info?

---

### Post by bodhi.zazen on 2006-09-28
Well one out of two.

The skype for linux site has a very nice how to on microphones:

[[color=blue]Skype[/color]](http://www.skype.com/help/guides/soundsetup_linux.html)

---

### Post by happy-and-lost on 2006-10-02
Type glxinfo into the terminal (Apps-->Accessories) and post the output.

---

### Post by podunk on 2006-10-02
This page has tons of how tos:
[http://ubuntuguide.org/wiki/Dapper](http://ubuntuguide.org/wiki/Dapper)
including one on Nvidia drivers. I have an ATI card so I can't say it will work or not. It also has a how to for compiz. Compiz won't work until you have drivers installed.

I'll say this about compiz – it looks very cool but it's pretty bleeding edge and beta – I mean they release a new version or a bug fix every 4 hours or so  it looks like. :-)  If your computer is a older model, or doesn't have a fairly strong graphics system it will likely not work very well. If you're a new user like I am you'll likely have a hard time installing and configuring it.

You're using Kubuntu – there is lots of eye candy that will work that is easy to set up and looks very cool – you need to set up your vid card first. Use:
Main menu button
System
Adept (package manager)
and search for 3ddesktop and kxdocker. They are one click installs and look great. :-)

It can get sort of discouraging and frustrating switching to this Linux stuff. It's taken me 2 months to get my office rigs set up like I want them to be. I made a lot of mistakes along the way.

2 big mistakes I made were trying to run before I even knew enough to crawl. Trying to install the latest and greatest bleeding edge stuff before I even knew what all the menu items were for - compiz comes to mind. :-)

Ubuntu works – it's not broken – but I broke it several times because I was doing stuff with no knowledge. It had everything I needed right out of the box. It was going after my wants that caused the trouble. :-D

The second big mistake I made is using these how tos blindly with out studying the commands behind them. My rig is up and has a lot of the stuff I want on it (my vid cards are to old to run compiz well) and are ready to do some work with now.

I don't know how I got it that way. I copied and pasted a lot of commands in without knowing what they are really, so here we are 2 months down the road and I still don't know squat about Linux.

They have some online books about Linux in general here:
[http://tldp.org/tldp-redirect.php](http://tldp.org/tldp-redirect.php)

I started reading those last week. Every once in a while I get this ah-haaaaa moment!:-)

One other mistake! :-) I almost had it going on – and didn't back up my set up. Somehow or another I broke stuff and the more I fixed it the worse it got and I had to start all over. 

Hang in there! I booted up XP yesterday to put some files in a central place so I wouldn't have to look all over the drive to get them and move them here. Man! It sure was slow! I was very glad to get done with that and back on my Ubuntu!
It's worth the aggravation ten fold just to not have to sit there and watch the computer decide what to do next.

---

### Post by anaconda on 2006-10-02
I also had problems with mic, but they were solwed, just by going to "volume control" and uncheking the "mute mic"- option (or similar), which was enabled automatically after installing ubuntu !!

---

