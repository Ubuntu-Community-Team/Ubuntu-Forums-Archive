---
title: "ubuntu equivalent of some windows  software"
date: 2007-12-18
forum: Absolute Beginner Talk
---

### Post by ariel bebbe on 2007-12-18
what is  and where to download the equivalent of this windows software :

- netsim or packet tracer academy for network simulation

- Do i have to clean the registry someone talk about orphans packet what is that ?

- nokia pc suite for nokia mobile phone 

- ramboost optimizer 

- tweak to make xp system fast and responsive 

- everest home to control hdd and processor heat

- transparency effect like bricopack vista inspirat

---

### Post by Presto123 on 2007-12-18
I have had some problems with the Nokia Suite. But, if you want to try it, get Wine and use that to install the disk.

It just never worked for me, but, I don't think Wine currently supports it. 

Really, you don't need the tweaks to make Ubuntu fast (IMHO) because it is already MUCH faster than XP and ESPECIALLY Vista.

---

### Post by PetePete on 2007-12-18
- netsim or packet tracer academy for network simulation
 not sure what netsim is...

- Do i have to clean the registry someone talk about orphans packet what is that ?
ubuntu does not have a registry, this is a windows concept... so no.

- nokia pc suite for nokia mobile phone
not that i know of, you might need to use virtualbox or similar virtualisation to run a copy of windows within ubuntu

- ramboost optimizer
ubuntu is already efficient with memory..
- tweak to make xp system fast and responsive
you can look on these forums to make ubuntu more 'tweaked' if you require, but generally this isn't really needed.
- everest home to control hdd and processor heat
 can't control the heat, but you can monitor it with various programs... for kde I use ktemperature but as you prob use GNOME you'll want something else.
- transparency effect like bricopack vista inspirat
compiz , use your package manager to install it, lots of desktop effects

---

### Post by Niniel on 2007-12-18
> **Presto123 said:**
> Really, you don't need the tweaks to make Ubuntu fast (IMHO) because it is already MUCH faster than XP and ESPECIALLY Vista.

As far as I am concerned, that is nothing but a myth, or at the very least, grossly exaggerated. Ubuntu doesn't feel faster than XP to me, so even if you could show that by some measurement it *is*, say 10 %, faster, it just isn't very noticeable. Maybe you just need to switch off the XP effects, those give some appearance of slowness. 
Ubuntu does start up and shut down a lot faster though, and what a relief that is.

---

### Post by Jammy4041 on 2007-12-18
I reckon Ubuntu is much faster. It has a lot less stuff on it- it's a leaner meaner machine!

---

### Post by stchman on 2007-12-18
> **Niniel said:**
> As far as I am concerned, that is nothing but a myth, or at the very least, grossly exaggerated. Ubuntu doesn't feel faster than XP to me, so even if you could show that by some measurement it *is*, say 10 %, faster, it just isn't very noticeable. Maybe you just need to switch off the XP effects, those give some appearance of slowness. 
Ubuntu does start up and shut down a lot faster though, and what a relief that is.

As far as XP and Ubuntu speed.  I feel that a fresh install of XP is faster loading than Ubuntu.  That changes dramatically over time.  While Ubuntu remains the same XP gets clogged and corrupted.  You would then need to reinstall XP to get that new fresh feeling.

---

### Post by aliencam on 2007-12-18
orphaned packages do exist in ubuntu, it happens when you install a program and it in turn installs a bunch of stuff for it to work, but when you uninstall that program it doesn't uninstall all of those other little things.  there are 3 programs in the repositories (add/remove) that come up on a search for "orphaned" and i personally have used both "remove orphaned packages" and "kleansweep"  but they don't do much on a new install.  

by "- tweak to make xp system fast and responsive " do you mean how to make WIndows XP faster?? if so, then right-clicking on "my computer" >properties > advanced > graphics or display or something like that lets you make xp faster by removing graphical extras that aren't needed. 

 to make Ubnutu faster though, there are tons of things you can do. see [http://lifehacker.com/software/feature/slim-down-and-speed-up-linux-333798.php](http://lifehacker.com/software/feature/slim-down-and-speed-up-linux-333798.php)  make sure you read the comments on that page also. 
and just look around (search the forums, google, etc).  there is no "standard procedure" to making ubuntu faster, and most computers don't need to make it faster as it usually is fast enough by itself.  if you are having problems I would suggest disabling desktop effects, (right-click on desktop> change desktop background> visual effects or system>preferences>appearence>visual effects) as compiz effects can definitely slow down your computer. 

i don't know about CONTROLLING hdd and processor heat, but you can enable CPU processor throttling, and find programs that control fan speed.  those are mostly based on laptops though.  there is an "xsensors" that i see when searching for "temp" in add/remove that says it can monitor your temperatures and fan speeds, but i don't know about controlling fan speeds (I use a program called tp-fan, which is for thinkpad laptops only I believe)

for "transparency effects" i dunno what your windows program is, but that is gained by enabling compiz-fusion  you need to go to system>preferences>appearance>visual effects  and then to change the settings oyu have to get the compiz settings manager, which is called "Advanced Desktop Effects Settings"  that you can find in the Add/Remove programs search.

---

### Post by Jerry N on 2007-12-18
> **Jammy4041 said:**
> I reckon Ubuntu is much faster. It has a lot less stuff on it- it's a leaner meaner machine!

I don't find Ubuntu or any of the other several Linux distributions I have tried to be perceptibly faster than XP and I don't agree that it "..has a lot less stuff on it..".  I do run my XP with effects like exploding windows disabled and without wallpaper.  I also find that Ubuntu runs much better on my Athlon 2400+ machine with none of the effects enabled.  I tried Compiz-Fusion and view it as a production limiting resource hog.  (I am now donning my flame retarding Nomex suit:rolleyes:)

Jerry

---

### Post by aliencam on 2007-12-18
> **Jerry N said:**
> I don't find Ubuntu or any of the other several Linux distributions I have tried to be perceptibly faster than XP and I don't agree that it "..has a lot less stuff on it..".  I do run my XP with effects like exploding windows disabled and without wallpaper.  I also find that Ubuntu runs much better on my Athlon 2400+ machine with none of the effects enabled.  I tried Compiz-Fusion and view it as a production limiting resource hog.  (I am now donning my flame retarding Nomex suit:rolleyes:)

Jerry

lol I have just the opposite experience, as do most ubuntu users...  i guess it depends on how compatable ubuntu is with your hardware.  I had (on my desktop) 3GB of memory and an athlon 64 3200+ overclocked quite a bit, and i'd say ubuntu runs at least twice as fast as XP pro on that computer.  my new laptop (thinkpad x61 tablet core2 duo 1.8ghz 3 gb memory) runs ubuntu ... i want to say 100 times faster (slight exaggeration)  than it runs vista business.   i've only seen 1 computer that ubuntu ran slower than XP on  that it had 128MB of memory and a celleron from the pentium 4 era... 

but for slower systems, people usually use a different version of ubuntu (xubuntu or the alternative install cd)

i seriously think that swap space is the key in ubuntu speed.  I usually give ubuntu 5-10GB of swap space (i have more than enough hard drive space to do this) but when i give XP that much, it doesn't even use the swap ("virtual memory" in xp).  not saying that ubuntu can fully utilize 10 GB of it, but it can better than XP

---

### Post by bodhi.zazen on 2007-12-18
[http://linuxappfinder.com/windows](http://linuxappfinder.com/windows)

---

### Post by aliencam on 2007-12-18
you also may want to look at 
[https://help.ubuntu.com/community/UserDocumentation](https://help.ubuntu.com/community/UserDocumentation)

specifically: 
[https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows](https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows)

---

