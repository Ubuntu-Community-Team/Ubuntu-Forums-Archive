---
title: "windows &quot;.exe&quot;"
date: 2007-03-28
forum: Absolute Beginner Talk
---

### Post by dippydoo on 2007-03-28
I was wondering if it is possible to install windows apps (.exe format) on Ubuntu. I pluged my flashdrive in and foud the app that i wanted to install and it came up and said that it cant find the source. What does that mean and can it be fixed???

---

### Post by UltimaDude on 2007-03-28
I don't think so, WINE can emulate it, though it sometimes doesn't work.
Your best bet is Cedega though thats commerical(Paid)software.

There's a trial for cedega though.

---

### Post by deuchar1 on 2007-03-28
Windows executables can't be run on Ubuntu, but they can be executed under Wine, which is a Windows emulator. (Okay, I always get picked up when I call it that but it kinda is guys :P).

You can get Wine with the command    sudo apt-get install wine    in the terminal.

It's run from terminal - I forget the syntax for the various commands but you'll find them in its documentation.

---

### Post by dstew on 2007-03-28
Windows and linux are competely different operating systems. Programs written to run in one will not run in the other. The only way to get a windows binary (.exe) to run in linux is to use a windows emulator program, like wine.

---

### Post by Patrick K on 2007-03-28
You cannot install Windows apps directly in Linux. You can use an emulator like WINE (to install supported individual apps) or a virtual machine like VirtualBox or WMware (to install a different OS to run under in Linux). 

If you have WINE installed (it's in Synoptic), if you double click on a WIN .exe file, Wine will try to install it. Some apps work excellent, others not at all.

---

### Post by ubuntu27 on 2007-03-28
> **dippydoo said:**
> I was wondering if it is possible to install windows apps (.exe format) on Ubuntu. I pluged my flashdrive in and foud the app that i wanted to install and it came up and said that it cant find the source. What does that mean and can it be fixed???

What's the program that you want to install?
There may be a alternative one for GNU/Linux. If there isn't, depending on what program it is, you may be able to install it under [WineHQ]("http://www.winehq.com/")

---

### Post by dippydoo on 2007-03-28
I was trying to install a RSS reader that im using on my windows pc

---

### Post by SunnyRabbiera on 2007-03-28
Just remember:
wine will not do everything that windows will do, if you want a full windows experience is to either keep it on your HD or run it on a virtual machine.
Also remember that linux are two different operating systems and use different ways of installing new apps, and alos remember that linux is a windows alternative rather then a replacement.
as for a rss program there are plenty of them on linux

---

### Post by Falados on 2007-03-28
> **dippydoo said:**
> I was trying to install a RSS reader that im using on my windows pc

Try Liferea.  Its a good RSS Aggregator and its a native linux app.  I believe it is in Ubuntu's repositories (Either Universe or Multiverse)

---

### Post by goghgoner on 2007-03-28
If you have or sign up for a Google account then customize your homepage -- you can add an RSS reader there or just configure different feeds through different portals (that way you can access it from any machine independent of the OS). Sounds complicated but it is very simple -- I can watch my email inbox, ubuntu forum posts, local news, and play a game at the same time. 

Firefox also has RSS readers available under Tools -> Add-ons in version 2 -- I've used that in the past and that was easy, too.

---

