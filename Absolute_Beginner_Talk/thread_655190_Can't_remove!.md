---
title: "Can't remove!"
date: 2008-01-01
forum: Absolute Beginner Talk
---

### Post by Strasher on 2008-01-01
Happy new years everyone!
Well on to the problem, OK my problem is that I installed the reconstrutor  program. i uninstalled the program via sudo apt-get remove but the files that it created are still there!
They are taking up a gig of space so i really want them gone! I've tried to drag them into the trash but i get this ```
Cannot move "home/aver...onstructor to the trash because you do not have permissions to change it or its parent folder
``` but i used the user editor and changed my account to root.
how to I get rid of this?
Cheers!
-Strasher :popcorn:

---

### Post by RomeReactor on 2008-01-01
Hi. Where in your home folder are these remaining files located? you can use the rm command as root--using sudo--to remove the files; if I had a folder named **remaining** on my home folder (and my user name is **romereactor**), to remove it **and** the files inside:
```
sudo rm -R /home/romereactor/remaining
```

Please note that you must be very careful using the rm command, as you can easily render your system unusable by removing system libraries by accident.

Another way would be to open Nautilus as root so you can delete the files visually:
```
gksudo nautilus /home/USERNAME
```
substitute USERNAME for your username, so Nautilus opens in your home folder and not in Root's; you should be able to navigate to the directory you want to remove and do so. Again, be careful not to delete anything else while Nautilus is open with administrator privileges, and close it as soon as you finish.

---

### Post by Strasher on 2008-01-01
Thanks!
-Strasher :popcorn:

---

