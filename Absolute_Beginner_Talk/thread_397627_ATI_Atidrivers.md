---
title: "ATI Atidrivers"
date: 2007-03-30
forum: Absolute Beginner Talk
---

### Post by hizdudeness on 2007-03-30
O.K. I've ruined 3 installs of ubuntu trying to get ATI drivers onto my computer. I've googled around with out much success. I got the latest driver from ATI installed using the .run file, on their site, but my computer ran like junk, and the control cener didnt work. I've tried several different tutorials and still end up in the same place either the install doesn't work and I have to hunt down my backup .conf file and recover, or it ends up not working and I end up with tons of drivers littered on my computer. 

 Since I'm on install number 4 I figure its about time to get some help. I've currently reinstalled my OS and ran updates, but I haven't proceeded past this for fear of jacking something up for lucky number 4. I would be extremely grateful for some direction. 


I've installed the ubuntu 6.10 Edgy EFT
I have a 3.3 ghz pentium D 
2 gigs of DDR2
ATI Radeon x1600 pro 


I got this "envy" install to work on another computer for my nVidia card, but that computer is at work. This tutorial crashes on my ATI
[http://discoverx.wordpress.com/2007/03/12/a-fast-way-to-install-ati-and-nvidia-drivers-in-ubuntu/](http://discoverx.wordpress.com/2007/03/12/a-fast-way-to-install-ati-and-nvidia-drivers-in-ubuntu/)

Let me know if I need to clarify things, or better explain myself. I'm new to linux so if it involves the terminal you can assume that I don't know the specific commands. 


Chris

---

### Post by TonKi on 2007-03-30
I would give envy another try and use the up-to-date version, just follow the faq and guide on the page and it should work fine.
Its the same as installing the drivers by hand, you just need to type less ;)

[http://albertomilone.com/nvidia_scripts1.html]("http://albertomilone.com/nvidia_scripts1.html")

---

### Post by hizdudeness on 2007-03-30
There isn't a tutorial for ATI specifically. The only reason that I even found it was because I used it with a Nvidia card and noticed ATI was an option. It loads and installs, but it crashes when I hit crl-alt-F1 or backspace and I cant complete the install. 

I'm going through the step by step instructions from this thread 
[http://ubuntuforums.org/showthread.php?t=305665&highlight=ATI+How+To+Step+by](http://ubuntuforums.org/showthread.php?t=305665&highlight=ATI+How+To+Step+by)

but when I get to step 4 and type 
[PHP]fakeroot sh ./ati-driver-installer-8.31.5-x86.x86_64.run --buildpkg Ubuntu/edgy[/PHP]

It looks like its going to work and then prints this:

[PHP]Generating package: Ubuntu/edgy
./packages/Ubuntu/ati-packager.sh: line 56: dpkg-architecture: command not found
Error: unsupported architecture: 
Removing temporary directory: fglrx-install[/PHP]

---

### Post by kittyhawk63 on 2007-03-30
I've learned to install fglrx and "not" to install updates. That is the only thing that keeps my ATI card working.
kh

Edit: I have found that the updates had nothing to do with my video problem.

---

### Post by spacedogg on 2007-03-31
A little background...

I'm taking a Linux class and they suggested that we use Ubuntu. I installed it on a second HDD in my main computer. My computer has an ATI X850XT PE, Athlon64 4000+, MSI NEO4 Platnium mobo, 2 gigs of ram, X-Fi music extreme (which has no drivers at this time), and an ATI TV Wonder 650 (which also has no drivers). My monitor is a Dell 2005FPW which has a native resolution of 1680 x 1050.

When I loaded up Kubuntu I couldn't select anything higher than 1024 x 768, so naturally I tried to load up the fglrx drivers. These hosed up my system about 4 times. The fifth time I decided I'd do some serious research and see what I could find. I got them to work once, but when I could not get direct rendering to work (from my understanding, direct rendering needs to be enabled to allow the video card to process 3D textures) I decided to try over again. 

The current status...

I found [this wiki]("http://wiki.cchtml.com/index.php/Ubuntu") and followed the manual instructions to install the newest set of drivers released by ATI on 28 March. My control panel actually works, but thre's nothing there that I really need to use. It doesn't have anything to do with changing resolutions though, you have to do that through the aticonfig command in a shell window. 

I'm very new to linux and have been lucky to get this stuff working as well as I have. I'd follow the wiki, making sure that you have all of the packages needed installed before you attempt to load the drivers.

---

### Post by jvc26 on 2007-03-31
I got my 9800 pro (yes a different model than yours, but the guide has a list of supported/unsupported ati cards) to work suing this guide. flgrx on the whole is rubbish as ATI really havent pulled their fingers out to get a decent linux support sorted. I also had no luck with envy to be fair so used this instead:
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
Il

---

