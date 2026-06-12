---
title: "Help!  Live ubuntu can't burn to DVD"
date: 2006-05-09
forum: Absolute Beginner Talk
---

### Post by damianubuntu on 2006-05-09
Hi,
My father has killed his XP box with viruses, and has unbacked up stuff on it.  Proud of my new ventures into Ubuntu, I sent him a live CD and talked him through booting off the live CD, mounting his windows drive and hopefully burning his files to DVD, (all done over the phone with an ageing man](*,) )

The problem is that after moving files to the DVD burner window and then celecting write to disc, Ubuntu declares that the files are too big for the media.  File size is c. 1.2gb, blank DVD=4.7Gb so there shouldn't be a problem.

I guess its the size of the virtual drive that Ubuntu live creates (if that's what it does, I'm guessing here...)

Is there a work around apart from burning the files in very small chunks at a time (some of which may be too big anyway)

Help me convince my skeptical old man that Ubuntu is cool!

Cheers

---

### Post by cgjones on 2006-05-09
I haven't done much CD/DVD burning in Ubuntu, but could you burn the files directly from the Windows partiton? The Ubuntu Live filesystem is (I believe) loaded into a RAM disk, so you should be limited to however much RAM is in the system.

---

### Post by damianubuntu on 2006-05-09
Hi,
the windows partition won't boot anymore, hence using the Ubuntu live!

---

### Post by cgjones on 2006-05-09
Sorry, I didn't mean burn them from Windows, I meant that instead of copying the files you want to burn to the DVD burner window (once again, I'm not too familiar with burning in Ubuntu), could you burn them directly from where they are. How exactly are you going about trying to burn the files? Are you using the file browser (Nautilus), or are you using a program like GnomeBaker?

---

### Post by damianubuntu on 2006-05-09
I'm using the nautilus burner.  I'd rather use gnomebaker, but since ubuntu is live, I can't install anything!  I tried getting him to burn from windows, but the 'write to disc' option only turns up once he's got the files are in the DVD creator window.
At the moment he's taking them in 600 mb slices onto a unch of CDrs but its not ideal!
It also turned out that Nautilus wouldn't handle DVD rw sessions, cos we tried repeat burning to a rewriteable, but it wanted to delete  the original dvd contents when we tried to incrementally add....hey ho!

Thnaks for replying BTW :-)

---

### Post by cgjones on 2006-05-09
Well, at least you've got something working. And you might be able to install programs to the live filesystem. I think Ubuntu Live uses UnionFS, which I thought I read somewhere could be altered realtime. I'm not positive about that though.

---

### Post by AndrewCaul on 2006-05-09
Would he be willing to install Ubuntu?

---

### Post by Jagot on 2006-05-09
[QUOTE=damianubuntu]I'm using the nautilus burner.  I'd rather use gnomebaker, but since ubuntu is live, I can't install anything![/QUOTE]

You can indeed install packages when using the Live CD.  Using GnomeBaker of K3B would be far nicer that Nautilus.

---

