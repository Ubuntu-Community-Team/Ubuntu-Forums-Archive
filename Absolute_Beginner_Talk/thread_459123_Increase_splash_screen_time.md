---
title: "Increase splash screen time"
date: 2007-05-30
forum: Absolute Beginner Talk
---

### Post by noorez on 2007-05-30
How can I increase the time that the splash screen is shown? I like the look of some of them and I think it would be nice if it lasted longer then like 1 or 2 seconds.

---

### Post by cydec on 2007-05-30
And what do you mean by the splash screen?

1. The first one where he is loading? (Most of the time with a loading bar)
2. The login screen?
3. The plashscreen where X is loaded? (Most of the time with a small bar of ubuntu).

---

### Post by plcdfa on 2007-05-30
Jeez, it's one of the strangest requests I've ever seen. You really want your computer to boot **slower**? (Anyway, 1-2 seconds is very fast, you must have a strong machine, provided that you're too writing about the boot splash screen. If not then don't read any further.) Anyway if you want to do this follow these steps:
1. create a a file in /etc/init.d called sleep.sh
2. paste this text into it:
```
#!/bin/sh 
sleep x
```
x should be the number of seconds you want the boot process to wait for
3. save it (also make it executable)
4. go to /etc/rcS.d
5. create a symlink to the above created file with the name S20sleep.sh

Next time you boot the whole screen should freeze for the specified amount sof seconds at some point. If you don't want to stop the progress bar just slow it, then look at what files are the existing symlinks in rcS.d and rc2.d are referencing (they should all be in init.d,) open those script files, and write a line " sleep 1 " to the end of some of them to make the bar stop for 1 second several times. You can also use usleep if you want to specify microseconds.

---

