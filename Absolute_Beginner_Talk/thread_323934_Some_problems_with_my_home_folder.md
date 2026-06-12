---
title: "Some problems with my home folder"
date: 2006-12-23
forum: Absolute Beginner Talk
---

### Post by Jcarr_toonist on 2006-12-23
I was trying to install a second hard drive on my system and I wanted the mount point to be in my home folder. In the mess that ensued I ended up changing the permissions on my home folder. Now whenever I log into X i get an error message that says my .drmc file is being ignored because it has the wrong permissions on it. It wants 644 and I have 777 on my entire home folder(not sure what I am supposed to have). 

If I put 644 permissions on the .drmc files it doesn't change anything and when I put 644 on the home folder i can't get in. 

doesn't anyone know how to fix this?

---

### Post by jimbren on 2006-12-23
open a terminal and in your home folder, enter this command:
```
sudo chown -R yourusername:yourgroupname *.*
```

That should fix you up.


jimbo

---

