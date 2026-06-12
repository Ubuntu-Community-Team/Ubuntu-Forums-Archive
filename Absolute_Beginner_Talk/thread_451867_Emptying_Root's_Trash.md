---
title: "Emptying Root's Trash"
date: 2007-05-22
forum: Absolute Beginner Talk
---

### Post by bodam on 2007-05-22
[FONT=Arial]So I deleted a bunch of system backups that were taking a large amount of my drive space out of /var/backup using the command 
[/FONT][FONT=Arial]gksudo nautilus

Unfortunately the space is still not registered as available so i 
suspect that it's still in Root's trash.  Any suggestions on how to clear it?[/FONT]

---

### Post by Ek0nomik on 2007-05-22
GUI

```
sudo nautilus
```

Than go into the root directory (make sure you show hidden files) and delete the .Trash-root folder.

---

### Post by wormser on 2007-05-22
> **Ek0nomik said:**
> GUI
```
sudo nautilus
```
It is [recommended]("http://www.psychocats.net/ubuntu/graphicalsudo") to use **gksudo** for gui applications.

---

### Post by Ek0nomik on 2007-05-22
> **wormser said:**
> It is [recommended]("http://www.psychocats.net/ubuntu/graphicalsudo") to use **gksudo** for gui applications.

splish splash I was takin' a bath.

---

### Post by bodam on 2007-05-22
Thanks Guys, you just helped me free up 84 Gigs of drive space.

I'm not exaggerating.  I had 106 free.   Now I have 190+ free.

Thanks again

Dave

---

