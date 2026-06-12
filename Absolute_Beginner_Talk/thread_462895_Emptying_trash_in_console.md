---
title: "Emptying trash in console?"
date: 2007-06-03
forum: Absolute Beginner Talk
---

### Post by Boris-- on 2007-06-03
I accidentally deleted my  trash icon and now I don't know how to empty it ;) Any ideas?

---

### Post by shearn89 on 2007-06-03
You can create a new link to the trash can by creating a launcher on the desktop, making it into a link to a URL and putting "trash:/" (i think) then i assume you can just drag it down to where it was before? This may not work, but i can't test it as I broke my install....

---

### Post by BaffledMollusc on 2007-06-03
> **Boris-- said:**
> I accidentally deleted my  trash icon and now I don't know how to empty it ;) Any ideas?
You could right click on the bottom panel, choose "Add to Panel", and then choose "Garbage Bin". That will get your trash icon back.

---

### Post by strider1551 on 2007-06-03
From the command line:
```
rm -rfv ~/.Trash/*
```
To explain the option, "-r" will remove directories in the trash, "-f" will prevent it from yelling at you if nothing is in the trash, and "-v" will list all the files removed.

If you mean the trash icon on the panel, you can just right click on the panel, click "add to panel", and find the trash icon.

---

### Post by Boris-- on 2007-06-03
Thank you very  very much :)

---

### Post by Bakerman on 2007-06-03
> **Boris-- said:**
> I accidentally deleted my  trash icon and now I don't know how to empty it ;) Any ideas?

If you want to make the trash icon appear on the desktop,

open gconf-editor, select apps > nautilus > desktop

in the right hand section, place a check mark next to 'trash_icon_visible'

it should then be placed back on your desktop.

---

### Post by thebrotherofasis on 2008-04-02
Where can I locate the Trash directory to see it from console?

The thing is that I run the rm -rfv ~/.Trash/* , but it doesn't empty my trash for I can see that it still has a file that needs administrator permissions to be removed. I want to be able to go to the physical folder and remove it with sudo.

Thank you

---

### Post by bumanie on 2008-04-02
If you can see the file you want to remove
> gksudo nautilus
Go to Places --> Computer --> File System
Then navigate to the file you want to get rid of and you will be able to remove it.

---

