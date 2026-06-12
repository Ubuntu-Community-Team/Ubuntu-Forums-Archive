---
title: "path to trash"
date: 2007-12-17
forum: Absolute Beginner Talk
---

### Post by fmbugdadi on 2007-12-17
Can anyone tell me what the exact path to the recycle bin is so I can navigate to it from terminal?

---

### Post by diatribe on 2007-12-17
its one of the hidden folders in your home directory, use ls -a to see them; alternatively if you right click an object in the trash and check its properties it should tell you its path

---

### Post by FuturePilot on 2007-12-17
It should be /home/<USER>/.Trash

---

### Post by aysiu on 2007-12-17
```
cd ~/.Trash
``` will take you there.

---

### Post by Junglizer on 2007-12-17
trash is lame, I prefer the black void of nothingness located @ /dev/null

---

### Post by jken146 on 2007-12-17
Can anyone tell me where the trash is in Xubuntu?  There is no /home/<user>/.Trash and after some poking I can't find it.

---

### Post by Aseld on 2007-12-17
It won't be there if you haven't deleted anything.

---

### Post by FuturePilot on 2007-12-17
> **jken146 said:**
> Can anyone tell me where the trash is in Xubuntu?  There is no /home/<user>/.Trash and after some poking I can't find it.

It should be in the same place. Be sure to replace <USER> with your user name.
You can also open Thunar and make the hidden files visible. You should see it in your home folder.

---

### Post by jken146 on 2007-12-17
I have deleted many things.  In Thunar it says the path is **trash:///**

---

### Post by jken146 on 2007-12-18
I still can't find the absolute path. grrr!

---

### Post by aysiu on 2007-12-18
> **jken146 said:**
> I still can't find the absolute path. grrr!
Try /home/*username*/.local/share/Trash/files

---

### Post by FuturePilot on 2007-12-18
> **jken146 said:**
> I still can't find the absolute path. grrr!

Hmm. I just checked my Xubuntu machine and apparently Thunar (or XFCE not sure which is responsible here) puts the trash somewhere else as there seems to be no .Trash folder for me either. Now the question is  where does it put the Trash?:-k

Edit: aysiu answered it. :)

---

### Post by jken146 on 2007-12-18
> **aysiu said:**
> Try /home/*username*/.local/share/Trash/files

Thank you very much aysiu!

I just discovered the info directory and the restore function that the trash has in xubuntu.  Nice.

---

### Post by stchman on 2007-12-18
Doing a

```
cd ~
```

will get you to your home directory.

---

### Post by CloudedLens on 2008-06-20
The trouble is that the .Trash folder has been moved. It is no longer in $HOME/.Trash
Try this: cd $HOME/.local/share/Trash
Note that you can also navigate to that folder manually, if you so desired.

EIDT: I just realized that I had only read one page of this thread. Whoopsie?

---

### Post by duxducis on 2008-07-12
Try /home/positron/.local/share/Trash/files it works with Ubuntu 8.04

---

