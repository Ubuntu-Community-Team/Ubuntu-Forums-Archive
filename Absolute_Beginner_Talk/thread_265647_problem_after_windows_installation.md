---
title: "problem after windows installation"
date: 2006-09-26
forum: Absolute Beginner Talk
---

### Post by kepos on 2006-09-26
i did the following thing: i already had ubuntu installed, but it was necesary to install windows. so i placed another disk in my box, and set it as master, and one that was master drive was set to slave.
after that i installed Windows on master drive,and ubuntu instaltion was still present on my slave drive.

question is, how to reinstall my grub n order to see both, windows and ubutnu.

I followed some instruction that i get on this forum, but it isn't working. they told me to do this:
boot from live cd
enter a root terminal by 'sudo -i'
enter 'grub'
and use output of 'find /boot/grub/stage1' in following two lines
root (hdx,x)
setup (hdx,x)



Please help, i need my ubuntu back.

---

### Post by xyz on 2006-09-26
Look at this...hope it helps. Yes indeed there's lots about that on the forum. Good luck.
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#head-778ecd20f83f92ebaa5aaec5f1b4615539c2f8d3](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#head-778ecd20f83f92ebaa5aaec5f1b4615539c2f8d3)

---

### Post by mokmoki on 2006-09-26
based on what i've read in previous posts, windows doesnt want to be installed second... i believe windows messes up some configurations that ubuntu has already previously installed.

it's better to install windows first then ubuntu...

regarding your question, i have no idea... i'm also a linux newb ^_^

---

### Post by xyz on 2006-09-26
Check "aysui"here:
[http://www.ubuntuforums.org/showthread.php?t=265076](http://www.ubuntuforums.org/showthread.php?t=265076)
as you probaly already have since you've visited other threads. That's great some folks don't even look aroun a bit.

Just remember we've all been there...
Try to state what you don't understand precisely of a given explanation...I'm taking a guess?
If you look at the above thread...open a terminal and type

sudo nano -B /boot/grub/menu.lst

if nano's no good to you, try another text editor and type

sudo gedit -B /boot/grub/menu.lst

in a terminal.
Then copy:

title           Windows XP
root            (hd0,4)
savedefault
makeactive
chainloader     +1

and paste it at the end of the file you just opened (boot/grub/menu.lst)

Sometimes it takes a little time...

---

