---
title: "Need use Lice CD to access files to undo changes"
date: 2008-03-14
forum: Absolute Beginner Talk
---

### Post by roundhay on 2008-03-14
I added some commands to the following folder /etc/init.d/bootmisc.sh now Ubuntu will not load.

Using the live CD I can find the bootmisc.sh file on my hard drive but I can't save the file after removing the commands I added, I get any error telling me I do not have permission.

Can someone let me know how I can do this?

---

### Post by joshrobinson on 2008-03-14
use sudo

```
sudo gedit
```

browse for the file, edit it, and save

if your using kde, replace gedit with your text editor

---

### Post by roundhay on 2008-03-14
This doesn't work, If I use sudo nautilus I can find and open the file I need to change but becuase it is part of the ubuntu installaion on my hard drive I can't save the changes as I am not logged on and am accessing the file using the live CD.

I need to get permission to make ans save changes while using the live CD

---

### Post by joshrobinson on 2008-03-14
can you boot in recovery mode? without the live cd? if you have some nano experience you can edit the file that way

```
nano /etc/init.d/bootmisc.sh
```

use the down arrow to get to the lines you want to remove, then use the DELETE key, not the backspace, to remove the lines

when your done hold CNTRL then hit O
it will say save as just hit enter,
now hold CNTRL and hit X to quit

try to reboot

---

### Post by roundhay on 2008-03-14
Worked a treat, Thanks!!!

---

### Post by joshrobinson on 2008-03-14
> **roundhay said:**
> Worked a treat, Thanks!!!

no problem, glad you got everything running agian

---

