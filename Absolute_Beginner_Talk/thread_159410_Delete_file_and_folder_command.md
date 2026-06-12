---
title: "Delete file and folder command?"
date: 2006-04-12
forum: Absolute Beginner Talk
---

### Post by aktiwers on 2006-04-12
How do I delete a file or a folder I dont have permition to from the terminal?

I was trying to mount a HD, but made some mistakes, and now it has some empty folders in /media/ that I want to delete.

Is there a sudo command to do this?

Thanks

---

### Post by aysiu on 2006-04-12
```
sudo rm /media/disk/file.extension
```
```
sudo rm -rf /media/disk/directory
```

---

### Post by aktiwers on 2006-04-12
[QUOTE=aysiu]```
sudo rm /media/disk/file.extension
```
```
sudo rm -rf /media/disk/directory
```[/QUOTE]


Thanks! This worked smothly! :)

---

### Post by mehtuus on 2008-07-18
> **aysiu said:**
> ```
sudo rm /media/disk/file.extension
```
```
sudo rm -rf /media/disk/directory
```

I had a similar problem, but unfortunately this did not work for me. What I ended up doing is to *temporarily* enable the root login from the main login screen by going to **System>Administration>Login Window**, selecting the **Security** tab, and placing a checkmark next to "**Allow local system administrator login**".

---

### Post by Shippou on 2008-07-18
sudo rm -rf               <-- please don't give a damn trying this!

Just kidding. :)

I'm glad your problem was resolved. The rm command is so cool! It only deletes empty folders by default, though. To delete a folder with contents, just use the -r extension (that is why sudo rm -rf is dangerous because of the -r extension, and also -f too).

For explanations of sudo rm -rf, visit the link in my signature, or you can go here as well:

[http://www.balthisar.com/printing/09tutorials/05sudorm-rslash](http://www.balthisar.com/printing/09tutorials/05sudorm-rslash)
[http://forums.mactalk.com.au/31/42417-what-does-sudo-rm-f-do.html](http://forums.mactalk.com.au/31/42417-what-does-sudo-rm-f-do.html)

or just google it, as they say. :)

---

### Post by aktiwers on 2008-07-19
Wow who is digging up this old stuff :oops:

Leave me alone!!! 

(just kidding) :)

---

