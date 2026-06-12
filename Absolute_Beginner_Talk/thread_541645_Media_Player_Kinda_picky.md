---
title: "Media Player Kinda picky"
date: 2007-09-03
forum: Absolute Beginner Talk
---

### Post by Aishiko on 2007-09-03
OK, I'm kinda picky about the controls on my media player, I just need one that will do all the common video types (avi, mkv, mpg, ogg, etc) and for controls either let me define the controls for the keyboard short-cuts, or have these as the default (as I normally watch in the dark and can't see the keyboard and go by feel 99% of the time);
Enter or Enter+ALt = full screen
Space = play/pause
Arrow Up/Down = Volume up/down
. or Ctrl+Space = Stop

Basicly I want something that has controls very similar to Media Player Classic or GomPlayer.  So far I've tried Totem (not at all happy with the user interface) and Kaffine (won't play anything but doesn't tell me I need any codecs or anything).

I'll try out a few more but while I'm doing so I thought I'd pick the communties brain to see if anyone else wanted something similar and if they found it.

Thank you for your time and response if you chosse to do so.

---

### Post by aquavitae on 2007-09-03
You can usually change all the keyboard shortcuts from the settings menu of any app.  

The problem with kaffeine is that codecs aren't installed.  Go to [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Multimedia_Codecs]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Multimedia_Codecs") for instructions on how to install them.
If you're using KDE, this might be more useful: [http://kubuntuguide.org/Feisty#Multimedia_Codecs_Installation]("http://kubuntuguide.org/Feisty#Multimedia_Codecs_Installation")

I personally find that the best is to use different apps for movies and music - kaffeine for movies and amarok for music.  I just set the keyboard shortcuts to be the same on both.

Hope this helps!

---

### Post by Aishiko on 2007-09-03
I'll give it a try but I've looked but I didn't see anything that poped up and said "keyboard short cuts configurations" or any other such obvious thing, but then 5am is not the best time to try doing anything that requires a lot of brain power is it?

I'll check out both the links.

---

### Post by Aishiko on 2007-09-03
Ok now Kaffine is working as I like (or darn close to what I'm used to!)  I think I'll keep it,  (and you :P)

---

### Post by aquavitae on 2007-09-04
Great!

---

### Post by Aishiko on 2007-09-04
Well, I've found not all my Avis get played right, on a few the audio and video get out of sync sometimes quickly, sometimes suddenly or very quickly.  Do you know of any other codec packages out there?  I found (under windoze) that the CCCP (community Codec package, or something like that) had them all, but they have no intention of porting it over to linux, I'm just wondering if there is something similar for linux anywhere, as this package would play any video file just right.

---

### Post by aquavitae on 2007-09-04
Try installing mplayer.  I find it will play just about anything.  Also, do you have the win32codecs package installed?  Lots of people swear by vlc - never got into it myself but I've heard it will play anything too.

---

### Post by misfitpierce on 2007-09-04
Yup good ol' VLC is light and will stream and play just about anything. :)

---

### Post by Aishiko on 2007-09-04
I downloaded Mplayer and it won't play avis, I'd forgotten about VLC I'll have to go and get it (again, I had it as a portable player on my thumbstick til someone broke it :()

---

### Post by Aishiko on 2007-09-04
VLC works but doesn't have the nice keyboard shortcuts, so I'll use Kaffeine as my primary and VLC for any files that don't play well with Kaffiene (yes pun intended). 

Thank you for remionding me about it and for the help getting Kaffiene not only working just right but playing most of my files.  Now if I could just figure out hoe to make Kaffiene the defualt player.

---

### Post by aquavitae on 2007-09-05
mplayer required the win32codecs package to play avis - do you have it installed?

Are you using kde or gnome?  I know how to set kaffeine as the default in kde but I'm not sure in gnome - I think its under settings, default applications though.  In kde its under system settings - file types (as far as I remember).  Look around there and I'm sure you'll find it.

---

### Post by misfitpierce on 2007-09-05
> **Aishiko said:**
> VLC works but doesn't have the nice keyboard shortcuts, so I'll use Kaffeine as my primary and VLC for any files that don't play well with Kaffiene (yes pun intended). 

Thats what I do...

---

### Post by Aishiko on 2007-09-05
yep got the win32 codecs, but they were installed before I got mplayer, could that be the issue?

I'm using I don't know it's the default set-up.

I have a bar with (Ubuntu symbol) Applications    Places    System  

I go to System -> Prefrences -> Perferred Applications -> under that I get a pop up GUI and under multi media I got a choice of Custom, Totem, and Rythmbox.  I tried Custom and typing in the box for the command line (and the box for running in the terminal checked and unchecked) and nothing do I need to reboot for this to take affect or am I messing up the command section, and what am I running KDE or Gnome, I think I should know so I know what programs I can and can't run.

---

### Post by Aishiko on 2007-09-05
Well I figured out the Default is Gnome, and I don't care for gnomes (short little illusionst-thieves! :P)  But seriously, I'm downloading KDE.

easy but there is the core package and like 10 more to download and install.

So I think I'll try the KDE desktop, as well Gnome after a bit more exploration is coming off as well too basic not enough customzation for me, heck I really modifided the XP installation I have left is very modified every thing from the effects to how programs come up.

I hope KDE is more modifiable.

---

### Post by misfitpierce on 2007-09-05
> **Aishiko said:**
>  I'm downloading KDE......

.....So I think I'll try the KDE desktop, 

......I hope KDE is more modifiable.

Honestly I like the KDE environment way better. Had more trouble with Compiz-Fusion in KDE but I dont use effects really anymore. It is just as customizable as gnome maybe even more but I will promise its not as simplified. :) KDE rocks. Explore and enjoy. :popcorn:

---

### Post by Aishiko on 2007-09-05
actually I tend to turn off all those fancy power hungry affects so I get more performance out of the programs I do run that are CPU and Mem hungry!
Heck I can do things in Ubuntu right out of the box that lagged the system to the point I had to chosse one or the other!

misfit I'll let you know which I perfer if your intrested :)

---

### Post by aquavitae on 2007-09-05
I usually prefer Kde too - but I waver :)
> Well I figured out the Default is Gnome, and I don't care for gnomes (short little illusionst-thieves! :P)Someone being playing too many games....? :D

If you're really looking for performance you could always try xfce (i.e. instead of gnome or kde).  Its quite a nice desktop, but not quite as easy to customize as kde (which I find easier than gnome).  I use in on my laptop - ancient beast with 64Mb ram - and it goes at a reasonable speed.  But its probably best to stick with kde if you have a decent pc.

---

### Post by Aishiko on 2007-09-05
I was a loner and spent my free time immersed into fantasy worlds.  I've switched back to Gnome until I can figure out how to run the "feel wizard" of KDE again.  I made a mistake and chosse a feel that I was like "OK, I've seen this before, what about Y feel?" and couldn't find the wizard.

My PC is a Dual PIII 700Mhz, 1 gig of RAM (PC100), 2/3 of a Tbyte of storage (not counting boot drive with /home directory), 2 ethernet cards, a 64MB Nivida MX440 Video card, a Promise 100 expantsion card, a 5 port USB2 expastion card, a CD burner (8X), a DVD drive, and finally, all connected to a APC 350 UPS.  Installed but not connected is a floppy drive and Zip250 drive.

This Computer used to be used as a home server running Server2003 on a 20 gig HDD until it started randomly rebooting and givign "stop errors" aka the blue screen of Death, usually with in 48 hours of restart.  and as you well know a server that isn't reliable is worthless, I don't care if the hardware is the latest, newest, and bestest, if the server software isn't reliable then it's not worth it.  Ubuntu, the beta, only version that supported my hardware, has been running rock solid sofar.  that to me is impressive.  a beta, buggy software is more stable then a prodection enterprise edition of server2003?? that is insane.

---

### Post by aquavitae on 2007-09-06
The "feel" wizard I think you're talking about is kpersonalizer.  Just got to Run in the menu and type it in.  But all it does is set some defaults in the kde settings - e.i. you can change them in the system settings.  Btw, I've always found kcontrol to be much better for settings up kde that the system settings.  For some reason ubuntu doesn't put kcontrol in the menus, but you can access it by typing it in.

How does Kde run on you system?

> This Computer used to be used as a home server running Server2003 on a 20 gig HDD until it started randomly rebooting and givign "stop errors" aka the blue screen of Death, usually with in 48 hours of restart. and as you well know a server that isn't reliable is worthless, I don't care if the hardware is the latest, newest, and bestest, if the server software isn't reliable then it's not worth it. Ubuntu, the beta, only version that supported my hardware, has been running rock solid sofar. that to me is impressive. a beta, buggy software is more stable then a prodection enterprise edition of server2003?? that is insane.Yeah, thats MS for you...  We use an MS server at work and about once a week a message comes round "The server will be rebooted in ten minutes.  Please save you work".  And I read somewhere about a linux server (debian I think) which hasn't been rebooted since 1980!

---

### Post by Aishiko on 2007-09-06
you get a 10 minute warning???  I didn't even get that!

and a server that has been up and running for almost 3 decades?  that is neat, though it sounds like the hardware would be really out of date.  But then there is a light bulb in Cali (Ithink it's in cali, might be NY) that has been on for over a century, and even has it's own webcam.  Even though they have newer lighting and it doesn't do what it orignally did they still keep up and running as a point of pride and living history.

---

### Post by aquavitae on 2007-09-06
Well, we get the 10min warning, nothing happens in 10min, we think we somehow missed it, and then they do it after an hour.  I'm on a campaign to switch the office to linux!  Unfortunately we use too much windows dependant software.  But I have a stealth ubuntu in a virtual machine, and cygwin shell for whenever I get too irritated with windows explorer or windows' attempt at a command prompt.

Yes, the hardware on the server must be ancient, but then a server doesn't really need a gui or any intense software, so a linux terminal would still run fine on it.

A light bulb for over a century!  They made 'em good in the ol' days.

---

