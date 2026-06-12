---
title: "Making Windows Partion First?"
date: 2007-07-24
forum: Absolute Beginner Talk
---

### Post by nbeerbower on 2007-07-24
XP won't boot in grub. I'm assuming it's because I trimmed the Windows system partiton and now it's no longer first.

Suggestions? How can I make it first?

---

### Post by Cypher on 2007-07-24
The location of the Windows partition doesn't prevent it from booting, but perhaps something got messed up when you trimmed it. If you have the XP CD, boot into it and try doing a recovery..

---

### Post by DiG3RATi on 2007-07-24
you can do a fixmbr in recovery console, but you'll have to reload grub with the live cd to get back to ubuntu.  Sounds like the partions may be numbered differently, so perhaps grub can no longer locate Windows.  Maybe simply reloading grub from ubuntu would fix this...?

Or perhaps there's a config file you can edit... (like boot.ini in windows)

---

### Post by nbeerbower on 2007-07-24
fixmbr did not remove Grub... Windows appears in Grub but it gets stuck on "Starting Up..." before it gets to the Windows logo.

Could I just reinstall Windows, or better yet remove Ubuntu?

---

### Post by Cypher on 2007-07-24
If you are able to re-install Ubuntu/Windows, that's the easiest way of fixing things and the best thing to do is to install Windows first the way you want it. Make sure to leave enough space for Linux (if you still want to use it) and then install Ubuntu and allow it to install GRUB. When installed AFTER Windows, it will do the right thing and allow seamless dual-booting..

---

