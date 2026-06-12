---
title: "[SOLVED] Where does root's trash go?"
date: 2008-03-10
forum: Absolute Beginner Talk
---

### Post by sayakb on 2008-03-10
I was creating some icons using Gimp, and writing the pngs inside the /usr/share/icons folder with Nautilus opened as root. But I often deleted many files by just pressing delete the Del button, so ofcourse, they moved to trash. But I never found my trashcan full. Also, I am certain that they move to some sort of .trash folder since as soon as I delete some png file, it is renamed to "harddrive.png (3rd Copy)" or something.. so that means I have around 220-250MB of my space occupied by the extensive amount of pngs I deleted? Plus, I found no .Trash anywhere in the /usr/share/icons folder or its parent directories.. How do I find and delete them?
Any help would be appreciated.

---

### Post by taurus on 2008-03-10
Maybe in /root/.Trash!

```
sudo ls -la /root/.Trash
```

---

### Post by Dr Small on 2008-03-10
The Trash goes to the .Trash folder of whoever you are logged in as, thus as root, it would go to /root/.Trash

Dr Small

---

### Post by sayakb on 2008-03-10
Yes yes.. I found it.. how stupid of me..
Thank you both..
:D

---

### Post by sayakb on 2008-03-10
Wow.. thanks a LOT...
There was 3.2GB of data in there.. :D

---

### Post by Oldsoldier2003 on 2008-03-10
> **LinuxIsInnovation said:**
> Wow.. thanks a LOT...
There was 3.2GB of data in there.. :D

which says a lot for using the command line as opposed to the gui....

---

