---
title: "How do I check how much hard drive space I have left?"
date: 2005-06-14
forum: Absolute Beginner Talk
---

### Post by sedination on 2005-06-14
Hello,

I am a complete newbie to Linux and have been playing around with Ubuntu 5.04 for the last week or so. Sorry for being totally clueless, but how do I check how much space is left on my hard drive?

Thanks.

---

### Post by kiddo on 2005-06-14
My favorite way is right-clicking on my hardware-monitor applet and going to the ressources pane, but it can also be accessed as an application (run "gnome-system-monitor").

The other way I know is to use the command line, wait I'm trying to guess the right command right now... hmm, I think it's "df", it outputs me a lot of info, containing % of used space on each mount.

---

### Post by Seti on 2005-06-14
```
df -h
``` 
will show the size of each partition and the percent available.

---

### Post by sedination on 2005-06-14
Thanks! Works great.  :)

---

### Post by Gustav on 2005-06-14
Or you can just start nautilus and look at the bottom.

---

