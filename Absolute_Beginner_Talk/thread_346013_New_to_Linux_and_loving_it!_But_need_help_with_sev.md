---
title: "New to Linux and loving it! But need help with several issues........"
date: 2007-01-25
forum: Absolute Beginner Talk
---

### Post by M3-Linux on 2007-01-25
First of all let me introduce myself: 

I'm Sina. I made a HUGE switch from WinBLOWS and decided to do away with it entirely (if I can). Got sick to death of the crashes, security issues, viruses, POOR memory allocations, spyware, and the list goes on and on and on. I tried SuSe and absolutely loved that. The interface was eye-catching and it was an AMAZING OS with all the multimedia stuff it had out of the box, so to speak. Had several issues with sound, video and sometimes resources and switched to Ubuntu to see if that helped. The issues grew bigger from there. 

Let me give you guys a list of all the issues I'm having with Ubuntu right now: 

1) I've got a FW400 External 500GB Hard Drive that I have a lot of great files on and I can't get Ubuntu to even see it. It's supposed to be under /dev/sda1 but I can't seem to get Ubuntu to see it. Funny thing is that it worked beautifully the first few times. I'd click on the drive, it was mounted automatically, and I'd have access to everything on it. Second time I'd click on it half the stuff would disappear, and eventually to nothing. It seemed really weird. But it gets worse........I reboot the machine and while it sees the drive, I can't seem to mount it anymore or get access to it at all. Now everytime I turn on my machine, it doesn't even see it anymore. I went to the terminal and typed in the fstab command and it wasn't even there. It's connected, plugged in and everything. But it's almost as if nothing exists. Plus Ubuntu doesn't seem to have a Root account so how do I set one up and have administrator privilages? 

2) My internet browsers (firefox, epiphany, and mozilla) while VERY fast unexpectedly quit on me sometimes. I click a link and they quit out of nowhere. Don't know what the issue is, but hopefully it can be fixed. 

3) I'm getting a TON of annoyances: My Num Lock, Caps Lock and Scroll Lock are constantly flashing back and forth for some reason. Sometimes as I type, I get repeated letters beyond my controooooooooooooooooooooooooool. Like I'll hit O for example and it keeps going. And it happens at the most random keys as well. Space, Backspace, certain letters I type go on and on until I hit backspace and then it'll delete everything I just typed. VERY strange. 

4) I have a high-end M-Audio Delta 1010LT Pro Audio PCI sound card and while I have the drivers for it, the ONLY program that seems to work with it is Beep Media Player which plays my MP3 files and whatnot. All the other players seem to play only the left channel and not both the left and right channels. I have the Audacity audio editor software and I can't seem to get ANY sound out of that. Playback or recording to edit any MP3 or Wave files that I have. 

5) I need to be able to play M$ WinBLOWS WMV files on Ubuntu. How do I get the proper codecs for these file types. WMA files would be nice, too. 

6) I have a Webcam and I have NO idea where to get drivers for it to work with Gaim, or some other IM program. 

7) And how the heck do I "unzip" and convert Zip, DEB, tar and rpm files to install programs that I download. 

8 ) I'm noticing VERY slow speeds sometimes on Ubuntu. Like it'll take a while to get program to start. 

9) I'm also experiencing non-responsive programs that are running. How do I fix this? 

That's about it for now. Sorry if it seems like too much, but I'm having a LOT off issues that seem worse than Windows per se, because Windows is just plug and play, but it's WAY too prone to crashing and I'm just done with M$ and their WinCRAP software. haha. If you guys need more details please get at me. I wanna learn Linux to its full potential once everything is fixed.

---

### Post by atomic drizzle on 2007-01-25
about admin account. in ubuntu u can have an admin account, but u still have to use the sudo command so it seems pointless to even set it up 
about un ziping. once u unpack the program, cd into the dir that has the program, then type either ./nameofprogram or sudo make install. 
also if the program is in the repositories, you can type: sudo apt-get install nameofprogram. if you want to search the repositories for a program, type sudo apt-cache search *keyword*  
if you can apt-get it then it will be installed automaticaly.

---

### Post by RomeReactor on 2007-01-25
For windows codecs, make sure you have universe and multiverse repositories enabled (open Synaptic and click on "Settings", then "Repositories", and check all boxes); then search for:

```
w32codecs
```

For your Firefox issues, try launching it form a terminal. Just type:

```
firefox
```

When it crashes, look at the output it gives there and post it here.

---

### Post by deadgobby on 2007-01-25
> **M3-Linux said:**
> First of all let me introduce myself: 

I'm Sina. I made a HUGE switch from WinBLOWS and decided to do away with it entirely (if I can). Got sick to death of the crashes, security issues, viruses, POOR memory allocations, spyware, and the list goes on and on and on. I tried SuSe and absolutely loved that. The interface was eye-catching and it was an AMAZING OS with all the multimedia stuff it had out of the box, so to speak. Had several issues with sound, video and sometimes resources and switched to Ubuntu to see if that helped. The issues grew bigger from there. 

Let me give you guys a list of all the issues I'm having with Ubuntu right now: 

1) I've got a FW400 External 500GB Hard Drive that I have a lot of great files on and I can't get Ubuntu to even see it. It's supposed to be under /dev/sda1 but I can't seem to get Ubuntu to see it. Funny thing is that it worked beautifully the first few times. I'd click on the drive, it was mounted automatically, and I'd have access to everything on it. Second time I'd click on it half the stuff would disappear, and eventually to nothing. It seemed really weird. But it gets worse........I reboot the machine and while it sees the drive, I can't seem to mount it anymore or get access to it at all. Now everytime I turn on my machine, it doesn't even see it anymore. I went to the terminal and typed in the fstab command and it wasn't even there. It's connected, plugged in and everything. But it's almost as if nothing exists. Plus Ubuntu doesn't seem to have a Root account so how do I set one up and have administrator privilages? 

2) My internet browsers (firefox, epiphany, and mozilla) while VERY fast unexpectedly quit on me sometimes. I click a link and they quit out of nowhere. Don't know what the issue is, but hopefully it can be fixed. 

3) I'm getting a TON of annoyances: My Num Lock, Caps Lock and Scroll Lock are constantly flashing back and forth for some reason. Sometimes as I type, I get repeated letters beyond my controooooooooooooooooooooooooool. Like I'll hit O for example and it keeps going. And it happens at the most random keys as well. Space, Backspace, certain letters I type go on and on until I hit backspace and then it'll delete everything I just typed. VERY strange. 

4) I have a high-end M-Audio Delta 1010LT Pro Audio PCI sound card and while I have the drivers for it, the ONLY program that seems to work with it is Beep Media Player which plays my MP3 files and whatnot. All the other players seem to play only the left channel and not both the left and right channels. I have the Audacity audio editor software and I can't seem to get ANY sound out of that. Playback or recording to edit any MP3 or Wave files that I have. 

5) I need to be able to play M$ WinBLOWS WMV files on Ubuntu. How do I get the proper codecs for these file types. WMA files would be nice, too. 

6) I have a Webcam and I have NO idea where to get drivers for it to work with Gaim, or some other IM program. 

7) And how the heck do I "unzip" and convert Zip, DEB, tar and rpm files to install programs that I download. 

8 ) I'm noticing VERY slow speeds sometimes on Ubuntu. Like it'll take a while to get program to start. 

9) I'm also experiencing non-responsive programs that are running. How do I fix this? 

That's about it for now. Sorry if it seems like too much, but I'm having a LOT off issues that seem worse than Windows per se, because Windows is just plug and play, but it's WAY too prone to crashing and I'm just done with M$ and their WinCRAP software. haha. If you guys need more details please get at me. I wanna learn Linux to its full potential once everything is fixed.

WOW you have a laundry list there. It would be a great help if you can post one problem at a time. 
Lets get your codecs working here. Codecs are restricted things that you can only install by your hands. That may help of the stuff you require.
There is Easy Ubutu
[http://easyubuntu.freecontrib.org/](http://easyubuntu.freecontrib.org/)
There is Automatix and please read before installing
[http://www.getautomatix.com/wiki/index.php?title=Installation](http://www.getautomatix.com/wiki/index.php?title=Installation)
Here is why stuff is restricted.
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
 How to install cool stuff from Synaptic.. Please check Synaptic before installing from Deb, RPM , or tar aka from source. 
Here is a little guide to help you get stuff installed like RPM and Tar
[http://psychocats.net/ubuntu/index](http://psychocats.net/ubuntu/index)
 OK Firefox is crashing. I know that problem and it can be a big pain in the butt. The reason why FF is crashing is caused by flashplayer. There is a couple if things to stop that bugger. One is to install flash blocker at
[http://flashblock.mozdev.org/](http://flashblock.mozdev.org/)
 Or you can move to FF 2.0 or install Flashplayer #9
[http://www.ubuntuforums.org/showthread.php?t=279990](http://www.ubuntuforums.org/showthread.php?t=279990) 
that one is for Flash #9
Here is for FF 2.0
[https://help.ubuntu.com/community/FirefoxNewVersion](https://help.ubuntu.com/community/FirefoxNewVersion)
 You will get to know a friend called Terminal here. If you recalled the times when to get stuff installed in DOS in the days. The terminal is all most the same thing. You have some some study to do.

---

### Post by Canis familiaris on 2007-01-25
> **M3-Linux said:**
> First of all let me introduce myself: 

3) I'm getting a TON of annoyances: My Num Lock, Caps Lock and Scroll Lock are constantly flashing back and forth for some reason. Sometimes as I type, I get repeated letters beyond my controooooooooooooooooooooooooool. Like I'll hit O for example and it keeps going. And it happens at the most random keys as well. Space, Backspace, certain letters I type go on and on until I hit backspace and then it'll delete everything I just typed. VERY strange. 


I also got the same problem sometime back. I reduced the shared VGA size in BIOS and this rectified the problem.

---

### Post by kevinatkins on 2007-01-25
That's quite a list! Looks a bit overwhelming, but I'll try and help you on a couple of the points. Before I do though, you mention a few stability issues. I've installed Ubuntu on probably half a dozen machines and it's been a model of good behaviour - I've found it very good overall on the stability front. As a Windows sys admin, apart from the appalling security problems, I've also found XP pretty good, too, to be fair (it's certainly light years ahead of Win 9x, ME, etc!). So I'm just wondering whether you might have a hardware issue somewhere.

Anyway, on to specifics; answers numbered as per your questions -

2) Firefox, Epiphany, Mozilla quitting when clicking on some links. I saw this myself once and traced it to the free / open-source flash plugin, which I found wasn't very good. If you've got the free flash / swf-dec plugin installed, bin it and grab the proper Adobe plugin, which is available in either universe or multiverse.

5) WMV / WMA codecs - as already suggested, you need the w32codecs package, available in universe / multiverse. Actually, the easiest way is to install Automatix and let that do the job for you. You'll be able to play most stuff except DRM encrypted content.

8) Slow speeds - this could be network settings, of all things. Please could you post back the contents of your /etc/hosts file.

9) Non-responsive programs - you can add a little applet to your panel. Right click on panel and select the 'force quit' applet. Now when a program freezes, just click on 'force quit' and zap the offending window. Shouldn't be necessary very often!!

Hope this helps. If you find that answers aren't what you were expecting, it might be worth breaking problems into separate threads and expanding on the details for each issue - it gives us more to work with. Stick with Ubuntu - it's well worth it!

---

### Post by russo.mic on 2007-01-31
I feel like your still missing a detail,

I came from SuSE and had this same question, so I know where your comming from.  To setup a root account in Ubuntu, you type :

sudo passwd

It will then prompt you for your current account password, and then let you pick a new one.  from there, you either use sudo to start commands as root for the most part.  You still can type su from a terminal and log into a root account, but I find myself rarely doing so.  

I'm new to Ubuntu myself, and I'm finding it's well worth the learning curve.  while it can be a bit daunting at first, Most of the shortcommings I find are due more to my lack of knowlage than shortcommings with the OS itself.  I've tried other major distros in the last month, including SuSE 10.2, Fedora,  and Sabayon, and keep comming back to Ubuntu.  Nothing else runs as smooth on my laptop.  

Good luck!  Don't give up!
Russo

---

### Post by mrdeeno on 2007-01-31
concerning #1, check your external drive partition type. 

i had an external drive when i started playing with Linux, and had problems with it (sometimes it sees it, sometimes it doesn't, no write capability, etc.) and I always assumed it was fat32.

But alas, it was NTFS.  I remember formatting it when i was exclusively on Windows, but now I recall that Windows will only let you format NTFS if the drive is over a certain size...not to mention i never intended to go to Linux at that time, so it didn't matter that it was NTFS.

That was the problem I had, but after converting it to fat32, it automatically mounts whenever i plug it in and i can read/write with no problems.

---

