---
title: "Rm folder copied fr Windows"
date: 2005-10-22
forum: Absolute Beginner Talk
---

### Post by webbie180 on 2005-10-22
How can I remove a folder copied from Windows to my desktop which I have no permission?

---

### Post by davmac on 2005-10-22
There are a couple of ways of doing this but I'd open up a terminal and type;

cd Desktop
sudo rm -rf directory_name

The sudo effectively means that the remainder of the command is run is if you were the root user.

If you want to find out more about the rm (remove) command, type "man rm".

Hope this helps,

Dave Mac

---

