---
title: "Which Ubuntu do you think will work best with my system specs?"
date: 2008-01-29
forum: Absolute Beginner Talk
---

### Post by dinonet on 2008-01-29
Hi guys, I have a fit-pc which is a cool little box and wanted to install one of the ubuntus. Would Xubuntu be the lightest or do you think I would be ok to try Ubuntu. I'm not sure how Gnome performs compared to KDE and Xcfe. Any info would be greatly appreciated! Here are my specs.

CPU: AMD Geode LX800 500MHz     
Chipset: AMD CS5536
Display: Integrated Geode LX display controller up to 1920x1440  
Memory: 256MB DDR 333MHz soldered on-board
Hard disk: 2.5” IDE 40GB
Ports:
 2 x RJ45 Ethernet ports 100Mbps
 2 x USB 2.0 HiSpeed 480Mbps
 RJ11 RS-232 (cable supplied)
 VGA DB15
 Stereo line-out audio (headphones)
 Stereo line-in audio / Mic

---

### Post by bumanie on 2008-01-29
i would suggest you use xubuntu. With those specs. I would also suggest you burn an alternate cd and not try to use the live cd when installing.

---

### Post by jordanmthomas on 2008-01-29
In my experience, xfce isn't really as light as everyone claims and for me runs at about the same speed as gnome.
You could run any of the desktops with that, but it would probably be slow and uncomfortable.  Personally, I'd use openbox or something similar.

If you use Ubuntu on that machine, you'll probably want to put some time into researching how to speed Ubuntu up.  Ubuntu really isn't the fastest distro out there.

---

### Post by aysiu on 2008-01-29
500 MHz processor with 256 MB of RAM? I'd go with Xubuntu or Fluxbuntu.

---

### Post by drusepth on 2008-01-29
With those specs, I'd recomment Fluxbuntu as well.

---

### Post by jrusso2 on 2008-01-29
I agree that XFCE does not seem much faster then Gnome.  If you can bring your memory up to 512 mb I would suggest that as memory is very inexpensive right now.

If not then I would suggest running Xubuntu or Linux Mint with Icewm or Flux depending on your taste as these are truly light weight environments.

I have also heard good things about PCLinuxOS's light weight version and Mephis light weight versions which i can't seem to recall their names atm.

---

### Post by dinonet on 2008-01-29
Thanks guys. I never even heard of Fluxbuntu. I guess if I want a nice real light option I should try one of your suggestions.

---

### Post by dinonet on 2008-01-29
Do you think Fluxbuntu  can run a light web server and some other things like ftp server, samba, etc?

---

### Post by jordanmthomas on 2008-01-29
It certainly can, it's no different than it would be with Ubuntu.

---

### Post by barts2108 on 2008-06-24
@dinonet

Did you get the geode based PC running ? also with the screen ?

I have AMD LX-800 here
chipset CS5536 with integrated LX800 video interface.
1 GB Ram 

I try intstall Ubuntu Hardy (8.04 LTS) but I cannot get the display to work on higher resolution than 800x600 and I need
1024x768.

Any thoughts ?

---

### Post by citizenchris099 on 2008-06-26
A couple ideas for those system specs all of which involve in one way Fluxbox or or Window Maker

[http://en.wikipedia.org/wiki/Window_maker](http://en.wikipedia.org/wiki/Window_maker)

[http://en.wikipedia.org/wiki/Fluxbox](http://en.wikipedia.org/wiki/Fluxbox)

depending on how much configuring you want to put into the set up you can either go w/a distro that already has fluxbox as the default window manager like Fluxbuntu or Linux Mint w/Fluxbox. Or you could take a regular ubuntu distro (neither of the previous two are officialy supported by Canonical Ltd) and install Fluxbox via synaptic. The former method would require a bit more set up on your part. Its not hard at all..here is a great walk through if you are starting from Ubuntu. Note that the following walk through is for Yellow Dog Linux (a Red Hat/Fedora Variant for PPC) but much of what it discusses applies to any Fluxbox set up.

[http://www.yellowdog-board.com/viewtopic.php?t=3546](http://www.yellowdog-board.com/viewtopic.php?t=3546)

Window Maker is a great one as well though not as light weight as Fluxbox. And what the previous posts have claimed about Xfce not being all that lightweight...well I have to say is for the most part true. Where it gets this rep as a light weight environ I dont know. I use Xfce because I dig it and am familiar w/it.

---

### Post by nnamdi on 2008-06-26
like wise i recommend xubuntu cos it is for low system configuration

---

### Post by barts2108 on 2008-06-26
Ubunutu 8.04 as well as 7.04 are able to run good on my system. However I want the geode video driver to be used as I need to rotate my screen 90 degrees.

The big bottleneck for such things is that the drivers I can find need kernel compilation. Not that I am afraid to do that, but it would be easier to have a pre compiled one in a installable package so that I do not need to alter multiple files by hand.

Anyone know a geode video driver (installation package) for Ubuntu 7.04 Generic ?

Reason I use 7.04 is that I have a touchpanel driver that is for 7.04

---

