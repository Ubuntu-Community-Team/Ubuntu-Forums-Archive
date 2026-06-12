---
title: "[SOLVED] Unable to perform partial upgrade -- what did I mess up ??"
date: 2007-09-15
forum: Absolute Beginner Talk
---

### Post by jerrynewt on 2007-09-15
Hello again everyone -- I have another problem for some of you gurus. Just got back in town after a few weeks of work in Louisiana and fired up the old pc. I have dual boot feisty and gutsy. Went into gutsy and found I had about 11 updates available so I downloaded and installed them. So far no problems. About ten minutes later the update icon shows up again, but this time it says there are 229 updates available !! One of them is the newer kernel (I currently running 2.6.22-10 generic). When I try and do the updates I get a message saying I can only do a partial upgrade. When I try and do the partial, the process goes to "reading cache" for about five minutes then the progress bar and info box kind of "bleach out" (the box remains but no progress bar or lettering) and no further activity of any kind. I can still go to another workspace and log on to the internet and everything else just fine, but nothing on the first workspace changes unless I restart x or reboot. Then the same thing happens all over again. Any ideas as to what is happening or how to deal with this problem? This just started when I got back yesterday. Thanks for your time.

---

### Post by Hospadar on 2007-09-16
Is it possible that you are out of hard disk space?  when you install (or upgrade) a new package it downloads the whole package to /var/cache/apt (or something like that, you'll know you've found it when you find a huge folder full of .deb files)  so if your disk is full you might try deleting some of these cached package files.

Also, what happens if you just try selecting a few of the upgrades at a time (like try deselecting them all and do just the first one, then try bigger and bigger chunks).

And lastly, though I doubt it will make a difference, you could try running the update from the command line.  I believe you will want to do ```
sudo apt-get update
sudo apt-get dist-upgrade
```

---

### Post by jerrynewt on 2007-09-16
A gold star for you today !!! Worked like a charm and I'm back in business. Thanks for the reply and help. Did the sudo apt-get update and sudo apt-get upgrade and everything updated and upgraded just fine. Thanks again and again and again !!

---

