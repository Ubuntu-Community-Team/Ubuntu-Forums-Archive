---
title: "Changing file permissions"
date: 2007-03-31
forum: Absolute Beginner Talk
---

### Post by chroniker on 2007-03-31
It's probably here somewhere but I've yet to find it.

While using Nautilus, how do I log in as root so I can change file permissions?

---

### Post by Scunizi on 2007-03-31
There's a great explaination of how this works here... [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions).  However, it is command line stuff.  If the file is in your home directory you might be able to just right mouse click, properties, permissions and make your changes there in the check boxes that are presented.

---

### Post by brennydoogles on 2007-03-31
> **chroniker said:**
> It's probably here somewhere but I've yet to find it.

While using Nautilus, how do I log in as root so I can change file permissions?

I'm not exactly sure how to do it with the GUI, but if you use the terminal you can either use the chown or chmod commands to edit permissions. The way you would do that would be 

```
sudo chown [COLOR="Red"]your username /path/to/file/or/folder[/COLOR]
```

Replacing the red text with the appropriate information ***NOTE: This option will change ownership of whatever you use it on. You do not want to do this with system files. You should only really do this if you want to change the ownership of something like a storage drive.***

You can also use the chmod command, which will simply change the permissions on the file. The way you would do this would be 

```
sudo chmod [COLOR="Red"]755 /path/to/file[/COLOR]
``` 

replacing the 755 with the appropriate number according to [this thread]("http://www.ubuntuforums.org/showpost.php?p=502685&postcount=48"). If you need any help feel free to ask, and welcome to the community!!!

---

### Post by taurus on 2007-03-31
<Alt>F2 -> gksudo nautilus[/code]

---

### Post by chroniker on 2007-03-31
> **taurus said:**
> <Alt>F2 -> gksudo nautilus[/code]
Now this is scary, cool but scary. Now I can cause all sorts of trouble for myself.

---

### Post by taurus on 2007-03-31
> **chroniker said:**
> Now this is scary, cool but scary. Now I can cause all sorts of trouble for myself.

Yip.

---

