---
title: "Editing fstab"
date: 2006-08-24
forum: Absolute Beginner Talk
---

### Post by yustr on 2006-08-24
Abolute beginner question:

I want to edit my fstab file (so I can have drives mount at start up)- do I just open /etc/fstab in gedit, make the changes then save it?

I know it seems silly but I've also read that messing up fstab can  mess things up.  

Thanks

---

### Post by aysiu on 2006-08-24
Read this for graphical editing:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

If you must edit from the command-line, make a backup copy: ```
sudo cp /etc/fstab /etc/fstab.backup
``` Then edit it: ```
sudo nano /etc/fstab
```

Don't listen to people who say "Oh, just *sudo gedit /etc/fstab*."

1. You may not be using Ubuntu, in which case *gedit* won't work.

2. You should always back up configuration files before editing them.

3. *sudo* should be used with only command-line applications: [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

