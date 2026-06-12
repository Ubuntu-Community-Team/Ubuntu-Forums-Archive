---
title: "Xubuntu"
date: 2007-04-04
forum: Absolute Beginner Talk
---

### Post by sammyd253 on 2007-04-04
I have an older Acer Travelmate 527txv laptop that has Ubuntu installed on it.  However, I need to check the version on it, I'm guessing it has 6.06 Dapper or 6.10 Edgy.  

My laptop specs are:

800mhz p3 CPU
512mb of RAM
DVD-ROM

Ubuntu works fine on my laptop, although I feel that it could be more responsive.  I've read that Xubuntu can give an older machine better performance.  Because of this, I would like to install Xubuntu on my laptop so that it feels quicker.  I do have a few questions though.

I read that Xubuntu can be installed right from Ubuntu by grabbing and installing a package through Synaptic.  After this, you can choose to run Xubuntu at the next login.  Is this true?  I am confused because I am thinking that the original Ubuntu will still be loading, and all I'll be getting is a different GUI (Xfce)(sp?).  Am I wrong?  Will this actually use Xubuntu and give me better performance?

I only use my laptop for light web browsing, IM, and the occasional word processing document.  Will all this functionality be included in Xubuntu, or will I need to grab extra packages like Gaim, Firefox, and OpenOffice (Or any other good office suite for that matter).

Also, I've noticed that DVD playback on my laptop can be somewhat choppy, even in windows.  I'm wondering if DMA isn't enabled on my laptop.  I plan to check this, and if it isn't enabled, turn it on.  Do you think that this could be causing my DVD playback to be choppy?  I believe the DVD-ROM is an 8x.

A long post I know, but all help is appriciated and I look forward to hearing back from everyone!  Thanks!

---

### Post by jdaybrest on 2007-04-04
i cant answer the boot questions but the software such as gaim (sp?) and open office, firefox and such are right there, or easily installable as a post-install option. I put xubuntu on my gateway tablet and it runs great. A lot of the soft ware is not included by default like the screen savers. but through synaptic or the software manager you can get what you want very easily

---

### Post by Kobalt on 2007-04-04
You just need to open up Synaptic and search for the *xubuntu-desktop* package. Install it (it may take time) and when it's done log out. Click on Options in your login screen, select Sessions and chose XFCE : voilà ! You're running Xubuntu...
It will be more responsive than Gnome it's true, though I've come to realise if you use such apps as Firefox/thunderbird they will consume a lot of RAM hence making your XFCE run a bit slower. Using XFCE I chose siwftfox rather than Firefox.

---

### Post by sammyd253 on 2007-04-04
Alright, well as seeing that Xubuntu is meant to increase desktop performance, what apps can I use that will also optimize performance?  

As Kobalt has already written, Swiftfox is an alternative to Firefox.

Are there lighter weight versions of OpenOffice or Gaim?  While it's important to me that I get the most performance out of my laptop using Xubuntu, it's also critical that I get the functionality of applications such as OpenOffice and Gaim.

As an alternative to Gaim, I'm really looking forward to the future release of Trillian Astra.  I'm not sure how far along this is, but from what I understand, it's supposed to work in Linux.  With the optimizations they are giving to this client, it might be the perfect solution.  However, I have no idea when this is to be released.

---

### Post by Browzilla on 2007-04-04
Xubuntu comes with Abiword, a light word processor, and Gnumeric, a spreadsheet app, but I haven't had time or need to mess around with that quite yet.  But Abiword is great.

---

### Post by maxamillion on 2007-04-04
If it wouldn't be too much trouble, you might want to attempt a fresh Xubuntu install or try [this tutorial]("http://www.psychocats.net/ubuntu/purexfce") to get to a pure xfce/xubuntu install because I have noticed that when you install xubuntu-desktop ontop of ubuntu it doesn't reap all the speed increase benefits of a fresh install. I assume this has something to do with packages that are modified by Xubuntu devs to use only gtk+ libs instead of gnome-libs and therefore you still end up with gnome-libs taking up system resources when running xubuntu that was installed ontop of ubuntu (sorry if i worded that strange, it makes sense in my mind but looks a little cryptic when i re-read it)

---

### Post by Maestro23 on 2007-04-04
For Office alternatives:

Gnome Office(AbiWord is great): [http://www.gnome.org/gnome-office/](http://www.gnome.org/gnome-office/)

Koffice: [http://www.koffice.org/](http://www.koffice.org/)

---

### Post by sammyd253 on 2007-04-04
> **maxamillion said:**
> If it wouldn't be too much trouble, you might want to attempt a fresh Xubuntu install or try [this tutorial]("http://www.psychocats.net/ubuntu/purexfce") to get to a pure xfce/xubuntu install because I have noticed that when you install xubuntu-desktop ontop of ubuntu it doesn't reap all the speed increase benefits of a fresh install. I assume this has something to do with packages that are modified by Xubuntu devs to use only gtk+ libs instead of gnome-libs and therefore you still end up with gnome-libs taking up system resources when running xubuntu that was installed ontop of ubuntu (sorry if i worded that strange, it makes sense in my mind but looks a little cryptic when i re-read it)

That's basically what my question was.  I couldn't imagine that just installing the Xubuntu-Desktop package would let me gain that much performance.  This weekend I think I will have time to grab a copy of Xubuntu and put it on my laptop.  I will check out all the apps you have mentioned, and I will test and make sure everything I need is there.


Also, Ubuntu has a VERY slow boot time on my laptop.  Is this process improved at all in Xubuntu?

---

### Post by maxamillion on 2007-04-04
> **Maestro23 said:**
> For Office alternatives:

Gnome Office(AbiWord is great): [http://www.gnome.org/gnome-office/](http://www.gnome.org/gnome-office/)

Koffice: [http://www.koffice.org/](http://www.koffice.org/)

I agree with Abiword, I use it daily for both work and school but I will warn that if you are opening a Microsoft Word document with heavy formatting, diagrams, and tables some things might not display correctly but that is generally rare. Abiword is perfect for 90% of word processing needs.

.... happy hacking :)

---

### Post by Browzilla on 2007-04-04
I have a pure Xubuntu install on an 800mhz Pentium III with 512 RAM.  Xubuntu here boots faster than Ubuntu did on my newer desktop, only a year old..

Haven't timed it or anything, but I'd guess maybe a little over a minute.
And that includes the BIOS diagnostics and all at the begining, before the boot actually starts.

---

### Post by sammyd253 on 2007-04-04
> **maxamillion said:**
> I agree with Abiword, I use it daily for both work and school but I will warn that if you are opening a Microsoft Word document with heavy formatting, diagrams, and tables some things might not display correctly but that is generally rare. Abiword is perfect for 90% of word processing needs.

.... happy hacking :)

Sounds perfect here too.  I'm not so much concerned about opening Word docs I've created in Windows in Ubuntu.  Basically what I would ultimately like to do is anytime I have a paper due for a class, I can write it in Ubuntu, and then ensure that it will work when opened by Word 2003 or 2007.  As long as this works, then I'm happy.

> **Browzilla said:**
> I have a pure Xubuntu install on an 800mhz Pentium III with 512 RAM.  Xubuntu here boots faster than Ubuntu did on my newer desktop, only a year old..

Haven't timed it or anything, but I'd guess maybe a little over a minute.
And that includes the BIOS diagnostics and all at the begining, before the boot actually starts.


Sounds good to me, I'll hope for these same results!  My current Ubuntu setup on my laptop literally takes about 5 min, from the time I hit the power button until I get to the login screen of Ubuntu.  Yeah, it stinks.

---

### Post by maxamillion on 2007-04-04
> **sammyd253 said:**
> Sounds perfect here too.  I'm not so much concerned about opening Word docs I've created in Windows in Ubuntu.  Basically what I would ultimately like to do is anytime I have a paper due for a class, I can write it in Ubuntu, and then ensure that it will work when opened by Word 2003 or 2007.  As long as this works, then I'm happy.




Sounds good to me, I'll hope for these same results!  My current Ubuntu setup on my laptop literally takes about 5 min, from the time I hit the power button until I get to the login screen of Ubuntu.  Yeah, it stinks.

Yes, typing in Abiword and opening in MS Word functions well ... I have done it when I find myself in a bind and have to print from a machine in a lab on campus.... enjoy :)

---

### Post by pxwpxw on 2007-04-04
sammyd253

If you want to see what xubuntu looks like, you could just install xfce4 

[http://packages.ubuntu.com/edgy/x11/xfce4](http://packages.ubuntu.com/edgy/x11/xfce4)

---

### Post by sammyd253 on 2007-04-04
Thanks for that.  However I am not that interested with the GUI.  If it's functional, that's great.  What I'm looking for is performance.  With both Windows XP and Ubuntu, performance was ok on my laptop, but it wasn't as responsive as I would have liked.  I understand that my laptop is older, and with the increasing demand of system resources from applications today, my laptop will perform slower.  

My goal is to minimize the use of system resources, allowing my laptop to perform the basic tasks I use it for as quickly and efficiently as possible.  I barely use my laptop now, as it has some other glitches (when running on battery, OS tells me I have 5 minutes left even if the battery is fully charged, DVD playback is jittery), but it is perfect for little things I like to do when I'm moving around (going home for a weekend from college).  Since I really only intend to use my laptop when I'm on quick trips, I want it to be quick so it's not tedious to use for minimal use.  

ps - This is off topic, but if anyone has recommendations for the problems I mentioned in this post (battery life, DVD playback), feel free to let me know.  I'm suspecting that the sensor inside my laptop is just messed up, and I want to check and see if DMA in enabled for my DVD player.  Any other suggestions are welcome!


*edit* - When setting this up on my laptop, how much space do you recommend I give to each partition?  I have a 20GB hard drive, and 512MB of RAM.  I was planning to partitioning in this way:

/ - 5GB
/home - 14GB
/swap - 1GB

I understand that when formatted, my 20GB drive won't actually show all 20GB.  The suggested partition scheme is just to get an idea of where I want to go.  Do you think I should give more partition to the / partition?

---

### Post by kerry_s on 2007-04-04
If performance is what your after, the best thing to do is go custom install and build the system to your needs. Ubuntu makes it very easy to do with the server install. The server install is just the base system and nothing else, no gui yet. First you need to make a list of what you want to use, maybe even test the programs out on your current install if you know your going to wipe it anyways. 

Here's what i do->

i use the net installer so my systems up to date when i'm finished-> [http://mirror.linux.org.mt/mirror/ubuntu/dists/feisty/main/installer-i386/current/images/netboot/mini.iso](http://mirror.linux.org.mt/mirror/ubuntu/dists/feisty/main/installer-i386/current/images/netboot/mini.iso)

type> server
skip the package selection, i want custom, so tab and enter

after the install and reboot:
login (just start typing when it stops, the word positioning is screwy, looks like it froze during boot, but it's actually finished)

type> sudo su

This is the part where you select what you want, here's what i do:
type> apt-get install xorg gdm fluxbox leafpad emelfm synaptic

type> reboot

select fluxbox in the session menu and login

Open synaptic and install what ever else you want

Have fun.

---

### Post by sammyd253 on 2007-04-04
This is hard for me to follow because I've never done anything like this before.  Also, there isn't much detail there so while I may be able to follow it, I don't actually know what I'm doing.  Are there any more detailed guides to something like this out there?

---

### Post by kerry_s on 2007-04-04
Actually, it's just that easy. That is pretty much as detailed as it needs to be, when you do it will see the exact steps. The only thing you would want to change is the apt-get line were you choose your applications and environment.

you want to keep this part> apt-get install xorg gdm
that is the X-window system and gdm is the login manager.

so for instance:

apt-get install xorg gdm your_wm synaptic

that is enough to get you to gui and then you can use synaptic to install what ever else you want. Depending on what you use you'll need to pick a file manger, editor, web browser, im, office, etc.... It's a blank slate you get only what you install.

---

### Post by DJiNN on 2007-04-04
> **sammyd253 said:**
> This is hard for me to follow because I've never done anything like this before.  Also, there isn't much detail there so while I may be able to follow it, I don't actually know what I'm doing.  Are there any more detailed guides to something like this out there?

Sammyd, kerry_s is correct when he says it's really that simple, even though this side of doing it, it probably seems rather daunting. :)  Where he has put "your_wm" you could, instead of outting fluxbox, put xfce. That would install the XFCE Window manager instead of fluxbox. (Which is also a Window Manager)

The reason that you would do something as described by kerry_s here, is that it makes for a very fast & "Unbloated" system, with only the apps that you want  to use & nothing else. [Fluxbox]("http://www.fluxbox.org") is a very lightweight & fast WM, and is an ideal alternative to XFCE (Which is the standard WM that comes with Xubuntu). You could also choose IceWM, OpenBox, BlackBox & a few others besides....... they are all good alternatives.

However, it seems to me as if you're very new to the whole Linux scene? If that's the case (And please excuse me if i'm wrong here) then i would recommend that you download the Xubuntu Desktop install CD and just go from there. It's simple, reasonably fast to install, and will give you a taste of what Ubuntu is like using the XFCE Windows Manager.

Once you have some experience & have learned some stuff about Window's Managers etc, and also what "apt-get" is & how to use the "Terminal" in Ubuntu (& it really isn't that hard at all, so don't be put off) then you'll be more able to understand & take advantage of the information that kerry_s has given you. The system that he has described to you here (Using Fluxbox & doing a "Server Install") will give you an even faster & more responsive setup than just the straightforward "Xubuntu" install.

I hope that some of that makes sense? :)  FYi, i've just installed the standard Xubuntu Desktop edition (Downloaded the latest Feisty Beta version) on an old P3 running at 1Ghz with 512mb Ram, and it's running really well. I think you'll be pleasantly surprised at just how good the de facto Xubuntu is. :)

Good luck........

DJiNN

---

### Post by RedSquirrel on 2007-04-04
> **sammyd253 said:**
> I have an older Acer Travelmate 527txv laptop that has Ubuntu installed on it.  However, I need to check the version on it, I'm guessing it has 6.06 Dapper or 6.10 Edgy.  

My laptop specs are:

800mhz p3 CPU
512mb of RAM
DVD-ROM

I have tried Xubuntu on even older hardware (AMD Duron 600 MHz with 320 MB RAM) and Xubuntu performed very well (much better than GNOME, for example).

I'm not sure why you have such long boot times. Mine is about one minute or less. You might want to see if something is failing when you boot up. For example, in a terminal, try:

```
dmesg | grep -i failed
```For now, though, you might just want to install Xubuntu and see how that boot time is.



> 
* Also, I've noticed that DVD playback on my laptop can be somewhat choppy, even in windows.  I'm wondering if DMA isn't enabled on my laptop.  I plan to check this, and if it isn't enabled, turn it on.  Do you think that this could be causing my DVD playback to be choppy?  I believe the DVD-ROM is an 8x.*Yeah, if DMA is not enabled, the playback could be choppy. However, there might be other issues too. Perhaps when you try Xubuntu, the playback will be better because there will be more system resources available (less stuff happening on your system that could interfere with playback).

I used to watch DVDs on my PC until my DVD-ROM drive motor died. To be honest, even when the drive was new, it was a pain in the neck to get movie playback to work all the time without being choppy or locking up altogether. (This was on win98, though. Haven't tried it under linux.)

---

### Post by sammyd253 on 2007-04-04
Thanks for all of the replies.  I overestimated the entire process.  When I first read it, I didn't take the time to really understand what kerry_s had taken the time to write.  After downloading the image he supplied, and doing a little bit of tweaking (had to run the install by typing server pci=noapci), Ubuntu went on just fine.  I ended up choosing fluxbox has my wm, since it's lightweight and it's supposed to be fast.  

I believe you DJiNN when you say that the default xubuntu install is quick and responsive.  However, I really like the idea of starting from scratch and only adding what I need one at a time.

As we speak the packages that kerry_5 are downloading and installing, and once I boot into fluxbox I'll load synaptic and grab some other software I need.  Hopefully I'll notice some good performance!  Thanks for all the help guys!

---

### Post by karamba_kid on 2007-04-04
For troubleshooting the dvd playback problem try this command :
hdparm -d /dev/hdc 
(where /dev/hdc is your dvd drive.)

it should output something like this :
alex@arbutus:~$ hdparm -d /dev/hdc

/dev/hdc:
 using_dma    =  1 (on)

If it says that it is off I believe you can turn it on with : 
sudo hdparm -d1 /dev/hdc && sync

I'm not too sure (I used to have to turn on dma on my desktop's drive for dvd's).  I haven't had many problems with dvd playback on this P3 600 MHz latitude with 512MB of memory with Xubuntu edgy installed. Good luck.

---

### Post by kerry_s on 2007-04-04
> **sammyd253 said:**
> Thanks for all of the replies.  I overestimated the entire process.  When I first read it, I didn't take the time to really understand what kerry_s had taken the time to write.  After downloading the image he supplied, and doing a little bit of tweaking (had to run the install by typing server pci=noapci), Ubuntu went on just fine.  I ended up choosing fluxbox has my wm, since it's lightweight and it's supposed to be fast.  

I believe you DJiNN when you say that the default xubuntu install is quick and responsive.  However, I really like the idea of starting from scratch and only adding what I need one at a time.

As we speak the packages that kerry_5 are downloading and installing, and once I boot into fluxbox I'll load synaptic and grab some other software I need.  Hopefully I'll notice some good performance!  Thanks for all the help guys!


Trust me when you see the performance of a custom install it is all you'll want to use. Make sure you go into apps> system> GDM setup and select a login screen so you don't get that first start error about missing theme anymore. You can also set auto-login and you won't have to see GDM login at all.

Also don't be offended by fluxbox's stock look it's very customizable.

---

### Post by DJiNN on 2007-04-05
> **sammyd253 said:**
> Thanks for all of the replies.  I overestimated the entire process.  When I first read it, I didn't take the time to really understand what kerry_s had taken the time to write.  After downloading the image he supplied, and doing a little bit of tweaking (had to run the install by typing server pci=noapci), Ubuntu went on just fine.  I ended up choosing fluxbox has my wm, since it's lightweight and it's supposed to be fast.  

Fluxbox is superb! (As is OpenBox IMHO).  Glad to hear that you gave it a try. Once you have done it, & seen the steps taken & how it all works etc, it all kind of makes sense and the next time (& there probably will be a next time) it will be both quicker & better! :)

> I believe you DJiNN when you say that the default xubuntu install is quick and responsive.  However, I really like the idea of starting from scratch and only adding what I need one at a time.

Absolutely!! I totally agree. The reason that i mentioned about the Vanilla Xubuntu install, was mainly because If you want a really fast & responsive system it's a great way to achieve it, but without the sometimes daunting task (& it can be somewhat scary at first) of doing a server install. 

But i would go with what kerry_s says all the way. If you're ready for it & don't mind the learning curve, then  it's most definitely the way to go, and kerry_s should know.... he's done it enough times! :lolflag:

> As we speak the packages that kerry_5 are downloading and installing, and once I boot into fluxbox I'll load synaptic and grab some other software I need.  Hopefully I'll notice some good performance!  Thanks for all the help guys!

Excellent! Sounds like it's going fine. I'd be interested to hear about your experiences & what you think of it, once you've finished installing & setting it up etc, if you get time.  Above all, have fun & enjoy. :)

I've just installed Xubuntu Feisty beta on an old PIII (1Ghz) that i have here, and it's running great. But, this has made me want to do a server install instead. Heck, i'm so impressed with Xubuntu per se (Especially now that i have finally found a way to browse network shares etc) that i may even do a server install (With Fluxbox et al) on my Core 2 Duo laptop, just to see what kind of speed i can attain & also whether i can actually do it. I think the nVidia driver thing could be a problem, or at least a stumbling block. But, there's only one way to find out eh? :)

DJiNN

---

### Post by sammyd253 on 2007-04-05
Alright, well I didn't get to finish my configuration yesterday since I did the network installation.  I prefer this method just like kerry_5 said because it makes sure that you are up-to-date, but since I'm at college, internet speed is very bad during the week.  I got through the entire installation and Ubuntu was up and running, sans a GUI.  I used apt-get to install the following:

xorg
gdm
fluxbox
leafpad
emelfm
synaptic

I got to restart after these packages all installed, and gdm kicked right in prompting me to login with my credentials.  I made a mistake though, I typed in my user name and password without selecting fluxbox as my wm for the session.  When Ubuntu tried to load, it got to Nautilus and just hung (this makes sense to me considering Nautilus isn't installed on my system).  I ended up shutting down my computer after this because I had to head out for work, which is where I am now.  So once I get back later this afternoon, I plan to login to fluxbox for the first time and start to learn my way around!

Quick question, is what kerry_5 suggested to me (server install, then install only packages I need) considered "compiling" my own Ubuntu install?  I hear that people compile their own OSes all of the time, and I never really understand what that means... 

And DJiNN, after taking some time with Ubuntu on my laptop, I plan to dual-boot with Vista on my main rig as well.  I don't think Nvidia should be much of an issue to get working, as I've done some research on that and it seems pretty easy and straightforward to setup.  I even have SLI in my box and that seems easy to setup.  Funny how it's easy to enable in Linux, but a chore in Vista atm.

Once I get home this evening and login I'll let you know how it goes!

ps - Do I have to select fluxbox from gdm when it loads?  Or should it have loaded that by default?  I didn't get to really observe gdm when it first loaded, so I can't recall if I missed fluxbox or not.

---

### Post by DJiNN on 2007-04-05
> **sammyd253 said:**
> 
I got to restart after these packages all installed, and gdm kicked right in prompting me to login with my credentials.  I made a mistake though, I typed in my user name and password without selecting fluxbox as my wm for the session.  When Ubuntu tried to load, it got to Nautilus and just hung (this makes sense to me considering Nautilus isn't installed on my system).  I ended up shutting down my computer after this because I had to head out for work, which is where I am now.  So once I get back later this afternoon, I plan to login to fluxbox for the first time and start to learn my way around!

Good to hear that you got this far, nice one. :)  I'm not surprised it crashed.... you have to select Fluxbox & make it your default from within the GDM, from what i can remember anyway. I'm sure that kerry_s will put you right on that one. 

> Quick question, is what kerry_5 suggested to me (server install, then install only packages I need) considered "compiling" my own Ubuntu install?  I hear that people compile their own OSes all of the time, and I never really understand what that means... 

I'm not sure i would call it that. I took this quote from Wikipedia because i think it explains a "Compiler" quite well......

> A **compiler** is a [computer program]("http://en.wikipedia.org/wiki/Computer_program") (or set of programs) that translates text written in a [computer language]("http://en.wikipedia.org/wiki/Programming_language") (the *source language*) into another computer language (the *target language*).

Does that help? So i personally would say that it is when you "Compile a Kernel" for instance, or "compile a program" from the source code (As in when you download a tarball & extract, then compile) 

What you're doing with a server install, is loading (or "Installing" may be a better term) a "Base" or "minimal"system, and then only installing the things that you (personally) need to make it work or function in the correct way, for you. 

Of course, the English language being as ambiguous as it is, you could indeed say that you're "Compiling" an OS, and in a way i guess that's what it is. :) 

I think i'll leave it there & let someone who's far more savvy  than i, chime in with a better description and/or explanation...... before i dig myself into a hole that i can't climb out of! :lolflag:

> And DJiNN, after taking some time with Ubuntu on my laptop, I plan to dual-boot with Vista on my main rig as well.  I don't think Nvidia should be much of an issue to get working, as I've done some research on that and it seems pretty easy and straightforward to setup.  I even have SLI in my box and that seems easy to setup.  Funny how it's easy to enable in Linux, but a chore in Vista atm.

You're probably right. It's just that everytime that i've tried to get "Most" lin distros working at a decent res on the laptop (1680x1050) i've hit problems, and i've had enough of trying to find out how to do it the "Hard" way. It's a lot easier to find a distro that works "Out of the Box" as it were, than to sit for hours trying to figure out how to make something work. That's the main reason that i'm running Feisty on the laptop..... because it just works so well.

I'm already Dual booting on the Laptop (With XP & Feisty) but am seriously considering the server install, mainly just to see if A:) I could do it and B:) Just how fast it could be. 

Of course, most of this is moot when the Feisty release of Automatix is available. :)

> Once I get home this evening and login I'll let you know how it goes!

Nice one.... look forward to hearing about it. 

> ps - Do I have to select fluxbox from gdm when it loads?  Or should it have loaded that by default?  I didn't get to really observe gdm when it first loaded, so I can't recall if I missed fluxbox or not.

When the GDM comes up asking for your name & PW, you get a chance to change the "Session" then by clicking on the "Session" option. (At least i think that's what it's called..... funny how you can see something every day & still not remember what it's called!).  There you select Fluxbox, & hit OK and then another selection box should come up asking if you'd like to make this the default WM or just for this session. Choose default & go from there & all should be well. :)

DJiNN

---

### Post by sammyd253 on 2007-04-05
Thanks for all of that.  As for selecting fluxbox as the default, I do remember back to when I used some other distros that had both Gnome and KDE as wm's, and I could pick between the two.  I'm sure all will be well once I get home this evening and try it.  I must say though, what's really going on behind the scenes when you choose a specific wm, rather than just presenting you with a GUI, it's like it's a whole new operating system.  What I mean is, if I use Gnome and make a few icons on the desktop, and configure some other options, once I load KDE, all those configurations I've made, even for specific applications will be different (At least I think that's how it works).

I really need to look up this automatrix thing because everyone keeps talking about it.

I asked about the compiling stuff because I've heard about certain Linux distros that actually let you compile the entire thing, tweaking the OS down to the nitty-gritty, spec'ing it directly to your hardware.  Thought that was pretty cool, seems like it would be the ultimate in performance, but probably a tedious and difficult process.

Hopefully if you attempt a reinstall of Ubuntu DJiNN, you can get the Nvidia drivers working properly and displaying at the resolutions you want.  Depending on when you tried it last, things may have come a looooong way. :-)


Also I wanted to ask, is there a way to clean up downloaded/installation files after running apt-get?  The first time I tried to run it, I ran:

apt-get install xorg gdm fluxbox leafpad emelfm synaptic

Everything downloaded, but then I get some error and nothing installed.  To fix this I just rebooted, and then ran apt-get on each individual package, and it worked fine.  Now that I have these packages installed and working, do I need to clean anything up?  I for one do not like clutter, so if there is anything I can do to keep things tidy then I will :-)

---

### Post by DJiNN on 2007-04-05
> **sammyd253 said:**
> What I mean is, if I use Gnome and make a few icons on the desktop, and configure some other options, once I load KDE, all those configurations I've made, even for specific applications will be different (At least I think that's how it works).

I know what you mean. Sometimes i think a degree in Physics would be easier than trying to overcome the differences between different WM's etc. But then i realise that it's only my lack of understanding of such things that really makes it often incomprehensible. :) 

> I really need to look up this automatrix thing because everyone keeps talking about it.

[Automatix]("http://www.getautomatix.com") is what really made my introduction into Ubuntu a lot easier than it would have been, and a lot quicker as well. I think the Feisty version will coincide with the final Feisty release, so not too far off now. 

> I asked about the compiling stuff because I've heard about certain Linux distros that actually let you compile the entire thing, tweaking the OS down to the nitty-gritty, spec'ing it directly to your hardware.  Thought that was pretty cool, seems like it would be the ultimate in performance, but probably a tedious and difficult process.

Aaaah, i see what you mean. I tried to install Lunar Linux once, and Gentoo as well, both of which are like that, but didn't get very far before i just gave up & installed "Some other Distro".  I think if i had some time & a need for a streamlined setup, then i'd probably go for it, but nowadays i just want to start using the OS as quickly as possible.  As i see it, there's just too many variables in it & too much to go wrong. But i've spoken to people who love it, and they certainly learn a lot about Linux in the process. :)

Have you ever tried Zenwalk? It's based on Slackware & is a really fast & solid Distro. If you ever get some time & fancy trying out some other distros i can heartily recommend it. It's XFCE based, but you can quite easily put fluxbox on either by downloading & installing a prepared package or by compiling the prog on your own (Which is not as hard as it first seems) and then installing. 

> Hopefully if you attempt a reinstall of Ubuntu DJiNN, you can get the Nvidia drivers working properly and displaying at the resolutions you want.  Depending on when you tried it last, things may have come a looooong way. :-) 

Heehee..... they most certainly have come a long way, and it looks as if it's not getting any slower.  I've got Feisty on the Laptop, with the nVidia drivers installed etc, and it works a treat, but i'm really tempted to do a server install & have a go at it myself..... (Gulp!) :)  I'm away for Easter though, so i think i'll wait until i return to try it.  :)

> Also I wanted to ask, is there a way to clean up downloaded/installation files after running apt-get?  The first time I tried to run it, I ran:

apt-get install xorg gdm fluxbox leafpad emelfm synaptic

Everything downloaded, but then I get some error and nothing installed.  To fix this I just rebooted, and then ran apt-get on each individual package, and it worked fine.  Now that I have these packages installed and working, do I need to clean anything up?  I for one do not like clutter, so if there is anything I can do to keep things tidy then I will :-)

There is a command that you can use (or several commands even) to purge the system. In fact i think there are more than a few ways that you can do it, either with the CLi or by using such programs as deborphan etc. 

But i think the best way (From what i can gather) is to NOT use "apt-get" when installing programs, but to use "aptitude" instead, because it's much better at cleaning up whatever it's installed than apt-get is.  Just replace "apt-get" with "aptitude" whenever you're installing something, then, if you wish to remove it at some later point, it removes everything that was installed (After doing whatever dependancy checks etc that are needed). 

Having said that, i personally find aptitude a pain in the neck to use, but that's probably because apt-get is so easy, and because most of the time i use Synaptic.

---

### Post by RedSquirrel on 2007-04-05
> **sammyd253 said:**
> I asked about the compiling stuff because I've heard about certain Linux distros that actually let you compile the entire thing, tweaking the OS down to the nitty-gritty, spec'ing it directly to your hardware.  Thought that was pretty cool, seems like it would be the ultimate in performance, but probably a tedious and difficult process. 

Yes, you can compile everything from scratch. Have a look: [http://www.linuxfromscratch.org/](http://www.linuxfromscratch.org/)

I haven't done all of that, but I have compiled a fair bit of stuff in the past (apps, compilers, libraries, etc.). It can get a bit tedious after a while, but you certainly learn *a lot*. (And it's a good exercise for working on one's tolerance for frustration!)


Fluxbox is a great choice. I use it almost 100% of the time these days. Some of the links in my sig might help when you start doing some customization. There is a lot of support on these forums too.

Have fun! :)

---

### Post by sammyd253 on 2007-04-05
I  loaded synaptic and searched for gaim, i marked it for installation and it did it's thing.  I can't find it anywhere on my system now, do you know how I can access it?

---

### Post by DJiNN on 2007-04-05
> **sammyd253 said:**
> I  loaded synaptic and searched for gaim, i marked it for installation and it did it's thing.  I can't find it anywhere on my system now, do you know how I can access it?

Aha, this is where it becomes obvious that you're using Fluxbox as your WM, because, unlike Gnome, KDE, and even sometimes (but not "Always") XFCE, Fluxbox doesn't automatically add stuff to the menu. You have to do it manually, by editing the menu file (i think, haven't done it for quite a while now) which if i remember correctly is situated in your /home/.fluxbox directory.

You'll have to read a bit about editing the menu i'm afraid, because everytime you add something or change something, you're going to have to edit it and either add or subtract whatever you're changing. 


It's not difficult at all, but just takes a bit of getting used to, and it's a bit of a pain having to do it everytime. 

There is a program (i think it's menumaker) that you can run, which will (With the correct switches) read your installed programs & what have you, and then proceed to make a menu for you.  I think it should be in the repos as it's fairly popular, especially with Fluxbox/OpenBox users etc.

---

### Post by RedSquirrel on 2007-04-05
If you use the **menu** package, *most* of the packages you install will be *automatically* added to your Fluxbox menu. You can also use fluxbox-generate_menu. gaim is one of the things that is added automatically.

In any case, the menu HOWTO in my sig describes menu configuration. ;)

If you run:

```
sudo update-menus
```in a terminal, that should rebuild the menu and add gaim for you. If it didn't, you might have to restart _Fluxbox_ (not the computer) to make sure the change took effect. **fluxbox Menu -> Restart**

---

### Post by sammyd253 on 2007-04-05
Sounds good.  I'm also curious about my wireless adapter.  I haven't tried it in my laptop yet but I want to make sure it works properly.  It's a USB wireless device and it worked on Ubuntu for me before, but does the basic install that I did allow for USB devices to work?  Or do I need to install them?

ps- my laptop is super responsive and running great.  I'm lovin' this!

---

### Post by kerry_s on 2007-04-06
> **sammyd253 said:**
> I  loaded synaptic and searched for gaim, i marked it for installation and it did it's thing.  I can't find it anywhere on my system now, do you know how I can access it?

Sorry, been busy, I'm glad "DJiNN" been taking care of you.
If your still running the stock menu just open a terminal and run> sudo update-menus

Your going to want to change that in ~/.fluxbox/menu to look like this->

```
 [exec] (Update-menus) {exec update-menus}
 [include] (~/.fluxbox/fluxbox-menu)
```

to edit:
leafpad ~/.fluxbox/menu

Here's my menu in case you want to snag some settings.

[begin] (Fluxbox)

[exec] (Run Program) {exec fbrun -nearmouse -text exec  -w 600 -h 50 -font verdana-18}
[exec] (Terminal) {exec xterm} 

[separator]

[exec] (File Manager) {exec emelfm} 

[submenu] (Net)
 [exec] (Firefox) {exec firefox}
 [exec] (Gaim) {exec gaim}
[end]

[submenu] (Sound)
 [exec] (VLC) {exec vlc}
[end]

[submenu] (Admin)
 [exec] (Synaptic) {exec gksu synaptic}
 [exec] (Root-Emelfm) {exec gksu emelfm}
 [exec] (Root-run) {exec gksu}
[end]

[submenu] (Other)
 [exec] (Graveman) {exec graveman} 
[end]

[separator]

[submenu] (Settings)
  [exec] (Edit-menu) {exec geany -i ~/.fluxbox/menu}
  [exec] (Edit-startup) {exec geany -i ~/.fluxbox/startup}
   [submenu] (Styles)
      [stylesdir] (/usr/share/fluxbox/styles)
      [stylesdir] (~/.fluxbox/styles)
   [end]
 [submenu] (Backgrounds)
  [exec] (Black) {exec fbsetroot -solid black}
  [wallpapers] (/usr/share/fluxbox/backgrounds)
  [wallpapers] (~/.fluxbox/backgrounds)
 [end]
[end]

[submenu] (ScreenShots)
 [exec] (Snap) {exec scrot %T.jpg}
 [exec] (Select) {exec scrot -s -b %T.jpg}
 [exec] (Wait 5) {exec scrot -d 5 %T.jpg}
[end]

[separator]

[submenu] (Debian-menu)
 [exec] (Update-menus) {exec update-menus}
 [include] (~/.fluxbox/fluxbox-menu)
[end]

[separator]

[exec] (Screen Off) {sleep 5; exec xset +dpms dpms force off }

[submenu] (Logout)
 [exit] (Exit)
 [exec] (Reboot) {exec sudo /sbin/reboot}
 [exec] (Shutdown) {exec sudo /sbin/shutdown}
[end]

---

### Post by kerry_s on 2007-04-06
For shutdown you have to edit sudo and groups.

sudo visudo
put
# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
%shutdown ALL=NOPASSWD: /sbin/reboot
%shutdown ALL=NOPASSWD: /sbin/shutdown

ctrl and x and y and enter to save

then

sudo leafpad /etc/group

add a shutdown group, use the next number, mine stopped at 114 so shutdown was 115. Add yourself to the group. mine->

```
root:x:0:
daemon:x:1:
bin:x:2:
sys:x:3:
adm:x:4:user
tty:x:5:
disk:x:6:
lp:x:7:cupsys
mail:x:8:
news:x:9:
uucp:x:10:
man:x:12:
proxy:x:13:
kmem:x:15:
dialout:x:20:user,cupsys
fax:x:21:
voice:x:22:
cdrom:x:24:user,haldaemon
floppy:x:25:user,haldaemon
tape:x:26:
sudo:x:27:user
audio:x:29:user
dip:x:30:user
www-data:x:33:
backup:x:34:
operator:x:37:
list:x:38:
irc:x:39:
src:x:40:
gnats:x:41:
shadow:x:42:
utmp:x:43:
video:x:44:user
sasl:x:45:
plugdev:x:46:user,haldaemon
staff:x:50:
games:x:60:
users:x:100:
nogroup:x:65534:
dhcp:x:101:
syslog:x:102:
klog:x:103:
crontab:x:104:
user:x:1000:
lpadmin:x:106:user
scanner:x:107:user,cupsys
admin:x:108:user
gdm:x:109:
nvram:x:110:user
udev:x:111:user
messagebus:x:105:
haldaemon:x:112:
powerdev:x:113:haldaemon
ssl-cert:x:114:cupsys
shutdown:x:115:user
```

---

### Post by kerry_s on 2007-04-06
Also you might want to change your fonts or fluxbox settings. There is a new feature called overlay. Here's what i'm using.

leafpad ~/.fluxbox/overlay

##Fonts##
*.font: verdana-12

##aspect can also be center, tile or random (when you must give a path to the directory, not to a single file)##
#*background: aspect

##Rounded corners##
*.roundCorners:		TopRight TopLeft BottomRight BottomLeft


This is for blanket wide settings so no matter what theme your using certain things will stay the same, i just keep my fonts and rounded corners.
There are many more settings-> [http://fluxbox.sourceforge.net/docbook/en/html/fluxstyle-man.html](http://fluxbox.sourceforge.net/docbook/en/html/fluxstyle-man.html)

---

### Post by RedSquirrel on 2007-04-06
> **kerry_s said:**
> 

Here's my menu in case you want to snag some settings.
Some great ideas in there. For a few more, you can run:

```
fluxbox-generate_menu -o ~/.fluxbox/menu-ideas
```to generate a file of ideas for menu entries that you can just copy and paste to your menu.

---

### Post by Scott-S on 2007-04-06
> **DJiNN said:**
> Have you ever tried Zenwalk? It's based on Slackware & is a really fast & solid Distro. If you ever get some time & fancy trying out some other distros i can heartily recommend it. It's XFCE based, but you can quite easily put fluxbox on either by downloading & installing a prepared package or by compiling the prog on your own (Which is not as hard as it first seems) and then installing.

Zenwalk was my first taste of Linux and I can't praise it enough. It's small and fast and works on my Dell Optiplex  GX1 better than win2k on a Dell Dimension 4300. I'm trying Ubuntu/Xubuntu now-trying to get a feel for different distros-and am enjoying it; but Zenwalk is worth checking out.

Scott

---

### Post by sammyd253 on 2007-04-07
Alright, sorry for my lack of updates, I've been super busy.  I got all the information about the menus and I will be trying out that stuff later, thanks for all the guidance there!  

I have 2 more questions now lol.

Can I put a different wallpaper up in fluxbox (as the desktop background), if so, how do I do this?

I have a USB wireless adapter and I want to use it to connect to the internet.  I've tested this device on Ubuntu before and it has worked.  Does anyone know a good application or front-end I could use in fluxbox as a wireless utility?  I want to be able to connect to different access points when I take my laptop different places.  Help in getting this to work is greatly appriciated!

---

### Post by RedSquirrel on 2007-04-07
> **sammyd253 said:**
> Alright, sorry for my lack of updates, I've been super busy.  I got all the information about the menus and I will be trying out that stuff later, thanks for all the guidance there!  

I have 2 more questions now lol.

Can I put a different wallpaper up in fluxbox (as the desktop background), if so, how do I do this?

Yes you can do that. [Here]("http://fluxbox-wiki.org/index.php/Background") is a page from the Fluxbox wiki that covers the topic in some detail. :)

Steps:

Install **feh** (using Synaptic, for example).

Use the menu entry in the example kerry_s gave above:

```
  [submenu] (Backgrounds)
  [exec] (Black) {exec fbsetroot -solid black}
  [wallpapers] (/usr/share/fluxbox/backgrounds)
  [wallpapers] (~/.fluxbox/backgrounds)
 [end]

```That will give you a menu item that is a list of all the wallpapers on your system and you just have to click on one to set that as your wallpaper. You can also add another [wallpapers] line for wherever you store your wallpapers on your system.

If you're still using the stock Fluxbox menu, you can add the Backgrounds item like this:

```
leafpad ~/.fluxbox/menu
```Change it from this:

```
[begin] (fluxbox)
[include] (/etc/X11/fluxbox/fluxbox-menu)
[end]

```to this:

```
[begin] (fluxbox)

[submenu] (Backgrounds)
   [exec] (Black) {exec fbsetroot -solid black}
   [wallpapers] (/usr/share/fluxbox/backgrounds)
   [wallpapers] (~/.fluxbox/backgrounds)
[end]

[include] (/etc/X11/fluxbox/fluxbox-menu)

[end]

```In your ~/.fluxbox/init file, find the line that looks like:

```
 session.screen0.rootCommand:
```and change it to:

```
 session.screen0.rootCommand:    fbsetbg -l
```Restart Fluxbox:
**Fluxbox menu -> Restart**.

By the way, whenever you make changes to the _init_ file, you have to restart Fluxbox to see the changes. 


Can't help with the wireless stuff I'm afraid...

**EDIT:**

I attached a screenshot so you can see what the Backgrounds menu item looks like (on my system).

---

### Post by kerry_s on 2007-04-07
For wireless> wlassistant
or 
network-manager <just like in ubuntu or xubuntu


If you want a certain thing from another system, you can mark it for installation in synaptic, look through the list of what it installs, cancel it and grab the thing you want.

For example: 
you want the network stuff from ubuntu, just mark ubuntu-desktop for install, look at what it uses, then cancel.

---

### Post by DJiNN on 2007-04-12
> **RedSquirrel said:**
> I attached a screenshot so you can see what the Backgrounds menu item looks like (on my system).

Hey RedSquirrel, that is a great desktop. Really clean & minimal and the theme is gorgeous. What theme is it?

Just wanted to also say "thanks" for all the brilliant info that you've already shared in this thread. It's really helping me getting back into Fluxbox again, which i see as a totally good thing! :)

DJiNN

---

### Post by RedSquirrel on 2007-04-12
> **DJiNN said:**
> Hey RedSquirrel, that is a great desktop. Really clean & minimal and the theme is gorgeous. What theme is it?

Just wanted to also say "thanks" for all the brilliant info that you've already shared in this thread. It's really helping me getting back into Fluxbox again, which i see as a totally good thing! :)

DJiNN


Thanks for all the compliments. It seems to me that whenever Fluxbox is discussed, a lot of people contribute some pretty interesting info. :)

The theme is the Vista Black (link in my sig). I made a few *minor* modifications to some of the font sizes and colours. I've been using it for a while now and I'm getting a little tired of it. I was looking on [boxwhore]("http://www.boxwhore.org") (awful name for that site, IMO) last night for something new but only for a few minutes (it was getting pretty late by then!). BTW, that wallpaper came from Gnome Art - "PlasPowerWoods". I have played around with gkrellm and the slit, but I always end up turning them off!

I'm glad you're getting back into Fluxbox. I thoroughly enjoy it. These days, I'm compiling my own from the svn source; kind of fun having the bleeding edge release. ;)

---

### Post by grimpage on 2007-04-13
Not to sure where to go with this question/concern but I gotta ask. 

How secure is the Xubuntu in general? 

I realize that many exploits can stem from all manner of (windows) applications, and in truth I came to accept that in my Xp operating system. I am still comforted by the low pitch background beep from one of my numerous firewalls blocking another access attempt. Sometimes, on a whim I'll open my security applications in the hope that some new excitement has happened.....a high threat attack. It's like a game. A game I don't really know how to play. Oh I wouldn't admit it anywhere else but when things are quite, and everyones tucked nicely in there beds, I get the sudden urge. The urge I can't deny. Quickly drawing the shades.....I.....I execute all seven of my anti-virus/spyware apps (yes seven for you see I am a collector). 

Are there any good apps I should be looking into for my security and virus concerns?
Or is everything already taken care of? 
Does everyone already know except me?

I'm not one to look any gift's horse in the mouth, but if you tell me I need look no further I might not believe you.

---

### Post by grimpage on 2007-04-13
How did my post end up at the end of the lists? I knew I was a bottom feeder but come on. Is this gonna update me or what? I sure hope so.

---

### Post by sammyd253 on 2007-04-13
I would imagine that Xubuntu is just as secure as any other version of Linux out there.  Fact is, I've been told numerous times that anti-virus, spyware, and firewall solutions aren't completely necessary on the Linux platform.  Here's what I think...  In Linux, I can do without the anti-virus and spyware protection.  I do want a firewall though, I believe these are critical in keeping unwanted users out.

grimpage, first I want to ask you, how is the performance of your XP install?  You stated earlier that you use multiple firewalls, anti-virus solutions, and spyware solutions.  It doesn't affect your computer if you're running multiple spyware solutions, but having many different versions of anti-virus and firewall software installed simultaneously on your machine can cause a lot of problems.  You should pick one of each, and properly configure it.  This will cause less conflicts, and will make your system much more efficient.

You may have a hard time accepting that you don't need anti-virus and spyware solutions on a Linux install.  It's ok though, I don't blame you, I blame hackers around the world.  While it's easy to target Microsoft, the fact of the matter is this:  It's obvious that they are the absolute leader in PC operating systems.  Because of this, they are the target to many hackers, and this is why there is a plethora of software out there to remedy this.  Unfortunately for you, you've become accustomed to having to always use this software.  With Linux, it's completely different.

However, I do believe that there are anti-virus and spyware apps that are installable in Linux, though I can not recommend any.  Someone else on these forums should be able to address this.  My point of this post was just to share my point of view on computer security in general, and I hope I helped you in some way or another.

---

### Post by Antilavista on 2007-04-13
> **kerry_s said:**
> If performance is what your after, the best thing to do is go custom install and build the system to your needs. Ubuntu makes it very easy to do with the server install. The server install is just the base system and nothing else, no gui yet. First you need to make a list of what you want to use, maybe even test the programs out on your current install if you know your going to wipe it anyways. 

Here's what i do->

i use the net installer so my systems up to date when i'm finished-> [http://mirror.linux.org.mt/mirror/ubuntu/dists/feisty/main/installer-i386/current/images/netboot/mini.iso](http://mirror.linux.org.mt/mirror/ubuntu/dists/feisty/main/installer-i386/current/images/netboot/mini.iso)

type> server
skip the package selection, i want custom, so tab and enter

after the install and reboot:
login (just start typing when it stops, the word positioning is screwy, looks like it froze during boot, but it's actually finished)

type> sudo su

This is the part where you select what you want, here's what i do:
type> apt-get install xorg gdm fluxbox leafpad emelfm synaptic

type> reboot

select fluxbox in the session menu and login

Open synaptic and install what ever else you want

Have fun.

This seems to be what I'm looking for :D 

I followed these instructions and the result is amazing, what a nice clean fast system this gives.

I'm new to Linux and from what I had read this is the sort of performace I was expecting.

I've managed to install Firefox and add it to the menus (posting from it now), Found this thread last night and started playing, next thing I knew it was 3:00am. 

I don't want to hijack this thread but I may ask a few questions here if you don't mind. Might be nice to keep it in the same place if a couple of us are trying it.

Thanks kerry_s you have opened my eyes8-[ =D>

---

### Post by grimpage on 2007-04-13
Wow thanks for the reply. I'm safer already...mmmmm warm blanket feeling! Seriously though, XP is running fine. I try not to think about security too much...happy thought's happy thought's happy, who am I? why I have no identity *cough*. I do have several more questions - most importantly:

How do you start a new thread? Am I missing (as in not seeing) something?

It would be really nice to start my own topics rather than jumping into other peoples. Another important question:

What type, and how many partitions are absolutely necessary? 

I can take a guess at around three: {/,/boot, and swap}. 

Is there anyway around this? 

My drive currently has two preexisting from my XP install. I tried using Gparted stand alone but it would not let me create more than four, and wouldn't recognize my external drive. The program mentioned something about extending, or including another partition on top of one of my preexisting partitions. I screwed around a bit but I couldn't really find what I was looking for:

Does anyone have tips about extending the allowable number of partitions on a single drive?

I'm not ready to wipe my apps (hehe) or XP off the map here. Any help will be seriously appreciated.

---

### Post by sammyd253 on 2007-04-13
> **Antilavista said:**
> This seems to be what I'm looking for :D 

I followed these instructions and the result is amazing, what a nice clean fast system this gives.

I'm new to Linux and from what I had read this is the sort of performace I was expecting.

I've managed to install Firefox and add it to the menus (posting from it now), Found this thread last night and started playing, next thing I knew it was 3:00am. 

I don't want to hijack this thread but I may ask a few questions here if you don't mind. Might be nice to keep it in the same place if a couple of us are trying it.

Thanks kerry_s you have opened my eyes8-[ =D>

Feel free to post questions here.  I'm finding this post to be my Ubuntu reference guide lol.

For grimpage:
If you want to make a new post somewhere, just click into a forums section from the home page, and then click the make new post button.  That's it.

I've been told it's good to go with 3 partitions:

/ - Obviously you need this partition.  Make it at least 15GB if you can.
/home - All of your personal settings and files (mp3, pictures, video) can go here.  If you need to reformat and reinstall Linux, don't format this partition again.  All of your settings and files will be retained.
/swap - Normally you make it twice the size of your system memory, but if you're using say, 2GB, then just make it 1GB or so.  If you have a lot of system RAM, it's rare that you're OS will have to access this partition.

Format the / and /home partitions using the ext3 filesystem.

You should be able to make as many partitions on your drive as you want.  I'd recommend backing up your data, and then restructuring your entire partition table from scratch.  You can dual boot XP and Ubuntu if you want.

---

### Post by grimpage on 2007-04-13
Yeah backing up is always a good idea, but its not perfect. A lot of hassle is created in registry data, and other infrastructure issues similar to that. 

I'll definately take what you said in mind. 

Thanks for the help clarifying the essentials, I get really nervous about making mistakes! Especially with memory, some things I could do I'm sure wouldn't just go back to "normal."

---

### Post by sammyd253 on 2007-04-13
My definition of backing up and your definition of backing up probably don't match up.

When I say to backup, I mean that you should basically copy your windows profile along with any other music/pictures/videos you have stored on your PC.  You can always reinstall applications, you don't need to backup anything from the registry...

---

### Post by Antilavista on 2007-04-15
After reading through this thread countless times and a bit of searching and messing about I have managed to get Fluxbox 1.0rc3 running on top of Ubuntu Server.

I am now a bit stuck, I've searched around but can't find a definitive way of installing Nvidia drivers on my system.

Anybody here able to give me any advice/point me in the right direction?

Please bear in mind I'm new to all this.

TIA

---

### Post by zazen666 on 2007-04-20
> **kerry_s said:**
> If performance is what your after, the best thing to do is go custom install and build the system to your needs. Ubuntu makes it very easy to do with the server install. The server install is just the base system and nothing else, no gui yet. First you need to make a list of what you want to use, maybe even test the programs out on your current install if you know your going to wipe it anyways. 

Here's what i do->

i use the net installer so my systems up to date when i'm finished-> [http://mirror.linux.org.mt/mirror/ubuntu/dists/feisty/main/installer-i386/current/images/netboot/mini.iso](http://mirror.linux.org.mt/mirror/ubuntu/dists/feisty/main/installer-i386/current/images/netboot/mini.iso)

type> server
skip the package selection, i want custom, so tab and enter

after the install and reboot:
login (just start typing when it stops, the word positioning is screwy, looks like it froze during boot, but it's actually finished)

type> sudo su

This is the part where you select what you want, here's what i do:
type> apt-get install xorg gdm fluxbox leafpad emelfm synaptic

type> reboot

select fluxbox in the session menu and login

Open synaptic and install what ever else you want

Have fun.

Hi guys,
Sorry to jump in here a bit late-but I am also interested in doing acustom server install with just this software I want/need.
I am interested in using Xubuntu's window manager or maybe openbox.
Can some one give me the steps again, what commands will I need to do?
Thanks

---

### Post by DJiNN on 2007-04-23
> **Antilavista said:**
> After reading through this thread countless times and a bit of searching and messing about I have managed to get Fluxbox 1.0rc3 running on top of Ubuntu Server.

I am now a bit stuck, I've searched around but can't find a definitive way of installing Nvidia drivers on my system.

Anybody here able to give me any advice/point me in the right direction?

Please bear in mind I'm new to all this.

TIA

I'm not 100% sure, but my first port of call would be [Automatix2]("http://www.getautomatix.com"). Install that & let Automatix install the nVidia drivers for you (It's a part of what it does after all) :)

Failing that, i have heard that the docs & How-To's on the nVidia site are pretty good, even for Linux, so maybe that's worth a try.

How are you getting on with it all anyway? Fluxbox is pretty neat isn't it? :)

---

### Post by DJiNN on 2007-04-23
> **zazen666 said:**
> Hi guys,
Sorry to jump in here a bit late-but I am also interested in doing acustom server install with just this software I want/need.
I am interested in using Xubuntu's window manager or maybe openbox.
Can some one give me the steps again, what commands will I need to do?
Thanks

Commands to do "what" exactly? :) If you're going to use XFCE as your manager, then it may be worth just installing Xubuntu & be done with it. 

I can't remember the actual process to install Flux/Openbox etc when doing a Server install (Although i fully intend to be doing one myself soon - just haven't got around to it yet)  but if you do a search for any of kerry_s threads you'll find out how to do it. Also, last time i looked there was a pretty good (& active) OpenBox thread.

Good luck......

DJiNN

---

