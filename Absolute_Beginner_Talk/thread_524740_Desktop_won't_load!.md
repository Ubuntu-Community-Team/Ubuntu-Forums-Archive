---
title: "Desktop won't load!?"
date: 2007-08-13
forum: Absolute Beginner Talk
---

### Post by GuidoCalvano on 2007-08-13
Heeelp!!

I am relatively new to ubuntu and I think I screwed up. Yesterday night I think I may have shut down ubuntu a bit too fast. Next morning the gnome desktop loads a big brown square with nothing on it (well sound juicer id load the first time, with its title bar off the top of the screen (or maybe its window frame not loaded I don't remember), closed it turned of "save session automatic" in the failsafe gnome, under "System->preferences->session" and now I just have a brown screen).

I can load the failsafe gnome though. This does just about everything, but still something went wrong pretty bad in gnome and I don't want to trod on the grass. I like the nice and comfy middle of the path.

I work professionaly on my computer and so I need a solution fast rather than perfect. I am more than willing to sacrificy any configuration choices on my desktop as long as I can eliminate the risk of this causing new problems as fast as possible. I definitely don't want to have to reinstall my applications if this can be  prevented in any way. 

The main difference with the failsafe and the conventional gnome appears the startup script. I would like to know which scripts are involved in loading the default gnome, and then get them as fresh from a fresh install as possible. I think the only out of the ordinary configuration in my computer was "save session automatic". So anyone know any solutions?

Big thanks in advance,

            Guido

---

### Post by nvrpunk on 2007-08-13
try deleting the /home/user/.gnome directory and then doing a normal session under that user.  see if that fixes it.

sudo rm -r /home/username/.gnome

---

### Post by GuidoCalvano on 2007-08-13
Having looked at my filesystem using nautilus (showing hidden folders) I couldn't find the file. Just this one;


.gtkrc-1.2-gnome2

EDIT: A closer read you said directory. One sec

---

### Post by nvrpunk on 2007-08-13
hmm, im not on my nix box atm, im at work.  I will look later and see, there are gnome configuration files stored in your home folder in a .folder thats hidden.  I imagine if you delete those and restart gnome it will remake the directory with fresh settings that work.  

You could also make another user and try logging on.  If that works then what I said will work.  Otherwise it is a more serious problem.

---

### Post by GuidoCalvano on 2007-08-13
No need. My conventional gnome is up. Thanks loads!!

I misread thought file, rather than directory. Did it for .gnome (well I moved it to a backup folder ;) don't like risks...). Didn't work. Did the same for .gnome2. Problem solved. Ctrl alt backspaced a couple oftimes to make sure everything went ok for both failsafe, gnome and last session. confirmed. 
nice and clean.

Big big thanks! Especialy since you're at work.

---

