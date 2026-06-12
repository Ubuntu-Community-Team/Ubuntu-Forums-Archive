---
title: "Root Theme"
date: 2006-10-09
forum: Absolute Beginner Talk
---

### Post by PPAAUULL on 2006-10-09
Ok This might sound silly but my theme that I have as a user does not match that of the root and I wish to make it match. is there any way I can do this?

Thanks for the help.

---

### Post by Kateikyoushi on 2006-10-09
Set them to look the same with system >> preferences >> theme.

---

### Post by PPAAUULL on 2006-10-09
But I have the theme that I want but the root is something else so evrey time I go into synaptic or root nautulis it is diffrent.

---

### Post by smartalecks on 2006-10-09
Copy and paste these commands into your terminal

```

sudo ln -s ~/.themes /root/.themes
sudo ln -s ~/.icons /root/.icons

```

That should do it.

---

### Post by PPAAUULL on 2006-10-09
Thanks you so much it worked!!

---

### Post by Ben Sprinkle on 2006-10-09
What that does is link the above folders into the root folder. ;)

---

### Post by Perfect Storm on 2006-10-09
More eyecandy info: [http://ubuntuforums.org/showthread.php?t=77694](http://ubuntuforums.org/showthread.php?t=77694)

---

### Post by PPAAUULL on 2006-10-09
Thanks for the help.

---

### Post by shafin on 2007-12-04
Thanks for the info

---

### Post by Zalbor on 2007-12-04
I just tried, and no matter what I do, the theme of root programs is the same as the one I have. Did this just change in Gutsy?

---

### Post by shafin on 2007-12-04
This worked for me in gutsy,however,you may copy all themes at usr/share/themes to /home/user/.themes folder and them execute the comands.give it a try

---

