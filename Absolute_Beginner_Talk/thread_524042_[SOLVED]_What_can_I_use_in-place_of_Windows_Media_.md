---
title: "[SOLVED] What can I use in-place of Windows Media Player"
date: 2007-08-12
forum: Absolute Beginner Talk
---

### Post by WebSiteGuru on 2007-08-12
This probably had been asked before. I am a noob at Linux and need assistance.

I had tried to install Windows Media Player(WINE) and I cant get it to work with FireFox. So I can view the video file from the web. I had also tried MPlayer with 32codecs, etc and it is coming up with error.

I am currently scratching amy head and frustrated.


Need hep. PLZ!

---

### Post by misfitpierce on 2007-08-12
Install Automatix.. link to page in sig. Can download codecs and a media player all in one place. Songbird is a nice media player has iTunes feel and look but has nice plugins like shoutcast etc.

---

### Post by Kobalt on 2007-08-12
There are community supported [alternatives to Automatix]("http://ubuntuforums.org/showthread.php?t=519872") actually, it's just as easy and you don't need to rely on some third party software at least. 
You must be looking for the multimedia codecs instructions I guess. There is [a sticky]("http://ubuntuforums.org/showthread.php?t=413624") about it at the top of the Absolute Beginner section.
If the built-in audio player of Ubuntu, Rhythmbox, doesn't suit you I'd recommend trying Exaile! or amaroK.

---

### Post by WebSiteGuru on 2007-08-12
Trying automatix now. I can not find the add/remove for the program in sticky.

---

### Post by Arthur Archnix on 2007-08-12
People aren't here trying to make your life more difficult than it has to be. Ubuntu has looked at Automatix and found it to be a poorly written program that can actually do damage to your system. So you can trust some random forum person who says it works fine for them, or you can trust the forum admins and ubuntu developers who advise you not to use it.

---

### Post by WebSiteGuru on 2007-08-13
> **Arthur Archnix said:**
> People aren't here trying to make your life more difficult than it has to be. Ubuntu has looked at Automatix and found it to be a poorly written program that can actually do damage to your system. So you can trust some random forum person who says it works fine for them, or you can trust the forum admins and ubuntu developers who advise you not to use it.

Forgive me for being a newbies (noob). Being New, I dont know better. Automatix had been removed from my system. I never said that they did. I am just trying to get my ordeal solve.

And from what I understand Kobolt is not displayiong his/her rank as forums admin. If you wish to RAM me for not knowing better and trying to fix my problem. It is your choice.

I ONLY had started using Linux since 2 weeks ago. And I am learning.... Forgive me for being a noob.

---

### Post by WebSiteGuru on 2007-08-13
BTW! My problme still STAND!  :(](*,) :(

---

### Post by Arthur Archnix on 2007-08-13
So, there's some video online that window media player would usually take care of and you want to watch it in Ubuntu, under Firefox I presume?

I watch WMV files from www crooksandliars.com all the time, so no worries, this can work.

First, if you haven't already, add mediabuntu to your repos.
```
sudo gedit /etc/apt/sources.list
```
and add: deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) feisty free non-free

Save, close and then
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install w32codecs 
```

At this point, it may already work, go try watching a wmv file from the website I mentioned. Use that one since I know for sure that there is no problem with the video or the website. If it doesn't work, try installing vlc to use instead of mplayer.
```

sudo apt-get install vlc  vlc-plugin-* mozilla-plugin-vlc
sudo apt-get install avahi-daemon
sudo apt-get install avahi-utils
```

---

### Post by WebSiteGuru on 2007-08-13
Thank you for trying to help. I had follow your instruction and it works on the site you indicated. But for the site I am trying to access it did not goes well. :(

I hate having to load Windows back just to use the site. :(

---

### Post by asmoore82 on 2007-08-13
> **Arthur Archnix said:**
> People aren't here trying to make your life more difficult than it has to be. Ubuntu has looked at Automatix and found it to be a poorly written program that can actually do damage to your system. So you can trust some random forum person who says it works fine for them, or you can trust the forum admins and ubuntu developers who advise you not to use it.

Thank You!!

I'm a long time linux user who just made the switch to Ubuntu.
I keep reading this Automatix stuff on the forums but I have refused
to try it because it makes my Spidey Sense tingle.

You, sir, have just proven my instincts are correct.

Next on my Smiling Enemies list is this "Envy" I've heard about for installing "drivers."
Nope, don't think so; my laptop has ATI and my Girlfriend's Dell has nVidia and Ubuntu's
out-of-the-box solution "Restricted Drivers Manager" worked perfect in both situations.

3rd party Software Managers (Automatix/Envy) can only screw up what Ubuntu already does right!

------------------------------
My trail of OSes

Windows Me => Red Hat 7.2 => Red Hat 7.3 => Red Hat 8.0 => Red Hat 7.3
     => Red Hat 9.0 => Red Hat 7.3 => Mandrake 7? => Gentoo 2004.2 (failed)
     => Red Hat 7.3 => Gentoo 2004.2 (failed) => Fedora Core 1?
     => Gentoo 2004.2 (Success) => archlinux => Ubuntu 7.04

---

### Post by Arthur Archnix on 2007-08-13
Well, maybe it's not a W32 codec you need then. Do this:
```

sudo apt-get install ubuntu-restricted-extras
```

If that doesn't work, and if it's safe for work :wink: post a link to the website you're having trouble with.

---

### Post by Paulmd on 2007-08-13
> **WebSiteGuru said:**
> This probably had been asked before. I am a noob at Linux and need assistance.

I had tried to install Windows Media Player(WINE) and I cant get it to work with FireFox. So I can view the video file from the web. I had also tried MPlayer with 32codecs, etc and it is coming up with error.

I am currently scratching amy head and frustrated.


Need hep. PLZ!

What website is it?

CNN has started to use Flash movies, which seem to work pretty well in the browser.

RealPlayers videos work, in the browser, generally, but not from the BBC. But launching the standalone browser works.


MP4s play OK, If you download them, and play with VLC (you'll have to install it).

WMVs, so far are iffy for me, but VLC seems to do the best job. (For some reason Totem and MPlayer don't work for me -at all-, either).

I've gotten MOVs to work, at last, in VLC, mostly (I needed to allocate more video ram).

Most formats don't seem to play nice inside the browser for me, either, but usually you can right click on the video, and copy the link to VLC, and it works OK.

I can't see using Wine to get a windows browser plugin to work under linux. Wine being flaky enough as it is.

I feel your pain.

There are various video plugins available for Firefox, go to the Synaptic package manager and search for 'mozilla' there should be several.

---

### Post by WebSiteGuru on 2007-08-13
> **Arthur Archnix said:**
> Well, maybe it's not a W32 codec you need then. Do this:
```

sudo apt-get install ubuntu-restricted-extras
```

If that doesn't work, and if it's safe for work :wink: post a link to the website you're having trouble with.

I will try that tonight when I get home.

Oh! The site is safe. :popcorn: Rated G site, but it is a paid site to see anything (as far as I know). I am trying to get this work so my wife can watch it. (Trying to please the lady of the house, if you know what I mean ;))  Since she had to stay home and take care of the baby. :D :KS

Link below:
[http://www.thaitv.tv](http://www.thaitv.tv)

Thanks again in advance!

---

### Post by WebSiteGuru on 2007-08-13
> **Paulmd said:**
> What website is it?

See my last post.

> **Paulmd said:**
> 
CNN has started to use Flash movies, which seem to work pretty well in the browser.

RealPlayers videos work, in the browser, generally, but not from the BBC. But launching the standalone browser works.


MP4s play OK, If you download them, and play with VLC (you'll have to install it).

WMVs, so far are iffy for me, but VLC seems to do the best job. (For some reason Totem and MPlayer don't work for me -at all-, either).

I've gotten MOVs to work, at last, in VLC, mostly (I needed to allocate more video ram).

Most formats don't seem to play nice inside the browser for me, either, but usually you can right click on the video, and copy the link to VLC, and it works OK.

Thanks for the info. :D

> **Paulmd said:**
> 
I can't see using Wine to get a windows browser plugin to work under linux. Wine being flaky enough as it is.

If I have a choice, I wont even touch it. ;) But since I also have a lot of PC Programs that I can not live without. I will have  to deal with it. :lolflag:

> **Paulmd said:**
> 
I feel your pain.

:):KS:lolflag:

> **Paulmd said:**
> 
There are various video plugins available for Firefox, go to the Synaptic package manager and search for 'mozilla' there should be several.

Thanks, I'll look into it.

---

### Post by Paulmd on 2007-08-13
> **WebSiteGuru said:**
> See my last post.



Thanks for the info. :D



If I have a choice, I wont even touch it. ;) But since I also have a lot of PC Programs that I can not live without. I will have  to deal with it. :lolflag:



:):KS:lolflag:



Thanks, I'll look into it.


Alright, I think i have some info.  The site uses a LOT of scripting, making opening a direct link problematic, also problematic to find out what format the videos are without registering. Most likely, as you stated originally they are Windows Media. But WMP can play other common formats besides its own. So it's not a guarantee that they are ASF or WMV. 


There is also a link to this plugin on the website:

[https://addons.mozilla.org/en-US/firefox/addon/1879](https://addons.mozilla.org/en-US/firefox/addon/1879)

Since they link to it, maybe it's required to get their videos to work under Firefox for Linux... Maybe. I haven't tried.



There is also a tech support number listed. Maybe they can help.

[http://www.thaitv.tv/TH/Contact/ContactUs.aspx](http://www.thaitv.tv/TH/Contact/ContactUs.aspx)

IPtv Technical Support
Tel: 323-259-2149
Toll Free Technical Support: 1-877-477-4788

---

### Post by WebSiteGuru on 2007-08-13
> **Paulmd said:**
> Alright, I think i have some info.  The site uses a LOT of scripting, making opening a direct link problematic, also problematic to find out what format the videos are without registering. Most likely, as you stated originally they are Windows Media. But WMP can play other common formats besides its own. So it's not a guarantee that they are ASF or WMV. 

They did that so no one can direct link to the video files.

> **Paulmd said:**
> 
There is also a link to this plugin on the website:

[https://addons.mozilla.org/en-US/firefox/addon/1879](https://addons.mozilla.org/en-US/firefox/addon/1879)



Since they link to it, maybe it's required to get their videos to work under Firefox for Linux... Maybe. I haven't tried.


Tried that at least 3 times. NO workkie! :(

> **Paulmd said:**
> 
There is also a tech support number listed. Maybe they can help.

[http://www.thaitv.tv/TH/Contact/ContactUs.aspx](http://www.thaitv.tv/TH/Contact/ContactUs.aspx)

IPtv Technical Support
Tel: 323-259-2149
Toll Free Technical Support: 1-877-477-4788

I'll see if I can contact them and see what they say. I'll come back with the updates!

Thanks!

---

### Post by Arthur Archnix on 2007-08-13
I registered for a free trial service and couldn't get a video to play. Then I found a page that said they'd shut down their trial service server. Hopefully tech support will tell you more.

---

### Post by WebSiteGuru on 2007-08-14
> **Arthur Archnix said:**
> I registered for a free trial service and couldn't get a video to play. Then I found a page that said they'd shut down their trial service server. Hopefully tech support will tell you more.

I hope so, I have not had a chance to call them yet. Got too busy yesterday, and didnt evern have a chance to get on the computer last night :(.

---

### Post by WebSiteGuru on 2007-08-17
OK! I think I might know the problem, and no I have not had a chance to call them yet (sorry, keep getting tied up with the family). 

But here is the scoop. Since the video file is embed into the page (and I think they check that just incase someone direct link to the video file). And my MPlayer trying to open it in a new window. (that is considering directlink) So it is giving me the error. See Attach image for the error I am getting. Is there anyway I can get MPlayer to start playing video in the embed page?

---

### Post by WebSiteGuru on 2007-08-17
Bump! I hope you dont mind me doing so. If you are I am deeply sorry.

---

### Post by mstephens on 2007-08-20
Hi

Your error "Couldn't resolve name for AF_INET6"  should be fixable for MPlayer  by following the instructions here:

[http://forums.suselinuxsupport.de/index.php?showtopic=56668&pid=234497&mode=threaded&show=&st=&#]("http://forums.suselinuxsupport.de/index.php?showtopic=56668&pid=234497&mode=threaded&show=&st=&#")

---

### Post by WebSiteGuru on 2007-08-20
> **mstephens said:**
> Hi

Your error "Couldn't resolve name for AF_INET6"  should be fixable for MPlayer  by following the instructions here:

[http://forums.suselinuxsupport.de/index.php?showtopic=56668&pid=234497&mode=threaded&show=&st=&#]("http://forums.suselinuxsupport.de/index.php?showtopic=56668&pid=234497&mode=threaded&show=&st=&#")

Thanks! I'll try that tonight. :D That would make the lady of the house happy, and you know what that mean. ;) :popcorn:

---

### Post by WebSiteGuru on 2007-08-20
That fixed the AF_INET6 error. But it still not play. :( I'll close this problem thou.

---

### Post by Paulmd on 2007-08-21
> **WebSiteGuru said:**
> That fixed the AF_INET6 error. But it still not play. :( I'll close this problem thou.

It's not solved until it works.  When you get the chance to talk to IPtv tech support, let us know what they suggested and whether or not it works. As it may help others with similar issues.

Even if they say "our site does not work with linux", at least you'll have an answer. :)

---

### Post by WebSiteGuru on 2007-08-21
> **Paulmd said:**
> It's not solved until it works.  When you get the chance to talk to IPtv tech support, let us know what they suggested and whether or not it works. As it may help others with similar issues.

Even if they say "our site does not work with linux", at least you'll have an answer. :)


Thanks, I'll try to get with them when I have a chance to call.

---

### Post by WebSiteGuru on 2007-08-21
2 Things I noticed thou.

1st, it will not play on that site (I will have to call them to find out why)

2nd, this error about audio. I need to change the config or install something, but I don't know what.

Also, can I configured MPlayer to play in the embed mode? Instead of popping up.

---

### Post by WebSiteGuru on 2007-08-21
bump

---

### Post by stchman on 2007-08-21
> **WebSiteGuru said:**
> This probably had been asked before. I am a noob at Linux and need assistance.

I had tried to install Windows Media Player(WINE) and I cant get it to work with FireFox. So I can view the video file from the web. I had also tried MPlayer with 32codecs, etc and it is coming up with error.

I am currently scratching amy head and frustrated.


Need hep. PLZ!

VLC is a good choice.  Follow my procedures here to get your system up and running with proper codecs and such for playing video and audio.

[http://www.stchman.com/cd_rip.html](http://www.stchman.com/cd_rip.html)

[http://www.stchman.com/dvd_rip.html](http://www.stchman.com/dvd_rip.html)

---

### Post by WebSiteGuru on 2007-08-21
> **stchman said:**
> VLC is a good choice.  Follow my procedures here to get your system up and running with proper codecs and such for playing video and audio.

[http://www.stchman.com/cd_rip.html](http://www.stchman.com/cd_rip.html)

[http://www.stchman.com/dvd_rip.html](http://www.stchman.com/dvd_rip.html)

So, if I do all those instruction I should be able to watch encrypted video from the web, right?

I think I have VLC installed. Should I uninstall it then go through the steps?

How about having FireFox reconize it as a plug in instead of MPlayer?

---

### Post by WebSiteGuru on 2007-08-22
> **stchman said:**
> VLC is a good choice.  Follow my procedures here to get your system up and running with proper codecs and such for playing video and audio.

[http://www.stchman.com/cd_rip.html](http://www.stchman.com/cd_rip.html)

[http://www.stchman.com/dvd_rip.html](http://www.stchman.com/dvd_rip.html)


OK! I just did the dvd one this morning. :D Hopefully things goes well when I play DVD. :D

---

### Post by WebSiteGuru on 2007-08-23
WOOT WOOT! I dont know what I did, I start uninstalling stuffs after I installed all the vlc instruction and it start working. :D Thanks everyone for helping, :guitar::guitar::guitar:

---

### Post by Arthur Archnix on 2007-08-23
Excellent!

Happy ubuntuing!

---

### Post by parvinder on 2007-09-07
Try this it worked for me... I am now able to play Windows Streaming Audio and Video but you cannot resize the screen.

[http://ibeentoubuntu.blogspot.com/2007/06/playing-music-in-ubuntu-7.html](http://ibeentoubuntu.blogspot.com/2007/06/playing-music-in-ubuntu-7.html)

Also, install MPlayer from synaptics manager if haven't installed it.

---

