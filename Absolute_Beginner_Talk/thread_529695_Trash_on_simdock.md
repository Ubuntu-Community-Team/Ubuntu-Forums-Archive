---
title: "Trash on simdock?"
date: 2007-08-19
forum: Absolute Beginner Talk
---

### Post by paullinux on 2007-08-19
Who knows how to make the trash visible on simdock?

---

### Post by saipu on 2007-09-01
You may try this :
1. Create a new launcer in Simdock
2. Name it as Trash
3. Enter this for the command : nautilus --browser ~/.Trash
4. Choose Trash icon for the laucher

---

### Post by DarthPooky on 2007-11-21
> **saipu said:**
> You may try this :
1. Create a new launcer in Simdock
2. Name it as Trash
3. Enter this for the command : nautilus --browser ~/.Trash
4. Choose Trash icon for the laucher

Could you give us the specific code for that?

---

### Post by christopher4evr on 2008-06-01
I know this is an old thread but this is the first thing that came up when I googled for this so I thought I'd put this titbit of information here...

Instead of:
nautilus --browser ~/.Trash
try,
nautilus --browser trash:

Now you can easily empty the trash.

---

