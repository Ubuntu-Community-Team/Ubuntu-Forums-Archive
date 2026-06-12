---
title: "Permissions"
date: 2007-05-25
forum: Absolute Beginner Talk
---

### Post by goobermaster on 2007-05-25
Hello, I have just started using Linux, and this being the 'Absolute Beginners' forum, thought that it would be the most appropriate area to ask questions in. I currently have two.

When I set up linux, I made three partitions - the main directory (/), a swap, and a /programs (which is far larger and is intended to hold my collection of wine-related games).

However, I have been trying to move files into /programs, and it is saying that I do not have the permission to do so. I have tried to login as root in the terminal (with sh - and sudo), and have gained access to the root user (i.e. my name becomes root@compname), but it still will not let me transfer files. Are there any suggestions to help me remedy this problem?

My second question has to do with wine itself - none of the sound options work - i.e. when I run winecfg, and go to audio options, no matter which driver set I select, the audiotest and control panel options just error out with an "audiotest/control panel not implemented yet". I realize that this might not be the place to ask about wine, so any links to help me resolve this would be appreciated.

Thanks in advance.

---

### Post by ryanVickers on 2007-05-25
Well, I'm no wine or crossover expert, or even slightly helpful on the topic, but What I would do to fix your copying problem is start file browser as root (gksudo nautilus) and then select the folder/mount point "/programs", then go into properties.  Make the owner you, and give you full read/write.  Then in the group section, choose your group (your user name) and again make it full read/write.  That should work*.

*allow you to do whatever when your not root.

---

### Post by goobermaster on 2007-05-25
Thank you very much about the first topic! It worked like a charm!

Now only the wine issue is left...

---

