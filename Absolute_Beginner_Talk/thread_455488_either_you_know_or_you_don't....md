---
title: "either you know or you don't..."
date: 2007-05-26
forum: Absolute Beginner Talk
---

### Post by Jareth on 2007-05-26
...but, I just stumbled on some sites that give realy long winded methods of placing shortcuts to folders on your desktop.

The way I do it is just to drag the folder with the middle mouse button on to the desktop and select link here. Just that and it works for the home folder too.

I know it might be obvious but some folk might not realise it, so no 'duh?' responses thanks.

---

### Post by Bachstelze on 2007-05-26
duh?








Sorry, couldn't help :p

---

### Post by Jareth on 2007-05-26
tut

---

### Post by aysiu on 2007-05-26
Can I ask what the long-winded explanations are? I know of only two ways to do it and neither is long-winded.

What you described: middle-click-drag the folder to the desktop, let go, and select *link here*

The other method: ```
ln -s /path/to/folder ~/Desktop/folderlinkname
```

---

### Post by Jareth on 2007-05-26
ok, long winded is relative, but I found the page again:

[http://www.hamsterinthewheel.com/forum/viewtopic.php?t=231](http://www.hamsterinthewheel.com/forum/viewtopic.php?t=231)

---

### Post by aysiu on 2007-05-26
> **Jareth said:**
> ok, long winded is relative, but I found the page again:

[http://www.hamsterinthewheel.com/forum/viewtopic.php?t=231](http://www.hamsterinthewheel.com/forum/viewtopic.php?t=231)
Well, that's different, because it's an interface that allows you to easily hide and unhide icons for various things (not just one folder): home, trash, volume icons (external media).

---

### Post by Znupi on 2007-05-26
It's two diferent things. Using **gconf-editor** to show your Home folder on the desktop, makes nautilus create an 'auto-icon' on your desktop, which you can remove only with gconf-editor again. But, you can simply create a launcher with the command "nautilus" on the desktop, and it's the same thing basically, and you can delete it with Shift-delete.

---

### Post by steve.horsley on 2007-05-26
There's the really icky windowsy way - right-click the file and select Make Link. This creates a "Link to xxx" that you can drag/drop cut/paste. I really feel like I need a bath after doing tht though. I think it's the "Link To" that makes it feel all wrong.

---

