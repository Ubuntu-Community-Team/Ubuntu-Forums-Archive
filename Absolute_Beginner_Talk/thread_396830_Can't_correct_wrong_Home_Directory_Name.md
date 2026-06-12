---
title: "Can't correct wrong Home Directory Name"
date: 2007-03-29
forum: Absolute Beginner Talk
---

### Post by leftybob on 2007-03-29
While exploring the System folder, under Administrator - Users and Groups - User Settings - Properties - Advanced tab, I accidentally changed my Home Directory name slightly.
Now when I try to start up I can't get back to the desktop in order to change it back; is there a file I can change at the command line that will correct the Home Directory name to show the name Gnome is looking for at startup?
Thanks in Advance

---

### Post by dbbolton on 2007-03-29
```
sudo nano /etc/passwd
```the first item in each line is a username; yours should be the last line.

for example, my username is 'daniel', and the last line of /etc/passwd is:
```
daniel:x:1000:1000:Daniel Bolton,,,:/home/daniel:/bin/bash
```

---

### Post by leftybob on 2007-03-30
Thanks dbbolton, that got me going.
I really appreciate it!
 - Leftybob

---

### Post by dbbolton on 2007-03-30
you're quite welcome.

---

