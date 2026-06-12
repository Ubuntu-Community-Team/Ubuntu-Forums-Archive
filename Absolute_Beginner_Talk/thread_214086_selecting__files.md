---
title: "selecting  files"
date: 2006-07-12
forum: Absolute Beginner Talk
---

### Post by MaximB on 2006-07-12
I have about 1000 files in one folder
I want to select...say...the first 200 files
how can I select them without using "shift" and clicking file by file...?
I'm using nautilius.

---

### Post by lapsey on 2006-07-12
select an item, hold shift, and move the cursor keys (or home or end) to select more items in nautilus.

or, in thumbnail view select a blank area and click and drag to draw a selection box

---

### Post by MaximB on 2006-07-12
and how can I change the view to the view list of windows..with no details
so I get a several colums of files ?

---

### Post by lapsey on 2006-07-12
> **MAXDDARK said:**
> and how can I change the view to the view list of windows..with no details
so I get a several colums of files ?

View > View as Icons. Or Ctrl + 1.

---

### Post by MaximB on 2006-07-12
no...I don't want icons
I want a list but without details..I want to have several colums 
I want to be able to select as many files I can with the mouse.

---

### Post by lapsey on 2006-07-12
view as icons and zoom out. the icons can get incredibly small



if that's not good enough, then paste this into The Terminal (Applications > Accessories > Terminal) to get and launch Thunar, a file manager that DOES allow what you are after. a little exploration and you will find out how to change the view in Thunar.

```
sudo apt-get install thunar; thunar ~/ 
```

there are other ones but that is the first one i can think of.

---

