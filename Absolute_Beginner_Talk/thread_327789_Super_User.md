---
title: "Super User?"
date: 2006-12-29
forum: Absolute Beginner Talk
---

### Post by Straft on 2006-12-29
Ok I tried running my graphics card driver, and it pops up a box saying I need to be logged in as a "Super-User", I'm assuming they mean the "root" account, so logged out of my account and tried logging into the root account, It says "The system administrator is not allowed to login from this screen", so where do I login at?

---

### Post by taurus on 2006-12-29
Try the **sudo** command...

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Apple 101 on 2006-12-29
Just login normally.  Then open a terminal and add 'sudo' (without quotes) to the start of the command. (Beaten to it...)

---

### Post by Straft on 2006-12-29
Thank's all, I did "sudo -i -u root" and drag and dropped the .run file into the terminal and hit enter and it worked. Thanks much :)

---

