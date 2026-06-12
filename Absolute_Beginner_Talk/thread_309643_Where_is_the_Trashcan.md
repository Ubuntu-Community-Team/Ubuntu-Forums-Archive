---
title: "Where is the Trashcan?"
date: 2006-11-29
forum: Absolute Beginner Talk
---

### Post by Buck2348 on 2006-11-29
I deleted two folders in the GUI (right-click, Move to Trash) but when I looked into the trash they were not there.  The folders in question were on a Windows (NTFS) partition.  Is there more than one file for Trash, and where in the file system is it (or they) located?  Properties for Trash on the Desktop just gives its location as "On the Desktop" but /home/username/Desktop does not show it.  Thanks.

Buck

---

### Post by coder_ on 2006-11-29
The location for the Trash can is:  ~/.Trash     (Just in case you didn't know, '~' is your home directory.  Better to be safe and state it than sorry.)

I'm not sure if that's what you are looking for though.

---

### Post by CatKiller on 2006-11-29
You'll have a ~/.Trash folder, and on each other partition you'll have a .Trash-*username* folder. These contain the files deleted by a particular user. The wastebasket window should aggregate all the files deleted by that user, but hidden files will still be hidden.

Also, if you deleted files as root, it's probably worth knowing that /root is root's Home folder rather than /home/root, so files deleted as root may end up in /root/.Trash.

---

### Post by Buck2348 on 2006-11-30
Exactly what I wanted to know.  Thanks so much.  If you look at this thread again maybe you could answer another one.  Either my browser or the Forum system seem not to be working right for me.  The three little icons at the bottom right of a post all lead me to a full quoted reply, and there is no tooltip on them.  Also none of the formatting buttons at the top of the box into which I'm typing have any effect.  Is it me, by browser, or the Forum?

Thanks again for the info--it's great to be able to ask a question and have it answered correctly and quickly.

Buck

---

### Post by CatKiller on 2006-11-30
They're working fine for me, so I don't think it's the forum. I'd guess it's some browser/configuration thing that's not doing PHP properly, but the only thing I know about PHP is that each of the buttons links to the same PHP script :)

---

### Post by speeddemon8803 on 2006-11-30
my brotha its in the gray area in the bottom of your screen..i believe on the left side..but i am positive its on the bottom...these other guys are makin ya go to a wild goose chase that you dont need to go to :) *looks at their bean counts* yikes lol...anyways hope mine helps more than hurts...and btw im tryin not to confuse ya :)

---

### Post by aijazbaig1 on 2007-03-17
hello.

I had removed my trashcan from the panel by mistake so i added it again by using a add to panel shortcut (right click on panel and then add to panel).

However, now the trashcan is actually in the panel. i mean earlier it used to be sitting in the right most corner of the panel. thus how it is blocking the available space used for multiple window minimizations.

Additionally do u also know the exact location of the folder trash.
I tried to do a cd to trash from my home folder like 
```
 cd .trash
```
but it said that there is no such file/directory. i was in my default directory then. by default i mean /home/aijaz/ which is my default working directory.

Hope to hear from u,

Aijaz.

---

### Post by AtrejuT on 2007-03-17
the folder you want is .Trash where the capital T is important.
You should be able to click on the icon in the panel, selct 'move' and move it to where you want it.

atreju

---

### Post by aijazbaig1 on 2007-03-19
Yeah.
I finally managed to get the trash can on my bottom panel. However it isnt in the original place this time. It is somewhere in the middle of the panel instead of the righmost corner where it is supposed to be.

Now the available space on the bottom panel for minimized windows has decreased.

Does any one know how to align the icon to be placed on the righmost corner next to the workspace-selection gray boxes. 

Hope to hear from u,

Aijaz.

---

### Post by entangled on 2007-03-26
I've just done this too and had the problem of trashcan being in the taskbar.
You can right click and move the trash icon but it seems to stop against the workspace boxes. I found that the workspace boxes also move (using right click menu) and you can drag them to the left, making room for the trash icon to the far right (you can then drag it there). Just play with moving any objects on the taskbar to see how it works.

---

