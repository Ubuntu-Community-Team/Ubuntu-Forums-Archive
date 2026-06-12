---
title: "Update Manager error."
date: 2007-08-26
forum: Absolute Beginner Talk
---

### Post by Robshaus on 2007-08-26
When I activated Package Manager to install 20 updates (I've been on vacation) the following error message appeared  "E: dkpg was interrupted. You must manually run 'dkpg --configure -a'  to correct the problem.
E:_ cache -> open() failed. please report."
When I type at the command prompt the command above system says "command nor recognized".    Please advise instructions to correct the problem.
Thank you.       Robert:popcorn:

---

### Post by jamvegan on 2007-08-26
Did you try running it with sudo?
```
sudo dpkg --configure -a
```
And actually, when I looked at what I had just copied from your post, I saw that the command name was misspelled (p and k reversed).

---

### Post by Robshaus on 2007-08-26
Did not use sudo.  Will try right now.   Thanks

---

### Post by Robshaus on 2007-08-26
Using sudo and spelling pkg correctly seems to work. Package Manager is running.  
Thank you. :)

---

