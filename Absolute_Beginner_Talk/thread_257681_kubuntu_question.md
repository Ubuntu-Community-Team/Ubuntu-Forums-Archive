---
title: "kubuntu question"
date: 2006-09-14
forum: Absolute Beginner Talk
---

### Post by swp6499 on 2006-09-14
can anyone tell me how to access my xorg.conf file in kubuntu?? thanks

---

### Post by aysiu on 2006-09-14
Alt-F2 ```
kdesu konqueror
```

---

### Post by swp6499 on 2006-09-14
in terminal?? i need to edit something and completely having a brain shutdown..?

---

### Post by aysiu on 2006-09-14
No.

You press the Alt button on your keyboard. While holding that button down, also press the F2 button.

This key combination will pop up a "run" dialogue.

In that dialogue, type ```
kdesu konqueror
```

---

### Post by jISh on 2006-09-14
Hmm
Alt+F2 and
kdesu kate /etc/X11/xorg.conf 

Should be more specific.

---

### Post by aysiu on 2006-09-14
> **jISh said:**
> Hmm
Alt+F2 and
kdesu kate /etc/X11/xorg.conf 

Should be more specific.
That is the more direct approach. However, that doesn't give swp6499 the opportunity to make a backup copy of the file before editing it.

---

### Post by claydoh on 2006-09-14
Even easier, go to /etc/X11/ and simply right-click on the file, and select "Actions-Edit as Root" which will open the file using kdesu and kwrite. Kwrite makes a backup copy when you save.

---

### Post by swp6499 on 2006-09-14
thanks to both of u..i really appreciate it...but i still cant change my resolution even editing the xorg.conf file this is a ongoing problem...

---

### Post by aysiu on 2006-09-14
Maybe take a look at some of [these solutions](http://ubuntuforums.org/showpost.php?p=129379&postcount=21)?

---

