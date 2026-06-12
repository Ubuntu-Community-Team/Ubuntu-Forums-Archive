---
title: "Does Ubuntu have &quot;Cntrl-Alt-Delete&quot; equivelent?"
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by drakebarimore on 2007-06-09
I'm slowly picking up on things and I am learning by running into the same problems over and over again.  When I finally get tired of having to confront the same old problem time after time, I ask for help.

For this post, I have two questions:

1.  Does Ubuntu have the windows Cntrl-Alt-Delete equivelent?
           Not terribly often, but often enough, I'll get a screen freeze which won't release the mouse
           (or if it does release the mouse, I can't click on anything cause the screens froze).  I wish
           that I could do a key combonation to force the offending window shut or get some kind of 
            control back (without having cut power and reboot).

2.   Once I have worked with my Ubuntu long enough and have gotten it configured to my likeing,        
       can I copy it to a cd to be used as an install cd, so that if I majorly screw things up I can simply  
       reinstall with all my configurations / preferences already in place?

Thank you to a community of caring sharing people.

---

### Post by darkfame on 2007-06-09
Take a look at this thread: [http://ubuntuforums.org/showthread.php?t=41174]("http://ubuntuforums.org/showthread.php?t=41174")

Edit: If the whole graphical interface (X.org) becomes unresponsive, and you're unable to recover it. Try logging into a shell (Ctrl-Alt-F1) and open up the process monitor (top) and kill the process you suspect is causing it. If all else fails, try Ctrl-Alt-Backspace (it restarts the graphical interface).

---

### Post by gerscht on 2007-06-09
1) AFAIK you can install a program with automatix which 'emulates' the CTRL-ALT-DEL'. Otherwise hit Ctrl+Alt+Esc and your mouse will transform in a skull head... click on the application you want to close.
2) just save the /etc and the /home folder including hidden directories, that will preserve your settings.
Use
```

sudo dpkg --get-selections > /home/UISERNAME/selections.txt

```
to get all installed applications. 
On the new machine a
```

sudo apt-get update
sudo dpkg --set-selections < /home/USERNAME/selections.txt

```
Will install exactly the same packages as you have installed now

I hope this helps

---

### Post by durrell on 2007-06-09
You can do Ctrl+Alt+Backspace, which doesn't do a full reboot but it does close all of your programs and makes you login again. There may be something else, but if there is I don't know about it.

Edit: There you go, the guy above me knew.

---

### Post by orb9220 on 2007-06-09
FYI **automatix which 'emulates' the CTRL-ALT-DEL'**

Not anymore using beryl. Beryl breaks that one.

---

### Post by gerscht on 2007-06-09
> **orb9220 said:**
> FYI **automatix which 'emulates' the CTRL-ALT-DEL'**

Cheers for that, I've never tried it, but I just realized that Beryl also breaks CTRL-ALT-ESC+Mouse click :(

---

