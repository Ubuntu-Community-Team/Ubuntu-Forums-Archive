---
title: "Fresh Installation Script for Macbook Pro 3,1"
date: 2010-05-03
forum: Apple Hardware Users
---

### Post by hellmitre on 2010-05-03
Hey kids, I've written a script that takes a brand new fresh installation of Ubuntu and configures everything for you. It installs smcfancontrol, a script written very wonderfully by joushou (over at [http://ubuntuforums.org/showthread.php?t=1102465&highlight=smcfancontrol]("http://ubuntuforums.org/showthread.php?t=1102465&highlight=smcfancontrol")) to be a bit more strict about heat issues on Macbook Pros. It installs pommed (an Apple hotkeys manager, which provides keyboard backlighting) as well as kernel modules to allow hardware information to be accessed. It is divided into two sections; one installs only the base software for better hardware management (backlighting, heat control); the second installs the development and desktop software that I personally like on my machine. 
This script has been tested several times on my machine and has served me well, significantly cutting the overhead time for taking a fresh installation of Ubuntu and configuring it all the way I like. It walks you through every step. 

I've enjoyed writing it and I hope it proves useful for someone else. :D

Latest version can be had by downloading it straight from my server; if that's down, the link below is probably relatively up-to-date.
Server link: [http://hellmitre.homelinux.org/hosted/fresh.sh]("http://hellmitre.homelinux.org/hosted/fresh.sh")

EDIT: The script now offers two options: entirely automated, doing everything without prompting; and step by step.

---

### Post by linuxopjemac on 2010-05-04
nice

---

### Post by damagu on 2010-05-19
As soon as I have a chance to backup my data, I'm gonna do a clean install of Lucid on my Macbook Pro 3,1 and give this script a try. It looks like it does a lot of the stuff I normally spend ages doing but a lot more too. Thanks so much for sharing it.

---

### Post by hellmitre on 2010-06-03
Glad you could find some use for it :). It's saved me quite a bit of time. I'm not taking any classes over the summer, only working, and once I've got a bit of free time I'm going to add some extra functionality to this; i.e., a fully automated installation that asks you no questions and installs everything.

---

### Post by damagu on 2010-06-22
I just tried running the script and got this error:

[FONT="Courier New"]$ sudo ./fresh.sh 
[: 15: Illegal number: 
./fresh.sh: 60: Syntax error: "fi" unexpected (expecting "then")
[/FONT]

Sorry

---

### Post by hellmitre on 2010-06-22
It's fixed.

---

