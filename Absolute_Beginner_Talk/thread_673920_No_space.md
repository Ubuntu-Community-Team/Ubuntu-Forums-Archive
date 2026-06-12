---
title: "No space"
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by baz.g on 2008-01-21
Hi, i am running Ubuntu 7.10 from a 4gb USB pen. I stupidly decided to try and install loads of games from synaptic package manager but now i get loads of errors about no disk space. The games did not install successfully so i was thinking maybe the temporary files that were downloaded is what is using up all the space so i cleaned out the /tmp directory. But i still get the no disk space errors. I have also cleaned out all the folders in thunderbird. I am even getting the "no disk space" errors when i try to move any folders/files to the desktop or the home folder :(

Please help :)

---

### Post by renzokuken on 2008-01-21
have you emptied your trash folder?

if not empty the **/home/.Trash_*username*** folder from the terminal

---

### Post by aos101 on 2008-01-21
You could try running:
```
sudo apt-get clean
```
which according to [here](http://www.debianuniverse.com/readonline/chapter/05) will flush the package cache and free up some space.

---

