---
title: "[SOLVED] Im on Linux!!"
date: 2007-12-22
forum: Absolute Beginner Talk
---

### Post by nathan1936 on 2007-12-22
Hey! I just started ubuntu, and so far so good. I like the layout! Im on the live CD but im going to switch to ubuntu permanently
1. I was just wondering if/how I could make the desktop a little more flashy? I want a nice sidebar, maybe update my icons?

2. Also what program will I need to play mp3's?

3. One more thing, how do I access the harddrive? 3.1 can I format the hd, and put a fresh copy of ubuntu on? 3.2 Please explain how.

I saw something on ubuntu on youtube where the desktop is like a 3d cube and it looked really nice! So if I could get these few things done, I would really appreciate it.
Thanks for all the help so far!

PS
When I started the live cd, these prompts came up:
176.956 Buffer I/O error on device fdo logical block
and some other numbers with the same Buffer I/O error stuff in a second line. 
4. Just wondering what these are.

Thanks!

---

### Post by iris-n on 2007-12-22
All this can be done, quite easily indeed. For custom icons, wallpapers, themes and so I like to fetch them at [http://www.gnome-look.org/](http://www.gnome-look.org/)
The 3d cube is a plugin, called compiz-fusion. Once you're installed you can get it too, just come back here.
There are two music players installed by default, you just need to get the right codecs. Again, once you're installed it's quite straightforward.
To format the HD and make a fresh install is the easiest way to install. The installer itself will do this for you. If you're unsure, find gparted on your Live CD (System->Administration->Gparted) and format through it.

As for the error, I'm sorry but I haven't seen anything like it.

---

### Post by happymellon on 2007-12-22
> **nathan1936 said:**
> Hey! I just started ubuntu, and so far so good. I like the layout! Im on the live CD but im going to switch to ubuntu permanently
I was just wondering if/how I could make the desktop a little more flashy? I want a nice sidebar, maybe update my icons?
Also what program will I need to play mp3's?
One more thing, how do I access the harddrive? can I format the hd, and put a fresh copy of ubuntu on? Please explain how.

I saw something on ubuntu on youtube where the desktop is like a 3d cube and it looked really nice! So if I could get these few things done, I would really appreciate it.
Thanks for all the help so far!

PS
When I started the live cd, these prompts came up:
176.956 Buffer I/O error on device fdo logical block
and some other numbers with the same Buffer I/O error stuff in a second line. 
Just wondering what these are.

Thanks!

If you want some nicer icons, look at gnome-look.org, They have lots of different themes. Other desktop widgets, you could check in to GDesklets (in add/remove) that has a few things.

MP3's will require you to read the sticky thread under Multimedia, called Enabling Multimedia. Although it says Feisty, you can pretty much replace any Feisty reference with Gutsy and it works.

Running the Installer (On the Live CD desktop) will let you resize partitions if you want to dual boot, or pick the use entire drive option and Ubuntu will do the rest.

The 3D effects can also be pretty simple depending on your video card. ATI will require you to edit a config file. Otherwise you can go to Appearance under System >  Preferences and the last tab (Visual Effects) lets you turn on the 3D desktop.
Ubuntu doesn't give an advanced options by default, so in Add/Remove install the Advanced Desktop Effects Settings program and you should then get an Advanced button in the Visual Effects window.

---

### Post by nathan1936 on 2007-12-22
well, i dont know whats going on. GParted, just hangs on the loading bar and sais scanning all devices. Any reason its doing this?
I have vista installed on this computer too, could that be effecting it?

---

### Post by ChrisNiemy on 2007-12-22
Hi,

on the Gparted related problem I can confirm, that gparted for me crashes (not hangs up) when it's reading the partitions. Vista not installed. But perhaps it is related to it.

However, when gparted hangs up or crashes, just start it again and again. For me this helped. Also when it made changes and re-read partions it crashes. But changes are made correctly.

Regards, Chris

PS: If you can't find a fix for this problem, you really should try the live cd "Parted Magic":
[http://www.partedmagic.com/](http://www.partedmagic.com/)

It's based on gparted, very userfriendly and runs without any problems for me. Then when installing ubuntu you can just use these created partitions you made (maybe should make sure, that they're going to be formatted again by the installer).

---

### Post by StGeorge on 2007-12-22
Hold on.
This is command line stuff.
Take your time and use it 4 the apps you like.
If you like Music then Amorak.
If you like Control then Terminal.
Take a day off and relax in that you have achieved the impossible.
If you rush in then you will get disalusioned.
Enjoy Ububtu.

---

### Post by Tom Mann on 2007-12-22
> **StGeorge said:**
> Hold on.
This is command line stuff.
Take your time and use it 4 the apps you like.
If you like Music then Amorak.
If you like Control then Terminal.
Take a day off and relax in that you have achieved the impossible.
If you rush in then you will get disalusioned.
Enjoy Ububtu.

I wouldn't entirely say that.

Attempt to play an MP3, you'll get a dialog asking you to install codecs. If ubuntu-restricted-extras is in there, BINGO!

You already have Rhythmbox installed.

---

