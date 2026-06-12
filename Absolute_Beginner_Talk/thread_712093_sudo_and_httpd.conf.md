---
title: "sudo and httpd.conf"
date: 2008-03-01
forum: Absolute Beginner Talk
---

### Post by Tashu on 2008-03-01
I am not sure how to save the file - httpd.conf. It's in /opt and is protected and I tried to save it but due to the root privileges so I couldn't. 

I usually use sudo in terminal to do updates, or go in control panel. With the GUI text document, I couldn't figure out how to sudo GUI text document. Any suggestions?

It'll be not a one time save, I probably will debug the server file.

---

### Post by bukwirm on 2008-03-01
If you're using a terminal, you should be able to simply type "sudo *text_editor_name filename*".

---

### Post by jan quark on 2008-03-01
```
gksudo gedit /path/to/textfile 
```

now you can save

---

### Post by Tashu on 2008-03-01
Thanks, I'll try it out.

---

