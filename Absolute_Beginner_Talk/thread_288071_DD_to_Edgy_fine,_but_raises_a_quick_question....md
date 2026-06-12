---
title: "DD to Edgy fine, but raises a quick question..."
date: 2006-10-29
forum: Absolute Beginner Talk
---

### Post by staib on 2006-10-29
Hi all - upgraded from 6.06 to Edgy and all went well, although I needed to get a new version of Automatix2 and renew a couple of programs that weren't happy.  But all is now fine...

My question is this. I want to re-apply some of the sounds from 6.06 (which are now wav files on my desktop) to the usr/shared/sounds folder but cannot simply overwrite them or drag them as that is a protected system folder.

What is the easiest way to convince the PC that I really am its owner and want to do this (and also rename the new Edgy sounds to keep them as backups...) 

Any pointers or help appreciated... cheers :) 

Nick

---

### Post by meborc on 2006-10-29
you can start up nautilus as root user... 

```
sudo nautilus
```

now you have te permission to do anything... BUT BE CAREFUL, YOU MIGHT DO SOMETHING YOU CAN NOT CHANGE BACK :mrgreen:

---

### Post by maniacmusician on 2006-10-29
it may be safer to use sudo on a per-command basis, with a command like

sudo cp path/to/new/file/sound.wav path/to/current/file/sound.wav

with the first path being the path to the file that you want to be used, and the second path being the path to the file that you want to replace.

---

### Post by staib on 2006-10-29
Thank you sir, for the promptness of your reply - indeed, Nautilus shall sail forth boldly, but with great care ;)

---

### Post by maniacmusician on 2006-10-29
umm you wouldnt want to use sudo nautilus. that can cause some problems
 if you must use nautilus, go the route of:

gksudo nautilus

---

### Post by staib on 2006-10-29
Mission accomplished - thanks guys :)

---

### Post by staib on 2006-10-29
Thanks for the advice maniacmusician, but I leapt in there and all seems well. 

I used sudo rather gksudo nautilus...  What is the difference - or why were you suggesting the latter approach?

Cheers.

---

### Post by maniacmusician on 2006-10-29
this page holds a better explanation: [http://psychocats.net/ubuntu/graphicalsudo](http://psychocats.net/ubuntu/graphicalsudo)

---

### Post by staib on 2006-10-29
Cool - thanks for that link - gksudo it is for next time then. :cool:

---

