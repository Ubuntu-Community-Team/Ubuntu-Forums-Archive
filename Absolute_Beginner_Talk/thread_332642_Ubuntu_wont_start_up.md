---
title: "Ubuntu wont start up"
date: 2007-01-06
forum: Absolute Beginner Talk
---

### Post by oscar78 on 2007-01-06
My Dell Inspiron 5100 is on its last leg, and has been for the past few months.  Before buying a new computer and throwing this piece of junk away, I would like to back up some material, but as of this morning I cant seem to boot to Ubuntu.  The machine starts up fine and gets me all the way to the login screen, I type my name and password, the Ubuntu coffee-colored background comes up, and my mouse is there, but nothing else.  

I've tried rebooting a number of times, with no success.  Booting in recovery mode gets me to a terminal, so I'm guessing that my computer just cant boot the gui...

I suspect that my problem is more of a hardware one, but nevertheless I ask you people: can you think of a way to get my gui up and running again, if only for a short while?  

Thanks

---

### Post by sailor2001 on 2007-01-06
if I'm not mistaken...get a mempis live disk (downloadable from someone else's computer) Login as root/root and click on installation center and on right side of that screen is repair.....both grub and x screen...........install as root

---

### Post by oscar78 on 2007-01-06
Thanks.  Could you tell me where I could find a Memphis Live Disk?  I googled it but only got links to music in memphis :)

---

### Post by sailor2001 on 2007-01-06
MEMPIS not memphis

---

### Post by jvc26 on 2007-01-06
An idea would be to start ubuntu in recovery mode and try:
```

sudo dpkg-reconfigure xserver-xorg
startx

```
Then post back with what happened.
Il

---

### Post by oscar78 on 2007-01-06
After having reconfigured xorg and starting x, I encounter the same blank screen, only now its in a different shade...i must have changed a setting that i shouldn't have...

---

### Post by Bigbluecat on 2007-01-06
Are you running Beryl.

I have had this problem with Beryl. At the same time if I logged into a gnome session I had no window borders.

My temporary solution is to open a terminal and enter the following:

```
metacity --replace
```Can't hurt to try this.

I did not find the root cause though. My Beryl install was a little out of date as the repositories had changed and I had not updated mine.

---

