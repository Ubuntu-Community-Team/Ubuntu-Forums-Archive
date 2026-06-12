---
title: "Simple Question"
date: 2007-03-10
forum: Absolute Beginner Talk
---

### Post by Rindan on 2007-03-10
I am an Ubuntu/Linux n00b.  I partitioned up my HD, got Ubuntu and XP to share some space with a working dual boot, and even got my nVidia card working.  Feeling as if my hax00r skills were clearly l337 enough to do more, I bit off a tad more then I could chew and tried in get Beryl working... with predictable results.  I got three steps into the instructions and promptly ruined my system such that I can only boot into console mode.

Now, I am pretty sure I can undo the damage... except for the tiny fact that I have not a clue how to edit files... much less edit them as root, in the console.  So, if anyone can tell me how to call up a text editor and then edit as root, I would appreciate it greatly.



P.S.  Still feeling a little to big for my britches and looking to kill my computer before I get it working again, if anyone knows of a link to some nice simple directions that assume I am an utter idiot for installing Beryl, please do post.

---

### Post by mikewhatever on 2007-03-10
sudo nano file_path_and_name

for example

sudo nano /etc/X11/xorg.conf

---

### Post by Rindan on 2007-03-10
That worked and my system is running normally again.  Thanks!

---

