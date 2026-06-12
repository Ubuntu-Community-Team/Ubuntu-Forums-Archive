---
title: "Removing Java and gtk-qt-engine from Desktop"
date: 2007-08-24
forum: Absolute Beginner Talk
---

### Post by Gorlinux on 2007-08-24
Hi,

I recently installed Java 6 but encountered some difficulties. I followed the instructions to the letter, but I was not successful. Now I have decided to remove Java altogether. I have a couple of problems:

1. How do I remove Java?
2. How do I remove the items which by following the instructions effectively downloaded them to my desktop? When I try to move them to trash, I get this message:

Cannot move "/home/gorli...ux-i586.bin" to the trash because you do not have permissions to change it or its parent folder.

I would really appreciate your assistance. Thanks.

:(

---

### Post by Hobo Joe on 2007-08-24
Not sure about the first one, but the second one is becuase the you don't have permisions for the desktop.

To get them, press ALT+F2, and it will give you a run prompt. You need to type 'gksudo natilus'. That will give you a browser with administrative rights.

---

### Post by Gorlinux on 2007-08-24
Thanks, I tried using ALT+F2 then run. After that, when I tried to delete (i.e. move to trash) the folders and programs on my desktop, I still get the same message:

Error while moving
Cannot move "/home/gorli...ux-i586.bin" to the trash because you do not have permissions to change it or its parent folder.

I checked the properties of one of the items which I wanted to remove and under permissions the owner says root. On the bottom it says "You are not the owner, so you can't change these permissions." It seems that Ubuntu is not recognizing me as the owner, am I understanding this correctly? Perhaps if there is a way to make me the owner, I would be able to remove them from my desktop. 

Any advice would be greatly appreciated. Thanks.

---

### Post by Tyke91 on 2007-08-24
yeah, i've also run into this problem before (not with ubuntu, but with damn small linux) 

i'd like to know why root doesnt have permissions to do some things on his computer...

---

