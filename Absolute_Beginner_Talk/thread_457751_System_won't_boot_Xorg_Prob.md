---
title: "System won't boot Xorg Prob"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by freefromXP on 2007-05-29
OK so I am going through the learning steps.  I got system running, got beryl working and everything was looking good.  Then I made a change to my Xorg.conf to try and get WOW working and I hit ctrl/alt/backspace.  System won't boot says Xorg.conf problem.  I can login to the black screen but can't get to desk top.  I am on the live CD now how can I fix my Xorg while on live CD.

  I can navigate to my Xorg.conf on the drive I have fiesty installed on but can't edit or change

---

### Post by Ek0nomik on 2007-05-29
If you can login on the black screen, you're in good shape!

Run this command after logging in:

```
sudo nano /etc/X11/xorg.conf
```

Now you change your file back to the way it was (assuming you remember what you changed. ;))

Ctrl+O will write out (save)
Ctrl+X will exit (quit)

Now you can type:

```
sudo shutdown -r now
```

---

### Post by freefromXP on 2007-05-29
TY Trying Now

---

### Post by freefromXP on 2007-05-29
Thanks Ek0nomik   back up and running.  ;)

   It did take to times to see file till I realized X11 was case sensitive. :D

---

### Post by Ek0nomik on 2007-05-29
Yep, everything in Linux will be case sensitive, so that's something to keep in mind.  :)

Glad you got it working.

---

