---
title: "Moving files"
date: 2007-12-15
forum: Absolute Beginner Talk
---

### Post by oscarthefish on 2007-12-15
Desktop has started to get cluttered up so could anyone tell me how i can move a file from the desktop to a folder please. Thanks

---

### Post by Pumalite on 2007-12-15
Click and drag

---

### Post by banewman on 2007-12-15
Or in terminal type - 
sudo mv -v /path/to/file /new/path/to/file
:)

---

### Post by oscarthefish on 2007-12-15
Already knew about click and drag but was hoping to learn how to use the command line. Thanks for the replies.

---

### Post by SOULRiDER on 2007-12-15
> **banewman said:**
> Or in terminal type - 
sudo mv -v /path/to/file /new/path/to/file
:)

No sudo unless its encessary.

Just do
```
mv file destination
```
For example, move "hello.txt" from your desktop to your home directory
```
mv ~/Desktop/Hello.txt ~/
```
Note that ~ is the same as /home/YOURUSERNAME

---

