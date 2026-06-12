---
title: "Can not delete this file 39d2.msi"
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by ahoman66 on 2007-06-28
I have a file that is in my trash bin that will not go away...
"/home/gord...r/39d2.msi" cannot be deleted because you do not have permissions to modify its parent folder.
Any help would be great.

Thanks
Allen

---

### Post by invalid on 2007-06-28
```
sudo rm -r ~/.Trash/*
```

---

### Post by ahoman66 on 2007-06-29
Sorry it has taken so long to respond. Thanks for the help but that did not work. 
This is what shows up...

rm: cannot remove `/home/ahoman66/.trash/*': No such file or directory

The file is in a wine folder. Could there be a problem with my current wine installation?

Thank you
Allen

---

### Post by glennric on 2007-06-29
> **ahoman66 said:**
> Sorry it has taken so long to respond. Thanks for the help but that did not work. 
This is what shows up...

rm: cannot remove `/home/ahoman66/.trash/*': No such file or directory

The file is in a wine folder. Could there be a problem with my current wine installation?

Thank you
Allen

Make sure you capitalize "Trash".
It should be 
```
sudo rm -r ~/.Trash/*
```

---

### Post by Rocket2DMn on 2007-06-29
I do believe .Trash has a capital T, though I'm not in front of my linux box to confirm that.  You can open Nautilus and do CTRL+H to show hidden files/folders which includes the trash.

---

