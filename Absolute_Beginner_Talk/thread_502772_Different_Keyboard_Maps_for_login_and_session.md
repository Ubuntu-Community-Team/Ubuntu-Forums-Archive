---
title: "Different Keyboard Maps for login and session"
date: 2007-07-17
forum: Absolute Beginner Talk
---

### Post by Gorgo13 on 2007-07-17
Hi there!

I'm an absolute beginner. I got some issue with the keyboard mapping.

I installed Ubuntu two times and the first time I selected the Swiss German keyboard mapping during the installation process, which resulted in a correct correspondance between Login Screen keyboard map and the session keyboard map.

The second time I installed Ubuntu, I might have selected the default keyboard mapping (US english I guess), so the login screen has a US English mapping, while the session has a Swiss German mapping. It's very annoying of course for the password step at the login...

So now, and since I do not want to re-install it a third time, I would like to know how to change permanently the keyboard mapping for the login screen... I tried to change the language (lower left corner of the login screen), but nothing as changed at all.  :mad:

Thanks for your help! :o

---

### Post by paradoc on 2007-07-17
System-->Preferences-->Keyboard-->layouts...........choose yours.

Experiment a bit!........nothing to break.

The choice you make should be permanent each session.EDIT: unless of course you have to use a liveCD when you 
will have to change the default US keyboard to your own each time

Have fun!

---

### Post by Gorgo13 on 2007-07-17
Hi there!

and thanks for your reply. There must be something wrong with my system, because I already tried that. Actually the keyboard layout in the System>Preferences>Keyboard... is already set to Swiss German. But whatever I do, the keyboard mapping for the login screen is still US english (and I'm not using LiveCD).

Regards

---

### Post by paradoc on 2007-07-18
Bump

HELP needed here from non US /Keyboard /English users............. PLEASE!

---

### Post by Anicka on 2007-07-18
What does you xorg.conf say? Try with ```
grep XkbLayout /etc/X11/xorg.conf
``` and see if it says us or ch.

Edit: a link [http://ubuntuforums.org/showthread.php?t=74016](http://ubuntuforums.org/showthread.php?t=74016)

---

### Post by paradoc on 2007-07-18
Thanks!, Anicka

If he's not online at the moment, I hope he gets this promising link........for the record, but irrelevant I know, mine is > thlon:~$ grep XkbLayout /etc/X11/xorg.conf
        Option          "XkbLayout"     "gb"

---

### Post by Anicka on 2007-07-18
...and mine is "se", but I guess it could be a universal problem. (Except for the default, pre-set, "never have to worry"-type keyboards [if there is such a thing]).

---

