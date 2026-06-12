---
title: "Delated sources.list swap file"
date: 2007-05-07
forum: Absolute Beginner Talk
---

### Post by Polemistis on 2007-05-07
Hi,

im new to linux

I was recently updating the sources.list file using vim and didn't close properly. When I loaded it again, the file said it was locked but I managed to open it and make changes. When I quit, I don't think I quit properly again.
I then did

```

apt-get update
```

However, it said it was locked. SO therefore I decided to delete the swap file, because I thought it no longer would be locked. I had to use root permissions to do this but I did manage to delete the .sources.list.swap file.

However now when I do apt-get update, I get the message:

```
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory
```

Any solutions

---

### Post by Nythain on 2007-05-07
first off you need to sudo apt-get, thats why its permission denied

---

### Post by Polemistis on 2007-05-07
> **Nythain said:**
> first off you need to sudo apt-get, thats why its permission denied

cheers... it slipped my mind :P

---

### Post by Nythain on 2007-05-07
hehe... im notorious for trying to run aptitude in terminal while having synaptic open myself :)

---

