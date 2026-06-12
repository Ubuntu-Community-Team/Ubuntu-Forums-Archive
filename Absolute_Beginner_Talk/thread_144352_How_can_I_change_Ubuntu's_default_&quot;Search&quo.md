---
title: "How can I change Ubuntu's default &quot;Search&quot; Folder from the Terminal or with Script?"
date: 2006-03-14
forum: Absolute Beginner Talk
---

### Post by dvarsam on 2006-03-14
Hello all !!!

Very often, I search for files inside my Ubuntu...

From the Menu, I select "Places\Search for Files...".

In the choice named "Look in folder:",  I would like to change the DEFAULT from the "Home" folder to some other path to a FAT32 Partition.

Because the path is long, I do NOT like typing it EACH & EVERY time...


1. What is the command to do this from the Terminal?
    (I believe it is probably some .txt file I need to edit)

2. At the same time, what happens if the FAT32 is not "mounted"?
    Can I make an "IF" statement & how would I go about that?
    Example:

    if [ Hard Drive hdc = Mounted ]; then

    Set "Look in folder:" = "\mnt\fat32_Partition\My Backup\"

    else

    Set "Look in folder:" = "\Home"

    fi

Thanks.

---

### Post by Pragmatist on 2006-03-14
Ok, here is what I've discovered. ```
gnome-search-tool
``` is the program that is fired. You can read more with ```
man gnome-search-tool
``` From the man page I read you can type this (I tried it and it works):
```
gnome-search-tool --path=/home/username/blah1/blah2/blah3
``` and it will open beginning with, in this case, blah3 :)

So, all you need to do, is find out how to edit the command used when you select search from a menu (I think you can use the menu editor, ```
smeg
``` to do this

---

