---
title: "Need a little help with fresh install of ubuntu 6.10 alternate"
date: 2006-12-26
forum: Absolute Beginner Talk
---

### Post by fsando on 2006-12-26
I've just installed from the ubuntu 6.10 alternate cd in a dual boot setup (XP/ubuntu)
My system:
Notebook Asus W1J core2duo 2.16, ati x1600 1680x1050
The situation:
Before installing I created an empty space with partition magic, I let the installation install in the empty space. Installation apparently ran without any hickups.
Booting seems fine too: Grub appears to work, I can choose between xp and ubuntu, there are those extra choices for recovery, memcheck etc.

My problem:
Booting runs smoothly and ends up at the desktop (I suspect) because 
after boot my screen is skewed so it is unreadable. I presume this is related solely to my screen/video card in some way.

After a boot into recovery mode I looked at xorg.conf - it contains a bunch of entries refering to ati and to my screen. They all show the correct resolution with different color depths.

I am determined to have linux installed and at the moment ubuntu has been, by far, the most attractive distro - so I just need to iron out this hopefully small isue.

How to solve this? - I'm guessing
1) Update the ati driver - how to do this from recovery mode?
2) Change some settings in xorg.conf - what should I write here?
    2a) Tried vi but don't know how to save from vi
Perhaps this notebook/ati card is not yet supported in ubuntu? Therefore last option:
3) Wait some months until ubuntu supports this notebook/ati supports ubuntu?

Does anyone have a suggestion - perhaps you even know what my problem is.
Thanks in advance

---

### Post by adewale on 2006-12-26
sorry i can only help you with how to save press esc then colon then press wq

---

### Post by fsando on 2006-12-26
Hi adewale
Thanks that helps too ;) - when you are an absolutely newbie like me, even the most trivial knowledge becomes a major obstacle that may halt any further progress.
fsando

---

### Post by foolsh on 2006-12-26
yes sounds like a xorg.conf problem

1:) not sure i'll get back to you on that one maybe

2:) you could change the default bitdepth to 16 perhaps 24 32 bits is to high, or change the video card driver to vesa its a generic video driver, remove resolution entries that are to high for your monitor i.e. 1024x1024 which is to high for my POS monitor

2a:)vi is really cool i like it
to edit a document press the insert key first
to save a document press escape then type :w! and hit return
to exit press escape and type :q! and hit return


3:) dunknow bout this one updates happen all the time


when you boot up normally and the screen goes blank press control+alt+f1 or any fkey from 1to6 
this should get you to a console to log in
to edit the xorg.conf file use
sudo vi /etc/X11/xorg.conf
to check if you changes worked 
sudo /etc/init.d/gdm restart
for ubuntu
or 
sudo /etc/init.d/kdm restart
for kubuntu

post your xorg.conf file here and we can probly help


---i love lists---

---

### Post by fsando on 2006-12-26
Hi foolsh
Thanks for your reply I am going to research this in more detail

> **foolsh said:**
> 

post your xorg.conf file here and we can probly help



I'd love to,  but it proves a little hard - I'm actually in somewhat of a maze of catch 22s:
- When in recovery mode I don't know how to access the Internet let alone post here.
- I have no access to external drives - at least I don't know how to get acess
- I don't even know how to access my local windows partitions
- from windows I can, of course not access ubuntu

One thing, though, that might work is booting the livecd it may be able to access my installed ubuntu partition? I got the livecd to work in 1024x768 with full net access.

But they are going to show lord of the rings on a local channel in a few minutes time so I'll be 'gone' for the rest of the evening. ;)

I'll be back soon, though, if I survive the onslaught of the dark force.

---

### Post by Hendrixski on 2006-12-26
Sounds like you've got some fun ahead of you.  :)  You may find it's not easy at times, but it's always fun, and when you finally get it then you'll be so proud of yourself that you'll gloat to all of your friends.

Did you have the same problem with the skewed screen when you were running the live CD, or did the skewing happen after you executed a command or something?

if you're in safe mode without the visual interface you can still connect to the internet.  Install lynx or another text based browser.  It's really cool... just, doesn't have all the multimedia stuff.  you may have to "sudo apt-get install lynx".  Also you can change directories with "cd"  ... so "cd /etc/X11" will get you to the directory you need and then "pico xorg.conf" shows you the conf file.  you can then cut and paste it into into this forum through lynx.

There's probably an easier, less nerdy, way to do that... don't listen to me, I'm an old school UNIX fan, so I still do everything through command line.  But if you're up for a challenge.  :)

---

### Post by TooRight on 2006-12-26
Do you perhaps need different video drivers?

I had to do:

> 
sudo apt-get update
sudo apt-get install linux-restricted-modules-$(uname -r)
sudo apt-get install xorg-driver-fglrx
sudo depmod -a
sudo aticonfig force--initial
sudo aticonfig --overlay-type=Xv
sudo shutdown -r now


to get my ubuntu looking right

---

### Post by sindrum_murdnis on 2006-12-26
I have the same video card and have had the same problem. my solution is posted here

[http://ubuntuforums.org/showthread.php?t=310189](http://ubuntuforums.org/showthread.php?t=310189)

check it out see if this helps. I have pics posted with my problem so maybe you can compare.

---

### Post by fsando on 2006-12-26
THANKS everybody
I'm posting from ubuntu with the correct screen resolution, and I am happy.
The ring was destroyed and the dark forces were defeated ;)

I followed this advice:

> **TooRight said:**
> Do you perhaps need different video drivers?

I had to do:

```
sudo apt-get update
sudo apt-get install linux-restricted-modules-$(uname -r)
sudo apt-get install xorg-driver-fglrx
sudo depmod -a
sudo aticonfig force --initial
sudo aticonfig --overlay-type=Xv
sudo shutdown -r now
```
to get my ubuntu looking right

And thanks to sindrum_murdnis's link:
Then added this to /etc/X11/xorg.conf (before the last shutdown command - I should probably have started with this but it works now):
Btw vi is at bit confusing to work with.
```
Section "Extensions"
        Option "Composite" "Disable"
EndSection

```

To Hendrixski
Yes I had the same problem with the livecd. It would either stop midway or end at the skewed screen. Under further options (F6) I removed the "quiet" to see what happens, and it turns out it always stops at
'configuring network interfaces'  pressing Ctrl+Alt+Del will allow the process to continue and it ends at the 1024x768 readable screen. That's why i figured it had to be solvable.

To sindrum_murdnis
My problem may be the same but it looked different. My screen was completely unreadable, it was very very skewed, looked mostly as if some signals were out of sync, for instance the login menu would stretch across most of the screen - the upper edge of the menu would be at the right side of the screen and the lower edge would be to left side and the short vertical sides would stretch across.

Thanks to all for your helpful answers
Fsando

---

