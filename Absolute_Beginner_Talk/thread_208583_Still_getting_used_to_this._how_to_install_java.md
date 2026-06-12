---
title: "Still getting used to this. how to install java?"
date: 2006-07-03
forum: Absolute Beginner Talk
---

### Post by chrisdoesntknow on 2006-07-03
How do i go about isntalling java? I downloaded the jre-1_5_0_07-linux-i586.bin but now how do i go about installing it so i can actually use it?

Second question: How do i get movies to play in ubuntu?

My othe question is, on my powerbook how do i go about fixing the sensitivty of the touch pad?

its a 12" powerbook G4.

---

### Post by T700 on 2006-07-03
There is a program called [Automatix]("http://www.ubuntuforums.org/showthread.php?t=177646") that will automate installing Java, setting Ubuntu up so you can view movies, listen to most formats of music, and do many other little things to make life easier.  It is safe and simple--I highly suggest it.

Sorry, no idea on the touch pad.

Paul

---

### Post by meng on 2006-07-03
From repositories you can install jre 1.5.0 update 6, if you really need update 7 then you should follow the instructions on the sun website!
[http://java.sun.com/j2se/1.5.0/install-linux.html](http://java.sun.com/j2se/1.5.0/install-linux.html)

---

### Post by meng on 2006-07-03
Regards your other questions, Totem should be the default media player but depending on what type of movie you're trying to play you will probably need to visit: [http://wiki.ubuntu.com/RestrictedFormats](http://wiki.ubuntu.com/RestrictedFormats)

Regarding the touchpad, play around with the mouse settings. Not sure if this will work though, I haven't had much luck getting meaningful change in sensitivity on my Dell notebook in Xubuntu.

---

### Post by chrisdoesntknow on 2006-07-03
sorry. I've been out of it these past few hours. I've been up now for way too long. I'm still confused. What do i need to do to get java run time environment to work on my powerbook. (read: powerpc not x86 or AMD 64).

I appreciate the answers that were already given, but i'm still confused as to what exactly to do. A simplified answer would be great. :)

---

### Post by T700 on 2006-07-03
[quote=chrisdoesntknow]sorry. I've been out of it these past few hours. I've been up now for way too long. I'm still confused. What do i need to do to get java run time environment to work on my powerbook. (read: powerpc not x86 or AMD 64).

I appreciate the answers that were already given, but i'm still confused as to what exactly to do. A simplified answer would be great. :)[/quote]

Please reread my earlier answer.  It doesn't get any easier than to install a small program that will install Java and lots of other things that you'll soon be looking for.

Paul

---

### Post by chrisdoesntknow on 2006-07-03
i'm trying to install automatix fromt this guide, but i get a problem on line 34 or something like that. any advice?  [http://www.getautomatix.com/wiki/index.php/Installation#Installing_on_Ubuntu_6.06_Dapper_Drake](http://www.getautomatix.com/wiki/index.php/Installation#Installing_on_Ubuntu_6.06_Dapper_Drake)

---

### Post by T700 on 2006-07-03
[quote=chrisdoesntknow]i'm trying to install automatix fromt this guide, but i get a problem on line 34 or something like that. any advice?[/quote]

Without knowing exactly what you're having a problem with and the exact error, I couldn't even guess what's wrong.  See the link in my sig; it has a detailed explanation of Automatix and a link to *very* simple installation instructions.

Paul

---

### Post by mstlyevil on 2006-07-04
If all you want is java don't install Automatix just for that. Here is what you do. Open the terminal and paste these commands.

```
sudo apt-get update
sudo apt-get install sun-java5-jre
```

This will install sun java for you.

---

### Post by crystal on 2006-07-04
If you try what mstlyevil suggested and get a "cannot find package" kind of error, you might want to look in /etc/apt/sources.list

I am installing Sun's JRE now and had that problem. I had:
> deb [http://sg.archive.ubuntu.com/ubuntu/](http://sg.archive.ubuntu.com/ubuntu/) dapper universe
deb-src [http://sg.archive.ubuntu.com/ubuntu/](http://sg.archive.ubuntu.com/ubuntu/) dapper universe

## comments

deb [http://sg.archive.ubuntu.com/ubuntu/](http://sg.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://sg.archive.ubuntu.com/ubuntu/](http://sg.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

Apparently the problem is that Sun's JRE is available in dapper, not dapper-backports, so one should add 'multiverse' to the dapper related lines:

> deb [http://sg.archive.ubuntu.com/ubuntu/](http://sg.archive.ubuntu.com/ubuntu/) dapper universe multiverse
deb-src [http://sg.archive.ubuntu.com/ubuntu/](http://sg.archive.ubuntu.com/ubuntu/) dapper universe multiverse

## comments

deb [http://sg.archive.ubuntu.com/ubuntu/](http://sg.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://sg.archive.ubuntu.com/ubuntu/](http://sg.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

I was rather confused at the time and so added the lines instead of modifying the existing ones, so apt-get complained about duplicate package listings but continued anyway.

---

