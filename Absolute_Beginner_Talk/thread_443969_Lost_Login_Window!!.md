---
title: "Lost Login Window!!"
date: 2007-05-14
forum: Absolute Beginner Talk
---

### Post by kfehr911 on 2007-05-14
I had moved my monitor today and when I restarted I had no login window.  The sound prompt still cued so I gave it a try. I successfully logged in to X but I was curious as to why so I logged out to try again.  This time the sound cue played again but my monitor said that it was over range.  This was a change from the blank screen or scrambled image before. At this point the computer crashed and I wondering what I could have upset when I moved the monitor?  I positive that it is the configuration info being sent to the monitor but how could that have changed when I simply moved a piece of hardware? Not only that but wouldn't that config also effect X.  I sitting here working on X with no problems so what the problem?  Any help or leads would be helpful. Thanks

---

### Post by taurus on 2007-05-14
Boot into recovery mode from GRUB menu and reconfigure your monitor section again.

```
dpkg-reconfigure -phigh xserver-xorg
shutdown -r now
```

---

