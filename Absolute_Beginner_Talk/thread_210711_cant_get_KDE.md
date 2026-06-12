---
title: "cant get KDE"
date: 2006-07-07
forum: Absolute Beginner Talk
---

### Post by mit on 2006-07-07
using the following command in the terminal i am trying to get the KDE desktop so i can swop between Gnome and KDE but get the following result;


sudo aptitude install kubuntu-desktop

Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
Couldn't find any package whose name or description matched "kubuntu-desktop"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.

thanks mit :)

---

### Post by FredB on 2006-07-07
erh...

I tried and it works for me.

Did you try updating your repository info, using something like sudo aptitude update ?

And what happens if you try sudo apt-get install kubuntu-desktop ?

---

### Post by ovimunt on 2006-07-07
Hi,

You may want to have a look here [http://www.ubuntuforums.org/showthread.php?t=185758](http://www.ubuntuforums.org/showthread.php?t=185758) for additional repositories.

---

### Post by T700 on 2006-07-07
Before doing the install: ```
 sudo aptitude update
```

Paul

---

### Post by mit on 2006-07-07
Hi,

Yeah, the update was required first.  When it has finished downloading the KDE GUI will it give me the option when logging on to select which GUI?

Thanks

Mit

---

### Post by T700 on 2006-07-07
When you come to the log in window, look at the lower left of the screen.  There you can select the one you want.  

Paul

---

### Post by mit on 2006-07-07
Paul,

Thanks. I look forward to being able to choose between them. :KS 

mit

---

### Post by james016 on 2006-07-07
How do you upgrade from 3.5.2 to 3.5.3? Or does it automatically install KDE 3.5.3?

---

### Post by FredB on 2006-07-07
For upgrading to 3.5.3 :

[http://www.kubuntu.org/announcements/kde-353.php]("http://kubuntu.org/announcements/kde-353.php")

Just adding a repository, a key, and a little update :)

---

### Post by mit on 2006-07-07
Got KDE, but i think I prefer Gnome, so will stick with that! 

Just out of curiousuty, when the system starts, it says booting the Kernel Ubuntu 6.06 ..... but the log on GUI shows Kubuntu.

I love the fact you can choose either. Top job :KS 

Mit

---

### Post by james016 on 2006-07-07
> **FredB said:**
> For upgrading to 3.5.3 :

[http://www.kubuntu.org/announcements/kde-353.php]("http://kubuntu.org/announcements/kde-353.php")

Just adding a repository, a key, and a little update :)

Another question: After adding the repository and the key and running aptitude -update, how do I do the actual update of KDE? Is it something along the lines of: 
```
sudo aptitude -update kubuntu-desktop
```


Thanks

---

### Post by james016 on 2006-07-07
After a bit of digging around the net, I now have KDE 3.5.3 installed as well as Gnome :D

---

