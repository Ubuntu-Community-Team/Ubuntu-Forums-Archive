---
title: "update not working from terminal"
date: 2006-11-29
forum: Absolute Beginner Talk
---

### Post by swp6499 on 2006-11-29
sudo apt-get update && sudo apt-get upgrade not working in terminal anymore...although if there is a update and run update from terminal it sets off the update notification in the panel...and will update from the update manager...anyone encountered this before?

---

### Post by ciscosurfer on 2006-11-29
> **swp6499 said:**
> sudo apt-get update && sudo apt-get upgrade not working in terminal anymore...although if there is a update and run update from terminal it sets off the update notification in the panel...and will update from the update manager...anyone encountered this before?My best guess is that when you were trying to do it from the terminal, the repos that you have in your sources.list were down.  When you went to update through the update manager, they were back up.

Keep in mind, [you can always use mirrors]("http://wiki.ubuntu.com/Archive").

---

### Post by swp6499 on 2006-11-29
mirrors were up in terminal and update manager..that doesnt seem to be the problem..although it would be nice if thats all it was...any other ideas?

---

