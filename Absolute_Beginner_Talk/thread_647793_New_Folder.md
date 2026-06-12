---
title: "New Folder"
date: 2007-12-22
forum: Absolute Beginner Talk
---

### Post by allsys3 on 2007-12-22
this may seem silly but how do you create a new folder within a folder?

---

### Post by santiagoward2000 on 2007-12-22
> **allsys3 said:**
> this may seem silly but how do you create a new folder within a folder?

Hi!
Just open the folder, right-click and select **Create folder...**

---

### Post by allsys3 on 2007-12-22
for some reason there is a little lock symbol over the file system folder and the "create folder" is not accessible

---

### Post by taurus on 2007-12-22
Where is that directory anyway?  You cannot create another directory if you don't have write permission to that directory.  So, try running nautilus with root.

Applications -> Accessories -> Terminal
```
gksudo nautilus
```

---

### Post by allsys3 on 2007-12-22
when i open places-computer it says in the file browser "home folder" and "file system". The file system icon has a little lock over it that prevents me from doing pretty much anything to any of the files or directories there. is ther a way to get rid of this little lock thingy as i dont recall it being there before.

---

### Post by jken146 on 2007-12-22
You don't have permission to write to a great deal of files.  That's a good thing.  You usually only need to have write permissions within your home directory (/home/your-user-name).  If, however, you do need to create a folder somewhere else, use ```
sudo mkdir /path/to/new/directory
``` or ```
gksudo nautilus
```

---

### Post by allsys3 on 2007-12-22
that does indeed create a new directory but i cant copy anything into it

---

### Post by PeterJS on 2007-12-22
The new folder will have the same security permissions as it's parent. You really shouldn't be messing with the file system at large, what are you trying to accomplish? and why can't it be safely done within your home directory?

---

### Post by allsys3 on 2007-12-23
i was at a site that had cool splash screens for when you log on. it said to create a directory called splashscreen in /boot/grub/ and save the pictures there.needless to say it hasnt worked out for me.

---

### Post by PeterJS on 2007-12-25
Oh, yep that's something that really does need root permission. Try running:
```

gksu nautilus

```
And when you get to the step about editing menu.lst you're going to want:
```

gksu gedit /boot/grub/menu.lst

```

Grub splash is really pretty, well worth the effort.

---

