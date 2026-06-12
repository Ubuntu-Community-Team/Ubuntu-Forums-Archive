---
title: "iBook G4 - Ubuntu Won't Install - Blank Screen"
date: 2008-01-16
forum: Apple PPC Users
---

### Post by Wizzel on 2008-01-16
I am trying to install the 7.10 PPC Ubuntu on my girlfriend's iBook G4. I hold down 'c' when the computer starts up and it finds the installation but soon after, the screen goes black and the CD stops spinning (i can hear it). Anyone have any suggestions?

---

### Post by ditsch on 2008-01-16
The 7.10 CD caused weird behaviour on my iBook while the 7.04 worked. I remember to have read something about a kernel module bug in Gutsy preventing to boot from Live CD (PPC), but I cannot find it any more. :( 

The solution for me was to install 7.04 from CD and upgrade it to 7.10 afterwards.

---

### Post by Wizzel on 2008-01-16
Thank you...I will try that. Is the upgrade burned onto a CD or downloaded and run itself?

---

### Post by Whiffle on 2008-01-16
It can be done either way.  Apt-get, the package manager, can take care of it once you get feisty running.

---

### Post by prematurebaby on 2008-01-16
7.10 works fine for me and i have an iMac g4 running it on virtual PC. so you shouldn't need to do it that way. The installation is pretty much straight forward. Unless you're saving over the Mac Operating system, but that would be stupid. Linux is good but not that good lol.

---

### Post by Wizzel on 2008-01-16
Well I hate to say it but I have no plans to dual boot her computer. I am going to wipe Mac OS and just install Ubuntu. I made the switch from Windows XP a month ago and haven't looked back. Mac OS is definitely stable, but extremely limited and I think quite boring. Also, it runs very slow on her iBook G4. She apparently upgraded to the newer OS, the one before the latest one. Her parents didn't take into account that given a jump in operating systems, the requirements to run them also get higher :).

I threw an extra 512mb of RAM in the machine bringing it to over 700 and I am going to basically redo her Mac with alternative software. Amarok or Banshee replacing iTunes (I know about DRM :)) and other things. Don't get me wrong, I love Windows XP and Mac OS, but I think Linux kills them all.

I went with installing 7.04 and that worked. Thanks for the suggestion. I know some of you might not understand why I do this, but about 20% of it is for her, and the other 80% is for me. She is very picky. We were looking at distros and she was pointing to the pretty ones (typical) which included DreamLinux and PCLinuxOS. I told her "yeah" "yeah." And here I am installing Ubuntu :). This is a challenge for me and it is all very fun. I want to become an active member of the community as everyone seems to enjoy helping each other.

Thanks again for the suggestion. Any other suggestions would be great for installing on a Mac iBook G4. I did my research and found a bunch of guides with helpful stuff but if you have something to add to the party, feel free.

-Wizzel

---

### Post by Wizzel on 2008-01-17
Well I think I found a deal breaker here. I can't seem to find any support for Flash players for PPC hardware. I have googled it and it has numerous other options. My question is, do any of them work? If not, it looks like I am at the end of the road and will have to reinstall MacOS. She needs the YouTube. :(

---

### Post by prematurebaby on 2008-01-17
You still probably should've not put ubuntu over mac because mine is 700 mb ram and it runs both OS's just fine. mine is also running tiger too. i dont see how you think mac is boring either, because mac is the best operating system out there. im not a big fan of windows but it comes in second. then linux. then other unknown operating systems. so linux is just a fun alternative. plus mac has alot of unix stuff too. so dont ever save over an operating system except windows, because that operating system can actually die on ur computer pretty much =):lolflag: so take that into consideration.
- prematurebaby

---

### Post by ditsch on 2008-01-17
> **Wizzel said:**
> Well I think I found a deal breaker here. I can't seem to find any support for Flash players for PPC hardware. I have googled it and it has numerous other options. My question is, do any of them work? If not, it looks like I am at the end of the road and will have to reinstall MacOS. She needs the YouTube. :(

If you have upgraded to Gutsy, take a look at the Gnash plugin. Of course, it is not as good as Adobe Flash but it is quite usable in Ubuntu 7.10.

---

### Post by Wizzel on 2008-01-17
> **ditsch said:**
> If you have upgraded to Gutsy, take a look at the Gnash plugin. Of course, it is not as good as Adobe Flash but it is quite usable in Ubuntu 7.10.

Thanks again man. I will do that.

---

### Post by stmiller on 2008-01-17
Yeah Gnash is also in Feisty backports if you enable that in the Add/Remove preferences. It plays youtube and some other flash things, though taxes your CPU a bit.

---

### Post by Wizzel on 2008-01-18
Alright. Back to the drawing board but far from considering giving up. I upgraded to 7.10 without much trouble from the alternate CD. I lost my ethernet connection ability and wireless still does not work. I followed the guide. It told me that no files had been changes, updated or anything. I enabled the restricted driver, transferred the wl_apsta.o file over from my main computer and it said the driver was enabled. Still not internet.

Any ideas on how to fix any or both of my internets. Thanks again to everyone for helping. This is awesome.

---

### Post by Wizzel on 2008-01-18
Alright. All internet is working. Computer is running at 99% of its usage, which is weird because nothing is open. Does wireless service have something to do with this?

Also, I am looking now for the best alternatives to certain programs.

I am thinking instead of iTunes I can do Amarok or Banshee. Which is better?

For iPhoto, I can do Picasa, or something else. Any suggestions?

Thanks again guys.

The fan seems to be staying on 100% of the time. I am not sure why this is. If it turns out Ubuntu is too demanding for this laptop, I might install another lighter PPC distro. Anyone have any idea which one would be best?

---

### Post by ditsch on 2008-01-18
I assume the desktop effects are consuming much of the power, but you can be sure if you examine the running processes. If it turns out this is the case, disable them. 

As for program alternatives, I always suggest to try several programs to find the best suit for your needs.

---

### Post by oswaldkelso on 2008-01-18
> **Wizzel said:**
> Well I think I found a deal breaker here. I can't seem to find any support for Flash players for PPC hardware. I have googled it and it has numerous other options. My question is, do any of them work? If not, it looks like I am at the end of the road and will have to reinstall MacOS. She needs the YouTube. :(

if its only youtube and not flash games install miro or clive and mplayer they work great

add the necessary repositories to your sources.list (/etc/apt/sources.list)

open a terminal as root
# apt-get install clive mplayer

open a terminal as normal user

to get the video type clive youtube_video_address

e.g.

g5@debian1333:~$ clive [http://www.youtube.com/watch?v=QZSIkH-rIVo](http://www.youtube.com/watch?v=QZSIkH-rIVo)

..........................................................................

to play type mplayer and video name ( start typing and press tab to auto complete)

............................................................................
e.g.

g5@debian1333:~$ mplayer 3ddeskondebian.flv

---

### Post by stream303 on 2008-01-18
> **Wizzel said:**
> Alright. All internet is working. Computer is running at 99% of its usage, which is weird because nothing is open. Does wireless service have something to do with this?
...
...
The fan seems to be staying on 100% of the time. I am not sure why this is. If it turns out Ubuntu is too demanding for this laptop, I might install another lighter PPC distro. Anyone have any idea which one would be best?

I had the same issues on my G4 iBook.

When I ran "top" in the terminal, I saw that Network Manager was sucking up 100% of the cpu.  I think it is what was causing my alternate-install to run so slowly at first.
[B]
*** UPDATE***
To safely stop or remove Network Manager, please read:[/B]

[https://help.ubuntu.com/community/WifiDocs/NetworkManager](https://help.ubuntu.com/community/WifiDocs/NetworkManager)

I did have to bring the ethernet interface back up manually once with
```
sudo ifup eth1
```

I also had to restart the POWERNOWD daemon.  I opened up Services in system prefs, and temporarily unchecked the CPU Frequency Manager (powernowd).  I then restarted powernowd by checking it again and now the system seems back to normal.  I did have to reboot with powernowd disabled, and after the reboot re-enabled it and that seemed to take.  Not sure if you'll have to do this.  At least the iBook seems to be running normally again.

---

### Post by Wizzel on 2008-01-19
Awesome. I will try that network thing tonight. I still need wireless to work, which I hope will. I will follow your instructions. Also, another issues I have found.

1.Firefox seems to crash randomly. No idea why. Some specific pages, probably containing weird flash, java or something else.

2. I got Gnash installed but when I visit YouTube, it tells me I need to find a suitable codec. The box seems to load and look like its about to display the video. Any ideas?

---

### Post by stream303 on 2008-01-20
I just got educated on how to safely remove / stop Network Manager.  Just removing it with Synaptic or dpkg is the wrong way to do it.  Please read:

[https://help.ubuntu.com/community/WifiDocs/NetworkManager](https://help.ubuntu.com/community/WifiDocs/NetworkManager)

---

