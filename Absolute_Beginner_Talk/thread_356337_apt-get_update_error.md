---
title: "apt-get update error"
date: 2007-02-08
forum: Absolute Beginner Talk
---

### Post by baysl on 2007-02-08
In terminal I run command:

sudo apt-get update

And then error accured:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

What do I do to fix this problem?

---

### Post by taurus on 2007-02-08
```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by banditti on 2007-02-08
Tried it and that did not work for me.  

Also, and this is just a suggestion, but there are quite a few threads about this, can we consolodate?  this has the most posts:

[http://ubuntuforums.org/showthread.php?t=356257](http://ubuntuforums.org/showthread.php?t=356257)

---

### Post by Bachstelze on 2007-02-08
The problems are totally different and unrelated...

---

### Post by banditti on 2007-02-08
Your right, my bad.  jumped the gun.

---

