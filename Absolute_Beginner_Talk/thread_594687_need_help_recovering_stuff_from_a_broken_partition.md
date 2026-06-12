---
title: "need help recovering stuff from a broken partition usin knop+pix"
date: 2007-10-28
forum: Absolute Beginner Talk
---

### Post by petegreenhorn on 2007-10-28
Hi, after posting for help with a broken login and getting no help i decided to do a reinstall . but i would like to recover my email inbox and addresses from thunderbird . can anyone help . i'm online via Knoppix and i'm not very good at computing . the partitions that i can't access normally are still there and i can get at some things , just i don't know where to look for the thunderbird stuff
Any help greatfully rec

---

### Post by kellemes on 2007-10-28
I think Ubuntu installs it here /home/"user"/.mozilla-thunderbird/profiles
Not sure since I'm using my own strange little setup, but it's somewhere in a hidden directory in /home/user
If you copy the profiles directory you'll be fine.. As you browse further into the directory-tree you'll see all the stuff you want to backup.
Later you can simply copy back the hole thing.. **or** you can use the profile from an alternative location by starting-up Thunderbird like this:
```
thunderbird -profilemanager
```
and from the dialog point to the new location of where you put these profiles you want to use..

---

### Post by petegreenhorn on 2007-10-28
thanks for the reply Kellemes

i'll go give it  a try

---

