---
title: "Large Print Console font at boot time?"
date: 2007-01-27
forum: Assistive Technology &amp; Accessibility
---

### Post by joann on 2007-01-27
Hello.

I was wondering if there is any way that I could make my console font larger at boot time? 

Any help would be very nice.
Joann

---

### Post by frafu on 2007-01-28
Hello, 

I did a little search in the forums and it turned out these threads that might be relevant: 

[http://ubuntuforums.org/showthread.php?t=264005&highlight=boot+console+font](http://ubuntuforums.org/showthread.php?t=264005&highlight=boot+console+font)

[http://ubuntuforums.org/showthread.php?t=329369&highlight=boot+console+font](http://ubuntuforums.org/showthread.php?t=329369&highlight=boot+console+font)

[http://ubuntuforums.org/showthread.php?t=200834&highlight=boot+console+font](http://ubuntuforums.org/showthread.php?t=200834&highlight=boot+console+font)

Have a nice day. 

Francesco

---

### Post by joann on 2007-01-29
The changes made the font bigger, but I was wondering if there was anyway to make the font any larger?

Thanks for the links Frafu. After reading the information I was able to change my font by making a few changes to my /etc/default/console-setup file. I also used a few fonts that were located in the /usr/share/consolefonts/ directory... but I still have not tried all of the fonts.

Joann

---

### Post by frafu on 2007-01-30
If you still have problems, I will tell Henrik to look at this thread (if he does not do it by himself); he knows much more about this than me. 

Francesco

---

### Post by Henrik on 2007-01-31
The regular boot up text has been completely removed in later versions of Ubuntu, so we won't be putting in any official work toward making those more visible. 

For those who are interested in the booting messages in detail, there are a few options You have yourself found the font settings. Some work has been done on a spoken boot ([https://wiki.ubuntu.com/SpokenBoot](https://wiki.ubuntu.com/SpokenBoot)) and you can always read the log files afterwards.

---

