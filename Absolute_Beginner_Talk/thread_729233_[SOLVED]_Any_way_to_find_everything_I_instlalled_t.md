---
title: "[SOLVED] Any way to find everything I instlalled today and uninstall?"
date: 2008-03-19
forum: Absolute Beginner Talk
---

### Post by optimusmedia on 2008-03-19
I have messed up something after trying out some software.  Of course I did this with a few different programs and didn't keep up with what I installed.

Is there a way to see what was installed today?  Or uninstall anything installed within a certain time?

This would give the effect of a "restore point" like windows has (yes, i know the problems with windows' restore points - this is not a yeah windows post).

Thanks!

Ron

---

### Post by &lt;&lt;joe&gt;&gt; on 2008-03-19
umm not that i know, and that means almost nothing.
But i think this would be an awesome feature.

---

### Post by (((X))) on 2008-03-19
Yes, If you used synaptic package manager.
File>history will show you a nice overview of changes made.

---

### Post by optimusmedia on 2008-03-19
Thank you, (((X)))

ah i did with some - but apt-get from the command line too.

The problem I am having ([here if you are interested]("http://ubuntuforums.org/showthread.php?t=729129")) however leaves me from seeing my screen.  Got a terminal line I can use?

---

### Post by The Cog on 2008-03-19
> **(((X))) said:**
> Yes, If you used synaptic package manager.
File>history will show you a nice overview of changes made.

OOH!!! That's been under my nose all this time, and I didn't know it was there. Love it.

---

### Post by glennric on 2008-03-19
You can also look at the file /var/log/apt/term.log.  You have to root permissions to view it.  Type
```
gksu gedit /var/log/apt/term.log
```

---

### Post by optimusmedia on 2008-03-19
> **glennric said:**
> You can also look at the file /var/log/apt/term.log.  You have to root permissions to view it.  Type
```
gksu gedit /var/log/apt/term.log
```

Also great to know!  Ubuntu support rocks :guitar:

---

