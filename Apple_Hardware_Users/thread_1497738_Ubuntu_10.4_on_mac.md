---
title: "Ubuntu 10.4 on mac"
date: 2010-05-31
forum: Apple Hardware Users
---

### Post by theminipimp on 2010-05-31
I am having problems running Ubuntu lucid lynx on mac if any one could write a guide for installation. What it does is stay there and when i hit enter on install it just freezez. PM me or continue the thread.

---

### Post by ArtemT on 2010-05-31
it could be a bad copy of the disk? what are your specs?

---

### Post by theminipimp on 2010-05-31
Intel Core 2 duo 2ghz , nvidia 9400, 5,2 macbook, with 2 gb of ram i am trying again on another disk

---

### Post by magneze on 2010-05-31
I recently upgraded a similar spec iMac from 9.10 just by using the upgrade button.

---

### Post by theminipimp on 2010-05-31
Well I don't have ubuntu installed yet so I can't upgrade and I can't find 9.0 anywhere. Can you give me a 
link. Also I got a boot launcher software and when I try to launch into mac it just turns the apple logo into a 
circle with a slash going across or a quit sign

---

### Post by magneze on 2010-05-31
Have you resized your OSX partition using Bootcamp?

---

### Post by theminipimp on 2010-05-31
no i resized it using terminal but yeah and it osx won't work

---

### Post by magneze on 2010-05-31
How did you resize it using terminal?

---

### Post by theminipimp on 2010-05-31
i used certain commands i got from the wired magazine how to wiki than i typed in the partition and it did so

---

### Post by magneze on 2010-05-31
Probably worth putting the commands here or a link to the Wired article as that's probably what broke things.

---

### Post by theminipimp on 2010-05-31
Lol I am such a noob to Linux nut here are the terminal instructions from the articale I did every thing but
install xp 

Open Terminal (Applications\Utilities\Terminal)
Type: diskutil list
Hit RETURN and a list of your partitions should come up. You should have one partition (disk0s2) right now if you already have Mac OS X installed. This list will also tell you how much hard drive space you have to partition. On my computer I had 232.5GB of space (The slightly smaller number, i.e. not the one with the * in front, is the one you want to use. It should be at the bottom of the list).
The syntax for your code looks like this:
diskutil resizeVolume disk0s2 80G JHFS+ Linux 72.5G JHFS+ XP 80G
(This is the setup I used, 80GB for Mac, 72.5GB for Linux, and 80GB for XP. Note that when choosing your partition sizes, make sure they add up to the amount of space you have at your disposal.)
Do not worry about the filesystems right now, as we will format them individually later
The partitioning should take a few minutes. It will show a "Verifying 0% ........................" line for a while, but it's not frozen. Wait a few minutes and it will complete partitioning.

---

### Post by theminipimp on 2010-05-31
Here are the instructions that I followed I did everything but xp

Open Terminal (Applications\Utilities\Terminal)
Type: diskutil list
Hit RETURN and a list of your partitions should come up. You should have one partition (disk0s2) right now if you already have Mac OS X installed. This list will also tell you how much hard drive space you have to partition. On my computer I had 232.5GB of space (The slightly smaller number, i.e. not the one with the * in front, is the one you want to use. It should be at the bottom of the list).
The syntax for your code looks like this:
diskutil resizeVolume disk0s2 80G JHFS+ Linux 72.5G JHFS+ XP 80G
(This is the setup I used, 80GB for Mac, 72.5GB for Linux, and 80GB for XP. Note that when choosing your partition sizes, make sure they add up to the amount of space you have at your disposal.)
Do not worry about the filesystems right now, as we will format them individually later
The partitioning should take a few minutes. It will show a "Verifying 0% ........................" line for a while, but it's not frozen. Wait a few minutes and it will complete partitioning.

---

### Post by magneze on 2010-06-01
Try using Bootcamp in OSX to do the resize.

Then you probably want to install reFIT from here:
[http://refit.sourceforge.net/](http://refit.sourceforge.net/)

 Then you can install Ubuntu from a bootable CD with the standard instructions

---

