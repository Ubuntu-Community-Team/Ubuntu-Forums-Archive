---
title: "quick! how do i delete files"
date: 2006-01-05
forum: Absolute Beginner Talk
---

### Post by zahidism on 2006-01-05
ok sooo...i finally got my wireless working (used module-assistant to compile) woooooo!!!!!! *does the happy dance* now i wanted to install firefox 1.5 (jeez...it seems so much more complicated than windows....everything is so automated in windows...oh well) err...i unpacked firefox to my desktop by accident, this brings about my question...how do i delete things????

---

### Post by lucidite on 2006-01-05
[QUOTE=zahidism]how do i delete things????[/QUOTE]
Are you talking about a file on your desktop?
If so, you can right-click on it & there should be a "delete" in the menu. You can press the "delete" button on your keyboard.
If you're trying to delete something else, what are you trying to do?

---

### Post by bored2k on 2006-01-05
```
rm file.gz
rm -rf folder
``` should work. I'd recommend doing ```
man rm
```

Of course, you could always use any GUI application, but they're no fun ;).

**[http://linux.about.com/od/commands/l/blcmds.htm](http://linux.about.com/od/commands/l/blcmds.htm)**

---

### Post by zahidism on 2006-01-05
well i know i can right click and delete and stuff but when i unpacked the firefox tarball i did it with xvzf and i guess it locked it? only root has access to it so i guess i'd have to go in through the terminal, i meant deleting files (or folders) from the terminal

---

### Post by bored2k on 2006-01-05
Apparently you did sudo tar xzf. You'd have to do sudo rm file.gz or just sudo nautilus ;).

---

### Post by Chipmunk on 2006-01-05
prefix the commands with sudo. 
such that you'd type ```
sudo rm ~/Desktop/filename
```

Be VERY VERY careful using rm with sudo. Especially the -rf option, (recursive without prompting). If you're in the wrong directory and delete stuff as root, (which is what sudo turns you into for that command), linux trusts you and will let you happily delete the entire filesystem.
Guess who's done that?:rolleyes:

---

### Post by steve.horsley on 2006-01-06
> **bored2k]Apparently you did sudo tar xzf. You'd have to do sudo rm file.gz or just sudo nautilus  said:**
> 

But since you have already unzipped the program, you could just move the directory to the right place:
> sudo mv firefox /opt

Then you can run it with the command:
[QUOTE]/opt/firefox/firefox

---

### Post by diggs on 2006-01-06
use automatix. great for installing programs. from what I gather, the nerds around here like typing in code and scaring off n00bs like us with all these commands ;). 

Automatix won't help for deleting files though.

[http://www.ubuntuforums.org/showthread.php?t=66563&highlight=Automatix](http://www.ubuntuforums.org/showthread.php?t=66563&highlight=Automatix)

if you want there is a way to set things up so that you can delete/edit files from boot up. let me know if you like :)

---

### Post by estel on 2006-01-06
You can give yourself powers to delete it by making it "belong" to you:
```
sudo chown -R YOURNAME foldername
```

---

