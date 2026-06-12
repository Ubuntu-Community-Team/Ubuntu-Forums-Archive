---
title: "brand new-bie"
date: 2006-11-02
forum: Absolute Beginner Talk
---

### Post by hotballz87 on 2006-11-02
so i just installed ubunto today, but have no idea what im doing, i need help setting everything that i had back up.......

1. how do i run dual monitors, im lost on this one to begin with

2. i have all these programs that run for windows and mac, but not a linux based OS. is there a program i can get to install these?

3. i have a widescreen monitor. how do i change the res. to get it to match? all the resolutions are for a regular monitor.

    thanks for the info, and i hope this is better than windows.....

---

### Post by _lynX on 2006-11-02
> **hotballz87 said:**
> so i just installed ubunto today, but have no idea what im doing, i need help setting everything that i had back up.......

1. how do i run dual monitors, im lost on this one to begin with

2. i have all these programs that run for windows and mac, but not a linux based OS. is there a program i can get to install these?

3. i have a widescreen monitor. how do i change the res. to get it to match? all the resolutions are for a regular monitor.

    thanks for the info, and i hope this is better than windows.....

First off, welcome to Ubuntu!

1) I don't know the answer to this, so I'll leave it for another member to answer.

2) You can install wine, a Windows compatibility layer, from the repos by opening the [Terminal](http://www.psychocats.net/ubuntu/terminal) and typing *sudo aptitude install wine*. You can then run .exe files by right-clicking them and choosing the "Open with 'Wine Windows Emulator'" option.

*Please note that not all applications will run using Wine. You can find which will probably work by viewing the AppDB at [http://www.winehq.com/](http://www.winehq.com/).*

3) I know how I would do this, but I am not sure it is the safest way, so I'll let someone else reply to this one as well. (Maybe I'll learn something new as well)

Good luck!

---

### Post by Scheater5 on 2006-11-02
Welcome to the world of linux and ubuntu.  First of all, what version of Ubuntu are you using?  I would assume either 6.06, "Dapper Drake," or 6.10, "Edgy Eft."  Many users, myself included, have had problems with the monitor settings in the new 6.10, and some are not easily resolved.  
Unfortunately I'm afraid I can't help you, assuming you are using Gnome, the default Ubuntu desktop manager, since that is not what I use normally.  I just booted into Gnome and checked it out and there seems to be no easy way to change the settings to something that is not detected automatically.  
Speaking of which, perhaps it is that your monitor has been detected incorrectly - look under the Preferences menu for something related to that (I'm afraid I'm not familiar enough with Gnome).  If you find it, Ubuntu has probably selected "plug 'n play" for your monitor, which under normal circumstances works fine - but I know that I myself had problems with my widescreen.  I had to change it to a "generic" monitor with my dimensions to get the proper resolution to show up in the "screen resolution" settings menu.  
If this doesn't work, then you may have to manually edit a text file known as Xorg (or, X.org) which contains many of your system's settings.  I typically don't use Gnome, so if this instructions are not detailed enough, I will leave it to another member to "flesh them out."

---

### Post by adam.tropics on 2006-11-02
How you set up dual monitors depends largely, as far as I am aware, on what video card your system uses. Which resolutions are available, depend that you have the correct card using the correct video drivers. So in order, you need to check what video card you have, and just ensure you have the correct drivers installed. Then look into the resolution and dual screen setup. Also be aware that unless there has been some development I am not yet aware of, which is entirely possible, you may run into further resolution issues with your widescreen monitor...ie it helps if both screens can use the same resolution. But first thing is to make sure the video drivers are good then move on from there. You will find many many posts here with regards to your particular video card I assure you, just use the search... Post back if you are still stuck.

---

### Post by insub2 on 2006-11-02
1. I don't know this one.  I suggest searching the forums to see what you can get.

2. _lynx told you truth.

3. I had (basically) the [same problem]("http://www.ubuntuforums.org/showthread.php?t=104893") when i was a newbie. (I'm assuming you are using Gnome/regular Ubuntu)

What you need to do is edit your xorg.conf file.
First, open a terminal back it up
```
$ sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```
Then edit it
```
$ gksudo gedit /etc/X11/xorg.conf
```
this will open the file in gedit where you can change it.
in the **"Monitor"** section, make sure the **HorizSync** and **VertRefresh** match your monitor.  You should be able to find this in the manual or a google search "*your monitor* horizsyng wertrefresh"
Then in the "Screen" section, add the resulution you want to use to all the lines that start with "Modes"

If something goes wrong, you can restore to the backup with
```
sudo mv /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```

Good luck and Welcome to the beautiful world of linux!!!

---

### Post by mahy on 2006-11-02
Ad 2) The old saying goes "When in Rome, do as the Romans do". They same applies here. You should learn to use Linux programs wherever possible and only use foreign apps as the last resort. I'm pretty sure you'll find (with some guided help) a replacement for every piece of software you use in windows and/or MacOS.

---

