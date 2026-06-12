---
title: "Make xhost + permanent"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by orbeus on 2007-10-22
Hi.

xhost  + has solved an issue I had with ctontab but it seems to reset on reboot.
Is there any way to make this permanent?

TIA
O

---

### Post by magli on 2007-10-22
You can add commands which you want run automatically to your .xsessions file. The commands in this file will then be run whenever you login.

So, create a new file in your home directory called ".xsessions". Add a line to the file which simply says "xhost +" - without the quotation marks.

Also not that in linux, and file/folder beginning with a dot (.) will be hidden, so you will not see this file in your home directory.

---

