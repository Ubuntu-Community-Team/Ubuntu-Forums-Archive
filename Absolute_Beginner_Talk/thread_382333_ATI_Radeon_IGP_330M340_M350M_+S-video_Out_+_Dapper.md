---
title: "ATI Radeon IGP 330M/340 M/350M +S-video Out + Dapper"
date: 2007-03-11
forum: Absolute Beginner Talk
---

### Post by piri on 2007-03-11
Hello!  The ATI Radeon IGP 330M/340M/350M thinger in my laptop seems to be working properly.  However, I'd like to go about enabling the s-video out so I can play videos on my tv.  (I miss it terribly!)

After poking around the forums, I've come up with a somewhat sketchy plan of action.    Any comments or suggestions that others might have would be much appreciated.  (it'll prolly be awhile before I can actually try anything due to time constraints)

[COLOR="Green"]items on-hand
ATI Radeon IGP 330M/340M/350M on a 3+year old laptop >.<;;
Ubuntu Dapper Drake
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)
[http://gentoo-wiki.com/HOWTO_TV-Out](http://gentoo-wiki.com/HOWTO_TV-Out)
pot of coffee

find/install/configure fglrx (first guide link)
modify xorg.conf for dual monitors (thinking the aticonfig prolly takes care of this)
--one monitor being the lcd on the laptop, using the regular radeon driver
--second monitor as the television, using the fglrx driver

run aticonfig with proper settings (second guide link)
remembering to check that something about overlay is listed somewhere to correct the blank videoplayer screen on the tv display

So, I guess that takes care of enabling s-video out to work properly.
Next would be to set something up with MPlayer and a shortcut of sorts to play videos and output it to the TV, as described in the third post of [http://ubuntuforums.org/showthread.php?t=23628&page=2](http://ubuntuforums.org/showthread.php?t=23628&page=2)
[/COLOR]

Does this sound about right?  I'm a complete noob when it comes to Linux, but figure that if the thought process is correct then the rest can be fleshed out by looking up the proper commands and such.

In the near future, my plan is to get MPlayer configured to properly play the video files I use.  On some it doesn't display the soft-subs from .mkv files.
The very last thing is figuring out if it is possible to use both English and Japanese text in the Open Office programs at the same time, without having to reboot to switch from one language to another.  If I can accomplish these three things (s-video out, MPlayer and Japanese word processing) it will make me very happy and I'll be able to completely change over both my machines to Ubuntu.

Thank you!  :biggrin:  (sorry for the long post!)

---

### Post by edemark on 2007-03-18
check this might help

[http://www.consultmatt.co.uk/linux_nx9005](http://www.consultmatt.co.uk/linux_nx9005)

good luck

---

### Post by zkeng on 2007-04-08
Hi

I am able to use tv-out with my  ATI Mobility Radeon IGP 340M card in my laptop.

I saw alot of tricky workarounds before I found out that it works just fine with ATITVOUT as long as you use the right commands. This is how I do it:

I use the default ATI-driver that is shipped with ubuntu (dapper in my case).
Then install ATITVOUT from the synaptics package manager.
Now plug the TV into your computer and restart it (the tv must be pluged in on bootup to enable the tv-out port).
Open the terminal and write the following commands:

sudo atitvout -r detect (and your attached display units will be detected)

(now type your root password as asked)

sudo atitvout -r pal (configures PAL mode since I am in Europe. Use "ntsc" instead for US or Asia)

sudo atitvout -f t (will send the screen to the TV)

sudo atitvout -f l (will send the screen back to your monitor, probably you will also be propted for the root password again after watching some videos)

And thats it.
If you dont get any colors on the tv it is probably one of the following reasons. 1. You have the wrong display mode (pal or ntsc). 2. Your tv does not support s-video and you have to use a (very inexpensive) adapter to plug the video cable into a normal video port instead.

/Micke

---

### Post by piri on 2007-04-08
wah wah wah I LOVE YOU MICKE/ZKENG!!

I just tried this and it works like a dream (after realizing that non-PAL mode is "NTSC").  Oh, my dear sweet TV-out, I've missed you so!

Thank you so very Very VERY MUCH!!  You have made me a very happy camper! *^_^*

---

### Post by zkeng on 2007-04-10
Glad it worked out for you Piri. I have changed the wrongly spelled ntsc-mode in the howto above so that I will not misslead anyone else.

/regards

---

### Post by Seidojohn on 2007-04-13
zkeng's solution (atitvout) worked perfectly with my  ATI Radeon Mobility M6 LY (in a Toshiba Satellite 1905-S301)
Thanks for sharing the wisdom zkeng!

---

### Post by ffoletti on 2007-06-02
Zkeng you did it! Now I'm COMPLETELY SWITCHED to ubuntu! your howto works on my HP pavillion with ati radeon IGP 320 on feisty! ! ! !  Yeeeeeeeeeeeeah!
Thanks so much!

I just have to try to get the "lt" mode (both tv and screen) working, but I'll give a try and eventually post any news!

Bye! Now going to watch some video... :p :popcorn:

---

### Post by Tulip on 2007-10-23
Hello,
This has also worked on my compaq nx9010 running Gutsy, as long as I drop the resolution to 800x600 or 1024x768. Any higher gives me a VBE call failed errors.

However I do get some cropping of movies during playback on the TV along the bottom of the screen. Its crops off the bottom third of the movie in 800x600 and a fair bit less in 1024x768, but its still noticeable.

 The cropping occurs in full screen and normal playback, using Totem and VLC. So close and yet I feel so far...

Any thoughts?

---

### Post by Tulip on 2007-10-24
I've found a work-around using MPlayer - its preferences allow the choice of a different driver, and if I select gl2 X11 (OpenGL) Multiple textures version, it will play without cropping the movie.

 Its not without some problems - the control panel 'flashes' on and off through the movie and has to be minimised, and so does the right click menu when selected.

I'd still like to hear of a tidier version if anyone has one though.

---

### Post by marcolinux on 2007-11-10
@tulip
i've got the same notebook,,, can you tell me if you use the ati open or did you install somewhat else?
it would be useful if you can post yr xorg.conf... i've got 800x600 resolution and i can't figure out how to have better resolution.

thanks a lot!
marco

---

### Post by lsd_us3r on 2008-02-03
> **zkeng said:**
> Hi

I am able to use tv-out with my  ATI Mobility Radeon IGP 340M card in my laptop.

I saw alot of tricky workarounds before I found out that it works just fine with ATITVOUT as long as you use the right commands. This is how I do it:

I use the default ATI-driver that is shipped with ubuntu (dapper in my case).
Then install ATITVOUT from the synaptics package manager.
Now plug the TV into your computer and restart it (the tv must be pluged in on bootup to enable the tv-out port).
Open the terminal and write the following commands:

sudo atitvout -r detect (and your attached display units will be detected)

(now type your root password as asked)

sudo atitvout -r pal (configures PAL mode since I am in Europe. Use "ntsc" instead for US or Asia)

sudo atitvout -f t (will send the screen to the TV)

sudo atitvout -f l (will send the screen back to your monitor, probably you will also be propted for the root password again after watching some videos)

And thats it.
If you dont get any colors on the tv it is probably one of the following reasons. 1. You have the wrong display mode (pal or ntsc). 2. Your tv does not support s-video and you have to use a (very inexpensive) adapter to plug the video cable into a normal video port instead.

/Micke


Can you post your xorg.conf file?

 I'm running gutsy on my HP Pavilion ze5270 which has an IGP 340M but all I get when using atitvout is "VBE call failed."  .... thanks for any help...

---

### Post by www.rzr.online.fr on 2008-02-18
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/atitvout/+bug/189393](https://bugs.launchpad.net/ubuntu/+source/atitvout/+bug/189393) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				same issue with igp320M running hardy :

[http://rzr.online.fr/q/vbe](http://rzr.online.fr/q/vbe)

---

### Post by Linuxgenius on 2008-04-26
i tried this on a compaq evo n1020v and i get this


linuxgenius@linuxgenius-laptop:~$ sudo atitvout -f t
[sudo] password for linuxgenius: 
Forcing Rage Mobility/Rage 3D Pro LT mode
VBE call failed.
Maybe this command is not supported by your graphics adapter?
Did your parameters (if you specified some) really make sense?
Please try all other available commands before complaining!
linuxgenius@linuxgenius-laptop:~$ 
linuxgenius@linuxgenius-laptop:~$ sudo atitvout -f l 
Forcing Rage Mobility/Rage 3D Pro LT mode
linuxgenius@linuxgenius-laptop:~$ 
linuxgenius@linuxgenius-laptop:~$ sudo atitvout -f l t
Forcing Rage Mobility/Rage 3D Pro LT mode
VBE call failed.
Maybe this command is not supported by your graphics adapter?
Did your parameters (if you specified some) really make sense?
Please try all other available commands before complaining!
linuxgenius@linuxgenius-laptop:~$ sudo atitvout -r detect
Forcing Radeon/Rage 128 mode
CRT is attached.
linuxgenius@linuxgenius-laptop:~$ sudo atitvout -r detect
Forcing Radeon/Rage 128 mode
CRT is attached.
linuxgenius@linuxgenius-laptop:~$

---

### Post by freezerburn666 on 2008-04-29
same issue on my 340m using the "ati" driver. my father has a desktop with a ati 9200 se (9250) and he also gets vbe call failed. very discouraging, i wish there was an easy way to make this work as my father would be fully converted to ubuntu if he could only watch his tv shows and movies on the tv screen...

---

### Post by www.rzr.online.fr on 2008-05-01
I reported this upstream :
  [http://rzr.online.fr/q/xrandr](http://rzr.online.fr/q/xrandr)

---

### Post by GepettoBR on 2008-05-12
zkeng's solution worked for me in Gutsy, but since the Hardy upgrade I get the VBE Call Failed error, which is weird because my TV displays everything from GRUB to right before gdm loads, which makes me think something is wrong with my xorg.conf. Unfortunately, I have no idea how to tinker with it.

 I am also o a Compaq Evo n1020 using ATI Radeon IGP 340M.

---

