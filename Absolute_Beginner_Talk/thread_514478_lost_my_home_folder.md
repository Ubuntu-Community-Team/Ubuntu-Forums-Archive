---
title: "lost my /home folder"
date: 2007-07-31
forum: Absolute Beginner Talk
---

### Post by rutilajw on 2007-07-31
So I didn't really do anything today major with ubuntu.  The only I think that could cause this problem is that I downloaded fluxbox and logged on using it to check it out a bit.  I also messed around a bit with fluxconf and fluxmenu.  But this is what happened, none of my media is there anymore.  My /home/jacob folder now only contains Desktop.  It should have my pictures, videos, games, etc. 
Is there something I can do to go back to how it was like with wndows theres system restore.

---

### Post by kevinlyfellow on 2007-07-31
if you can remember the name of any particular file, you can
```
sudo updatedb
locate *filename*
```

I wonder what could have done that...

---

### Post by meierfra on 2007-07-31
Is your home folder on a separate partition?

---

### Post by rutilajw on 2007-07-31
huh? i typed in sudo updatedb, it did that. then i typed locate and the filename and it just didnt do anything

nope everythings on one partition

---

### Post by meierfra on 2007-07-31
Do you know how much disk space you used before this happened? And how much 
now?

---

### Post by rutilajw on 2007-07-31
yea im only using 3.6 gigs now and before i had like 1500 pictures and 5 movies. sooo i guess they are gone.  
now the question is, is there any way to go back to how my computer was before today?

actually, i have 20 gigs or so used, but i checked all of the folders and they dont add up to that much space. the only thing i can assume is that they are in lost and found, cause i cant read that folder.
how do i get the permissions to access the lost+found folder?

---

### Post by meierfra on 2007-07-31
> how do i get the permissions to access the lost+found folder?

```
sudo nautilus
```

and navigate to lost and found.

---

