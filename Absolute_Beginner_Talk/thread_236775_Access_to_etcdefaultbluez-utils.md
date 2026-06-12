---
title: "Access to /etc/default/bluez-utils"
date: 2006-08-15
forum: Absolute Beginner Talk
---

### Post by willywilly on 2006-08-15
Never ran Linux before, so please excuse my lack of basic knowledge.

I want to edit /etc/default/bluez-utils with a Texteditor to add my Bluetooth mouse - but I can not save it afterwards. What do I have to do for this? The owner of the file is "root". What now?

Thanks in advance. :)

---

### Post by martinmanzana on 2006-08-15
You may not be able to save since you are not editting as the root user. I am new to linux too. I wouldn't let me save a system file I had editted. Then I tried the following command:```
sudo nano filename.ext
```

nano is my favorite text editor, you can use your favorite. But the thing is to run in as the root user. Hope it helps.

---

### Post by willywilly on 2006-08-15
Thanks for pointing me in the right direction. :D

Is there a possibility to enable an app that is already running to have those root-privileges? For example I'd like to remove the "Examples"-Link in my /home/MYNAME dir - but for that the file-explorer would need to have sudo-rights as well. How do I do that?

---

### Post by kerry_s on 2006-08-15
You can use nautilus as root, in terminal> sudo nautilus / <this will give you full access to read and write to all files/folders.

---

