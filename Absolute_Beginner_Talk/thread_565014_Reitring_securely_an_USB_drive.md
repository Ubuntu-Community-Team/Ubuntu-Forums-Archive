---
title: "Reitring securely an USB drive"
date: 2007-10-01
forum: Absolute Beginner Talk
---

### Post by Fixman on 2007-10-01
Under windows, there was an option to "securely retire your USB drive"  that deactivated it, and so there was no risk of loss of data. How can I use tis option under Ubuntu?

Oh, and Unmount Volume doesn't work

---

### Post by Pumalite on 2007-10-01
What version do you have?

---

### Post by 67GTA on 2007-10-01
You should be able to right click on the desktop icon and choose "unmount".

---

### Post by philinux on 2007-10-01
What options are given when you right click on the drive in question?

---

### Post by BennBuntu on 2007-10-01
You shouldn't have to, but sometimes I've had to have root permissions to unmount.

Go to terminal

sudo umount  /media/"whatever it's mounted as"

if you hit tab a few times after the /media/  it will show you what's mounted.

---

### Post by houstonbofh on 2007-10-01
> **67GTA said:**
> You should be able to right click on the desktop icon and choose "unmount".
This has been the method since Dapper.  Does this not work for you?

---

