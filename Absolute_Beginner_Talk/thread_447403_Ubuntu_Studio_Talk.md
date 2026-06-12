---
title: "Ubuntu Studio Talk"
date: 2007-05-18
forum: Absolute Beginner Talk
---

### Post by izizzle on 2007-05-18
Recently, a new distro named UbuntuStudio has been relesed. This is a multimedia distro, like Dreamlinux, but it is based on Ubuntu. It uses the ubunru repos along with some of its own packages. This may be a great milestone for Canonical Ltd. and Ubuntu. More info [www.ubuntustudio.org](www.ubuntustudio.org)

---

### Post by k33bz on 2007-05-18
am i able tojust go get the softwware packages that ubuntu studio has with out having to install ubuntu studio?

---

### Post by shen-an-doah on 2007-05-18
> **k33bz said:**
> am i able tojust go get the softwware packages that ubuntu studio has with out having to install ubuntu studio?

[http://ubuntuforums.org/showthread.php?t=442506](http://ubuntuforums.org/showthread.php?t=442506)

Third post down.

---

### Post by k33bz on 2007-05-18
perfect, thanks

---

### Post by lesbianpenguin on 2007-05-18
can it be installed on mac g4 machine? im a complete newbie :P

---

### Post by izizzle on 2007-05-18
> **lesbianpenguin said:**
> can it be installed on mac g4 machine? im a complete newbie :P

Sorry dude, this one is for PC only. But Ubuntu can be installed on G4.

---

### Post by izizzle on 2007-05-18
Is this distro made by Canonical itslef? is it like ubuntu, kubuntu, and xubuntu?b or is it different.

---

### Post by shen-an-doah on 2007-05-18
> **izizzle said:**
> Is this distro made by Canonical itslef? is it like ubuntu, kubuntu, and xubuntu?b or is it different.

It's an "unofficial" variant of Ubuntu as far as I know. It's put together by the Ubuntu studio team. The user MetalMusicAddict on here is a prominent part of the team...

---

### Post by MetalMusicAddict on 2007-05-19
Ubuntu Studio is/will be as official as Xubuntu.

---

### Post by stmiller on 2007-05-19
> **lesbianpenguin said:**
> can it be installed on mac g4 machine? im a complete newbie :P

Yeah, come check out the Apple PPC forum section. Lots of info there for Macs and Ubuntu.

---

### Post by gugin on 2007-05-19
becareful...it doesn't install like ubuntu. I've installed feisty on three pc's, but this one is a bit different. no live cd. no restricted modules.. there's something wrong.

---

### Post by MetalMusicAddict on 2007-05-19
> **gugin said:**
> becareful...it doesn't install like ubuntu. I've installed feisty on three pc's, but this one is a bit different.
Its only different to what you know. This type of disk is the same one since Ubuntu's start. The live disk is the new one.
> no live cd.
We dont plan on having one.
> no restricted modules..
Yes they are. Look on the disk. **/Ubuntu Studio Install DVD/pool/main/l/linux-restricted-modules-2.6.20**
> there's something wrong.
Nothings wrong. Its just not what your used to.

---

### Post by izizzle on 2007-05-20
Whats the difference between ubuntu and ubuntustudio? What software is included in ubuntustudio?

---

### Post by zettberlin on 2007-05-20
I installed the Ubuntustudio-packages atop a fresh by-the-book install of Kubuntu Feisty, added XFCE and some more extras -  it works quite well now:

[http://gnupc.de/~zettberlin/law/xfce-komplett-mai2007.png](http://gnupc.de/~zettberlin/law/xfce-komplett-mai2007.png)

still I got some questions:

1.) as I installed the lowlatency-kernel I needed to reconfigure the entire graphics-system (xorg and nvidia-proprietary drivers from universe packages)
Will this go automagically in the future?

2.) installing the lowlatency-kernel did not configure group audio, limits.conf or even took care of the loading of alsa_seq. 
Is this done if I install the entire metapackage?

3.) If I run my amd64-system at 128 F/P*2 I get an xrun every 10 minutes, raising the Frames/Buffer to 256 helps this a bit but still I get xruns in an 10min-fraction intervall (every 20 or 30 min that is) 
What evil demon could this be ;-) ?

I look forward sharing my experiences with Ubuntustudio with other Linux-Audio people. I build an audio-workstation PC (AMD Athlon 64, MAudio Audiophile Soundcard, Nvidia Graphics) on wich Ubuntu feisty with the Ubuntustudio-Packages is the primary 64bit-Audiosystem. I have made up a little Handbook for this machine:

[http://gnupc.de/~zettberlin/law/silur/Documentation_en/](http://gnupc.de/~zettberlin/law/silur/Documentation_en/)

and a somewhat bigger one in german lang:

[http://gnupc.de/~zettberlin/law/silur/Documentation/](http://gnupc.de/~zettberlin/law/silur/Documentation/)

The licence is CC sharealike attribution so feel free to extract whatever information you find usefull for the project from this folders :-)

---

### Post by izizzle on 2007-05-20
dude, thats nothing. Check out my ubuntu 7.04 desktop. Its using only gdesklets and it looks better than ubuntustudio.

---

### Post by MetalMusicAddict on 2007-05-20
> **zettberlin said:**
> 1.) as I installed the lowlatency-kernel I needed to reconfigure the entire graphics-system (xorg and nvidia-proprietary drivers from universe packages)
Will this go automagically in the future?
All you needed were the restricted modules for the kernel. We cannot at this time install them for you. If, at a later time Ubuntu installs them for you then we will as well.

> 2.) installing the lowlatency-kernel did not configure group audio, limits.conf or even took care of the loading of alsa_seq. 
**Is this done if I install the entire metapackage?**
Yes. It should be set for you if you install our packages or from our disk. its not done in the kernel package.

> 3.) If I run my amd64-system at 128 F/P*2 I get an xrun every 10 minutes, raising the Frames/Buffer to 256 helps this a bit but still I get xruns in an 10min-fraction intervall (every 20 or 30 min that is) 
What evil demon could this be ;-) ?
This could be lots of things. It could be kernel/settings/HW.

---

### Post by zettberlin on 2007-05-20
> **MetalMusicAddict said:**
> All you needed were the restricted modules for the kernel. We cannot at this time install them for you. If, at a later time Ubuntu installs them for you then we will as well.


Of course I installed the restricted modules for the new kernel - as they are installed with the default-kernel, they are installed with the lowlat too - are`nt they ;-)

Still they seem to be not loaded correctly by xorg after the install of lowlat - I could easily fixe this issue - it was somewhat my  900th Linux-Installation or so. I just wonder, if our drummer, who has only seen Knoppix once on his computer would go as easily with this...

> **MetalMusicAddict said:**
> 
Yes. It should be set for you if you install our packages or from our disk. its not done in the kernel package.


That is very good news. :-)
Still I think, the lowlatency-kernelpackage should do this, just in case someone dislikes GNOME or the Artwork...

> **MetalMusicAddict said:**
> 
This could be lots of things. It could be kernel/settings/HW.

allright you mean what exactly? There is no folder /file kernel/settings/HW - is it in the /usr/src?

---

### Post by MetalMusicAddict on 2007-05-20
> **zettberlin said:**
> Of course I installed the restricted modules for the new kernel - as they are installed with the default-kernel, they are installed with the lowlat too - are`nt they ;-)
They get installed if you install from the Ubuntu/Ubuntu Studio disk but if you just grab **ubuntu-desktop** or **ubuntustudio-desktop** you dont get them.
> Still they seem to be not loaded correctly by xorg after the install of lowlat - I could easily fix this issue - it was somewhat my 900th Linux-Installation or so. I just wonder, if our drummer, who has only seen Knoppix once on his computer would go as easily with this...
Im not sure the issue so I dont know what to say. My nVidia card works fine after I install the kernel and modules.

> That is very good news. :-)
Still I think, the lowlatency-kernelpackage should do this, just in case someone dislikes GNOME or the Artwork...
We have no control over the kernel packages. So it wont happen there.

> allright you mean what exactly? There is no folder /file kernel/settings/HW - is it in the /usr/src?
It could be the kernel your running, your JACK settings, inadequate HW.

---

### Post by zettberlin on 2007-05-20
> **MetalMusicAddict said:**
> They get installed if you install from the Ubuntu/Ubuntu Studio disk but if you just grab **ubuntu-desktop** or **ubuntustudio-desktop** you dont get them.

Im not sure the issue so I dont know what to say. My nVidia card works fine after I install the kernel and modules.


OK - it is just a setup issue - of course I took care, that the corresponding restricted modules are installed with the new kernel. And it worked anyways but not o.o.t.b.

> **MetalMusicAddict said:**
> 
We have no control over the kernel packages. So it wont happen there.


Sad thing: but if it works with the metapackage, most users will be served OK


> **MetalMusicAddict said:**
> 
It could be the kernel your running, your JACK settings, inadequate HW.

OK - now I get you. The kernel is the lowlatency-kernel from universe, 
the System is:

AMD Athlon 64 3800+
MSI K9N Neo-F Mainboard
1GB RAM
1 IDE-HD for / and everything else
MAudio Audiophile 1024 (on a single IRQ)

I doubted, it could be the IDE-HD but on another System with the same Setup and a bigger CPU (AMD X2 5000) and a SATA-HD I get the same trouble.

---

### Post by Thomaseov on 2007-05-21
Hi zettberlin,

I just installed ubuntustudio audio and plugins by adding the repos as suggested on the official ubuntu pages, and I have the same problem of dead  x.  I have nvidia and athlon x2 4200, so similar situation as yours.  Not as expert at linux installs as you (this is only my 12th or so).  How do you get the restricted modules to load with the low latency kernel?  Is there anything else you had to do (you mentioned various audio configs you needed to do)?

Thomas

---

### Post by MetalMusicAddict on 2007-05-21
> **Thomaseov said:**
> Hi zettberlin,

I just installed ubuntustudio audio and plugins by adding the repos as suggested on the official ubuntu pages, and I have the same problem of dead  x.  I have nvidia and athlon x2 4200, so similar situation as yours.  Not as expert at linux installs as you (this is only my 12th or so).  How do you get the restricted modules to load with the low latency kernel?  Is there anything else you had to do (you mentioned various audio configs you needed to do)?

Thomas

In a terminal type: **sudo apt-get install linux-lowlatency**.

---

### Post by androssofer on 2007-05-21
is ubuntu studio a live cd? and if not will it be a live CD (well actually dvd) by gusty gibbon?

---

### Post by zettberlin on 2007-05-21
To fx the X-issue I did the following:

rerun:

nvidia-glx-config -enable

In one case this did not help so I ran:

dpkg-reconfigure xserver-xorg

and then again:

nvidia-glx-config -enable

In every case on must make sure that the restricted modules for the lowatency-kernel are installed. This should be done automagically, if one installs the lowlatency-kernel. To make everything perfectly clear you can issue the following:

apt-get install linux-restricted-modules-lowlatency

this should either post a message, that the restricted modules are installed already or install them if not...


For the audiosettings:

[https://help.ubuntu.com/community/UbuntuStudioPreparation](https://help.ubuntu.com/community/UbuntuStudioPreparation)

scroll down to "Real-Time Support" this is for dapper but can/must be done in feisty the same.

good luck ;-)

---

### Post by MetalMusicAddict on 2007-05-21
> **androssofer said:**
> is ubuntu studio a live cd? and if not will it be a live CD (well actually dvd) by gusty gibbon?

We have no plans on producing a live disk.

---

### Post by izizzle on 2007-05-25
WHy not?! Personally, i think that ubuntu studio Sucks. It is a complete copy of ubuntu with some sassy lokking themes and some extra applications. Ubuntu can can be better that that. AND, it is NOT a live CD? How the hell am I supposed to run it if I have an external DVD drive running on USB?!?

---

### Post by shen-an-doah on 2007-05-25
> **izizzle said:**
> WHy not?! Personally, i think that ubuntu studio Sucks. It is a complete copy of ubuntu with some sassy lokking themes and some extra applications. Ubuntu can can be better that that. AND, it is NOT a live CD? How the hell am I supposed to run it if I have an external DVD drive running on USB?!?

You appear to have missed the point of Ubuntu Studio. It's intended for multimedia production, that's why it comes with the latest versions of appropriate applications as well as **a low-latency kernel** for better sound recording. The kind of work Studio is intended for is not the kind of stuff you would do on an OS running from a CD. The idea of a live CD is to introduce people to the OS or to check hardware compatibility, you don't need a Studio disk to do this.

If you want, you don't have to install using the Studio DVD, you can just do a normal Feisty install and then ["upgrade" to Studio]("http://ubuntumusic.blogspot.com/2007/05/upgrade-to-ubuntu-studio.html").

Don't say something sucks just because it doesn't do exactly what you want it to when that's not what it's intended for. Would you criticise a vacuum cleaner because it made an inadequate leafblower?

---

### Post by izizzle on 2007-05-25
i stand corrected :D

btw, thanks for the link

P.S: is there a way to run the ubuntustudio live DVD from an external usb dvd drive?

---

### Post by mrbugspray on 2007-05-29
I am actually making a clone of  ubustu  to powerpc. Anybody wishing to help please e-mail me at [email]mr.miloshovel@gmail.com[/email] ;)

I need somebody to compile the low latency kernel to the ubustu-ppc iso. I also need documentation writers and just general suggestions. I need all the help i can get. :)

---

### Post by shen-an-doah on 2007-05-29
> **mrbugspray said:**
> I am actually making a clone of  ubustu  to powerpc. Anybody wishing to help please e-mail me at [email]mr.miloshovel@gmail.com[/email] ;)

I need somebody to compile the low latency kernel to the ubustu-ppc iso. I also need documentation writers and just general suggestions. I need all the help i can get. :)

I'll happily help, though I can't help with the compiling or anything and I won't have access to any Macs I could test it on till I'm back at uni in October, but I'll help in any other way I can. I'll also happily link to your efforts on my blog whenever you've got something sorted.

---

### Post by silent1643 on 2007-05-29
ub studio was visually nice, however i recently went back to the original ubuntu (clean install) for some reasons.

mainly it installed to many applications that i didn't need, and un-installing them all would have been a pain.. i didn't see an option in synap to just uninstall ubuntustudio-audio etc..

the theme was just to dark.. at some points you couldn't even see the text in the drop down menu's

finally my boot time was longer as well as starting some programs up compared to my previous.


I think studio is a nice addition for some, but then sometimes i think ubuntu just released this to get their name back in the headlines.. skeptic i am *yoda

---

### Post by mrbugspray on 2007-05-29
> **shen-an-doah said:**
> I'll happily help, though I can't help with the compiling or anything and I won't have access to any Macs I could test it on till I'm back at uni in October, but I'll help in any other way I can. I'll also happily link to your efforts on my blog whenever you've got something sorted.

If test ubuntu studio, and download ppc versions of the programs included and others you like, please do this and send me an e-mail and I will reply with ftp info. :)

---

### Post by shen-an-doah on 2007-05-29
> **silent1643 said:**
> I think studio is a nice addition for some, but then sometimes i think ubuntu just released this to get their name back in the headlines.. skeptic i am *yoda

The main Ubuntu team have nothing to do with US, it's an unofficial variant of Ubuntu.

---

### Post by b05q on 2007-05-29
hi.  i'd like to check ubuntustudio out, but only if i'll be able to get it to work with my external soundcard.  it's an m-audio firewire solo.  i know freebob is supposed to work with it, i gave it a quick try after installing feisty and it didn't Just Work.  right now audio production is the only thing i boot back into that other OS for.

is any of the hardware that i'm working with (m-audio firewire solo + my signature), known to have problems?

---

### Post by MetalMusicAddict on 2007-05-29
> **silent1643 said:**
> ub studio was visually nice, however i recently went back to the original ubuntu (clean install) for some reasons.

mainly it installed to many applications that i didn't need, and un-installing them all would have been a pain.. i didn't see an option in synap to just uninstall ubuntustudio-audio etc..

the theme was just to dark.. at some points you couldn't even see the text in the drop down menu's

finally my boot time was longer as well as starting some programs up compared to my previous.


I think studio is a nice addition for some, but then sometimes i think ubuntu just released this to get their name back in the headlines.. skeptic i am *yoda

Installing the metas does not a Ubuntu Studio make. If you use our installer you pick what you install. You can install a base and just grab the apps you want later.

> **shen-an-doah said:**
> The main Ubuntu team have nothing to do with US, it's an unofficial variant of Ubuntu.

Not exactly true. We're as official as Xubuntu.

As far as a PPC version we would have done it if all the parts were there for it but they are not. There are also some kernel issues.

---

### Post by shen-an-doah on 2007-05-29
> **MetalMusicAddict said:**
> Not exactly true. We're as official as Xubuntu.

Really? Woo, go officialness!

---

### Post by MetalMusicAddict on 2007-05-29
> **shen-an-doah said:**
> Really? Woo, go officialness!

Well, it doesnt mean much. :) It looks like they will be building our disks for Gutsy.

---

### Post by polaris20 on 2007-05-30
Ubuntu Studio is nice in concept, and it comes with all the apps that I'd need, but sadly it comes up a bit short, in terms of user-friendliness. 

I install the OS. Different from Feisty, but that's fine, I've been using Ubuntu since 4, and this is normal. 

I install the audio apps, graphics, and plug-ins. 

I plug in my Tascam US-122, a pretty common prosumer audio interface. No USB light. Okay, let's do a search in Synaptic for "Tascam". 

Sure enough, there's a package for firmware. Install that. Reboot with Tascam plugged in. No USB light. 

Pull the cable, plug back in; still no USB light. 

Now I found instructions that may or may not work from when Dapper was current, as well as a couple posts here about it in regards to regular Feisty, entailing editing conf files, downloading this, extracting that, etc. That's fine, I can follow the directions, and hopefully it'll work. 

But if Studio is intended to attract recording musicians away from Windows and OSX, this isn't the way to do it. 

You'll never get my bass player to deal with this. He'll just go back to Winbloze. 

This little stuff needs to be fixed/simplified. It's nearly there. Just not yet.

---

### Post by shen-an-doah on 2007-05-30
Is [this](http://ubuntuforums.org/showthread.php?t=431066&highlight=tascam) what you found? It worked perfectly for me.

---

### Post by polaris20 on 2007-05-30
> **shen-an-doah said:**
> Is [this](http://ubuntuforums.org/showthread.php?t=431066&highlight=tascam) what you found? It worked perfectly for me.

Haven't tried it yet. Which one worked well for you, the first post? It looks like he revised it a couple times. 

Point being, if you want to be competitive with Windows and OSX in terms of audio (and Ubuntu Studio is *very* close) then you've got to eliminate stuff like that. It should just be an apt-get away, case closed. 

just MHO.

---

### Post by shen-an-doah on 2007-05-30
> **polaris20 said:**
> Haven't tried it yet. Which one worked well for you, the first post? It looks like he revised it a couple times. 

Point being, if you want to be competitive with Windows and OSX in terms of audio (and Ubuntu Studio is *very* close) then you've got to eliminate stuff like that. It should just be an apt-get away, case closed. 

just MHO.

Yeh, the first one. I think a few of the revisions were just stuff like spelling mistakes and whatnot.

The reason it's a somewhat lengthy process, is because it's not just a case of installing a programme to use the US-122. You first need the drivers for the US-122, then you need to tell Ubuntu to update the firmware when it gets plugged in, and then you need to tell Ubuntu to use the US-122.

Sometimes things need to be slightly complicated. While what's happening might be complicated, how you do it really isn't. It's simply a case of following instructions and copying and pasting the various bits.

While this might be more complex than the windows way of "install driver, plug in, go", it doesn't mean it's worse. Considering that on some systems if you have XP service pack 2 installed, your US-122 will misbehave and create glitches that render it nigh unusable, I think I'll take the complicated Linux way :D

---

### Post by baracuda68 on 2007-05-30
> **gugin said:**
>  . no live cd.

Without starting a new thread, isnt there a way to add to the ISO to make it a "LIVE" CD?

---

### Post by MetalMusicAddict on 2007-06-01
> **baracuda68 said:**
> Without starting a new thread, isnt there a way to add to the ISO to make it a "LIVE" CD?

No.

---

### Post by dbbolton on 2007-06-05
openbox users:

i have made a relatively pleasant theme that integrates well with ubuntu studio.

[link](http://box-look.org/content/show.php/show.php?content=59671)

---

### Post by shen-an-doah on 2007-06-05
> **dbbolton said:**
> openbox users:

i have made a relatively pleasant theme that integrates well with ubuntu studio.

[link](http://box-look.org/content/show.php/show.php?content=59671)

That's pretty awesome. If only I used openbox instead of fluxbox :(

---

### Post by sk8dork on 2007-06-06
> **shen-an-doah said:**
> That's pretty awesome. If only I used openbox instead of fluxbox :(

i'm working on a rather pleasant theme for fluxbox, similar to dbbolton's openbox theme (we worked completely separately on these, no relation)
haven't released it yet but here is a screenie: [link]("http://www.sk8dork.com/pics/ubustu-fluxboxtheme4.png")

---

### Post by shen-an-doah on 2007-06-06
> **sk8dork said:**
> i'm working on a rather pleasant theme for fluxbox, similar to dbbolton's openbox theme (we worked completely separately on these, no relation)
haven't released it yet but here is a screenie: [link]("http://www.sk8dork.com/pics/ubustu-fluxboxtheme4.png")

Yeh, I saw that in the other Ubunstu thread, looks good. Can't wait till it's finished!

---

### Post by brian j on 2007-06-06
Still looks too much like Ubuntu Studio'ish....? ( Thats My Honest Opinion ).

---

### Post by shen-an-doah on 2007-06-06
> **brian j said:**
> Still looks too much like Ubuntu Studio'ish....? ( Thats My Honest Opinion ).

Surely that's the point?

---

### Post by brian j on 2007-06-06
Dah! Good Point :p

---

### Post by sk8dork on 2007-06-06
hehe, yeah, there isn't currently any official ubuntu studio theme for fluxbox, so that was why i started working on it. i like ubuntu studio, but i prefer fluxbox over gnome. you do, of course, still need to run gnome-settings-daemon with the official ubuntu studio theme installed to get the desired effect.

---

### Post by Zannax on 2007-06-14
I've just installed an Edgy a few weeks ago...
I guess I can't upgrade to Ubuntu studio from that, right?

I'm a bit afraid of upgrading to Feisty first, just when I was starting to get everything work fine in my Edgy :-(

If I install the various packages (low-latency kernel , jack, Ardour, etc...)  on Edgy would it be more complicated? Is there a bigger risk of messing up everything? :-)

---

### Post by por100pre1 on 2007-06-14
> **Zannax said:**
> I've just installed an Edgy a few weeks ago...
I guess I can't upgrade to Ubuntu studio from that, right?

I'm a bit afraid of upgrading to Feisty first, just when I was starting to get everything work fine in my Edgy :-(

If I install the various packages (low-latency kernel , jack, Ardour, etc...)  on Edgy would it be more complicated? Is there a bigger risk of messing up everything? :-)

I think you should upgrade to Feisty first, beacuse that's a bigger task to do. I did a clean install of Feisty in my PC last month and then used the Ubuntu Studio repos; everything went smooth this way.

---

### Post by Zannax on 2007-06-14
Ok thank you... I've also just found 
[this]("https://help.ubuntu.com/community/UbuntuStudio/DapperPreparation") explaining how to do what I was thinking of...

---

### Post by linol on 2007-06-14
Just to tell Ubuntu Studio developpers that Fedora 7 (with alsa 1.10.4 rc3) drives M-Audio Delta 192 prety well (a very attractive pci professional sound-card accessible for everyone) while UbuntuStudio 7.04 unfortunately still doesn't...  It shouldn't be very hard to reach soon hopefully!

thanks for all...

linol

---

### Post by linol on 2007-06-16
to update my request : M-Audio Audiophile Delta 192 sound card starts being driven by Gutsy in developpement now ;) 

Very good news (for me at last). Perhaps Gutsy Alsa audio drivers could be backported to "stable" Feisty...

linol

---

### Post by Zannax on 2007-06-30
I had a little problem with wireless when installing ubuntustudio on Feisty, that may well be a FAQ:

ubuntustudio package installed the new low-latency kernel, but didn't install the restricted-modules built for it... So my D-Link acx111 based wireless card was not working any more.

See [here]("http://ubuntuforums.org/showthread.php?t=488463")

hope this helps... :-)

---

