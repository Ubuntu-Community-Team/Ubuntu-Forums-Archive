---
title: "Taking Ubuntu Back To Original Installation State"
date: 2007-05-18
forum: Absolute Beginner Talk
---

### Post by Hillbilly Tilley on 2007-05-18
I installed Ubuntu Studio via the repos and apt-get commands....everything working fine new kernal and all.  I played around a bit and decided I do not need all of this stuff so I would like to uninstall.  I tried apt-get remove commands which did not work.  I have not tweaked very much so going back to the original installation would not be very painful.  Somewhere in the forums I ran across a command to go back to the original installation state but I cannot find it now.  Can anyone share this command with me.

Thanx,
          Hillbilly

---

### Post by Najand on 2007-05-18
Use "apt-get remove --purge PACKAGENAME"

---

### Post by Happy_Man on 2007-05-18
It's not a command so much as a: reinstall, since I don't think you can go back to normal Ubuntu from Ubuntustudio....

---

### Post by Hillbilly Tilley on 2007-05-18
```
Use "apt-get remove --purge PACKAGENAME"
```

I tried this and it said to use autoremove

Do I use "apt-get autoremove --purge PACKAGENAME"?

---

### Post by Najand on 2007-05-18
No, you should just run:
```

sudo apt-get autoremove

```

---

### Post by Hillbilly Tilley on 2007-05-18
```
I don't think you can go back to normal Ubuntu from Ubuntustudio....
```

I did not install the complete Studio package...just audio, audio-plugins, video, and graphics ....plus I installed the other kernal.

So I still have the straight ubuntu just with the studio packages added.

---

