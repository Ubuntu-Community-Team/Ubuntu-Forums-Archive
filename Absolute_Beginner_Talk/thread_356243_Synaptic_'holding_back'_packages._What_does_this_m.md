---
title: "Synaptic 'holding back' packages. What does this mean?"
date: 2007-02-08
forum: Absolute Beginner Talk
---

### Post by dr_d on 2007-02-08
I recently upgraded my kernel... and now Synaptic is holding back the following three packages:

linux-headers-generic
linux-image-generic
linux-restricted-modules-generic


Why are these getting held back? How do I fix this problem.

Any explanation would be greatly appreciated.
Thanks!

---

### Post by bapoumba on 2007-02-08
Hello,
have you locked the version of these packages or of any other package ?

---

### Post by Xyhthyx on 2007-02-08
We're having the same issue in this thread:
[http://www.ubuntuforums.org/showthread.php?t=356257](http://www.ubuntuforums.org/showthread.php?t=356257)

---

### Post by MrKlean on 2007-02-08
I have the same problem......mine aren't locked..and nobody seems to have an answer...

---

### Post by Bachstelze on 2007-02-08
Open up a terminal and do

```
sudo apt-get upgrade
```

If it's still not upgrading those packages, do

```
sudo apt-get dist-upgrade
```

and paste what you get.

---

### Post by banditti on 2007-02-08
This is just a suggestion, but there are quite a few threads about this, can we consolodate?  this has the most posts:

[http://ubuntuforums.org/showthread.php?t=356257](http://ubuntuforums.org/showthread.php?t=356257)

---

### Post by Paul41 on 2007-02-08
> **banditti said:**
> This is just a suggestion, but there are quite a few threads about this, can we consolodate?  this has the most posts:

[http://ubuntuforums.org/showthread.php?t=356257](http://ubuntuforums.org/showthread.php?t=356257)

I have been following both of these so that would make my life easier :) .

---

### Post by bapoumba on 2007-02-08
[http://ubuntuforums.org/showthread.php?t=356408]("http://ubuntuforums.org/showthread.php?t=356408")
Guess threads linked in the previous posts were merged to the one above ;)

---

