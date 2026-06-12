---
title: "Probably *THE* dumbest thread you've read today but, someones gotta try."
date: 2006-11-07
forum: Absolute Beginner Talk
---

### Post by sktfeelsdapper on 2006-11-07
Should I, being the secondary user (aside from root, meaning there is only me and root) be able to "killall" anything without being root?

Because I'm getting this specific error:

*Self edit: Well it's not doing it now, but before it was telling me I don't have permission to killall anything, but now it's asking me for my password. I vaguely remember being able to without sudo'ing.

Any help?

---

### Post by po0f on 2006-11-07
sktfeelsdapper,

It depends on what user the process is running under.  Run `top`, it should list the process owner in the second column.

---

### Post by yabbadabbadont on 2006-11-07
As long as the proces you are trying to kill was started by your user, you should be able to simply, "killall gnome-panel", for instance.  If the process doesn't belong to your user, then you will need to use sudo.

Edit: Doh!  Too slow. :)

---

### Post by autocrosser on 2006-11-07
Just proves----"If you don't know it--It's not dumb"  The FIRST thing you need to know in Linux---ASK when you have a problem.

---

### Post by yabbadabbadont on 2006-11-07
The only stupid question is one for which you already have the answer and are only asking to annoy others.  (rather than asking for confirmation of your answer)

---

### Post by x64Jimbo on 2006-11-07
> **yabbadabbadont said:**
> The only stupid question is one for which you already have the answer and are only asking to annoy others.  (rather than asking for confirmation of your answer)
Or one that is all over the forums and could have been found with searching - this one is not an example of that, however. 
Also, did you know that the command line will retain your sudo privs for about 10 minutes after your last sudo so that you can sudo over and over with only having to put in the root pw once?

---

### Post by sktfeelsdapper on 2006-11-07
Thanks guys :-D 

But seriously, I don't know what my problem is, I've been using Ubuntu for almost 2 months now and should know at least basic commands but for me this was puzzling. (I did a brief restint on windows which is probably why.)

But it's all good if I'm not suppose to do it without su if I didn't start it, I just wanted to make sure.

---

### Post by autocrosser on 2006-11-07
Then you could look at this: [http://www.unixguide.net/linux/linuxshortcuts.shtml](http://www.unixguide.net/linux/linuxshortcuts.shtml)

Has a wealth of information for all levels of users;)

---

