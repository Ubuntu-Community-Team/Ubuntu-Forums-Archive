---
title: "Add/Remove help!"
date: 2007-11-07
forum: Absolute Beginner Talk
---

### Post by Arken on 2007-11-07
When I go to install an application using the add/remove application tool, it says I need to reload my list. So I hit refresh, and then it continues to ask me! What do I do?

---

### Post by Arken on 2007-11-07
Bump, I'm also having an issue with the updater. Every time I do a system update, it says I'm up to date, but its been saying this for 3 days

---

### Post by jw5801 on 2007-11-07
In a terminal run:
```
sudo apt-get update && sudo apt-get upgrade
```Then if any errors get output paste the whole lot inside code tags here and we shall endeavor to debug.

---

### Post by Maestro23 on 2007-11-07
If the above suggestion doesn't work, please post your /etc/apt/sources.list

> cat /etc/apt/sources.list

---

