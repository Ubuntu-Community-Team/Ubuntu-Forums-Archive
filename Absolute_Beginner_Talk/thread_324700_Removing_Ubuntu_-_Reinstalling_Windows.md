---
title: "Removing Ubuntu - Reinstalling Windows"
date: 2006-12-24
forum: Absolute Beginner Talk
---

### Post by jrstubs on 2006-12-24
Ive recently installed ubuntu on this computer (actually yesterday). After playing around with it for hours I decided I should try to reinstall windows xp and put Ubuntu on my other older computer.
   The whole reason for this; My windows xp professional was totally messed up beyond belief. It hadnt been reinstalled for 3  years or so, and defrag and disk cleanup didnt do any good. No virus' either. Then I backed up all my files, burned my ubuntu boot disk, then at the installation I deleted all the partitions on both of my hard drives.
   I tried to play some of my computer games in wine, and it didnt work very good at all and I dont feel like messing around with stuff for hourshour, and I plan on getting a bunch of new PC games and im not too sure if ubuntu is the best operating system for gaming.

When I booted up my windows xp professional cd it was all good, I deleted all the partitions with NATSF (quick) , I setup everything right when it asked installation questions. Then when it was done installing and rebooted it was totally screwed up. When I opened windows and dragged them around it was like laggy, I dont know how to explain it, the mouse moved fine but the window wouldnt move smoothly, like it would disappear then appear someplace where a dragged it a second later.

I reinstalled it again but using the NATSF format instaed of NATSF(quick). it took about 20 minutes, then this screen appeared that said there were problems and it had to shutdown windows to prevent damage to the compter. I installed it again with the same option, and it had the same message appear. So I reinstalled Ubuntu last night before I went to bed, and now im here asking for help with my problem.

btw, my brother had the same problem when he had tried to reinstall windows on one of his computers after installing fedora core 5. And im not too sure if its NATSF, I just think thats how the format thing is spelled.

---

### Post by Lord Illidan on 2006-12-24
>  When I booted up my windows xp professional cd it was all good, I deleted all the partitions with NATSF (quick) , I setup everything right when it asked installation questions. Then when it was done installing and rebooted it was totally screwed up. When I opened windows and dragged them around it was like laggy, I dont know how to explain it, the mouse moved fine but the window wouldnt move smoothly, like it would disappear then appear someplace where a dragged it a second later.

It is called NTFS.

Also, it sounds like a problem with drivers. All you needed to do was install the graphics drivers. You could have an NVIDIA 6800 and it lags, without drivers Windows has to use VESA, which is slow.

I would also suggest dualbooting.

---

### Post by xpod on 2006-12-24
Once you`ve re-installed your windows you`ll probably need to install  drivers for your graphics card and mabey a few other things too...

A fresh windows install can be more of a pain than any ubuntu install believe it or not.

Go to device manager in windows...if you can, and that will give you a idea of whats missing.
You do know what "device manager" is dont you??

Theres good app`s like "everest" and "belarc" for windows that do a good job of listing all your hardware details as well but device manager is the place to start to get an idea of whats missing
i think.

You should have took backup`s of all your windows drivers first if you did`nt already have them somewhere:D

---

### Post by jrstubs on 2006-12-24
Ah.....I know what device manager is, but I forgot the part how my internet isnt working either on windows, I have to deal with all this stuff, I have a westell router connected to my computer and it wont pick it up for some reason. Im not sure but I'll figure it out hopefully.
And yes, Ubuntu is ALOT easier to install, everything was configured, my printer, my internet was up without doing anything, took only 10 minutes to install on my computer. If only windows was that simple.

---

### Post by xpod on 2006-12-24
> Ah.....I know what device manager is, but I forgot the part how my internet isnt working either on windows, I have to deal with all this stuff, I have a westell router connected to my computer and it wont pick it up for some reason. Im not sure but I'll figure it out hopefully.
And yes, Ubuntu is ALOT easier to install, everything was configured, my printer, my internet was up without doing anything, took only 10 minutes to install on my computer. If only windows was that simple.

Im sorry i asked about dm but you never know:D 
Im pretty new to pc`s full stop  and didn`t know these things myself not so long ago but i`ve also seen an alleged windows expert asking where "defragment" was on here a couple of weeks ago ago so you never sure who knows what??

Anyway,I dont know tooo much myself but i know you need drivers m8.
Dont you have no driver recovery cd`s or something you might have got with the pc?
If not it`s not too hard to get them as long as you got some kinda internet access.

I dont use a router but i imagime again you`ll be needing to install it`s drivers too..

Good luck either way m8...i can only tell you the basics but im sure somebody will give you more detailed advice if the need arises.

Im off to build 5 bloody bikes](*,)

---

### Post by PurplePenguin on 2006-12-24
If you manage to get your internet connection working, you'll need to search for the latest versions of all the drivers you'll need (video card, maybe even motherboard drivers if you've got built-in lan, sound or video, anything else that has its own add-in card, printer, scanner, etc).

If you can't get onto the net, hopefully you kept all of your driver discs that came with the computer.  They'll be old versions, but you can update them later.

The router should be easy to install.  Any disc that I've ever seen with a router doesn't actually have drivers on it, it just has a utility that helps you with the correct settings.  You'll probably have a web-based address that you can go to in order to make any router setting changes.

---

### Post by Zzl1xndd on 2006-12-24
more than likely your nic card drivers are also missing, thus it wouldnt connect to the net. if this is the case you'll need to download them. is it an inboard nic or a PCI card?

---

