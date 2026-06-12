---
title: "ubuntu not returning from hibernate"
date: 2007-09-11
forum: Absolute Beginner Talk
---

### Post by KuruJ on 2007-09-11
ubuntu is not returning from hibernate

it gets past the ubuntu loading screen and then it turns black.
i tried ctrl+alt+F1 and the "sudo shutdown -r now" command, even after restarting same thing occurs.

any sugesstions?

thanks

---

### Post by Midahed on 2007-09-11
Hibernation problems are commonplace.  

I'd do a search on the forum for the word 'hibernate' and you'll find loads of threads on the subject.  It''s also worth looking at the bug lists on Launchpad - again just search for 'hibernate' here:- [https://bugs.launchpad.net/](https://bugs.launchpad.net/)

Mike

---

### Post by glaubergoncalves on 2007-09-11
Are you using an Nvidia video-card? If that's the case, [this tutorial](https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend) have worked for me. If you understand at least a little Portuguese or can use Google Translate, you could read [the thread](http://ubuntuforum-pt.org/index.php?topic=20129.0) I've opened in Ubuntu Fórum PT about an issue pretty much like yours.

---

### Post by asmoore82 on 2007-09-11
> **KuruJ said:**
> ubuntu is not returning from hibernate

it gets past the ubuntu loading screen and then it turns black.
i tried ctrl+alt+F1 and the "sudo shutdown -r now" command, even after restarting same thing occurs.

any sugesstions?

thanks

how much RAM and swapspace do you have?

---

### Post by KuruJ on 2007-09-11
- i have an ati x1300 video card........i have had everything up and running fine for a couple weeks upto now

- 1Gig RAM, 2 Gig swapspace

just this time after put in hibernate......and returning it shows the ubuntu loading screen then it goes to a black screen with a "circle loading symbol"....and thats all it does, nothing else comes

i can hit ctrl+alt+F1 and do startx.......that loads the GUI......but I have to do that each time when starting ubuntu :S

how can we investigate why x server fails to start?

---

### Post by asmoore82 on 2007-09-12
I'm gonna guess that it is a problem with ATI's soon-to-be-replaced driver.

(ATI/AMD have announced that a fully functional((composition/AIGLX)) driver
for Linux will be coming next month((October)); version 8.42 I believe)

---

