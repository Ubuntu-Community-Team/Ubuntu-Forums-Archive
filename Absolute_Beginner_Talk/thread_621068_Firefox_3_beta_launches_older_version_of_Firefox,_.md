---
title: "Firefox 3 beta launches older version of Firefox, deletes history, data, etc."
date: 2007-11-23
forum: Absolute Beginner Talk
---

### Post by Protagonistics on 2007-11-23
A lot of people are having issues with some sort of weird problem with the new Firefox 3 beta which was released on Nov. 22 [here]("ftp://ftp.mozilla.org/pub/firefox/releases/3.0b1/").  The problem is that the Firefox launch file in the folder you download and extract launches your OLD version of FFox--but erases all of your plugins, history, data, etc. It has been suggested [here]("http://ubuntuforums.org/showthread.php?t=605721") that something is "hijacking" the launch of FF3. Yet others say it's as simple as right-clicking the tar, extracting the folder, and launching via "firefox" file within.

What is the problem?
Why is it happening?
How can it be fixed.

ps, [this]("http://phorolinux.com/installing-firefox-30-beta-1-on-ubuntu-710-gutsy-gibbon.html#more-72") does not help. 

Thanks, from all of us anxious FF users.

---

### Post by spupy on 2007-11-23
If i have the old firefox running at the same time, the launcher from the tar just opens a new tab. I have to stop firefox so the new version can launch properly. But the erasing thing didn't happen.

---

### Post by Protagonistics on 2007-11-23
It was suggested that you have to close FF totally for it to really muck things up. I never tried it with FF already open.

---

### Post by sandpaperback on 2007-11-23
I did have it launch my old version of FF, but didn't get any of the erasing that you speak of.

Edit:  Posted too soon.  I did have an instance of my old FF open already.

---

### Post by Protagonistics on 2007-11-23
Well look at that, I tried it one more time (after checking to see if my FF2 processes were dead in System Monitor and logging out just in case), I double clicked "Firefox" in the folder and it immediately imported all my things successfully. Never did that before. I'm still not sold on it's stability though- I think I know when my programs are shut down and I won't put up a [SOLVED] until a few others report that, after a thorough going over, they too had success.

Go 'head now:
Close FF
Check to see if you have any remnants of FF running. (Log out if you want)
Run "Firefox" beta launcher
Report results (especially about data such as history, plugins, bookmarks etc.)

---

### Post by The Cog on 2007-11-23
You need to make sure your old firefox is stopped before launching the new one, otherwise the new one just prompts the old one to open another window and then exits. Use:
**ps -ef | grep firefox**
and make sure firefox-bin isn't there. It sometimes hangs around after all the windiws have been closed. If necessary, use:
**killall firefox-bin**
to get rid of it.

However, FF3b1 is unuseably unstable. It keeps getting a runaway memory leak that kills the whole system if you let it go on for long enough.

---

