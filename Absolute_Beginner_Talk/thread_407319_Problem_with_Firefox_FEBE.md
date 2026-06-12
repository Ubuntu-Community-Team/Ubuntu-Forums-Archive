---
title: "Problem with Firefox FEBE"
date: 2007-04-12
forum: Absolute Beginner Talk
---

### Post by jacatone on 2007-04-12
I installed my Firefox extensions, themes, bookmarks etc. into Firefox using FEBE. Now I keep getting this annoying popup telling me some of the files need to execute permission to continue. Please see the snapshot I took of the error message. When I try clicking on Cancel or OK, my cursor just flickers and does nothing.  Anyone know how to fix this? Thanks.

---

### Post by aidanr on 2007-04-12
open a terminal, applications -> accessories -> terminal, and type:

sudo chown -R [username] ~/.mozilla
sudo chmod -R 755 ~/.mozilla

replace [username] with your account name and type in your password when prompted

---

