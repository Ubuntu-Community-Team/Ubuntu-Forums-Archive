---
title: "How do I extract &quot;tar&quot; files properly (tried a couple)"
date: 2007-05-21
forum: Absolute Beginner Talk
---

### Post by WHICKS on 2007-05-21
Hi, I was trying to load up a First person shooter  from sourceforge.net, and the file was called    	paintball2_build018_linux_full.tar.gz   .

How do I open this file properly once I download it.

Thanks, and sorry for the noob question.

---

### Post by taurus on 2007-05-21
Applications -> Accessories -> Terminal
```
cd ~/Desktop
tar xvzf paintball2_build018_linux_full.tar.gz
```

Look at Section 4 of this guide, [http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware).

---

### Post by starcraft.man on 2007-05-21
> **WHICKS said:**
> Hi, I was trying to load up a First person shooter  from sourceforge.net, and the file was called    	paintball2_build018_linux_full.tar.gz   .

How do I open this file properly once I download it.

Thanks, and sorry for the noob question.

The easy GUI way is to right click the file on your desktop (or in nautilus if its in your home folder) and click extract here. Long as it isn't corrupt it will extract in a new folder.

Ubuntu has a great archiver with lots of support built in, unlike another OS I know.....

Edit: Ha! I knew taurus would beat me to the post and give the terminal command :p

---

### Post by WHICKS on 2007-05-22
Thank you, I'll try the GUI version first.

I'll let you know how it goes.

---

### Post by darkworld on 2007-05-22
[http://monkeyblog.org/ubuntu/installing/]("http://monkeyblog.org/ubuntu/installing/")

---

