---
title: "E M E R G E N C Y!  Can't get to a desktop"
date: 2006-11-24
forum: Absolute Beginner Talk
---

### Post by gjtoth on 2006-11-24
After I tried to edit my xorg.conf file to get direct rendering to work, I can't get into the desktop.  I am dumped at the login in console.  I know what I have to remove.  I know the file name and location.  How do I get to it from the command prompt?  (can you tell I'm a recovering Windoze user?) ;)

---

### Post by taurus on 2006-11-24
```
sudo nano -w /etc/X11/xorg.conf
```

---

### Post by gjtoth on 2006-11-24
> **taurus said:**
> ```
sudo nano -w /etc/X11/xorg.conf
```

If this works, I'll buy ya a beer!

---

### Post by junglepeanut on 2006-11-24
If for some reason yo removed nano use vim.

I dont need a beer.

---

### Post by gjtoth on 2006-11-24
Nano worked... I'm up and running.... WHEW! You can bet I won't be doing THAT anytime in the near future (or distant future, for that matter!) ](*,) 

Thanks for a FAST response.  Guess I'll have to make another donation heheheh :mrgreen:

---

### Post by taurus on 2006-11-24
> **gjtoth said:**
> Nano worked... I'm up and running.... WHEW! You can bet I won't be doing THAT anytime in the near future (or distant future, for that matter!) ](*,) 

Glad to hear you are up and running again.  

> Thanks for a FAST response.  Guess I'll have to make another donation heheheh :mrgreen:

Actually, I do need a new 19" LCD to replace my old Dell 17" CRT!  :D

---

