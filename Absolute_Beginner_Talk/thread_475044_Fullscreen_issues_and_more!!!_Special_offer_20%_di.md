---
title: "Fullscreen issues and more!!! Special offer 20% discount!!!"
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by DrummerHead on 2007-06-15
Helloooouuu. First question, do you have a "present yourself" section? Wanted to present myself but didn't see it, maybe there isn't one.

Well, I have installed Ubuntu Feisty Fawn with Beryl eyecandy sweetness :) with a dualboot (I'm also a XP user, still necessary for most of my desing work and gaming). I've come to this forum to look for a solution to a problem I didn't see anywere (I googled a lot). Besides that, this forum has already answered lots of other questions :) so it seems this is a tight community.

Well, regarding my problem: When I'm playing a fullscreen application (games for example) something happens... I'm playing allright for, let's say 10 minutes, then fullscreen mode goes off like if something else was executed and calling for my attention... but nothing in fact is (not that I know). Then after let's say 30 seconds  fullscreen mode returns (without me doing anything). This has happened with all the games I've played in fullscreen mode, and it's quite annoying. Notice I'm using beryl, it might have something to do with this. I also have an nVidia 5600 videocard with (apparently) the latest generic drivers.



Also... have middle mouse scroll with firefox: [https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/111339](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/111339)
(It was a question I had in mind but found the answer :) )


[size=1]about the discount... it was just a marketing trickery MUAHAHAHAA made you fall huh? ^_^[/size]

---

### Post by Happy_Man on 2007-06-16
Have you tried disabling Beryl before gaming, to see whether Beryl is the problem? 

> about the discount... it was just a marketing trickery MUAHAHAHAA made you fall huh? ^_^

Actually, I thought you were a spambot and clicked the post to report you. Then I saw it was an actual question. In future, please don't do that. There are people a lot meaner than me on these forums....:(

---

### Post by tgalati4 on 2007-06-16
Linux is a multi-user and multi-threaded operating system.  You probably have 100 or more processes running (most are sleeping) and any one of them could wake up and take attention from full-screen mode.

In the terminal look at:

top  (control-C to quit)

to see what processes are competing for CPU cycles while playing your game.  It really could be any process, so you have to watch it to find the culprit.

Windows hands the computer over to the game, and when the game finishes, the computer is returned (mostly intact) back to Windows.

In Linux, the kernel space is separate from the user space.  Your game is running in user space.  There are strict rules as to how user space interacts with kernel space.  This contributes to stability as rarely will a user space application clobber the kernel.  Since full-screen mode is a hardware control, you can see there will be contention between the kernel (which interacts with the hardware) and user space (which is running the game).

You can see why folks stick to Windows for gaming.  It's a different architecture.  For everything else, Linux works well.

---

### Post by Happy_Man on 2007-06-16
> **tgalati4 said:**
> Linux is a multi-user and multi-threaded operating system.  You probably have 100 or more processes running (most are sleeping) and any one of them could wake up and take attention from full-screen mode.

In the terminal look at:

top  (control-C to quit)

to see what processes are competing for CPU cycles while playing your game.  It really could be any process, so you have to watch it to find the culprit.

Windows hands the computer over to the game, and when the game finishes, the computer is returned (mostly intact) back to Windows.

In Linux, the kernel space is separate from the user space.  Your game is running in user space.  There are strict rules as to how user space interacts with kernel space.  This contributes to stability as rarely will a user space application clobber the kernel.  Since full-screen mode is a hardware control, you can see there will be contention between the kernel (which interacts with the hardware) and user space (which is running the game).

You can see why folks stick to Windows for gaming.  It's a different architecture.  For everything else, Linux works well.
I learn something new every day I log on to this forum...... :D

---

