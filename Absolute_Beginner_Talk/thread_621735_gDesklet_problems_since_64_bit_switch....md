---
title: "gDesklet problems since 64 bit switch..."
date: 2007-11-24
forum: Absolute Beginner Talk
---

### Post by Ubun2User on 2007-11-24
Okay so I installed the 32 bit version like an idiot and I had to reinstall the 64 bit but thats cool because I was actually able to un-install Vista and make my whole computer Ubuntu!!!!

Anyway, I did the same thing as last time and added gDesklets but this time when I click gDesklets in Applications > Acc > gDesklets, the gDesklets Shell opens but it keeps turning dark gray and shutting down.  I actually tried to close it once before it turned gray and an error message poped up that reads.

The window "gDesklets Shell" is not responding.

Forcing this application to quit will cause you to lose any unsaved changes.

What did I do wrong...lol

---

### Post by ryanVickers on 2007-11-24
I don't think anything is wrong on your part - II have this problem too.  Just a coincidence it's 64 bit, or not... ???

---

### Post by Ubun2User on 2007-11-24
Hopefully someone will chime in here and let us what (if anything) we are doing wrong.

---

### Post by rsambuca on 2007-11-24
There is a little bug in the 64-bit version, but there is an easy workaround. [ Details in this thread]("http://ubuntuforums.org/showthread.php?t=582721").

---

### Post by Ubun2User on 2007-11-24
rsambuca...you seem to know a lot so I will now post my question from that thread here and maybe you can answer it and tell me if I should use the other fix.

"I used GNILF's old fix but the problem I am having now is that there is this background magnification box that stays around the desklet. Anyone have any ideas?"

Thanks!

---

### Post by Ubun2User on 2007-11-24
Oh yeah and if you think this...

/usr/lib/gdesklets/gdesklets
/usr/lib/gdesklets/gdesklets-shell
/usr/lib/gdesklets/gdesklets-daemon
/usr/lib/gdesklets/gdesklets-migration-tool
that says "#! /usr/bin/env python" and just add "2.4" so it looks like "#! /usr/bin/env python2.4".
Of course you would have to have python 2.4 installed to make this work.Good luck!


...will fix it, please tell me where to put this...lol

---

### Post by rsambuca on 2007-11-24
I had that problem a few times in the past.  Every once in a while it would do that.  If you restart X, you should be OK (Obviously not a real fix, though).  I haven't had that problem since I quit auto-running it on startup.  I seemed to notice it after I installed Skype.  It never seems to do it when I start the desklets manually, though.

---

### Post by Ubun2User on 2007-11-24
Well it looks like a restart fixed it, thanks!

---

