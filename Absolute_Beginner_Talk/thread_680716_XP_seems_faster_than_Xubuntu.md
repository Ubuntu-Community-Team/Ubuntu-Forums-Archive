---
title: "XP seems faster than Xubuntu"
date: 2008-01-28
forum: Absolute Beginner Talk
---

### Post by philtbelfast on 2008-01-28
Installed Ubuntus on several computers now, all working well and quickly.

But recently put Xubuntu on my Dad and Sister's older computers it seems to be significantly slower than XP.

Any ideas why this would happen?

One computer is a desktop

Intel Pentitum 4 3Ghz
248mb RAM

The other is a laptop

Intel Celeron M 1.3Ghz
248mb RAM

Kinda stumped about this.

---

### Post by LukeCarrier on 2008-01-28
Hey there,
 
How many sticks of RAM do you have, and what are their sizes? Using two sticks of different sizes or one faulty one can greatly decread the performance of a computer.
 
Luke

---

### Post by scrooge_74 on 2008-01-28
Describe slow?

I am running xfce4 and it been quicker than old XP on this same system the moment I installed

---

### Post by philtbelfast on 2008-01-28
Hey guys,

The RAM is fine on both theres just not very much of it.

By slow I mean when more than one thing is running it is at a crawl. Windows grey out and take ages to reappear etc etc. 

I reinstalled XP this morning and theyre both quite nippy, although I can imagine in a few weeks theyll probably be back at a crawl.

---

### Post by dgray_from_dc on 2008-01-28
It may be the release.  I have a 733Mhz /w 128MB of RAM.  I've used Dapper with no issues or lag.

I was forced to go to Gutsy for a few software changes that I needed and there is now significant lag for things as simple as starting Firefox or using the command line in the GUI.  It's almost as if I'm using Gnome or KDE now.

For me, it doesn't matter because I'm using it as a server.  Local logins are for admin only.

---

### Post by LaRoza on 2008-01-28
You are using a new operating system on an old computer. XP is over six years old.

You can try other distros for speed, or getting more RAM. The Other OS Talk forum has a sticky on it.

---

### Post by ijason on 2008-01-28
i would presume that it's a hardware incompatibility issue. not one severe enough to break the OS, but enough to lag it severely. i would try a few different versions, as others have suggested. 

i'm running 7.10 on a desktop that's over TEN years old!!! a busted old 750mhz system, although, it does have a little more ram, at 512megs. 7.08 performed very poorly, but when i switched to 7.10, things move along MUCH faster than it did for windowsXP

hardware wise, the most likely culprit is your video-card. do some snooping on the forum to see if anyone else has had problems with your specific video-cards and ubuntu. you may need to update the drivers and then things will speed right along.

---

### Post by Joeb454 on 2008-01-28
Like LaRoza said, check out the Other OS Talk sub-forum :)

Also, I'll recommend you one right here: [fluxbuntu]("http://www.fluxbuntu.org/js.html")

---

### Post by ijason on 2008-01-28
@job454

*snort* i love that fluxbuntu's website layout fails on firefox. text over-running container elements and being hidden by buttons.

---

### Post by seventhc on 2008-01-28
Celeron processors arent known for their speed either. I've worked on a lot of different computers, and anytime I was on a celeron, it was extremely slow. IMO no matter whats on a celeron it will be slower than it should be.

---

### Post by LaRoza on 2008-01-28
> **ijason said:**
> @job454

*snort* i love that fluxbuntu's website layout fails on firefox. text over-running container elements and being hidden by buttons.

Use Opera :)

@OP You can install Fluxbox on Xubuntu, without getting another distro

---

### Post by Dr Small on 2008-01-28
> **ijason said:**
> @job454

*snort* i love that fluxbuntu's website layout fails on firefox. text over-running container elements and being hidden by buttons.
I run Firefox, and that never happens to me...

---

### Post by philtbelfast on 2008-01-28
Hey cheers for all the suggestions

I looked into it the laptop was a Dell 2200 with Intel GMA 900 graphics which some people have been having trouble with.

I then looked into the desktop a Dell 3200C with (drum roll) Intel GMA 900 graphics.

I then had another search around and some other people have been having trouble with this card being sluggish.

Funny how you often find out what the problem is a short while after asking.

Does anyone have any suggestions for distros that might support this better? 

Cheers

---

### Post by jordanmthomas on 2008-01-28
What does this output?
```
cat /etc/X11/xorg.conf | grep Driver
```
If yours has "intel" as one of the drivers you may want to try installing the i810 driver instead and using it.  I have Intel 915GM and although the intel driver supports it, i810 has been much faster lately (not sure why this is as the intel driver used to be faster).

Also, graphics card support doesn't really vary from distro to distro, at least not by much.  Mine works slightly faster in ArchLinux than Ubuntu, but then again so does everything else.

---

### Post by philtbelfast on 2008-01-28
Sorry cant run the terminal command as, per their nagging, I reinstalled XP for both of them.

This post was really more out of my own curiosity and desire to learn something.

Its also a great example of why I love Ubuntu. In less than one hour Ive had 14 responses. Pretty darn good I'd say.

---

### Post by Joeb454 on 2008-01-28
Well if we solve problems quickly, then people will be more willing to stay ;)

---

