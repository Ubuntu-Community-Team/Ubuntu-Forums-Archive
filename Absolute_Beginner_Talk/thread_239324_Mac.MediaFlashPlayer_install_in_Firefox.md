---
title: "Mac.MediaFlashPlayer install in Firefox"
date: 2006-08-19
forum: Absolute Beginner Talk
---

### Post by amwil1024 on 2006-08-19
I'm stumped! I'm in Firefox and on Google video, but I can't play videos due to Firefox ain't got the Macromedia Flash Player Plug In.  Ain't that sweet!

I go to install but guess what? It don't install, says you gotta do it manually, so its getting sweeter!  No sweat, couldn't be any worse that the MMFP  downloads to desktop, click it and it's installed just like MS98SE right? Wrong!

It does download and I can see the 'tar' crap just sitting there all sweet as it can be, so I start clicking on any thing that says install, guess what , nothing happens.

MMFP web site says hey wait, just cut n paste this command in Terminal and your on your way, I do that and guess what, I'm not onmy way, no, not at all.

So, now I go to the forum here and do a search on, 'macromedia flash player install' and up pops a thread that starts talking about how sweet an easy it is to auto install Automatix or something like that, that will make my life a life of ease, as far as down loading and installing stuff. 

Real easy, yeah right, I see a spot about auto install of automatix and think I got it going on now baby!  I cut and paste the commands, one at a time as stated, all kinds of poop scrolls across the  terminal screen!  Yahoo, this has to be good! right? wrong!

Because I re-boot to be safe, run Firefox, open Google video, do the manual install thing once again for the MMFP, a screen comes up with open with X but I'm smart I open up and select automatix for sure, thats my savior, click my heart out, don't see anything, figure it musta done its thingy, reboot to be safe, run Firefox,open Google video, and guess what my friends? It tells me I have to install MMFP!!!!!!!

Cheese N Rice!!!!!!! I there anyone one here that can help an ole dumbass like me?????????????

---

### Post by EdThaSlayer on 2006-08-19
Ever tried going to the Add/Remove which can be found at the Applications menu?
Click on that(Add/Remove...) and type Macromedia in the search bar.

It should show you

Macromedia Flash Plugin
installer for the Macromedia Flash plugin for Mozilla(firefox is part of this too ^_^)

and just wait...restart the browser(who needs to restart the entire computer????)
and ta-daaaa!! It works...well it should work.

---

### Post by codejunkie on 2006-08-19
> **amwil1024 said:**
> I'm stumped! I'm in Firefox and on Google video, but I can't play videos due to Firefox ain't got the Macromedia Flash Player Plug In.  Ain't that sweet!

I go to install but guess what? It don't install, says you gotta do it manually, so its getting sweeter!  No sweat, couldn't be any worse that the MMFP  downloads to desktop, click it and it's installed just like MS98SE right? Wrong!

It does download and I can see the 'tar' crap just sitting there all sweet as it can be, so I start clicking on any thing that says install, guess what , nothing happens.

MMFP web site says hey wait, just cut n paste this command in Terminal and your on your way, I do that and guess what, I'm not onmy way, no, not at all.

So, now I go to the forum here and do a search on, 'macromedia flash player install' and up pops a thread that starts talking about how sweet an easy it is to auto install Automatix or something like that, that will make my life a life of ease, as far as down loading and installing stuff. 

Real easy, yeah right, I see a spot about auto install of automatix and think I got it going on now baby!  I cut and paste the commands, one at a time as stated, all kinds of poop scrolls across the  terminal screen!  Yahoo, this has to be good! right? wrong!

Because I re-boot to be safe, run Firefox, open Google video, do the manual install thing once again for the MMFP, a screen comes up with open with X but I'm smart I open up and select automatix for sure, thats my savior, click my heart out, don't see anything, figure it musta done its thingy, reboot to be safe, run Firefox,open Google video, and guess what my friends? It tells me I have to install MMFP!!!!!!!

Cheese N Rice!!!!!!! I there anyone one here that can help an ole dumbass like me?????????????
copy and paste this command in a terminal
```
mkdir ~/.mozilla/plugins
```
now go to a site that requires flash, that gives you the option to auto install the plugin like this one [www.kevinrose.com](www.kevinrose.com) yes im an old techtv fan for anyone that sees this and asks, and click the bar that pops up that says install missing plugins and flash should install automaticly this time.

---

### Post by codejunkie on 2006-08-19
> **EdThaSlayer said:**
> Ever tried going to the Add/Remove which can be found at the Applications menu?
Click on that(Add/Remove...) and type Macromedia in the search bar.

It should show you

Macromedia Flash Plugin
installer for the Macromedia Flash plugin for Mozilla(firefox is part of this too ^_^)

and just wait...restart the browser(who needs to restart the entire computer????)
and ta-daaaa!! It works...well it should work.
that will work, but only if the universe and multiverse repos are enabled in the /etc/apt/sources.list file.

---

### Post by amwil1024 on 2006-08-19
Yes, that almost worked, I went to 'add', did a search for MMFP, got it going, went to Google video, and video came up. 

Now here's the kicker, no sound!  

Honestly now gang, please tell me truthfully is Ubuntu really, really, really, ready to crush MS!?

I'll try one more time, can anyone help me get the sound function going???

---

### Post by codejunkie on 2006-08-19
> **amwil1024 said:**
> Yes, that almost worked, I went to 'add', did a search for MMFP, got it going, went to Google video, and video came up. 

Now here's the kicker, no sound!  

Honestly now gang, please tell me truthfully is Ubuntu really, really, really, ready to crush MS!?

I'll try one more time, can anyone help me get the sound function going???
click on System / Preferences / Sound and uncheck the box that says [B]Enable 
software sound mixing (ESD)[/B] and restart firefox, if this doesnt fix it you either need to logout then back in or try running ```
sudo killall esd
``` in a terminal then start firefox. this is assuming that your sound card was working before on other things but just not flash.

---

### Post by xpod on 2006-08-19
Having now been using Ubunto for two weeks AND having suffered the frustration of NO sound EVEN after getting automatix to install flash,java etc i am begining to realise this is probably one of the MOST common problems encountered by us here novices......
Second only to ALL the I.T experts who have trouble burning the ISO that is..

Mabey this could be one of the things the people who develop it all could look into making EVEN easier.
Would`nt it be GREAT for all those noobs just to be able to install and HAVE it all at least working properly.
All i had to do was use a couple of lines of code given by automatix arnie after i used automatix for the flash,java etc BUT had i not been pointed in the right direction i would probably STILL be there now fiddling about.

NOT all users are as keen as moi to keep pestering the forums OR even use the forums at all SO i can only imagine the problems some people are out there having....:confused: ](*,) .

YES it`s already easy to fix up(mmmmmm)......AND YES theres plenty good guides and threads relating to the prob BUT mabey just mabey things like this could be made simpler??????????

Personally i LOVE IT..The more problems the better(the more i then learn)

GOOD LUCK ANYWAY

---

### Post by EdThaSlayer on 2006-08-19
> **codejunkie said:**
> click on System / Preferences / Sound and uncheck the box that says [B]Enable 
software sound mixing (ESD)[/B] and restart firefox, if this doesnt fix it you either need to logout then back in or try running ```
sudo killall esd
``` in a terminal then start firefox. this is assuming that your sound card was working before on other things but just not flash.


and if that doesnt work you can always install alsa-oss(which works the best for me ^_^)

Go to the synaptic package manager and search for alsa oss...
after you have installed that create a shortcut to firefox on the desktop. You do that by right clicking and pressing Launcher.
So just type these things in
```

Name:Firefox
Generic Name:(leave this blank)
Comment:Web browser
Command:aoss firefox %u
```

or if you dont want to create such a shortcut right click on the firefox icon on the top left, to the right of "system", and just change the command to "aoss firefox %u"

Sound should work with flash now!

---

### Post by codejunkie on 2006-08-19
> **xpod said:**
> Having now been using Ubunto for two weeks AND having suffered the frustration of NO sound EVEN after getting automatix to install flash,java etc i am begining to realise this is probably one of the MOST common problems encountered by us here novices......
Second only to ALL the I.T experts who have trouble burning the ISO that is..

Mabey this could be one of the things the people who develop it all could look into making EVEN easier.
Would`nt it be GREAT for all those noobs just to be able to install and HAVE it all at least working properly.
All i had to do was use a couple of lines of code given by automatix arnie after i used automatix for the flash,java etc BUT had i not been pointed in the right direction i would probably STILL be there now fiddling about.

NOT all users are as keen as moi to keep pestering the forums OR even use the forums at all SO i can only imagine the problems some people are out there having....:confused: ](*,) .

YES it`s already easy to fix up(mmmmmm)......AND YES theres plenty good guides and threads relating to the prob BUT mabey just mabey things like this could be made simpler??????????

Personally i LOVE IT..The more problems the better(the more i then learn)

GOOD LUCK ANYWAY

I agree I think packages should just work out of the box but that's hard to do in linux. being a long time linux user, I know in linux almost anything is possible given enough dedication and reading guides, and i know choice is great, but choice is my biggest grip with linux there are just two many choices to do one simple thing. 

This also makes integrating applications and making them work out of the box very hard consedering the number of desktop enviorments there are, sound systems, video systems etc.

take for instance mplayer if you want to watch online videos in linux you need it. how can it work out of the box, when if you want to use it in gnome you need to configure it to use the esd or oss sound system, if you want to use it in kde you need to configure it to use the arts sound server etc you might even have to configure your video card depending on it's type.

there's just no intergration between desktop enviorments, applications, and distros and there needs to be. and this drives new and old users crazy trying to get things installed and setup when theres no standard way of doing things because this developer likes to put things here, and another developer likes to put the same thing somewhere else because he doesn't want to be like the other guy. ok im going to stop ranting now, id love to see applications work out of the box in linux to but the way it looks thats not coming any time soon.

---

