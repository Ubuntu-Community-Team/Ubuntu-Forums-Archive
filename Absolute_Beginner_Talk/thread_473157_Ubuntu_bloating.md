---
title: "Ubuntu bloating"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by Wake Rider on 2007-06-13
I am running Ubuntu Feisty with the KDE desktop. I do a full backup of my system using the tar command. The first time I did it it was 1.4 GB. The second time 3.4 GB and now a third time at 7.1 GB. That is just the compressed archive. I checked the actual folder and it was over 10GB.  

I checked where I am keeping my files such as schoolwork etc which is only 600MB. I am concerned at the rate it is growing (all this happened in the last few weeks) as Ubuntu is on a 35GB partition. I keep my system up-to-date but surely the updates can't be taking that much space. I haven't installed anywhere near enough programmes to use that much space.

 I noticed the kernel was upgraded from .15 to .16. How do I get rid of .15 without damaging my system and why is it taking up so much space, growing so quickly??:confused:

---

### Post by chuckyp on 2007-06-13
You can get rid of the old kernels by just removing them sudo aptitude purge linux-image-2.6.20-15 etc.....  Also keep in mind all of your old packages are being kept in apts archive.  You can free up some space by running sudo aptitude autoclean   and  sudo aptitude autoremove.    Man aptitude to see what those do prior to doing it.

---

### Post by Inxsible on 2007-06-13
you should keep atleast one older and stable kernel ..just in case the new one gives you problems. I would advise you against removing it unless you have a few others

---

### Post by Wake Rider on 2007-06-13
> **Inxsible said:**
> you should keep atleast one older and stable kernel ..just in case the new one gives you problems. I would advise you against removing it unless you have a few others

oops I've removed the older kernel. The .16-generic is working for me so far, but I erased my security blanket of having .15-generic. I just wanted to save some space. The folder that is really becoming mega large is the home folder, yet my actual work is 600MB. I'm not sure what is causing the space blowout but I have tried the suggestion a few posts up to clear out those archives. I'm just concerned that if the system continues growing at this rate then within a few months it will be larger than the 35 GB partition it is on and then the real fun starts!:(

---

### Post by HotShotDJ on 2007-06-13
Its not the kernels.  I've been running Kubuntu 7.04 since the beta and my / partition has about 4 gig of files on it (22% of a 18.4 gig partition).  And I assure you, I have a full compliment of applications installed!  Something isn't right.  My first question... do you have both Gnome and KDE installed?  (I only have KDE).  However, the rate of growth of your / partition suggests your logs being the culprit.  Check out /var/log and see if anything catches your eye. Be on the lookout for lots of error messages in the files.  Also, from a command line, try running: ```
sudo apt-get autoclean
```

---

### Post by Wake Rider on 2007-06-13
> **HotShotDJ said:**
> Its not the kernels.  I've been running Kubuntu 7.04 since the beta and my / partition has about 4 gig of files on it (22% of a 18.4 gig partition).  And I assure you, I have a full compliment of applications installed!  Something isn't right.  My first question... do you have both Gnome and KDE installed?  (I only have KDE).  However, the rate of growth of your / partition suggests your logs being the culprit.  Check out /var/log and see if anything catches your eye. Be on the lookout for lots of error messages in the files.  Also, from a command line, try running: ```
sudo apt-get autoclean
```

Yes I have both Gnome and KDE installed. I prefer using KDE, it has a nicer look than Gnome. I will have a look at /var/log

---

### Post by Wake Rider on 2007-06-13
Here is the /var/log:

[IMG]http://i76.photobucket.com/albums/j10/Ajnos_91/var-log.png[/IMG]

---

### Post by Wake Rider on 2007-06-13
What exactly am I looking for that could be causing such a massive memory consumption?

---

### Post by Soybean on 2007-06-13
You say you used tar to make a full backup of your system... where did you put the resulting archive? If it's on your system somewhere, it could've gotten included in the next backup, which would definitely explain the exponential growth.

There's a tool that comes with Feisty called the "Disk Usage Analyzer" that might be helpful for finding out where all the space is being used up. It's under Applications->Accessories in Gnome... I don't have KDE installed, though, so I don't know where it is there. 

Oh, and HotShotDJ was probably suggesting that you check the sizes of the files in /var/log. So either ```
ls -lh
```
or browse to it in the GUI file manager and fiddle around with the settings until it tells you how big things are.

---

### Post by Wake Rider on 2007-06-13
> **Soybean said:**
> You say you used tar to make a full backup of your system... where did you put the resulting archive? If it's on your system somewhere, it could've gotten included in the next backup, which would definitely explain the exponential growth.

There's a tool that comes with Feisty called the "Disk Usage Analyzer" that might be helpful for finding out where all the space is being used up. It's under Applications->Accessories in Gnome... I don't have KDE installed, though, so I don't know where it is there. 

Oh, and HotShotDJ was probably suggesting that you check the sizes of the files in /var/log. So either ```
ls -lh
```
or browse to it in the GUI file manager and fiddle around with the settings until it tells you how big things are.

The resulting tar archive was shifted using the mv command on to an external hard drive.

---

### Post by Wake Rider on 2007-06-13
Wow, using the rm * wildcard in the trash folder reduced the size of my home folder from nearly 9 GB to 400 MB!! Thanks for your help guys!!

---

### Post by HotShotDJ on 2007-06-14
LOL... the simplest thing!!  And I didn't even THINK of that!

---

### Post by bodhi.zazen on 2007-06-14
LOL

this is why I like to add a delete to the menu and bypass the trash.

---

### Post by H.E. Pennypacker on 2007-06-16
You need to use Disk Usage Analyzer (Applications > Accessories) to see what is taking up space, and how much space.  Click on the scan button, and let it check the hard drive.

---

