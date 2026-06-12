---
title: "plug-ins for browser"
date: 2005-08-29
forum: Absolute Beginner Talk
---

### Post by txm0523 on 2005-08-29
I am a newbie to Linux, especially to Ubuntu. Here is my problem. When I use either the Firefox or Mozilla browser, I am not able view certain things because it says I am missing the plug-ins. The Totem player window appears, but I get error messages instead that say I need the plug-ins.  When I go to either one of the browser's web pages to get the plug-ins, I am so confused about the downloading and installing of those plug-ins. With MS Windows ( ugh ) is was pretty easy, but now I am confused. Is there any way I can get the needed plug=ins and install them without having to have a degree in computer programing ? I tried searching the Synaptic Package Manager, but could not find what was needed. Help.....

---

### Post by aysiu on 2005-08-29
Have you been introduced to the Ubuntu Guide?

[http://ubuntuguide.org/](http://ubuntuguide.org/)

---

### Post by xmastree on 2005-08-29
Unfortunately, the advice there doesn't help.

Specifically, [this](http://ubuntuguide.org/#mplayer) section...
```
chris@ubuntu:~$ sudo apt-get install mplayer-386
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package mplayer-386
chris@ubuntu:~$ sudo apt-get install mplayer-fonts
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package mplayer-fonts
chris@ubuntu:~$
chris@ubuntu:~$ sudo apt-get install mozilla-mplayer
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package mozilla-mplayer

```
And I have enabled the extra repos, so where is this elusive mplayer? I'd like to be able to see multimedia in firefox without looking at the page source, finding the wmv/mov/mpg and entering its url to then download it.
That's rather a pain... ](*,)

---

### Post by aysiu on 2005-08-29
That's funny, because when I enter the same command, I get this:

```
 sudo apt-get install mplayer-386
Password:
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  libdirectfb-0.9-20 libggi2 libgii0 libgii0-target-x libsvga1 libxvidcore4
Suggested packages:
  libggi-target-emu libggi-target-monotext libggimisc2 libdvdcss mplayer-doc
Recommended packages:
  libggi-target-x libggi-target mplayer-fonts
The following NEW packages will be installed:
  libdirectfb-0.9-20 libggi2 libgii0 libgii0-target-x libsvga1 libxvidcore4
  mplayer-386
0 upgraded, 7 newly installed, 0 to remove and 0 not upgraded.
Need to get 4893kB of archives.
After unpacking 11.4MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com hoary/main libdirectfb-0.9-20 0.9.20-4 [475kB]
Get:2 http://archive.ubuntu.com hoary/multiverse libxvidcore4 2:1.0.3-0.0 [192kB]
Get:3 http://archive.ubuntu.com hoary/multiverse mplayer-386 1:1.0-pre6-0.3ubuntu6 [3583kB]
Get:4 http://us.archive.ubuntu.com hoary/main libgii0-target-x 1:0.8.5-2 [17.4kB]
Get:5 http://us.archive.ubuntu.com hoary/main libgii0 1:0.8.5-2 [126kB]
Get:6 http://us.archive.ubuntu.com hoary/main libggi2 1:2.0.5-1ubuntu1 [193kB]
Get:7 http://us.archive.ubuntu.com hoary/universe libsvga1 1:1.4.3-20ubuntu2 [307kB]
Fetched 4893kB in 31s (157kB/s)

Preconfiguring packages ...
Selecting previously deselected package libdirectfb-0.9-20.
(Reading database ... 88335 files and directories currently installed.)
Unpacking libdirectfb-0.9-20 (from .../libdirectfb-0.9-20_0.9.20-4_i386.deb) ...Selecting previously deselected package libgii0-target-x.
Unpacking libgii0-target-x (from .../libgii0-target-x_1%3a0.8.5-2_i386.deb) ...
Selecting previously deselected package libgii0.
Unpacking libgii0 (from .../libgii0_1%3a0.8.5-2_i386.deb) ...
Selecting previously deselected package libggi2.
Unpacking libggi2 (from .../libggi2_1%3a2.0.5-1ubuntu1_i386.deb) ...
Selecting previously deselected package libsvga1.
Unpacking libsvga1 (from .../libsvga1_1%3a1.4.3-20ubuntu2_i386.deb) ...
Selecting previously deselected package libxvidcore4.
Unpacking libxvidcore4 (from .../libxvidcore4_2%3a1.0.3-0.0_i386.deb) ...
Selecting previously deselected package mplayer-386.
Unpacking mplayer-386 (from .../mplayer-386_1%3a1.0-pre6-0.3ubuntu6_i386.deb) ...
Setting up libdirectfb-0.9-20 (0.9.20-4) ...

Setting up libsvga1 (1.4.3-20ubuntu2) ...

Setting up libxvidcore4 (1.0.3-0.0) ...

Setting up libgii0-target-x (0.8.5-2) ...
Setting up libgii0 (0.8.5-2) ...

Setting up libggi2 (2.0.5-1ubuntu1) ...

Setting up mplayer-386 (1.0-pre6-0.3ubuntu6) ...

```

---

### Post by xmastree on 2005-08-29
Hmmm, care to post your apt/sources.lst please?

Edit:

Belay that command ensign, it appears I didn't have the multiverse in there... :-\"

---

### Post by xmastree on 2005-08-30
oooookayyyy, so Firefox thinks it has the plugins now, reaches 99% then stops.
Well it beats seeing those jigsaw pieces, but it's still not working.

That's not a linux thing though, firefox plugins don't work well in Windows either.

 ](*,)

---

### Post by Wolki on 2005-08-30
[QUOTE=xmastree]oooookayyyy, so Firefox thinks it has the plugins now, reaches 99% then stops.
Well it beats seeing those jigsaw pieces, but it's still not working.[/QUOTE]


I had the same problem. I guess it could have to do with esd settings and mplayer not using it. I think i tried the totem plugin and it worked, i'm not sure however. (disk crashed and i was too lazy to do it on the new one). What also workes was a firefox extension that allowed me to open those media files directly in a standalone media player. Can't remember the name, sorry.

---

### Post by xmastree on 2005-08-30
It's certainly better. I watched a news video in firefox which was also wmv. But there are different types of wmv I found.
Totem will play some, gxine will play others so there must be differences between the files.

---

### Post by txm0523 on 2005-08-30
yes I have viewed, read and printed out the guide. But guess what ?  It didn't work.

---

### Post by TristanMike on 2005-08-30
[QUOTE=txm0523]yes I have viewed, read and printed out the guide. But guess what ?  It didn't work.[/QUOTE]If you have installed the codecs and things still won't play, have you changed the "vendorsub" entry and downloaded the "MediaPlayerConnectivity" extension?

---

### Post by xmastree on 2005-09-04
[QUOTE=Wolki] > Firefox thinks it has the plugins now, reaches 99% then stops.I had the same problem.[/QUOTE]I found a solution to that one. Wait till it reaches 99%, and the page has completely stopped loading.
Then hit reload. When the video is reloaded from the disk cache it plays correctly.  :)

---

