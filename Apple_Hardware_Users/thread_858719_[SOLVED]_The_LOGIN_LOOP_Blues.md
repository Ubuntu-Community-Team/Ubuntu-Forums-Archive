---
title: "[SOLVED] The LOGIN LOOP Blues"
date: 2008-07-13
forum: Apple Hardware Users
---

### Post by Brightbelt on 2008-07-13
Hi,
I'm on a Macbook Air with Hardy. I've done all my updates, but lately when I log in after turning on my laptop, I get a black screen where I see a red-letter message "Failed" (among other white-lettered stuff - it's all too fast to read really).

Then it loops me back to the Login screen again, so I have to enter my username and password again. On the 2nd attempt, it logs me in successfully and I DO finally get to my desktop.

Is there any fix for this? I actually encountered this in Ubuntu on my other computer, but it seemed to solve itself somehow over time and the loop stopped occurring. 

I appreciate any help on this. 

Many Thanks, Frank B.

---

### Post by cyberdork33 on 2008-07-15
This sounds like something broke during upgrade. Did you check bug reports in launchpad?
[https://bugs.launchpad.net/ubuntu](https://bugs.launchpad.net/ubuntu)

---

### Post by Brightbelt on 2008-07-16
Thanks Cyber, I found a similar bug but it referred to an older version of Ubuntu. Plus it was probably a PC and not a Mac.

So I filed a new bug report. I may try something like changing my GDM Login screen and seeing if that helps. 

Many Thanks, Frank B.

---

### Post by Brightbelt on 2008-07-16
Oops. I answered my own question - changing the GDM theme fixed the problem. 

I did 2 restarts to make sure; it seemed to fix the issue. 

I should try to report this on my bug report, right?

Thanks, Frank B.

P.S. I turned the bug report into a question, so as to avoid confusion for others.

---

### Post by cyberdork33 on 2008-07-16
I don't think that the Mac thing matters (which is why I referred you to the bugs). If the gdm theme comes with ubuntu then I would file a bug, otherwise, if you downloaded it somewhere, I would try to contact the creator.

---

