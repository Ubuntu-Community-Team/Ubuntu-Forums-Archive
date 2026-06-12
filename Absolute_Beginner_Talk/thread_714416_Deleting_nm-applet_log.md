---
title: "Deleting nm-applet log"
date: 2008-03-03
forum: Absolute Beginner Talk
---

### Post by High Camp on 2008-03-03
Hi All

I have nm-applet (the stock one that comes with Gutsy) managing my wireless connection. It's really nice that this program automatically connects to networks that you've connected to in the past. The problem is when you connect to networks with default names such as "default", "linsys", "d-link", etc. then it connects to any network with this name. I'm wondering if there's any way to have it not remember certain networks or delete the log file so I can start from scratch.

Thanks much,

---

### Post by High Camp on 2008-03-04
Anyone?

---

### Post by insub2 on 2008-05-10
I know this is a little late and hopefully you found you answer by now.
But in case you haven't what you need to do is open a terminal and type:
```
gconf-editor
```
Then navigate to you networks by way of system > networking > wireless > networks > *network name*.  Then right click on **all** the items under "Name" and unset value.  When you restart, all will be well.

I have attached a screenshot.

At time of writing, I know of no easier way.  They have yet to build a feature into nmapplet.  which is kinda dumb.



**Alternative method that doesn't seem to work on my Gutsy install but does on my edgy install**
Click alt+F2 to get the Run Application prompt and start typing gconf-editor and all the rest of the steps are the same.

---

