---
title: "[SOLVED] Can't delete a folder. Plz help!"
date: 2008-01-09
forum: Absolute Beginner Talk
---

### Post by Kosimo on 2008-01-09
Hello.
I've got a folder on my external drive, and I can't delete it:

When in terminal this is the message I get:

> laptop:/media/Dades$ sudo rm -R .Trash-root
rm: cannot remove `.Trash-root/.Trash-cosimo/SNES ROMs/Roms Super Nintendo/Castlevania - Dracula X (U).smc': No such file or directory
rm: cannot remove `.Trash-root/.Trash-cosimo/SNES ROMs/Roms Super Nintendo/FIFA International Soccer (U).smc': No such file or directory
rm: cannot remove `.Trash-root/.Trash-cosimo/SNES ROMs/Roms Super Nintendo/Kid Klown in Crazy Chase (E).smc': No such file or directory
rm: cannot remove `.Trash-root/.Trash-cosimo/SNES ROMs/Roms Super Nintendo/Madden NFL Football (U).smc': No such file or directory
rm: cannot remove `.Trash-root/.Trash-cosimo/SNES ROMs/Roms Super Nintendo/Magical Quest Starring Mickey Mouse': No such file or directory


I tried being sudo, in terminal, in nautilus with root privileges... No chance at all.

How can I force my system to delete this folder?

Thank you

---

### Post by OffAxis on 2008-01-09
-f is the force option for rm.
so...
```
sudo rm -rf .Trash-root
```

---

### Post by argraff on 2008-01-09
I'm not entirely sure, but I think the problem might be that you can't delete .Trash-root. Try going one folder in?

---

### Post by Kosimo on 2008-01-09
Still getting the same problem
> 
laptop:/media/Dades$ sudo rm -rf .Trash-root
rm: cannot remove directory `.Trash-root/.Trash-cosimo/SNES ROMs/Roms Super Nintendo': File exists


---

### Post by argraff on 2008-01-09
Did it delete all of the other ones?

---

### Post by austin.lund on 2008-01-09
Could the spaces be confusing things???  I doubt it.

What does "ls '.Trash-root/.Trash-cosimo/SNES ROMs/Roms Super Nintendo'" give?

Try removing the files individually first to see why -r isn't working.

Also try adding a -v to rm and see if it gives any more info.

OH... Also, what type of filesystem is it?  Try "df -T".

---

### Post by Kosimo on 2008-01-09
Thank you all for answering. I found an easiest solution...

Went into windows. Select the folder and delete it.

(I had to change the permissions, was read only)



How damn I couldn't do that in Ubuntu? It took me 3 seconds to delete it in win...

Anyway, I'm back on Gutsy and this damn folder is not there anymore.

---

### Post by austin.lund on 2008-01-09
Permissions hey.  

I seem to remember that you can deny the superuser the ability to unlink a file if you remove all permissions.  Perhaps somehow that is what happened to your files.  

Pity you got rid of them ;).  It would be interesting to see what ls -l would have given.  I have a feeling the permissions would have been the problem.

---

### Post by eolson on 2008-01-09
You had spaces in the file name.   When that happens you either need to put quotes around the whold file name or delimit each space with a backslaeh.

---

### Post by Kosimo on 2008-01-09
> **austin.lund said:**
> Permissions hey.  

I seem to remember that you can deny the superuser the ability to unlink a file if you remove all permissions.  Perhaps somehow that is what happened to your files.  

Pity you got rid of them ;).  It would be interesting to see what ls -l would have given.  I have a feeling the permissions would have been the problem.

I had a problem while copying folders from another ubuntu machine to the external drive. So I stopped the operation. Once in my pc I had the problem described before.

Once in windows I realize that that folder was read only. Uncheck the box and I did deleted it.

Easy.

Anyway, now is solved. :lolflag:

---

### Post by Kosimo on 2008-01-09
> **eolson said:**
> You had spaces in the file name.   When that happens you either need to put quotes around the whold file name or delimit each space with a backslaeh.

I hope to get the point to select a folder and delete it.

---

### Post by austin.lund on 2008-01-09
Just for reference, if anyone comes across this... my solution would have been to do:

chmod -R u+rw .Trash-root

Then try the rm command.

---

