---
title: "[SOLVED] Installed IM - Emenese - questions?"
date: 2008-03-08
forum: Absolute Beginner Talk
---

### Post by lover_of_sc on 2008-03-08
All,

I am very new to Ubuntu, I finally managed to download the IM Emenese and got it running trough the terminal. As soon as I shut the terminal down it shuts emenese as well, can that be avoided? Can I make it autostart when I start ubuntu, or can I make a shortcut so I don't have to write all of those commands every time I use it? 

Sorry to bother, I am trying to learn.... :-)

---

### Post by freelinuxhelp on 2008-03-08
to be able to close the terminal, you can try this:
nohup emenese &

to make it autostart, go to System, Preferences, Sessions, Add
and add the name of the program

to make a shortcut, rightclick on your desktop and choose Create Launcher

---

### Post by lover_of_sc on 2008-03-09
Oh that's brilliant! Thanks! Altough, can I move the unpacked folder from the desktop to a 'program' folder? If so, how do I do that?

---

### Post by vishzilla on 2008-03-09
Add > deb [http://apt.emesene.org/](http://apt.emesene.org/) ./
deb-src [http://apt.emesene.org/](http://apt.emesene.org/) ./
 to the repo
and
> sudo apt-get install emesene to install it

---

### Post by kleo skywalker on 2008-03-09
Also, if you're looking for an MSN clone, aMSN is supposed to do the job. (I never used MSN so I don't use aMSN either, Pidgin works for me. My brother uses aMSN as replacement for Windows Live Messenger and seems satisfied with it.)
It's in the repos too, so you can install using Add/Remove or Synaptic.

---

### Post by ch_123 on 2008-03-09
I heard aMSN is quite buggy, and I never really liked Pidgin/GAIM for one reason or another. Emesene is the best one Ive used and probably the most similar to Windows MSN/LM

---

### Post by lover_of_sc on 2008-03-09
Emesene appears to work ok so far, really like the ubuntu OS so far - really interesting! :-)

---

### Post by cometa2k7 on 2008-03-20
I tried Emesene, it fitted in well, but for more functionality, definitely try aMSN.

---

