---
title: "etc/X11/xorg.conf - no such file of directory??"
date: 2010-03-04
forum: Apple Hardware Users
---

### Post by jazzlukejosh on 2010-03-04
I've just spent an hour typing in my xorg.conf files and when I went to save, it said:
"Error writing etc/X11/xorg.conf: No such file or Directory"
I don't know what I've done wrong

---

### Post by mikewhatever on 2010-03-04
The file doesn't exist by default, so that you should create it. However, the error you got is because of the missing slash in the beginning.

**/etc/X11/xorg.conf** not [s]etc/X11...[/s]

---

### Post by jazzlukejosh on 2010-03-04
> **mikewhatever said:**
> The file doesn't exist by default, so that you should create it. However, the error you got is because of the missing slash in the beginning.

**/etc/X11/xorg.conf** not [s]etc/X11...[/s]

Can I create the file directory **/etc/X11/xorg.conf **from within the sudo nano editor thingy so I don't lose all my work

---

### Post by n0dix on 2010-03-04
> **jazzlukejosh said:**
> Can I create the file directory from with the sudo nano editor thingy so I don't lose all my work

Tried use gedit to paste the contend and then create the file with:
```
 $ sudo touch /etc/X11/xorg.conf 
```
Then, copy and paste.

---

### Post by mikewhatever on 2010-03-04
> **jazzlukejosh said:**
> Can I create the file directory **/etc/X11/xorg.conf **from within the sudo nano editor thingy so I don't lose all my work

Yes, absolutely. <sudo nano /etc/X11/xorg.conf> will create the file if it doesn't exist or otherwise open it for editing.

---

### Post by linuxopjemac on 2010-03-05
it is /etc/X11/Xorg.conf if I am not mistaken, with a capital X for Xorg.conf

---

