---
title: "[SOLVED] synaptic remove vs. complete remove"
date: 2008-04-18
forum: Absolute Beginner Talk
---

### Post by waggingwabbit on 2008-04-18
whats the difference between remove and completely remove in synaptic package manager?

---

### Post by unutbu on 2008-04-18
[http://ubuntuforums.org/archive/index.php/t-388278.html](http://ubuntuforums.org/archive/index.php/t-388278.html)

---

### Post by waggingwabbit on 2008-04-18
Solved! =d

---

### Post by stchman on 2008-04-18
> **waggingwabbit said:**
> whats the difference between remove and completely remove in synaptic package manager?

The Completely Remove option is supposed to remove all unused dependencies.

---

### Post by ajgreeny on 2008-04-18
> The Completely Remove option is supposed to remove all unused dependencies. 		               	             		  		 			I don't think that's quite right, what it does is remove all the config files that were added once you had used the program (or at least, most of them).  To remove unused dependencies you need to use ```
sudo apt-get autoremove packagename
```

---

