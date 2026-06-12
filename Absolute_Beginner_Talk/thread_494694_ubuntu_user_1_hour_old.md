---
title: "ubuntu user 1 hour old"
date: 2007-07-07
forum: Absolute Beginner Talk
---

### Post by leetj on 2007-07-07
hi
i am a new ubuntu OS user (1hr old) and i have a few questions about various things 
firstly i would like to speed up my pointer speed ,i have adjusted the mouse settings to the max in
ubuntu ,but its stil takes a few of strokes on my touch pad to get from one side of the screen to the other ,i am using an 'alps touchpad' on a toshiba laptop , 
 
secondly i would like some advice on what security suite i should use and where to get it ,free would be cool 

thirdly i want to try out the beryl software with the 3D effects but which one do i use with ubuntu

also i would like to use virtual box and keep windows OS 'INPRISONED' so i can still use cubase music production system       ,is virtual box  software free too? and were to get it

thank you for any future responses ..much appriciated  taa

lee

---

### Post by robertc36 on 2007-07-07
hello

1- no idea
2- you dont need it 
3-Make sure you have enabled restricted drivers or that your card can cope- you can install beryl from synpatic- Beryl is one flavour.
Or you could try compiz-fusion, there are lots of warning regarding not for beginners but if you have half a brain the instructions are very simple to follow.
4.Cubase is great but there are plenty of native music apps such as ardour- wired etc..
I guess it all depends on what you want to do, as i admit i have yet to find an adequate replacement for Ableton live, and getting midi to work is a nightmare.

---

### Post by Old Pink on 2007-07-07
> **leetj said:**
> hi
i am a new ubuntu OS user (1hr old)Love that feeling, remember my first shot at Ubuntu. Welcome to the community. :)
> **leetj said:**
> and i have a few questions about various thingsEveryone does! Shoot and I'll do my best :)
> **leetj said:**
> 
firstly i would like to speed up my pointer speed ,i have adjusted the mouse settings to the max in
ubuntu ,but its stil takes a few of strokes on my touch pad to get from one side of the screen to the other ,i am using an 'alps touchpad' on a toshiba laptop , Chances are the configuration file is kept somewhere, and using sudo and gedit you'll be able to bump it up further. Try googling it, or searching the forums. "Make mouse more responsive in Ubuntu" is a good place to start. :)
 > **leetj said:**
> 
secondly i would like some advice on what security suite i should use and where to get it ,free would be cool 
Haha, you're on Linux, you're as secure as you'll ever be from the moment you step on here. Viruses aren't a problem, and the requirement for sudo stops anything bad happening to your system without your permission. You could install a firewall, but chances are your router already has one. Stick "firewall" in the search box on these forums if you're after one. :) 
> **leetj said:**
> 
thirdly i want to try out the beryl software with the 3D effects but which one do i use with ubuntu
Assuming you're on 7.04, hit System > Preferences > Desktop Effects and activate it, to see if you're hardware supports that type of thing, I know mine doesn't. :( 

If that works well, head to the tutorial section of the forum and search Beryl there. :) 
> **leetj said:**
> 
also i would like to use virtual box and keep windows OS 'INPRISONED' so i can still use cubase music production system       ,is virtual box  software free too? and were to get it[http://ubuntuforums.org/showthread.php?t=183209](http://ubuntuforums.org/showthread.php?t=183209) 

Nice easy guide, step by step, should be set up in no time. :) 
> **leetj said:**
> 
thank you for any future responses ..much appriciated  taa

lee

You're welcome lee, keep in touch! :)

---

### Post by shearn89 on 2007-07-07
For music production, check out the ubuntustudio site: you can always add the software repositroies, and then just download the music software. I've heard its quite good, although maybe a little different in layout etc from cubase. You could also check out Wine for running windows software under linux.

---

### Post by davidjmayo on 2007-07-07
Hi Lee and welcome

Just to add to what Old Pink posted
> 
secondly i would like some advice on what security suite i should use and where to get it ,free would be cool 

The only security updates you need will come  from ubuntu. A message box will appear advising you updates are available (you should have seen this already when you started ubuntu if you have installed it --I'm not sure if the Live Cd does this) Just click the orange icon, wait for the download and that's it, all up to date no need to worry

---

### Post by 3rdalbum on 2007-07-07
Virtualbox is available in free-as-in-beer (a Debian package) and free-as-in-speech (source code). My suggestion is to use the Debian package one - it's not open-source, but it works well and is quite easy to install. I'd suggest not installing Virtualbox at this stage though - the risk of you breaking your system is a bit too great for me to recommend it right now.

You will not really get good results running Cubase on Virtualbox. Your USB MIDI interface if you have one might work, but music work requires low latency, and virtualisation introduces a very undesirable overhead that will kill the virtual system's ability to sync everything. MIDI should be okay, but audio tracks will be a problem. Use a native Linux program if possible.

---

### Post by leetj on 2007-07-07
wow they were  quick responses   thanx allot for your time people  
i feel already at home  ,i shall be using your advice  as soon as ive finished writting  this

i still cant get over not needing any bit sucking AV  app.  its like a world were everyone's human

thanx again 
lee

---

### Post by Jimmyfj on 2007-07-07
Just to extend on the issue of security - It will be nice for you, for your own consciousness to install a virus-scanner. Not that your system needs one, but to be sure that you don't pass on any viruses to any windows user you forward E-mails to. Just as a gesture from the Linux world and our way of computing. 

You'll find a good virus scanner in Programs/Add & Remove/Accessories

---

### Post by ugm6hr on 2007-07-07
This is useful for editing your touchpad settings.  You have to edit xorg.conf to include the synaptics driver.  This gives a full explanation (look out for the bit that mentions ALPS as being slightly different).

[http://gentoo-wiki.com/HARDWARE_Synaptics_Touchpad](http://gentoo-wiki.com/HARDWARE_Synaptics_Touchpad)

This bit is specifically important to you:
```
Option	"MinSpeed"	"0.09"
Option	"MaxSpeed"	"0.18"
```
Just try changing the values.

To see any effect, you have to restart X (I think Ctrl+Alt+Backspace will do it).  Just experiment a bit.  Don't forget to make a backup before editing though!

---

### Post by broncavfan on 2007-07-07
I've been using Linux MultiMedia Studio (LMMS) for my MIDI needs and it's treated me well.  Haha, the number 1 reason I switched from Windows was because when I upgraded my system to 64 bit I couldn't find any MIDI support.  Anyway, you can find out more at [http://lmms.sourceforge.net/](http://lmms.sourceforge.net/)   There's also a helpful post at [http://ubuntuforums.org/showthread.php?t=475118](http://ubuntuforums.org/showthread.php?t=475118)

Good luck taking your computer back from Microsoft!

---

