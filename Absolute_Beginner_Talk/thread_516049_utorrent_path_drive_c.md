---
title: "utorrent path drive_c"
date: 2007-08-02
forum: Absolute Beginner Talk
---

### Post by Vanish00 on 2007-08-02
I am following the install guide of utorrent at [http://ubuntuguide.org]("http://ubuntuguide.org")
Now for the path to the C: is defaulted to /home/user/.wine/drive_c.  Now when I install utorrent I enter the setup mode no problem.  Now my question is at the install guide it says, 

"Note specifically that you can set the directory you wish to use as the "C:" drive for Wine. By default, this is /home/USER/.wine/drive_c but you can set it to any directory you wish, including a pre-existing Windows directory on your computer."

So I tried to change my path to /media/hd1/wine/drive_c.  Then I get the error of "I can't initialize plug-ins directory."  What can I do to make this possible?  I'm dual booting and I want to store all my data on my windows partition.

---

### Post by Vanish00 on 2007-08-02
Anybody know a good reference at least?

---

### Post by atomkarinca on 2007-08-02
only solution i can think of is this:

- open wine configuration by typing winecfg in the terminal or with alt+f2
- under drives tab you can change the location of c drive.

this should be healthier than the other way around.

---

### Post by Vanish00 on 2007-08-02
I have two partitions one for ubuntu and xp.  Since my xp partition is bigger I tried to make my drive_c on that but I just get an error.  I can make it on ubuntu partition easy, but I know their isn't a lot of room

---

### Post by Vanish00 on 2007-08-02
bump

---

