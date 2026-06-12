---
title: "Calibrate graphical card colors?"
date: 2006-10-30
forum: Absolute Beginner Talk
---

### Post by Zwendel on 2006-10-30
Hi,

I have an XP PC on which I edit my photographs. I have an Ubuntu PC on which I display my photographs.

Now, the XP PC is more or less calibrated towards printing the photographs on a certain printservice. I use the ATI Catalyst control center to correct the colors to get close to that of the printing service. My pictures look absolutely smashing. ;) 

However, when displaying the same pictures on the Ubuntu PC with exactly the same monitor and monitor settings, but with a different graphical card they look very, very drap. :( 

So, I need to calibrate my Via Deltachrome card (onboard). I need to tweak the color display like I do with the Catalyst Control Center in XP but don't find anyway to do this. Ubuntu didn't even recognize the fact that I could use 1400x1050, I had to edit a config file to get that running. (could do that thanks to this forum)

So now the question is: how can I tweak my colors on Ubuntu so both displays on both PC's give more or less the same image. I'm talking changing Gamma, Brightness and Contrast per color (Red, Green and Blue) channel here.

I would most certainly appriciate your help here because if I can't resolve this it's back to XP and I don't want that. ](*,)

---

### Post by orb9220 on 2006-10-30
Sorry I never heard of Via Deltachrome card. But to access those kinda of features the card vendor supplies the gui for that since the drivers are closed source. 

For example my nvidia-settings allow me to do that but only because they took the time to write linux drivers and the linux nvidia-settings gui that gives me the same control that the windows nvidia-settings do.

For people doing any kind of Graphics work or programming I always tell them to go nvidia or ati since they are mainstream there is alot more support.

For you the only thing I can see is disabling your onboard video and getting an ati or nvidia card, unless it is a laptop.

You can get a 128mb card really cheap for around $40.

Now nvidia beta drivers have a gui for thier cards. But not aware of how good the ati settings are.

---

### Post by CatKiller on 2006-10-30
I did find a thing in Synaptic for loading in those colour profiles. Can't remember what it was called now though, and I'm not at my computer to check. I didn't like it much - not least of all because I could only find a profile for one of my monitors.

In the end I ended up staring at those standard test images and using xgamma to tweak the red, green and blue gamma settings for each monitor, and then entering the values into xorg.conf.

---

### Post by Zwendel on 2006-10-31
> **CatKiller said:**
> 
In the end I ended up staring at those standard test images and using xgamma to tweak the red, green and blue gamma settings for each monitor, and then entering the values into xorg.conf.

This sounds alright to me. What is xgamma? Where can I find it? Can you do more then just gamma?

Did you find the name of that Synaptic thing?

I'll Google it up after work.

---

### Post by CatKiller on 2006-10-31
> **Zwendel said:**
> What is xgamma?
From **man xgamma**:> **DESCRIPTION**
       **xgamma** allows X users to query and alter the gamma correction of a mon&#8208;
       itor via the X video mode extension (XFree86-VidModeExtension).


> Where can I find it?

You should already have it.

> Can you do more then just gamma?

With xgamma? Not as far as I know. You can adjust each of the colour channels independently if you want, though.

There's xvidtune that lets you change other things about the display, although I've not used it.

> Did you find the name of that Synaptic thing?

I'll Google it up after work.

I SSHed into my computer, and I still can't remember what it was - it may have been lprof.

---

### Post by Zwendel on 2006-10-31
A quick search in Google for xgamma resulted in this tutorial:
[http://applications.linux.com/article.pl?sid=05/02/07/2244242](http://applications.linux.com/article.pl?sid=05/02/07/2244242)

Which I'm going to try first. I'll keep you posted if it works out.

Thanks for the tips!

---

### Post by CatKiller on 2006-10-31
I think that's the tutorial I read. Quite some time ago now, which is why I didn't stand much chance of being able to send you there myself. Good luck!

---

### Post by Zwendel on 2006-10-31
No luck so far. :(

I'm want to try Xcalib now, downloaded it here:
[http://www.etg.e-technik.uni-erlangen.de/web/doe/xcalib/](http://www.etg.e-technik.uni-erlangen.de/web/doe/xcalib/)

but the
 $ make icclib_xcalib
as suggested in the README doesn't do a thing and being no to linux it's precisly this kind of thing thats difficult for me. ](*,) 

If somebody could help me to get this progy installed that would be great.

---

### Post by Zwendel on 2006-10-31
Alright,

it's back to square one.

After 3 hours of unsuccessfull probing and trying I'm quiting.

I can't get Ubuntu to aknowledge the fact that I have a VIA and not a VESA graphical card. Hence, I can't use xcalib or do any gamma correction at all. If I can't use xcalib it's back to XP and I would really, really hate that. :(

Save me!
Although I fear I'm doomed if I see that there are more DeltaChrome owners crying for help here in this forum. :(

---

### Post by CatKiller on 2006-10-31
VESA isn't a graphics card, it's a specifications association. What you're claiming is the graphics card is probably the driver you're using. The "vesa" driver is one of those works-on-anything, has-no-features deals. If you've got the wrong driver selected, then you'll want to either do **sudo dpkg-reconfigure -phigh xserver-xorg** for an interactive configuration tool, or edit your /etc/X11/xorg.conf file manually to change the Driver line of the Device section to the installed driver that you wish to use. Is it the "savage" driver that you use for a S3/VIA DeltaChrome thing? I'm afraid I've never used one of those.

I don't know why you're so hung up on this xcalib thing that you'll have to pick a different operating system if you can't get this one application to work that you hadn't even heard of this morning. But maybe it is that great. There are other ICC profile tools available, including ones in Synaptic, including the lprof that I alluded to earlier. You say it didn't make, but you don't say how it failed. Have you installed build-essential? Without it you won't have a compiler. Which might explain why you can't compile. You might also want to install and use **checkinstall** - that will integrate your compiled program in with the funky package management system, so it will be easy to update or uninstall it.

If you have patience or a sense of adventure (ideally, you'd have both), you'll find that Linux will be a liberating experience. If you have neither, then you have to ask yourself why you're even bothering to install your own operating system.

---

### Post by Zwendel on 2006-11-01
I was just getting very tired and very frustrated yesterday.

It's not just xcalib, it's the gamma correction I want and can't get withe the vesa driver. So I'm not sure that xcalib will save the day, or lprof, but neither wil work without getting the card to run on the propper driver.

So thanks for the tip on reconfigure, I'll give that a shot later on.

I have been looking for lprof in synaptic, didn't find it. Then looked for it on the Debian site and found it. But there were dependencies not satisfied, so I looked for those and one of them ,tzdata, refused to get installed (it's in the unstable selection).

I already have shown quite some patience and I like Linux a lot, or would have switched back to save haven (and pit of doom simultaniously) XP. But is frustrating that his "simple to use linux" as somebody advertised it to me is so dang complicated for a novice like me. It's a good ding I know a thing or 2 of computers in general our I would have drawned in the config files already. ;)

But sudo kpkg-reconfigure -phigh xserver-xorg it is!
First however, lots of hours without a computer, reloading the batteries so to speak. ;)

---

### Post by CatKiller on 2006-11-01
> **Zwendel said:**
> I have been looking for lprof in synaptic, didn't find it. Then looked for it on the Debian site and found it. But there were dependencies not satisfied, so I looked for those and one of them ,tzdata, refused to get installed (it's in the unstable selection).

My mistake - It's in the Universe section of the repositories. You might want to look at [this page]("https://help.ubuntu.com/community/Repositories/Ubuntu") for instructions on how to enable them. [This page]("https://help.ubuntu.com/community/Repositories") is quite a nice introduction.

CheckInstall is in the Universe repositories, too.

> I already have shown quite some patience and I like Linux a lot, or would have switched back to save haven (and pit of doom simultaniously) XP.

I agree. It's just that sometimes we need to remind ourselves of why we're doing the things we do ;)

>  But is frustrating that his "simple to use linux" as somebody advertised it to me is so dang complicated for a novice like me. It's a good ding I know a thing or 2 of computers in general our I would have drawned in the config files already. ;)

In my experience, it's probably that knowledge that's been your downfall so far - a complete novice doesn't have to unlearn years of a particular way of doing things like us ex-Windows users do. You may agree that Ubuntu is easy to **use**, it's just that sometimes it can be a bit fiddly to **configure** ;)

> But sudo **d**pkg-reconfigure -phigh xserver-xorg it is!
First however, lots of hours without a computer, reloading the batteries so to speak. ;)

Good luck.

---

### Post by Zwendel on 2006-11-02
Ok,

So I gave it a shot, but if I change my driver to anything but VESA I get this blue screen with an error message after which X doesn't start up and I have to restore my backup form xorg.conf.

Now, I did find this
[http://www.viaarena.com/default.aspx?PageID=420&OSID=25&CatID=2580&SubCatID=164](http://www.viaarena.com/default.aspx?PageID=420&OSID=25&CatID=2580&SubCatID=164)

But in the install.txt they talk about Suse, Fedora and Mandriva. Not about Debian nor Ubuntu. So, I don't know if I can do anything with these and if I can, I wouldn't now how to start! There is talk about rebuilding kernels etc and that's not up my alley.

Any advice?

---

### Post by gn2 on 2006-11-02
There are gamma sliders in the Display Settings of Xubuntu.

I don't know what package it is though.

Kgamma is a GUI gamma adjuster for KDE, and is available through Synaptic.

---

### Post by Zwendel on 2006-11-02
> **gn2 said:**
> There are gamma sliders in the Display Settings of Xubuntu.

I don't know what package it is though.

Kgamma is a GUI gamma adjuster for KDE, and is available through Synaptic.

It doesn't really matter GN2, for as long as my driver is stuck at VESA no gamma correction what so ever is possible. ](*,)

---

### Post by gn2 on 2006-11-02
> **Zwendel said:**
> It doesn't really matter GN2, for as long as my driver is stuck at VESA no gamma correction what so ever is possible. ](*,)

Wouldn't hurt to try adding xubuntu-desktop with Synaptic though?

If it was me I'd be trying one of the Distros that are supported by Via, there's quite a lot of Linux driver support on Viaarena.

Have you tried PCLinuxOS yet? That would be my suggestion. It seems more advanced (just my opinion) than Ubuntu and has many more user-friendly features.
And it's Mandrake based which is supported by Via.

---

### Post by Zwendel on 2006-11-02
> **gn2 said:**
> 
Have you tried PCLinuxOS yet? That would be my suggestion. It seems more advanced (just my opinion) than Ubuntu and has many more user-friendly features.
And it's Mandrake based which is supported by Via.

Nope, never heard of it. Mandrake based and supported by Via. Sounds worth checking out. I'll try to do that later when I've got some more time on my hands. Thanks for the tip!

---

### Post by CatKiller on 2006-11-02
> **Zwendel said:**
> So I gave it a shot, but if I change my driver to anything but VESA I get this blue screen with an error message after which X doesn't start up and I have to restore my backup form xorg.conf.

What have you tried changing it to? What does your xorg.conf look like? When you've broken your X server, are there any messages in /var/log/Xorg.0.log that tell you in what way it is broken?

There's a "via" driver that says this about itself: > X.Org X server -- VIA display driver
This driver for the X.Org X server (see xserver-xorg for a further description)
provides support for VIA/S3 CLE266/KM400/K8M800/UniChrome cards, which are
frequently found in low-form-factor VIA motherboards, and in some laptops. Is that what you've got?

> Now, I did find this
[http://www.viaarena.com/default.aspx?PageID=420&OSID=25&CatID=2580&SubCatID=164](http://www.viaarena.com/default.aspx?PageID=420&OSID=25&CatID=2580&SubCatID=164)

But in the install.txt they talk about Suse, Fedora and Mandriva. Not about Debian nor Ubuntu. So, I don't know if I can do anything with these and if I can, I wouldn't now how to start! There is talk about rebuilding kernels etc and that's not up my alley.

I guess I'm looking at a different one than you are, but this one doesn't seem that precise, either. But I **think** that this is the same as the via X.org driver I mentioned above. I could be wrong of course - it's not like I've tried to install this driver - but the instructions do say this at the bottom: > If users see the "via" module and the "4.1.68" version then the via 2D driver 
is successfully loaded.

---

### Post by Zwendel on 2006-11-02
Well, as far as I have been able to figure out that driver is only for UniChrome and not for DeltaChrome. I tried to install it but Ubuntu says a newer version is already installed. Trying to get Ubuntu to use that via driver I have makes the big bad blue screen appear on reboot. :(

I posted a simular question at PCLinuxOS forum and the answer I got there was that according to some general linux website there are no DeltaChrome drivers for Linux as of yet. They are under development but it can still take months. So down there I was advised to buy a cheap nvidia.

Either I do that, or I'll have to throw in the towel and switch back.... At least, until the drivers become available.

---

### Post by CatKiller on 2006-11-02
Both the via and savage drivers should be installed already - it would only be a case of enabling those drivers in your xorg.conf, as I understand it.

The Random-Guy-On-The-Internet(TM) could be right that there aren't drivers with specific support for DeltaChrome chips. I'd not heard of them till you mentioned them in this thread. The reading I've done on them since suggests that they've been out for quite a while though. You'd have to ask the S3 people at Via why they haven't bothered to release a Linux driver in the last three years, and let them know that you're buying a cheap nVidia card instead if that turns out to be the case.

A cheap nVidia card can be had for quite cheap, really.

Have you checked your logs yet? It might be something else.

---

### Post by gn2 on 2006-11-03
> **Zwendel said:**
> 
I posted a simular question at PCLinuxOS forum and the answer I got there was that according to some general linux website there are no DeltaChrome drivers for Linux as of yet.

Great OS that PCLinux, but Ubuntu forum's better. 

This may be worth looking at: [http://www.viaarena.com/default.aspx?PageID=420&OSID=32&CatID=2810&SubCatID=164](http://www.viaarena.com/default.aspx?PageID=420&OSID=32&CatID=2810&SubCatID=164)

;)

---

