---
title: "[SOLVED] Ubuntu stopped working for me after an update error."
date: 2008-03-13
forum: Absolute Beginner Talk
---

### Post by infernohit on 2008-03-13
I can't even get to my desktop because it's not loading. All I see is a black screen with a bunch of commands, and nothing happens.

---

### Post by Rocket2DMn on 2008-03-13
If you are getting a black screen after you boot the computer, check this out - it will tell you how to reconfigure X, this problem is fairly common - [http://ubuntuforums.org/showthread.php?t=690760](http://ubuntuforums.org/showthread.php?t=690760)
If you use restricted drivers, you can reinstall them once you get back into the GUI.

---

### Post by infernohit on 2008-03-17
That doesn't work for me because it doesn't even let me log-in. When I input my log-in info, it just says something then goes back to the log-in prompt. It's the correct info and everything, but for some reason it's not letting me log on.

---

### Post by Rocket2DMn on 2008-03-17
I'm in the process of giving Hardy a test run myself, and I have to say, the graphics stuff is making me mad, too.  You will probably have better luck getting your graphics to work with Gutsy.  I discovered myself that the method I linked you to above doesn't seem to work with Hardy b/c it doesn't ask about your video driver, or screen resolutions or anything - very frustrating.
You can try making a post on the Hardy Development forum - [http://ubuntuforums.org/forumdisplay.php?f=305](http://ubuntuforums.org/forumdisplay.php?f=305) but as far as I can tell, dealing with X in Hardy is a pain if stuff is not detected automatically.
You can check your Xorg log file from a TTY (CTRL+ALT+F1 like in the guide above) and run one of the following commands to look it over
```
//to display the whole file:
cat /var/log/Xorg.0.log
//to show the end of the file:
tail /var/log/Xorg.0.log
//to scroll through the file:
less /var/log/Xorg.0.log
```
Good luck.

---

### Post by infernohit on 2008-03-17
I don't think I can run commands because I can't log on. Whenever I try logging on it just goes back to the log on screen again.

---

### Post by Rocket2DMn on 2008-03-17
Even at a TTY?  I'm not talking about a graphical login, this is a terminal based login.
If you can't login to that full screen terminal, then you're having major issues.  Please confirm that you can't login to the full screen terminal when doing CTRL+ALT+F1.

---

### Post by infernohit on 2008-03-17
Yes, I can't log-in when I'm in the screen at alt + ctrl + F1. I put in my username then password, and press enter.

A bunch of words pop up and then it prompts me to the same log-in screen again.

---

### Post by Rob345 on 2008-03-17
Yeah I am having similar issues.  My machine was working fine, then did an update, rebooted and suddenly it hangs.

I have tried everything, booting from CD (doesn't work) booting in safe mode, changing boot line, all does the same thing.

Ive read alot of stuff, and learnt alot in the process, however its just frustrating!

Anyway, after it boots i can try to goto tty (yes ctrl-alt-f1) and it just says "loading, Please wait..." and thats it.  been like that for 10 mins or so.

I am such a nOOb. *sighs*

---

### Post by Rocket2DMn on 2008-03-17
OK that is a more serious problem.  Can you tell me what it is saying to you when you try to log in?  I need to know what it's saying to help you troubleshoot this.

Before you installed did you check the md5sum of the iso image file?
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
To find the correct hashes however, you need to go to your original download source and find the md5sum.txt file.  You won't find it on help.ubuntu because Hardy versions are released very frequently.
Did you burn the iso to a cd at a slow speed like 4x to prevent write errors?

---

### Post by infernohit on 2008-03-17
> **Rocket2DMn said:**
> OK that is a more serious problem.  Can you tell me what it is saying to you when you try to log in?  I need to know what it's saying to help you troubleshoot this.

Before you installed did you check the md5sum of the iso image file?
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
To find the correct hashes however, you need to go to your original download source and find the md5sum.txt file.  You won't find it on help.ubuntu because Hardy versions are released very frequently.
Did you burn the iso to a cd at a slow speed like 4x to prevent write errors?

I've installed Linux over a month ago, so I don't see what it has to do with the CD. Everything was working fine until I tried updating from the update manager and got an error. When I rebooted, it wouldn't start.

When I burned the iso to a CD, I did it at the slowest speed.

[http://i26.tinypic.com/2r23tqa.jpg](http://i26.tinypic.com/2r23tqa.jpg)

That's what I'm getting when I try to log-in. When I log-in it just goes back to that screen.

---

### Post by Rocket2DMn on 2008-03-17
OK, that sounds like a development problem, definitely not Absolute Beginner material :)
You should make a post on the Hardy Heron Development forum here - [http://ubuntuforums.org/forumdisplay.php?f=305](http://ubuntuforums.org/forumdisplay.php?f=305) - perhaps one of the developers can help you get that right, it may be as simple as getting an update installed.
You may also want to consider posting a bug report on Launchpad.net since it seems to me that there is a code problem in there - it's looking a C code file and is talking about assertions which is a method used in programming to ensure certain parameters are met before proceeding.  It seems that one of those assertions failed or is not setup correctly.
Remember, Hardy Heron is still in the Alpha stages and is considered unstable.

---

### Post by infernohit on 2008-03-17
Thanks, I'll try posting it there.

---

