---
title: "Error editing sources.list"
date: 2006-11-06
forum: Absolute Beginner Talk
---

### Post by mtgrocks04 on 2006-11-06
I'm trying to install beryl. When I go to edit my sources.list if I use sudo kate /etc/apt/sources.list I just get a blank document. If I go through konqueror and open it in kate I get this error:
The document could not be saved as it was not possible to write to file:///etc/apt/sources.list
Check that you have write access to this file or that enough disk space is available. 

I don't know what this means. I have been able to edit this file just the other day. Any thoughts?

---

### Post by aysiu on 2006-11-06
Well, really you should be using ```
kdesu kate /etc/apt/sources.list
``` but if you're sure you typed it correctly, and you still come up with a blank document... then you have a blank sources.list.

---

