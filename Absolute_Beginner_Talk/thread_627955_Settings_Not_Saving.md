---
title: "Settings Not Saving"
date: 2007-11-30
forum: Absolute Beginner Talk
---

### Post by esc1 on 2007-11-30
Lately when logging in to my Ubuntu my settings are completely different.  Trash and computer icons are on my desktop when I took them off long before. Under Applications, Places, and Settings there are no icons. My mouse speed is completely different. Font is different. One of my panels is not there. There's a small panel I never used before with nothing on it. I don't know what is going on. :confused:

---

### Post by Sef on 2007-11-30
Sounds like you may might have a corrupted desktop.  Let's see if reinstalling it works.

**Back up** your data first.  Not likely you will lose you data, but nothing is 100% guaranteed.

Applications > Accessories > Terminal

```
sudo apt-get update
```

```
sudo apt-get install ubuntu-desktop
```

---

