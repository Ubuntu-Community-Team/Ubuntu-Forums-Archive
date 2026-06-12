---
title: "Disk Cleanup"
date: 2006-09-05
forum: Absolute Beginner Talk
---

### Post by pbwalker on 2006-09-05
Ok...so I like to install apps, try 'em out...and if I like, I I keep. If I don't like it, I remove it. Is there a utility to scan the filesystem to make sure I have removed ALL files? All library's...all dependencies...etc.

Thanks!!!]

:p

---

### Post by pbwalker on 2006-09-05
> **pbwalker said:**
> Ok...so I like to install apps, try 'em out...and if I like, I I keep. If I don't like it, I remove it. Is there a utility to scan the filesystem to make sure I have removed ALL files? All library's...all dependencies...etc.

Thanks!!!]

:p


oops...forgot to say...I remeber seeing a post on here (but couldn't find it) on some "debclean" or "deb???" package...

Any ideas?

---

### Post by pbwalker on 2006-09-09
bump...

---

### Post by shahriar86 on 2007-11-22
I don't know whether these will be able to free much space for you but you can try these anyway

sudo aptitude clean

sudo aptitude autoclean

sudo aptitude autoremove

sudo apt-get autoremove

It did help me recover half a gig for me you try it and let me know

---

### Post by Brindled on 2007-11-22
correct me if i'm wrong but wasn't this thread started over a year ago?


regardless, i tried it and freed about 0.1 gig. thanks for the heads up.

---

### Post by linuxisfree on 2008-03-10
Very Nice! Got back 0.5GB of free space after doing that! Thanks!

---

### Post by Paqman on 2008-03-10
Check out [this thread](http://ubuntuforums.org/showthread.php?t=140920&highlight=deborphan) for lots of ideas. Mostly you just want gtkorphan. It's in the repos.

---

### Post by sgtbilko on 2008-07-19
Wow, freed up 1GB for me!

---

