---
title: "Default setting of Updates tab in Software Sources"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by schnuufi on 2007-04-24
Hi

I am puzzled about the default setting of the checkboxes of "Important security updates" and "Recommended updates" In the Updates tab of Software Sources (I am using Feisty). They are red and marked with a minus. What does that mean? Are the important security updates disabled? In this case, why aren't these boxes just empty, why are the boxes red and why are these fields not enabled by default? Should I enable these fields as a normal desktop user?

Regards
Schnuufi

---

### Post by Seisen on 2007-04-24
Post your source list in here that might be the problem

Applications>Accessories>Terminal
and put this in the terminal.

```
sudo gedit /etc/apt/sources.list
```

---

