---
title: "Disappearing trash still taking disk space"
date: 2006-10-25
forum: Absolute Beginner Talk
---

### Post by TooRight on 2006-10-25
I've been cleaning out some files to clear myself some harddrive space and was right clicking and sending them to Trash, or so I thought. I just realized that my trashcan icon still shows as empty, and upon checking it, it's empty... nor is there anything in the .Trash folder.... I didn't empty the trashcan, and the space those files cleared still isn't showing up. Does anyone have a clue what's going on? lol


***** Solved... since I was in Nautilus when i was doing it, the files went to the Root/.Trash folder instead... ooops :D

---

### Post by suRoot on 2006-10-25
I'm not sure what's up with your trashcan, but you could always try finding large files & removing them by hand:

```
find / -type f -size +20000k -exec ls -lh {} \; | awk '{ print $8 ": " $5 }'
```

Which should find anything larger than 20MB... delete what you wish (so long as you know aren't going to trash your system by deleting it) by typing

```
rm -rf /path/to/big-file
```

---

### Post by TooRight on 2006-10-25
Ooohhh, greatt tip!! *adding it to my terminal "quickies" file :D

I sooooooooooooooo love that commandline!! 

Thanks!!

---

### Post by CatKiller on 2006-10-26
> **TooRight said:**
> ***** Solved... since I was in Nautilus when i was doing it, the files went to the Root/.Trash folder instead... ooops :D

Actually, that's because you were in Nautilus **as root**. You shouldn't do that any more than you absolutely have to. Be careful out there.

---

### Post by caffienda on 2007-03-01
> **suRoot said:**
> I'm not sure what's up with your trashcan, but you could always try finding large files & removing them by hand:

```
find / -type f -size +20000k -exec ls -lh {} \; | awk '{ print $8 ": " $5 }'
```

Which should find anything larger than 20MB... delete what you wish (so long as you know aren't going to trash your system by deleting it) by typing

```
rm -rf /path/to/big-file
```


Is there a way to do this with a specific folder?  Let's say just the /home/ directory.
What about for a specific device?  I am having a space issue with /dev/sda1  that is very suspicious.  I'd like to see where the space is being allocated.

THANKS!

---

