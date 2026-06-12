---
title: "Need Xubuntu cd to use synaptics?"
date: 2007-01-27
forum: Absolute Beginner Talk
---

### Post by Daergeth on 2007-01-27
I update in synaptics and it requires my xubuntu cd, nver had this problem with Ubuntu, seems odd. :) Any help? Also where is the repository file, I totally forgot. :confused:

---

### Post by foxmulder881 on 2007-01-27
What exactly are you trying to update to get this message?

---

### Post by taurus on 2007-01-27
Open a terminal and edit /etc/apt/sources.list.  Place a # in front of a line regarding CD-ROM to comment it out, usually near the top.

```
sudo nano -w /etc/apt/sources.list
```
<Ctrl>x to exit and Y to save it.

---

### Post by Daergeth on 2007-01-27
Was downloading flrx drivers.

---

### Post by taurus on 2007-01-27
> **Daergeth said:**
> Was downloading flrx drivers.

[http://albertomilone.com/driver.html](http://albertomilone.com/driver.html)

---

### Post by kerry_s on 2007-01-27
synaptic> settings> repositores> third party tab, uncheck the cdrom.

---

