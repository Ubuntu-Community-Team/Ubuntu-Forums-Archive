---
title: "subversion and emerald"
date: 2007-11-26
forum: Absolute Beginner Talk
---

### Post by n3tg33k on 2007-11-26
Hello all,

I am a noob to linux and after a failed install of the subversion package my system will not boot.  During the installation of subversion and all related packages my system hard locked and I had to hard reset (hold down power button).  Upon rebooting it comes up with the splash screen and the progress indicator and then stops at the third hash mark on the indicator and stays there.  Anyone got any ideas as to what may be going on here.  I am also have general shutdown/ restart issues that I am working on as well. 

Thanks N3t

---

### Post by Hospadar on 2007-11-26
have you tried booting in recovery mode? (I think the second option in grub?)  that'll give you a console that shows you when it dies.

I doubt an issue with the package database would cause non-booting, but it might, it's also possible that there is some hard drive corruption from the hard reset.  Perhaps using a livecd to fsck your hard drive might fix the problem.

And just to clarify, I'm assuming you can't boot into ubuntu at all right now?

---

### Post by n3tg33k on 2007-11-26
> **Hospadar said:**
> have you tried booting in recovery mode? (I think the second option in grub?)  that'll give you a console that shows you when it dies.

I doubt an issue with the package database would cause non-booting, but it might, it's also possible that there is some hard drive corruption from the hard reset.  Perhaps using a livecd to fsck your hard drive might fix the problem.

And just to clarify, I'm assuming you can't boot into ubuntu at all right now?

Yes I am able to boot into recovery mode just fine but and all is well I get a command prompt so I am sure that it is something with the gui.  I have not yet tried a fsck on the drive but will do now from within the terminal.  Recovery mode 

n3t

---

### Post by n3tg33k on 2007-11-26
well I did an fsck and everything came back clean, I let the system sit for about 10 mins and it booted up.  We will see if this is a constant problem or not.  I suppose that it could be a ram issue or something.  Don;t know I will keep looking though thanks bud...

n3t

---

