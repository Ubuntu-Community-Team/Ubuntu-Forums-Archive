---
title: "mounted drive"
date: 2007-03-22
forum: Absolute Beginner Talk
---

### Post by progrockusa on 2007-03-22
Ok heres the deal.
When i setup the partition for installing ubuntu i made one partition /Hda1/media
now it shows on the desktop as hda1 at 12.8 gigs.
This is fine and everything except i can't create folders or add files to it.
It only gives me the option to unmount. 
Inside this partition is a folder called lost&found.
Now all i want to beable to do is make folders in it so i can store music and movies.

---

### Post by Bachstelze on 2007-03-22
What filesystem is the partition formatted with ?

---

### Post by progrockusa on 2007-03-22
ext3

---

### Post by taurus on 2007-03-22
Assuming your login name is **john** and that partition is _/dev/hda1_ and mounted to _/media/hda1_, run

```
sudo chown -R **john**:**john** /media/hda1
ls -la /media
```

p.s.  You **_[COLOR="Red"]should not[/COLOR]_** change permissions of your / or things will break.

---

### Post by Nekiruhs on 2007-03-22
I had the same problem, the problem exists between the chair and keyboard.  You are looking at the root folder, try going to the home folder and then the folder with your username, thats where you make folders and files.:lolflag:

---

### Post by yabbadabbadont on 2007-03-22
Open a terminal window and then use sudo to create a new directory on that drive.  Then use sudo to change the owner, group, and permissions so that your user owns it.  From then on, you can do whatever you like inside that directory.
```
cd /media/hda1
sudo mkdir MyDir
sudo chown myuser:myuser MyDir

```

Edit: Apparently I type way too slowly...  :lol:

---

### Post by progrockusa on 2007-03-22
> **yabbadabbadont said:**
> Open a terminal window and then use sudo to create a new directory on that drive.  Then use sudo to change the owner, group, and permissions so that your user owns it.  From then on, you can do whatever you like inside that directory.
```
cd /media/hda1
sudo mkdir MyDir
sudo chown myuser:myuser MyDir

```

Edit: Apparently I type way too slowly...  :lol:

that did the trick tyvm

---

