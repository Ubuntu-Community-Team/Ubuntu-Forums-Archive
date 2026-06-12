---
title: "Ubuntu - A couple of questions..."
date: 2006-04-08
forum: Absolute Beginner Talk
---

### Post by flackboy on 2006-04-08
Hi everyone.  I have a couple of dumb new user questions I hope you don't mind me bothering you with...

First, I have to say, I am in love with Ubuntu.  I've tried a few different distros in the past couple of years, but never found anything which grabbed me (or made it as easy to get into).  The Ubuntu live CD convinced me to buy a new HDD for my laptop, so I could install it alongside XP and hopefully, figure out a way to run my whole business on Ubuntu.

I'm happy with everything so far, but being a total novice to Linux, I have a couple of questions.  If anyone can help, I'd be really grateful.

1.  I've opened up the universe and multiverse repositories and have been installing a few new programs.  However I've had problems with games including Nethack and BZFlag.  I've marked them for install, they've downloaded etc. but then I'm damned if I can find them.  Any ideas?  Should I be downloading and installing them manually?

2. Bluetooth.  Ubuntu tell me it's shutting down my PCMCIA Bluetooth card when it closes.  However, I'm trying to find some software which will allow me to use the card to send/receive data.  Specifically to my mobile.  As this is part of my job, it would be great to be able to do this without booting into Windows.

As I said, sorry for the truly thick questions, but if anyone can help, it would be much appreciated.

Thank you,

Brian...

---

### Post by matthewv on 2006-04-08
First of all, welcome to the ubuntu forums! :)

RE your first question, if the programs you installed do not appear anywhere under the Applications menu, you'll probably have to try running them manually ie open a (Applications --> Accessories --> Terminal) and run either 'nethack' or 'bzflag' (without quotes). That should work... :) Once you have this working you can right click on the menu bar (where it says Applications Places System) and choose edit menus to add these games to your menus. Hope thats all clear. With regards to bluetooth, no idea, I've never used it :)

---

### Post by mlind on 2006-04-08
1. to find installed nethack, try
```

whereis nethack
which nethack
dpkg -S nethack

```

2. nautilus-sendto works if you just want to send stuff to your mobile. right-click on file and choose "Send to.."
For device pairing you may have install gnome-bluetooth packages, not sure about that.

---

