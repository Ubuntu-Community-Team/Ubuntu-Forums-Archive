---
title: "[SOLVED] How Do I Create A Shortcut To A Drive?"
date: 2007-03-01
forum: Absolute Beginner Talk
---

### Post by AlistairH on 2007-03-01
I've successfully managed to add a second hard drive, change ownership and permissions so this seems such a stupid question.

This is probably staring me in the face but I simply cannot see it. How can I create a shortcut on my desktop and/or within the file browser window so that I do not need to drill down through the file system to my mount point, /media/data?

Thanks in advance.

Ali

---

### Post by mahy on 2007-03-01
This is what i'd do:

```
cd ~        #jump to your home directory
ln -s /media/data newdisk
```

it'll create a symbolic link to /media/data named 'newdisk'

hope it helps!

---

### Post by BillGod on 2007-03-01
from a terminal window do this

ln -s /path/to/mountpint /home/username/Desktop/shortcut_name

---

### Post by Brandel Valico on 2007-03-01
I usually just open a Natulis window to the folder that contains the drive Folder and then drag a link into the left side panel. Which makes a link in my places Dropdown menu for me to use.

---

### Post by AlistairH on 2007-03-01
Thanks for the responses folks. I'm amazed at how quickly questions get answered in this place.

In actual fact, I didn't need to do anything. I had to go out this evening so powered down. Lo and behold, upon my return I found a 'data' icon on my desktop and in the 'Places' menu.

I presume this is because this is my mount point of my second drive. I'd imagine the techniques you've all outlined above will be required if I want to create other shortcuts.

Thanks again.

Ali

---

