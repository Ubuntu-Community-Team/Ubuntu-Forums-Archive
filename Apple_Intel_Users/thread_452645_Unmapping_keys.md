---
title: "Unmapping keys"
date: 2007-05-23
forum: Apple Intel Users
---

### Post by ivesjd on 2007-05-23
Ive installed feisty on my macbook. Love It. I use Yakauke for teminal, its default is set to F12. The only way I know of to reset it is once you have it open. Feisty defaults the F12 key to right click which i now have as right apple key as well. My question is, how do I remove right click from F12?

NOTE: xev doesnt work because F12 is right click. Could anyone tell me the code for the F12 key?

---

### Post by ivesjd on 2007-05-23
I booted the live cd and tried xev F12 and it gave me keycode 96, but it still does right click

**edit** 
I guess what I would like to do is remove gnomes default of right click with F12. Ive tried everything, Looked everywhere.
Could really use some help!
**/edit**

---

### Post by ivesjd on 2007-05-23
ended up reinstalling (due to other issues) and changed the F12 hotkey before installing mouseemu. Still would like to know how to do this though.

---

### Post by Gen2ly on 2007-05-24
Turning off 3 button mouse emulation would also give you this behavior.  This a kernel part that allows people to map contextual menus to key for people who have a 1 button mouse, for example.

[http://ubuntuforums.org/showthread.php?t=442941](http://ubuntuforums.org/showthread.php?t=442941)

---

