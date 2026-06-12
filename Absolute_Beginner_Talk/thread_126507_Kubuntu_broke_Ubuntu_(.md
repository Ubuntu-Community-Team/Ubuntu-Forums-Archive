---
title: "Kubuntu broke Ubuntu :("
date: 2006-02-06
forum: Absolute Beginner Talk
---

### Post by bionicyeti on 2006-02-06
I was screwing around and decided to install kubuntu, just to see if I liked it. Now I can't get back into my gnome session. It takes my username and passwd, I hear the music then nothing. Just the plain brown screen. Gnome failsafe doesn't work either. KDE still works. I installed KDE via apt-get install kubuntu-desktop.

Thanks in advance for any help.

---

### Post by RavenOfOdin on 2006-02-06
I had a problem among those same lines, though it was a lot more convoluted.

Did you, in installing kubuntu-desktop from Synaptic, respond to "Please select your default window manager" with "kdm"?

I think that interferes with GNOME and causes bunches of problems in short order.

---

### Post by Sutekh on 2006-02-06
This is a problem I struggled with for a long time, and is one that I've seen crop up several times.  There will be a long list of possible fixes that you can try to get things working again. 

[Ubuntu Forums - KDE Broke GNOME!!]("http://www.ubuntuforums.org/showthread.php?t=96621&highlight=kde+broke+gnome")
[Ubuntu Forums - kubuntu (kde) broke my gnome installation]("http://www.ubuntuforums.org/showthread.php?t=85942&highlight=kde+broke+gnome")
[Ubuntu Forums - Gnome freezes please help me!]("http://www.ubuntuforums.org/showthread.php?t=88278&highlight=gnome+login+freeze")

Those threads all contain methods that all failed for my problem.  I hate to be defeatist, but in my experience they won't work.  

This thread *could* get things working (I never had a chance to try this method, plus it doesn't involve an install of KDE)
[Ubuntu Forums - Gnome hangs at brown screen after GDM login.]("http://ubuntuforums.org/showthread.php?t=102359")


**If you find that these don't work, or you can't be bothered trying, what I'd like you to try is to create a new user in KDE, and then try to log into GNOME with that new user.  If everything works then that's your new user! **

This thread has some info for moving user settings and stuff across.
[Ubuntu Forums - Fix Gnome after KDE install]("http://www.ubuntuforums.org/showthread.php?t=96959&highlight=kde+broke+gnome")

This problem was particularly annoying because I couldn't reproduce it again on a fresh install.  Nowadays I have a user for GNOME and one for KDE, just in case.

---

### Post by bionicyeti on 2006-02-07
Thank you. Creating a new user worked.

---

