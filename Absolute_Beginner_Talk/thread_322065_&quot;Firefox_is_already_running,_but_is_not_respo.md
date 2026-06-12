---
title: "&quot;Firefox is already running, but is not responding&quot;, now what?"
date: 2006-12-19
forum: Absolute Beginner Talk
---

### Post by Dave54 on 2006-12-19
I attempted to open Firefox, and got this message:
> Firefox is already running, but is not responding. To open a new window, you must first close the existing Firefox process, or restart your system.
There was no Firefox window open.
1: What causes this error? (not "what does the error mean", but "what did I do to cause it?")
Now, if I were in Windows XP, I would hit Ctrl+Alt+Del to open the task manager, find Firefox, then close it.
2: Where do I find some sort of "task manager" like in windows, or how else do I "close the existing Firefox process"?
Logging out and in did not stop the process. I had to do a full reboot, which is very annoying.

Thanks for the help.
-Dave

---

### Post by kerry_s on 2006-12-19
in terminal> killall firefox-bin

Sometimes happens when clicked to many times.

---

### Post by aysiu on 2006-12-19
This should help:
[http://kb.mozillazine.org/Browser_will_not_start_up](http://kb.mozillazine.org/Browser_will_not_start_up)

---

### Post by senewag on 2008-03-28
Hi,
I am a rank beginner too, I could not open Firefox because of the above message, so I read the forums on this topic and did the following:
(1)  checked what processes were running (Firefox wasn't running)
(2)  Add/Remove   removed and then added Firefox....  still no solution

Then I read someone say that 95% of Firefox problems are related to the profile and I remembered that I had been playing around with my profile so I opened the profile manager and removed all my profiles (except the default) and the problem was fixed, I could now run Firefox.  I had probably stuffed up the profile somehow before when going about linking my ubuntu and windows profile.
You run the profile manager  like this:
  Click on Applications, Accessories, Terminal then enter "firefox -profilemanager" .

Thanks to all you guys who helped me with this problem, hope this also helps someone else out there.

---

### Post by ramjet_1953 on 2008-03-28
Hi, there!

For those of us who prefer to use a GUI, when at all possible, you can put the System Monitor applet on your taskbar by doing the following:

1. Right-click on a vacant part of the task bar.

2. Click on [COLOR="Blue"]Add to Pane[/COLOR]l

3. When the window opens, scroll down to the [COLOR="Blue"]System & Hardware[/COLOR] section.

4. Click on [COLOR="Blue"]System Monitor[/COLOR].

5. Click on the [COLOR="Blue"]Add button[/COLOR].

Viloa! You now have an easy, GUI for monitoring running program and processes and an easy way to kill errant programs.

Regards,
Roger 8)

---

### Post by plasticM on 2008-04-13
> **senewag said:**
> 
Thanks to all you guys who helped me with this problem, hope this also helps someone else out there.

Thanks for that senewag, worked a treat! Just opened the profile manager as suggested and clicked the "open firefox" button.

Seems like the problem is nothing to do with running processes, just the profile.  And most of the help I could find for this error message related to Windows. :(

---

### Post by crf on 2008-04-13
The misleading message that says "firefox is already running" when in fact it isn't, but you just don't have a profile folder is a known (and very old) bug. 

[https://bugzilla.mozilla.org/show_bug.cgi?id=278860](https://bugzilla.mozilla.org/show_bug.cgi?id=278860)

---

### Post by franzrebs on 2008-05-11
> **senewag said:**
> Hi,
I am a rank beginner too, I could not open Firefox because of the above message, so I read the forums on this topic and did the following:
(1)  checked what processes were running (Firefox wasn't running)
(2)  Add/Remove   removed and then added Firefox....  still no solution

Then I read someone say that 95% of Firefox problems are related to the profile and I remembered that I had been playing around with my profile so I opened the profile manager and removed all my profiles (except the default) and the problem was fixed, I could now run Firefox.  I had probably stuffed up the profile somehow before when going about linking my ubuntu and windows profile.
You run the profile manager  like this:
  Click on Applications, Accessories, Terminal then enter "firefox -profilemanager" .

Thanks to all you guys who helped me with this problem, hope this also helps someone else out there.

Thank you so much, mine works now!

---

### Post by jamdanaur on 2008-06-19
hi,
i can't seem to figure out where to find "applications" to try to resolve this problem on our sons computer. he is running windows xp.
thanks for your help.

---

### Post by GavinZac on 2008-06-19
> **jamdanaur said:**
> hi,
i can't seem to figure out where to find "applications" to try to resolve this problem on our sons computer. he is running windows xp.
thanks for your help.

There is no "Applications" on Windows XP. I'm afraid Windows XP is a sort of obscure, obsolete old operating system that people used to use at the turn of the century. This is the Ubuntu forum (a more modern, complete operating system that isn't quite so fiddly; however, its completely free, and safe from all those things that used to make computers a chore, like viruses and adverts), but there's actually a section dedicated to nostalgic people who feel like messing around with ol' XP. It's sort of buried away in a corner of the forum so here's a direct link :)

[http://ubuntuforums.org/forumdisplay.php?f=170](http://ubuntuforums.org/forumdisplay.php?f=170)

---

