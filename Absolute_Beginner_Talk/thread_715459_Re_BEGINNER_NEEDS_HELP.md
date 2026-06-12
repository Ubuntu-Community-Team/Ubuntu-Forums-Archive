---
title: "Re: BEGINNER NEEDS HELP"
date: 2008-03-04
forum: Absolute Beginner Talk
---

### Post by ubu beginner on 2008-03-04
hi!
sorry for the off-topic... how can I start a thread?!

I registered to this forum many weeks ago, but I still cannot find anywhere how to post a new message, so I will just reply here because I am sick of it. [I would RTFM if I had one!]



my technical problems to post follow

I switched to ubuntu (7) to avoid to end the daily crashes with win xp, but now ubuntu is crashing even more often!
- when I start the computer the keyboard does not work in the right language (I need to use a different button to insert the special character in my password)
- firefox is very slow and keeps closing without warning, perhaps because of the problem it has with flash? I installed the open source flash plugin, and now I can see videos in you tube (although the buttons on the right are not visible under the videos), but not those in videojug.com, for example
- sometimes when I open a downloaded video mpg or avi) the screen screws up completely and I need to restart (pieces of the video are scattered all over the screen like a chessboard!!)
- most important, now even my keyboard malfunctions more and more often! the numbers pad got crasy and pressing numbers moves the cursor around, (the numlock seems ineffective);some keys, like "o" and "f", stop working for several seconds while typing in firefox, while the numbers of the number pad are dead in text editor (but the keyboard works still fine under win xp)
- sometimes I cannot download files from yahoo mail

if this keeps getting worse I will have to forget ubuntu and go back to window$ once again. :-(
L.

---

### Post by aysiu on 2008-03-04
> **ubu beginner said:**
> hi!
sorry for the off-topic... how can I start a thread?!

I registered to this forum many weeks ago, but I still cannot find anywhere how to post a new message, so I will just reply here because I am sick of it. This is how you start a new thread (see the attached screenshot). In the meantime, I've moved your post to its own thread.

> I switched to ubuntu (7) to avoid to end the daily crashes with win xp, but now ubuntu is crashing even more often! Can you describe the crash?
> 
- firefox is very slow and keeps closing without warning, perhaps because of the problem it has with flash? I installed the open source flash plugin, and now I can see videos in you tube (although the buttons on the right are not visible under the videos), but not those in videojug.com, for example Uninstall Gnash and install Flash using [this guide](http://www.psychocats.net/ubuntu/flashmanual).> if this keeps getting worse I will have to forget ubuntu and go back to window$ once again. :-(
L. I have no idea why you're experiencing all these problems, but you're right--use what works for you. If Windows works for you, use it.

---

### Post by glennric on 2008-03-04
To install flash why not just use
```
sudo apt-get install flashplugin-nonfree
```
That seems a lot easier than the method on that web page.

---

### Post by Forrest Gumpp on 2008-03-04
@ubu beginner

When you do start a new thread, and you have entered your topic or question in the title field, click in the message window and wait for a bit.

There is an automatic title search function that brings up a list of five or six similar topics that may have been already posted before.  If there are no matches, you will get a message to that effect.

While this might seem like telling you how to suck eggs, I have a suspicion that many new users remain unaware of the topic comparison function because they have scrolled the page up to centre the message window** before** the title search results appear. They thus simply may not see them, and as a consequence end up posting what in many cases are repetitive or already answered questions.

Good luck, and welcome to active involvement in the Ubuntu Forums.

---

### Post by aysiu on 2008-03-04
> **glennric said:**
> To install flash why not just use
```
sudo apt-get install flashplugin-nonfree
```
That seems a lot easier than the method on that web page.
It also [has had problems](http://ubuntuforums.org/showthread.php?t=636397) in the past few months. Some people have said the problems have been fixed, but others have reported they're still having problems.

I'd say until Ubuntu 8.04 is released, the safe bet is a manual installation.

---

### Post by bazzawill on 2008-03-04
with firefox crashing and flash I use adobe flash through apt but I use the firefox plugin flash block this blocks all the annoying flash adds which used to cause my firefox to hang frequently now I just click on any flash applications I am expecting and want to run

---

### Post by ubu beginner on 2008-03-06
Thanks a lot, aysiu!
the instructions at [http://www.psychocats.net/ubuntu/flashmanual](http://www.psychocats.net/ubuntu/flashmanual)
worked, now my flash is finally ok!

the numbers pad seems to work too (but  the arrows up and down do not work in this reply textbox, perhaps that is normal?)

my system crashes were clearly due to firefox slowing down and eventually freezing (I usually use around 5-10 browser tabs open at the same time).

Thanks also for showing me where to start a new post!

I hate windows and its 9999 security updates and restarts, USB conflicts and crashes, etc. I will stick to ubuntu for as long as it is manageable  ;-)

Have a nice day!

---

### Post by ubu beginner on 2008-03-10
Hi!

I still have problems with ubuntu "gutsy". I list them all together as follows, because they could be related to each other.

-the keyboard: the numpad still behaves weird: sometimes the numbers do not respond at all, while for example "/" and "-" may move the cursor into a black rectangle around some place in the screen, typically the command bar of the browser; hitting again "/" or "-" may for example activate the menu from "File" or "Bookmarks". A few minutes ago I just tested the scroll lock button, and it locked out the screen!!!

-sometimes the keys "t, u, i, o, h, ..." stop responding for several seconds

-The browser firefox keeps closing without warnings whatsoever, and so do also Galeon and Midbrowser, which I tested too. This happens anyway only while the active window is another application. The only other applications I regularly use are aMule, vlc player and gedit.

-the sound comes distorted to the pc speakers when playing some mp3 music, especially the basses.
(I use the external sound card creative xmod, which is anyway not connected to the computer via USB, but independently connected with its power cable instead, since it would not work with ubuntu!)

-browsing the external hard disk (500 GB, partitioned in FAT32) is slow and sometimes freezes the the directory window.

-I am told that I am not "allowed" to make a shortcut to a folder in the external hard disk to the desktop, when I attempt to do that.

-sometimes at the startup there are two icons for each drive (in which case I restart with ctrl+alt+backsp)


I want to get this ubuntu thing running, it's still nothing compared to 1/10 of the troubles I had with windows xp...losive!

Thanks for your time

ubu beginner

---

