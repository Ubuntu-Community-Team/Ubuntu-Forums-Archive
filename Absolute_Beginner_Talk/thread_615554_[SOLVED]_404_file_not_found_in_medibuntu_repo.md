---
title: "[SOLVED] 404 file not found in medibuntu repo"
date: 2007-11-17
forum: Absolute Beginner Talk
---

### Post by ginestre on 2007-11-17
I finally got round to trying to  reinstall skype, which has never worked properly for me. I thought I'd settle down with a clean install and solve the problem this afternoon, since the kids are away. 

So, in synaptic, I marked the existing skype static installation for a reinstall. Accept etc. Press Apply, all systems go - 404 File Not found error . I waited half  a day in case it was just a network glitch, but no- there it was again: 404 file not found.

what has happened ?

---

### Post by ajgreeny on 2007-11-17
You will need to enable the medibuntu repos for skype, or just download the .deb file from [www.skype.com](www.skype.com)

---

### Post by ginestre on 2007-11-17
Yes, the medibuntu repositories are already enabled: this is what worries me. So- with the repo enabled, the 404 error still occurs. What am I missing, or don't know?

---

### Post by ajgreeny on 2007-11-17
Is Sicily (Italy) one of the countries that does not allow skype to be downloaded?  I know there are some but have no idea which they are.

---

### Post by por100pre1 on 2007-11-17
```
gksu software-properties-gtk
```

Disable the old Medibuntu repo.

Then [add]("https://help.ubuntu.com/community/Medibuntu") the actual one.

---

### Post by ginestre on 2007-11-19
Thanks for that- it did the trick!

---

