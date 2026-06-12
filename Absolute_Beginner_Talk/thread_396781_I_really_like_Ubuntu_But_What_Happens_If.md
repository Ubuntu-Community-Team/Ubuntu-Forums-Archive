---
title: "I really like Ubuntu But What Happens If"
date: 2007-03-29
forum: Absolute Beginner Talk
---

### Post by zero244 on 2007-03-29
When the time comes and I have to replace my motherboard. Will Ubuntu reconfigure for the new motherboard or will I have to do a fresh install and start over from scratch.
By the way I am really impressed with Ubuntu Edgy.
I hope I can stay in the linux world.
Its surprising how many people want to get away from Windows.....Vista being a good catalyst.
Thanks to the Linux Community for all the help.

---

### Post by oilchangeguy on 2007-03-29
why are you going to replace your mobo? problem, or upgrade? just do some reasearch before you buy. like googling the model with the word ubuntu in the search line.

---

### Post by click4851 on 2007-03-29
and yes, for the most part, with some exceptions, you will have to reload the operating system from scratch.

---

### Post by cowlip on 2007-03-29
It really depends.  I've had Ubuntu when it was Hoary Hedgehog and Xandros Linux not work after changing motherboards.  However, I've heard it can work for others.  I think it has something to do with the HAL.

In Windows there is a way to change motherboards and still keep your system running though-- you have to uninstall the IDE channels before changing the motherboard and set them as "generic".  Then it will boot up after changing the board, and you can set them to whatever your motherboard is.

[http://www.windowsreinstall.com/install/other/motherboard/win2k.htm](http://www.windowsreinstall.com/install/other/motherboard/win2k.htm)
[http://www.windowsreinstall.com/install/other/motherboard/problems.htm](http://www.windowsreinstall.com/install/other/motherboard/problems.htm)
[http://www.google.ca/search?q=windows+replace+hard+drive+motherboard+controller&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a](http://www.google.ca/search?q=windows+replace+hard+drive+motherboard+controller&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a)

[http://www.michaelstevenstech.com/moving_xp.html](http://www.michaelstevenstech.com/moving_xp.html)

---

### Post by macogw on 2007-03-29
I've moved an Ubuntu hard drive from computer to computer with no problems.

---

### Post by david_kt on 2007-03-29
> **zero244 said:**
> When the time comes and I have to replace my motherboard. Will Ubuntu reconfigure for the new motherboard or will I have to do a fresh install and start over from scratch.

I guess what you have to do is go to the shell (boot in safe mode) and issue this command:

[INDENT]sudo dpkg-reconfigure -phigh xserver-xorg[/INDENT]

This was what I did when I move my drive to another computer and it could not start or have other problem like graphic resolution.

DK

---

