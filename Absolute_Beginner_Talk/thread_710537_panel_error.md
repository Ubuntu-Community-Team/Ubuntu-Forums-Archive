---
title: "panel error"
date: 2008-02-28
forum: Absolute Beginner Talk
---

### Post by someoneouthere on 2008-02-28
when i'm clicking on the panel i'm seeing the following message...:


```
file not found
error accessing 'file:///home/xxxxx/Desktop/Link%20to%20Pictures': File not found
```

although it shows the error message it shows the properties...
what is it?

---

### Post by spiderbatdad on 2008-02-28
looks like some kind of bad link associated with the panel. Seems to me you could safely remove it. But always best to get more than one opinion when removing files.```
sudo rm -rf /home/xxxxx/Desktop/Link%20to%20Pictures
```

---

### Post by someoneouthere on 2008-02-29
> **spiderbatdad said:**
> looks like some kind of bad link associated with the panel. Seems to me you could safely remove it. But always best to get more than one opinion when removing files.```
sudo rm -rf /home/xxxxx/Desktop/Link%20to%20Pictures
```

done it is still there....

---

### Post by forrestcupp on 2008-02-29
More than likely your panel's background is set to be a picture that there is no file for.  Right click on the panel and go to properties, and see if the background is set to be an image.  If so, you can change it to an image that you actually have, or set it to be a solid color with which you can set it's transparency if you want.

---

### Post by vamsibethapudy on 2008-02-29
you might have changed the location of the original file.
hence the error.
just right-click on the link & remove it from the panel.

---

### Post by someoneouthere on 2008-02-29
just had to replace the image... after all
but thnx a lot for the help

---

