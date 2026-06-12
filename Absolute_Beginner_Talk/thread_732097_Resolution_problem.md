---
title: "Resolution problem"
date: 2008-03-22
forum: Absolute Beginner Talk
---

### Post by nemodot on 2008-03-22
I use Ubuntu 7.10. Today, when I turned on the PC, and Ubuntu started, it did on a 640x480 resolution, and there is no  other alternative in the resolution options. I restarted the system but it didnt help.  What can i do to solve this problem?

---

### Post by unutbu on 2008-03-22
This works for many people:
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by awiggin on 2008-03-22
I had the exact same problem this morning.

I did this:

sudo dpkg-reconfigure xserver-xorg

Then I followed all the directions and selected the right resolution when the time came (for me, it's 1440X900).  Then I rebooted the computer.  Voila!  Everything was fixed.

Good luck.

-awiggin

---

### Post by bruce89 on 2008-03-22
```
sudo dpkg-reconfigure **-phigh** xserver-xorg
```

is a lot less harrowing, as it only includes configuring the resolution. (not having *-phigh* prompts for all options)

---

