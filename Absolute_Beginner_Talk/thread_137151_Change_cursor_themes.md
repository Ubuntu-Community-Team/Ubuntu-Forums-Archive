---
title: "Change cursor themes?"
date: 2006-02-27
forum: Absolute Beginner Talk
---

### Post by Clark Nova on 2006-02-27
I've downloaded a cursor theme for my mouse pointer from Gnome-look.org but I can't work out how to install it. Is there a way to do it from the GUI? Do I need to copy the folder somewhere in particular?

Thanks :)

---

### Post by Xian on 2006-02-27
There's probably an easier way, but I've done it like this always:

1. Create a directory in your home folder (/home/<username>) called .icons.

2. Place the cursor theme directory into ~/.icons. 
The directory should have the form ~/.icons/THEME_NAME/cursors.

3. With gconf-editor, set the value of /desktop/gnome/peripherals/mouse/cursor_theme to the name of the new theme.

---

### Post by aysiu on 2006-02-27
[Make sure you have the proper repositories](http://www.psychocats.net/linux/sources.php)

Then: ```
sudo apt-get update
sudo apt-get install gcursor
```

---

### Post by Xian on 2006-02-27
You see, I knew there was an easier way. :)
But I'll still use my method (else I get accused of being hip).

---

### Post by Mr.Thunderbird on 2008-02-25
> **aysiu said:**
> [Make sure you have the proper repositories](http://www.psychocats.net/linux/sources.php)

Then: ```
sudo apt-get update
sudo apt-get install gcursor
```

Hi, I'm a bit new to this, but AFTER installing Gcursor, I get this when running it:



```
root@iouri-laptop:/# gcursor
(gcursor:28514): libglade-WARNING **: could not find signal handler 'extract_theme'.
(gcursor:28514): libglade-WARNING **: could not find signal handler 'open_theme_dir'.
(gcursor:28514): libglade-WARNING **: could not find signal handler 'entry_selected'.
(gcursor:28514): libglade-WARNING **: could not find signal handler 'size_changed'.

```

Oh, and the XCursor selector pop-up's but the button doesn't do anything, it hangs...

Thank you :)

---

### Post by aysiu on 2008-02-25
Maybe [this](http://ubuntuforums.org/showthread.php?t=628988) might help.

---

### Post by Mr.Thunderbird on 2008-02-25
Thanks for the very quick reply! 

Thanks for the link!

---

