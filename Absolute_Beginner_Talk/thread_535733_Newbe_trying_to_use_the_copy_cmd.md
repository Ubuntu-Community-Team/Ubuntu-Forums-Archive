---
title: "Newbe trying to use the copy cmd"
date: 2007-08-26
forum: Absolute Beginner Talk
---

### Post by aja on 2007-08-26
Hello 

Can someone please tell what i am doing wrong ??  I am trying to back up my xcorg.conf file with this 

sudo cp /etc/x11/xorg.conf /etc/x11/xorg.conf.good


and all I get is 


cp: cannot stat `/etc/x11/xorg.conf': No such file or directory


I know the file does exist

aja

---

### Post by por100pre1 on 2007-08-26
The X in X11 should be Uppercase.

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.good
```

---

### Post by ArtF10 on 2007-08-26
That actually happened to me once when I tried to open Xorg.conf...very strange.  I restarted and tried again, and it worked.

---

### Post by S15_88 on 2007-08-26
capitol X

---

### Post by Majorix on 2007-08-26
It won't work after a restart. It will never work. Because Linux is case-sensitive.

---

### Post by verbalshadow on 2007-08-26
The X should be capitialized if i recall correctly.

sudo cp /etc/**X11**/xorg.conf /etc/**X11**/xorg.conf.good

---

### Post by speeddemon8803 on 2007-08-26
> **verbalshadow said:**
> The X should be capitialized if i recall correctly.

sudo cp /etc/**X11**/xorg.conf /etc/**X11**/xorg.conf.good

Linux has always been and always will be CaSe SeNsItIvE so watch the caps of the things you are trying to type in...I get a lot of complaints/why didnt that work's...just watch your caps people and it should work..if you get errors after you KNOW your using the  correct caps and the correct locations...come back..we can hold your hand and help you try new stuff and troubleshooting...I am an A+ certified person...I do know that really doesnt apply to the Linux world but hey I know hardware! :) I soon hope to get Linux+ certified so I can help out fully in this field.

---

### Post by aja on 2007-08-26
Thank you ! I should have paid attention to the cap.

aja

---

