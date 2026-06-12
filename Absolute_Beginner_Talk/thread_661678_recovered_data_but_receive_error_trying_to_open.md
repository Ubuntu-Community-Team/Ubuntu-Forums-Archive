---
title: "recovered data but receive error trying to open"
date: 2008-01-08
forum: Absolute Beginner Talk
---

### Post by moosky13 on 2008-01-08
I've recovered the data with photorec but now I can't view the files.  Receive this error:you do not have the permissions necassary to view the contents of "recup_dir* .  I read on an earlier post to try: sudo chown -hR user: group dir, but that doesn't work.  I replaced the user part with my username "yermom" but I can't figure out the "group dir"part.  My recovered files are in my Documents folder.  Please help.

---

### Post by geirha on 2008-01-08
Writing this in a terminal should make all files and folders in Documents be owned by your user.
```
sudo chown -R $USER ~/Documents
```

---

