---
title: "Resolution of splash screen"
date: 2006-10-22
forum: Absolute Beginner Talk
---

### Post by usugar on 2006-10-22
Hi,

Anyone know how to change the resolution of the splash screen so that it matches that of my monitor?  Pure aesthetics I know but it's a bit annoying not only because it looks naff, but also because my monitor keeps telling me I'm using the "wrong" resolution which hides the start-up messages.

I know it must be possible because it's an option from the boot menu when you're using the LiveCD, but once installed it goes straight into the boot sequence.

[edit]: actually, on reflection, I'm not sure I mean the splash screen -- I mean the screen that shows all the services being started, before you reach the log-in screen...

thanks

---

### Post by localuser on 2006-10-22
Does this help?

[http://www.ubuntuforums.org/showthread.php?t=258484&highlight=kernel+booting+parameters](http://www.ubuntuforums.org/showthread.php?t=258484&highlight=kernel+booting+parameters)

---

### Post by thornomad on 2006-10-22
On a similar vein, since I installed xubuntu-desktop, my usplash screen shows the xubuntu-desktop logo ... however, I am back to gnoame.  How do I change that back?

Thanks,
Damon

---

### Post by CatKiller on 2006-10-22
> **thornomad said:**
> On a similar vein, since I installed xubuntu-desktop, my usplash screen shows the xubuntu-desktop logo ... however, I am back to gnoame.  How do I change that back?

[This page]("https://help.ubuntu.com/community/USplashCustomizationHowto") suggests that ```
sudo update-alternatives --config usplash-artwork.so
``` might work, although I don't know a huge amount about it.

---

### Post by usugar on 2006-10-24
> **localuser said:**
> Does this help?

[http://www.ubuntuforums.org/showthread.php?t=258484&highlight=kernel+booting+parameters](http://www.ubuntuforums.org/showthread.php?t=258484&highlight=kernel+booting+parameters)

That's marvellous Mr. Localuser.  Many thanks.

---

