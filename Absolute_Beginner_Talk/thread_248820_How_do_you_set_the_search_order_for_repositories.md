---
title: "How do you set the search order for repositories"
date: 2006-09-01
forum: Absolute Beginner Talk
---

### Post by whein on 2006-09-01
Silly question maybe, but is it possible to specify what order the available repositories get searched in to download/install packages?  I have a _really_ slow dial-up internet connection so I like to download any big files at work and carry them home on a USB drive.  I was able to set up a local repository on my machine using the directions at ["Can a local folder be added as a repository?"]("http://www.ubuntuforums.org/showthread.php?t=217816") (MANY MANY thanks for them btw) and it works great if I am not connected to the internet.  But sometimes it is easier for me to download one big file at work and then let Synaptic take care of finding all the little files to satisfy the dependancies.  Right now it always wants to download the big files even if I already have a copy in my local repository folder.  How do I change this?  I've tried changing the order of the lines in /etc/apt/sources.list and nothing seemd to change.  Enabling and disabling the internet repositores every time is a royal pain.  Also makes me redownload the index files every time I enable/disable, and that eats up a lot of download time as well.  Any ideas?
-Will

---

### Post by Klaidas on 2006-09-01
i don't know if this would work, but what if you re-ordered them in sources.list? (Just make a backup of it before trying this!)

Anyway, I think it would scan all of them :-k

---

### Post by whein on 2006-09-01
I already tried reordering sources.list, no dice.  I don't mind them scanning so long as I only have to scan once in a while.  But having to enable/disable and then reload the listings several times in a night means several rounds of 10-20 minute breaks.  Ouch!  :(
-Will

---

### Post by Bachstelze on 2006-09-01
Just create a temp dir in your home, put the downloaded DEB in it, open up Synaptic, File, Add downloaded packages, browse to the dir, voilà :)

---

### Post by msak007 on 2006-09-01
You may want to try using the apt preferences file to pin a priority on your local repo. The file doesn't exits by default (at least not on my machine), so create it first
```
sudo nano /etc/apt/preferences
``` 
and add this entry in it:

```
Package: *
Pin: origin ""
Pin-Priority: 999
``` This will pin your local repo as having a greater priority than all other repos, and will always search your local repo first and install an app from it (if available) even if there is a newer version in another repo. I would suggest changing the priority to 990, which will still check your repo first but will install the app in question from another source if a newer version is available. Try that and let me know how it works.

---

### Post by whein on 2006-09-01
Thanks for the help guys!  Yay!

HymnToLife:
I tried this and it seemed to want to install ALL of the files in the directory.  I just want to have them listed and then pick and choose, like I would for repositories on the Internet.

msak007:
Worked (eventually) :D
A note to other newbies to avoid some headaches, after creating/modifying the preferences file, you have to at the very least reload the package listings, and I also closed and reopened Synaptic to be safe.  Actually I closed and reopened Synaptic without reloading the package lists many times and had typed out a long reply before the light bulb went on and I figured out what I needed to do.  :)
-Will

---

### Post by msak007 on 2006-09-01
> **whein said:**
> msak007:
Worked (eventually) :D
A note to other newbies to avoid some headaches, after creating/modifying the preferences file, you have to at the very least reload the package listings, and I also closed and reopened Synaptic to be safe.  Actually I closed and reopened Synaptic without reloading the package lists many times and had typed out a long reply before the light bulb went on and I figured out what I needed to do.  :)
-Will

I'm glad it worked for you - it was a stab in the dark as I've never done that before. We both learned somethin new today :). Sorry I didn't mention to you that you do an update afterwards, I assumed it was a given any time you make any changes to apt or its preferences (sources.list, apt.conf, preferences, etc.) that you do an apt-get update afterwards. You know what they say about assuming though...Anyway I have one question - did you set the  priority as 990 or 999?

---

### Post by whein on 2006-09-02
I used the 990 setting.  I haven't checked whether this setting lets the newer online versions override older local versions, but it did the trick for making local versions ovverride online versions with the same revision level.  Thanks again!
-Will

---

