---
title: "Development Builds"
date: 2006-11-14
forum: Absolute Beginner Talk
---

### Post by nickburns on 2006-11-14
Where do I find the latest development builds?  I would like to help test the next build and contribute with bug testing.  I have looked high and low for the page and cannot find it, any help?

---

### Post by livingtarget on 2006-11-14
A good place to start for any info on the development builds is the Feisty Fawn forums; [http://www.ubuntuforums.org/forumdisplay.php?f=177](http://www.ubuntuforums.org/forumdisplay.php?f=177)

To get to Feisty in theory you replace all occurences of edgy with feisty in your /etc/apt/sources.list

You'd probably want to open the sources list in a text editor:
> gksudo gedit /etc/apt/sources.list 
-or seeing as you are using xubuntu-
> gksudo mousepad /etc/apt/sources.list 

Then replace each word that is saying edgy to feisty. A find and replace will do the trick just fine.

Then either use apt-get or aptitude. Some people insist on aptitude so I'll give you that one first. More on aptitude vs. apt-get can be found here: [http://www.psychocats.net/ubuntu/aptitude](http://www.psychocats.net/ubuntu/aptitude) .
> sudo aptitude update && sudo aptitude dist-upgrade && sudo aptitude dist-upgrade 
or using apt-get
> sudo apt-get update && sudo apt-get dist-upgrade && sudo apt-get dist-upgrade 

That should get you into Feisty. Also make sure you have backed up your data and you know what you are doing.

---

### Post by grim918 on 2006-11-14
Why would you have to run dist-upgrade twice. I thought that you only needed to run it once.

---

