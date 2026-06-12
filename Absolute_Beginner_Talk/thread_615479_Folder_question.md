---
title: "Folder question"
date: 2007-11-17
forum: Absolute Beginner Talk
---

### Post by aj5string on 2007-11-17
Hi...

right 2 questions...

first, i want to delete some folders from my desktop, however, when i try this, i get an error message, saying, "Error, not on the same file system while deleting..." What am i doing wrong?

2nd.  I want to add a shortcut to my home folder to my desktop - or ideally to my gdesklets launcher bar thing - but i cant!  How can i do this?

CHeers. Alex.

---

### Post by jken146 on 2007-11-17
Press Alt+F2, then type
```
gconf-editor
```
Navigate to apps>nautilus>desktop and tick the box next to home_icon_visible.

---

### Post by aj5string on 2007-11-17
Cool!

Any ideas why i cant delete the other folders?

Alex.

---

### Post by aj5string on 2007-11-18
Anyone?

I think i need to log in as root - i right clicked on the folder, and went to properties>permissions, and it said it was owned by root?

How do i log in as root, then delete a folder?

Alex.

---

### Post by atomkarinca on 2007-11-18
you don't have to login as root. type

```
gksudo nautilus
```

in a terminal and you will have the root access to the folder. other that that, you can change the permissions through that and delete it with your default nautilus.

---

