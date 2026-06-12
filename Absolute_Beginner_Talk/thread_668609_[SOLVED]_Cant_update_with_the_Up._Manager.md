---
title: "[SOLVED] Cant update with the Up. Manager"
date: 2008-01-15
forum: Absolute Beginner Talk
---

### Post by Yuliya on 2008-01-15
I used the Update Manager once and everything worked fine, but after I installed Java, this message started to appear:

Software index is broken

It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.

I do what it says there and then I get:

attila@attila-desktop:~$ sudo apt-get install -f
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
attila@attila-desktop:~$ 

and when I do what it says there, it says that everything has been done correctly.

What is the problem? I cannot longer use the Update Manager and I cannot watch the newspaper, though I have everything installed (I had the same problem before and I've checked my previous posts and done everything as before, but this time it doesn't seem to work)

---

### Post by nikoPSK on 2008-01-15
try it with superuser privileges. :)

```
sudo dpkg --configure -a
```

---

### Post by Yuliya on 2008-01-16
where do I find that option?

---

### Post by justleen on 2008-01-16
just copy an paste the whole comamnd into a terminal

---

### Post by Yuliya on 2008-01-17
done and works. Thank you.

---

### Post by nikoPSK on 2008-01-17
Please mark this thread as "SOLVED" :)
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

nikoPSK

---

