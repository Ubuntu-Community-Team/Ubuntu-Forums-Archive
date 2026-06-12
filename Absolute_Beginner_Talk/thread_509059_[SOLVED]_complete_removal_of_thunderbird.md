---
title: "[SOLVED] complete removal of thunderbird?"
date: 2007-07-25
forum: Absolute Beginner Talk
---

### Post by SPQQKY on 2007-07-25
Hey all. I am trying to completely remove Thunderbird. It won't allow me to change settings at all, so I decided to completely remove it. I have followed the steps outlined [Here]("http://ubuntuforums.org/showthread.php?t=140920") and restarted the system. I then reinstalled it thinking I could start fresh, but the same settings appear when I open Thunderbird. Any advice would be greatly appreciated.
Thanks.

---

### Post by waqas_butt0071 on 2007-07-25
go to synaptic manager search for thunderbird 

and uncheck all the options which are linked with thunderbird 
a conplete uninstalation.

---

### Post by swisscow on 2007-07-25
To remove thunderbird (if you've tried the synaptic way etc) go into your home directory, make sure you can view hidden files. You should see a folder called .thunderbird or something. Just delete that and thunderbird is gone (It works, I've done it - instructions from the thunderbird website)

---

### Post by aysiu on 2007-07-25
Paste these two commands in [the terminal:](http://www.psychocats.net/ubuntu/terminal) ```
rm -r ~/.mozilla-thunderbird
rm -r ~/.thunderbird
```

---

### Post by SPQQKY on 2007-07-25
> **swisscow said:**
> To remove thunderbird (if you've tried the synaptic way etc) go into your home directory, make sure you can view hidden files. You should see a folder called .thunderbird or something. Just delete that and thunderbird is gone (It works, I've done it - instructions from the thunderbird website)

Thanks, this one did the trick. :guitar:

---

### Post by freesitebuilder on 2007-08-19
sorry - didn't see this was [solved] - I've moved the post!

---

