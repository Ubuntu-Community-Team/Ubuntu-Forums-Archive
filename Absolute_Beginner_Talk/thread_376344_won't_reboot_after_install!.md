---
title: "won't reboot after install!"
date: 2007-03-04
forum: Absolute Beginner Talk
---

### Post by LieToPurify3 on 2007-03-04
i've had to try installing ubuntu a number of times because i originally had windows on my machine, but it got corrupted and i couldn't get past the bios screen and the partitions were all messed up. i used the live cd to install ubuntu, but each time i install, it does it completely fine, but when it says to click restart after the install, it never gets past a bar and a half.  this is the "shutdown" bar, not the bar that it shows when it is starting back up.  any idea why this is happening? and i'm a first time user.

---

### Post by freeflyer57 on 2007-03-04
Are you able to enter into Ubuntu? If so try to shutdown through Terminal

```
sudo shutdown -h now
```

---

### Post by LieToPurify3 on 2007-03-04
well i installed it, and its been on the 2nd bar  in the "shutdown" for like an hour now. i haven't touched it. so what do you want me to do again? ive never used any linux or anything before, so help me out please :p

---

### Post by freeflyer57 on 2007-03-04
go to applications->accessories->terminal


to shutdown type:

```
sudo shutdown -h now
```

to reboot type:

```
sudo shutdown -r now
```

---

### Post by LieToPurify3 on 2007-03-04
i went into the terminal and tried doing the shut down, and it went to the same bar as usual.  it still popped the ubuntu cd out; the same way it does after installation to let you take it out of your drive so it doesn't boot from the cd on startup.

---

### Post by LieToPurify3 on 2007-03-04
i can do the "boot from first hard disk" option, but it flashes "out of scan range" at first, adn then goes in. i cant, however, start up without the disk in the drive.

---

### Post by freeflyer57 on 2007-03-04
oh well in that cause it looks like a bad install. sorry I can't help past that.

---

### Post by j.miller565 on 2007-03-04
so are you still   trying to install it? If so, try using the Alternate CD instead of the Live CD. It can be found here: [http://releases.ubuntu.com/6.10/](http://releases.ubuntu.com/6.10/)

---

