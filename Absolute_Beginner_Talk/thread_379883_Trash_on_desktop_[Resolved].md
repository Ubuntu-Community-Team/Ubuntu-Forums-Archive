---
title: "Trash on desktop [Resolved]"
date: 2007-03-09
forum: Absolute Beginner Talk
---

### Post by dhaulk on 2007-03-09
Yea I was wondering I removed my trash from down on the bar. I got it back easy enough but I was wondering if there is a way to just have it on desktop where its easy to get to?

---

### Post by aysiu on 2007-03-09
> **dhaulk said:**
> Yea I was wondering I removed my trash from down on the bar. I got it back easy enough but I was wondering if there is a way to just have it on desktop where its easy to get to?
Are you using Ubuntu, Xubuntu, or Kubuntu?

---

### Post by dhaulk on 2007-03-09
I am using Ubuntu

---

### Post by aysiu on 2007-03-09
Press Alt-F2 and type ```
gconf-editor
``` Then go to Apps > Nautilus > Desktop

I think there should be a checkbox there for showing the Trash on the desktop.

**Edit**: [Apparently the checkbox is called *trash_icon_visible*](http://www.ubuntuforums.org/showthread.php?p=1359443#post1359443)

---

### Post by dhughes on 2007-03-09
Press the ALT key and then F2 you'll get a box called "Run Application", in the blank field type this: gconf-editor 

 The GNOME Configuration Editor will open.

  On the left side you'll see a list:  /, apps, desktop, schema, system click the little triangle next to "apps".

  Scroll down to "nautilus" click its little triangle, under that go to "desktop".

  On the upper right-side window you'll see a list of options, click the box next to  "trash_icon_visible"

 The Trash icon is now visible on your desktop.

  That's it!

 edit:

 Feel free to add others that are in the same area such as Home Icon, Network Icon, Computer Icon.

---

### Post by dhaulk on 2007-03-09
Ah yes thats much better thanks alot.

---

### Post by dhughes on 2007-03-09
You're welcome.

 Have a look around while your in there and change some stuff you can really customize GNOME with just a few check marks.

---

