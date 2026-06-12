---
title: "Transition from windows"
date: 2007-01-16
forum: Absolute Beginner Talk
---

### Post by MrJackdaw on 2007-01-16
Well... I have been using Ubuntu for a few weeks now and am becoming more and more confident. I have managed to get *most* of my software working - enough that I am confident that windows can go!

It's like the old DOS days all over again, only with nicer results!

So, How do I switch from Dual Boot XP/Ubuntu to Single Boot Ubuntu?

James

PS The only software that doesn't work under Crossover is Exampro, Tesbase and Memory map - all stuff I need for school, but is on my wifes desktop.

---

### Post by davebgimp on 2007-01-16
You can use Gparted to edit your partitions, deleting Windows to create free space. Then you can create a new ext3 partition or add it to your existing one. 

Lastly, you can edit **/boot/grub/menu.lst** and remove reference to the now non-existent  Windows partition.

If you are going to go the delete and resize route, take some tips from here:
[http://ubuntuforums.org/showthread.php?t=339583&highlight=resize+partition](http://ubuntuforums.org/showthread.php?t=339583&highlight=resize+partition)

Personally, I'd just back up and do a complete reinstall, wiping everything and putting Ubuntu on as the sole OS.

---

### Post by floke on 2007-01-16
Me too. I have a six month rule: if I haven't had the need for Windows after having Ubuntu for 6 months then its a complete fresh install over the entire disc. The result so far: using Windows to update the anti-virus software in case my wife uses it to go shopping on ebay!

3 months to bye-byes...

Good luck

---

### Post by tocleora on 2007-01-16
If I (a) understand what you're saying and (b) understand ubuntu well enough... If you mean make it to where you don't have to have Grub, my understanding is grub is required even if you don't use Windows, but I could definitely be wrong.  I have a few servers that are only running Ubuntu and Grub still runs although it doesn't show the menu.  If you want to get rid of the windows partition I believe you would use a program called gparted, you could remove the partition and repartition as a linux partition.  I've personally had bad luck with gparted so I opted to use partition magic myself, but I'm sure there are people on here who have had great luck with gparted so you may want to get some other opinions first.  Hope that helped in one way or another, or at least moved you a little further down your path. :)

---

### Post by MrJackdaw on 2007-01-17
<<Personally, I'd just back up and do a complete reinstall, wiping everything and putting Ubuntu on as the sole OS.>>

Yeah, this is the route to go! I'll have to leave it for a while however until I can get Crossover working with a dual monitor setup. Sigh. I was looking forward to giving Bill the boot!

James

PS Thanks everyone for the help!

---

### Post by jvc26 on 2007-01-17
The total reinstall method is likely to be cleaner, and so probs the easiest option - it also allows you to totally rethink your partition table so that its all nice and functional. It also saves you the trauma of having a partially removes OS which can cause you problems, or resizing partitions into space which I havent had the good fortune to get working every time. Good luck onwards with your quest :)
Il

---

