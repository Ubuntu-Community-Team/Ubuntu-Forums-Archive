---
title: "Cubedisappeared:("
date: 2007-05-05
forum: Absolute Beginner Talk
---

### Post by !Rami! on 2007-05-05
The cube thing on the botton right disappeared when i was entering desktop effects:(  please help this 13-yearold out, please!!!!!

---

### Post by useResa on 2007-05-05
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/desktop-effects/+bug/82957](https://bugs.launchpad.net/ubuntu/+source/desktop-effects/+bug/82957) [br].[/br] ---------------------------- [br].[/br] [br].[/br] 				The workaround - mentioned in the bug report - that got it working for me again is to issue the following commands (one at a time) in the terminal
```
gconftool-2 --type int --set /apps/compiz/general/screen0/options/hsize 4
``````
 gconftool-2 --type int --set /apps/compiz/general/screen0/options/number_of_desktops 1
```
Hope this will also help you.

---

