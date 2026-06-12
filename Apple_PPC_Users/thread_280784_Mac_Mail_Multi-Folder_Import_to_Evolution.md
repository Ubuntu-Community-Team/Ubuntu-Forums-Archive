---
title: "Mac Mail Multi-Folder Import to Evolution"
date: 2006-10-20
forum: Apple PPC Users
---

### Post by DonnieP on 2006-10-20
Not guaranteed, but worked for me (and I apologize if this is documented elsewhere already and I just couldn't find it):

Use this script on the Mac to convert folders of the newer Mac Mail emlx files to mbox files (thanks to creator, Marshall Elfstrand):
[http://vengefulcow.com/emlx2mbox/](http://vengefulcow.com/emlx2mbox/)

Then create a 'mail' folder in your Ubuntu home directory and copy the converted mbox files to ~/mail as suggested here (I used NFS to get them to Ubuntu):
[http://www.math.jhu.edu/help/evolution.html](http://www.math.jhu.edu/help/evolution.html)

Finally, use Evolution's built-in File Import | Import data and settings from older programs. It will discover your 'mail' directory (thinking they're PINE) and import all of them without having to go through the tedious single file procedure.

---

