---
title: "Manual Partitioning with Live CD/Green user"
date: 2007-11-15
forum: Absolute Beginner Talk
---

### Post by Paradoxfox93 on 2007-11-15
Since thi sis my firs tpost I'll give a short intro.  I consider myself fairly intelligent and moderately computer savy.  I just bought a laptop and as I've desired to put linux on it, a techie at my job reccomended Ubuntu.  So I've checked it out and like what I see enough to give it a run.  I've bought a Gateway laptop with what was supposed to be a an AMD Athalon 64 X2 1.6ghz, 1Gb, 160gb, and turned out to be a Turion (With all the same specs).  Anyway, So I've run live CD and done memory test and Verified CD integrity.  This is what I'd like the partitioning of my 160GB HD to look like

20GB - Ubuntu Instillation
10GB - Xubuntu Instialltion
1Gb - Swap
129Gb - General Data

So I have Partitioned that way.  I have the 20 marked as "/" for the root file system.    But I find I'm completely Clueless as to how I should really mark the rest.  What "Type"? Type is currently set to "ext3."  Currently I have them all as "Logical" Partitions.  Should I set the 20Gb as "Primary" or the 129gb?  Anything else you think a greenie would find helpful would be greatly appreciated.

Also...Here's a great bit of humor...the Vista CD that came with the laptop was for a 32bit computer...but damn if they didn't include the CD that would allow me to easily ~purchase~ the fabulous "Live Upgrades"!!!

---

### Post by DutyDuty on 2007-11-15
Someone, correct me if I'm wrong, but installing Xubuntu separately is pointless since Xfce can be downloaded separately and installed as a session to run instead of GNOME. Sorry that I can't tell you much more.

---

### Post by overdrank on 2007-11-15
> **Paradoxfox93 said:**
> Since thi sis my firs tpost I'll give a short intro.  I consider myself fairly intelligent and moderately computer savy.  I just bought a laptop and as I've desired to put linux on it, a techie at my job reccomended Ubuntu.  So I've checked it out and like what I see enough to give it a run.  I've bought a Gateway laptop with what was supposed to be a an AMD Athalon 64 X2 1.6ghz, 1Gb, 160gb, and turned out to be a Turion (With all the same specs).  Anyway, So I've run live CD and done memory test and Verified CD integrity.  This is what I'd like the partitioning of my 160GB HD to look like

20GB - Ubuntu Instillation
10GB - Xubuntu Instialltion
1Gb - Swap
129Gb - General Data

So I have Partitioned that way.  I have the 20 marked as "/" for the root file system.    But I find I'm completely Clueless as to how I should really mark the rest.  What "Type"? Type is currently set to "ext3."  Currently I have them all as "Logical" Partitions.  Should I set the 20Gb as "Primary" or the 129gb?  Anything else you think a greenie would find helpful would be greatly appreciated.

Also...Here's a great bit of humor...the Vista CD that came with the laptop was for a 32bit computer...but damn if they didn't include the CD that would allow me to easily ~purchase~ the fabulous "Live Upgrades"!!!

HI and welcome, I would suggest combining the 20gb and 10gb partition because you can install XFCE on ubuntu and have the same thing. Then 129gb just format a fat32.  But that is my opinion.

---

### Post by Paradoxfox93 on 2007-11-15
I want a clean install.  Like I said I'm pretty green about linux.  I want something that's not going to contain all the installed crap that I'm going to put on ubuntu.  I will use Xubuntu for work where I pretty much just need firefox (and a music player of course;-D)  so that It will be faster, lighter, etc. etc. and the stuff I'm not using while working will not get in the way.  Any Links to a how to for GParted and partitioning in general would be helpful.  I'm googlin' it right now and have been for about an hour now with out finding what I'm looking for.  I suck at google :(

---

### Post by Paradoxfox93 on 2007-11-15
> **overdrank said:**
> HI and welcome, I would suggest combining the 20gb and 10gb partition because you can install XFCE on ubuntu and have the same thing. Then 129gb just format a fat32.  But that is my opinion.

Ya know I CONSIDERED myself pretty computer savy...but the more and more I dig around with this linux busniess I feel like I'm jsut waaaay out of the loop.  I really have no idea what you mean.  I know what fat32 is I didn't know linux if linux could read that or not.  Or even what the hell ext3 is.  It's just the default more or less.

I ain't sweatin' it really.  I know I'll figure it out.  I'm patient and and stubborn (A Taurus no doubt).

---

### Post by overdrank on 2007-11-15
> **Paradoxfox93 said:**
> I want a clean install.  Like I said I'm pretty green about linux.  I want something that's not going to contain all the installed crap that I'm going to put on ubuntu.  I will use Xubuntu for work where I pretty much just need firefox (and a music player of course;-D)  so that It will be faster, lighter, etc. etc. and the stuff I'm not using while working will not get in the way.  Any Links to a how to for GParted and partitioning in general would be helpful.  I'm googlin' it right now and have been for about an hour now with out finding what I'm looking for.  I suck at google :(
Maybe this thread
[http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018)

---

### Post by overdrank on 2007-11-15
> **Paradoxfox93 said:**
> Ya know I CONSIDERED myself pretty computer savy...but the more and more I dig around with this linux busniess I feel like I'm jsut waaaay out of the loop.  I really have no idea what you mean.  I know what fat32 is I didn't know linux if linux could read that or not.  Or even what the hell ext3 is.  It's just the default more or less.

I ain't sweatin' it really.  I know I'll figure it out.  I'm patient and and stubborn (A Taurus no doubt).

I was in no way trying to imply that that you are not computer savy. I was just giving another option and my opinion. :)

---

### Post by Duck2006 on 2007-11-15
> **Paradoxfox93 said:**
> Since thi sis my firs tpost I'll give a short intro.  I consider myself fairly intelligent and moderately computer savy.  I just bought a laptop and as I've desired to put linux on it, a techie at my job reccomended Ubuntu.  So I've checked it out and like what I see enough to give it a run.  I've bought a Gateway laptop with what was supposed to be a an AMD Athalon 64 X2 1.6ghz, 1Gb, 160gb, and turned out to be a Turion (With all the same specs).  Anyway, So I've run live CD and done memory test and Verified CD integrity.  This is what I'd like the partitioning of my 160GB HD to look like

20GB - Ubuntu Instillation
10GB - Xubuntu Instialltion
1Gb - Swap
129Gb - General Data

So I have Partitioned that way.  I have the 20 marked as "/" for the root file system.    But I find I'm completely Clueless as to how I should really mark the rest.  What "Type"? Type is currently set to "ext3."  Currently I have them all as "Logical" Partitions.  Should I set the 20Gb as "Primary" or the 129gb?  Anything else you think a greenie would find helpful would be greatly appreciated.

Also...Here's a great bit of humor...the Vista CD that came with the laptop was for a 32bit computer...but damn if they didn't include the CD that would allow me to easily ~purchase~ the fabulous "Live Upgrades"!!!

I would partition as

10Gb for /  root
20Gb for /home
 1Gb for /linux swap
the rest for what you want

as for xubuntu you can load the desk-top in to ubuntu install

sudo aptitude update && sudo aptitude install xubuntu-desktop

---

### Post by Paradoxfox93 on 2007-11-15
> **overdrank said:**
> I was in no way trying to imply that that you are not computer savy. I was just giving another option and my opinion. :)

Naw...It's just been a growing feeling since I started digging around about ubuntu and linux since I began anticipating the arrival of my own computer, which I always swore I'd put linux on.  I might express it as less about savyness than just...well...I can tell right off the bat I have a lot to learn!

---

### Post by Paradoxfox93 on 2007-11-15
> **Duck2006 said:**
> I would partition as

10Gb for /  root
20Gb for /home
 1Gb for /linux swap
the rest for what you want

as for xubuntu you can load the desk-top in to ubuntu install

sudo aptitude update && sudo aptitude install xubuntu-desktop

Does that still provide me with the speed and efficiecy of Xubuntu? Does it get "weighed down" with all the installe dprogs that I throw onto Ubuntu?  More I think about it...I think I'm just used to windows wasting my resources

---

### Post by Duck2006 on 2007-11-15
> **Paradoxfox93 said:**
> Does that still provide me with the speed and efficiecy of Xubuntu? Does it get "weighed down" with all the installe dprogs that I throw onto Ubuntu?  More I think about it...I think I'm just used to windows wasting my resources

Yes it will work ok, at the log on screen you can pick gnome or Xfce and log in.

---

