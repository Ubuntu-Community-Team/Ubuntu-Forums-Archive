---
title: "new drive problems"
date: 2007-01-15
forum: Absolute Beginner Talk
---

### Post by Pappasan on 2007-01-15
I am a brand new Ununtu (6.06LTS) user and for the most part I really like it.  I needed a 2nd computer for the kids to use and this seems to fit all of my needs.  I installed it just fine and got all of my necesary applications up and running.  What it is missing is a centralized storage space for shared music, photos, etc for all of the users to access.  I installed second 80Gb HD and formatted it with Disk Manager (/dev/hdb1, Extended 3, /media/Data).  I can enable it but I then don't have permission to use it (owner is root).  I must be missing a step or two and haven't found anything in the forums that describe setting up 2nd hard drives post install.  I have a few questions for the community:

1.  Where is the HOWTO that I missed that described how to do this?
2.  How do I share the drive so any user can read/write/execute?
3. How can I place permanent a shortcut on the kid's desktop to the shared drive?

I am coming from MacOSX so there is some command line knowledge but would prefer to do this in a GUI enviornment whenever possible!

---

### Post by taurus on 2007-01-15
Applications -> Accessories -> Terminal
```
sudo chmod -R 777 /media/Data
```
Now, everybody can write (delete) to it.

---

