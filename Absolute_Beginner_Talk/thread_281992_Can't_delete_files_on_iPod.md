---
title: "Can't delete files on iPod"
date: 2006-10-21
forum: Absolute Beginner Talk
---

### Post by tdrusk on 2006-10-21
I am running Kubuntu. When I plug in my iPod it mounts and everything, but it won't let me delete folders off of it. Like I can see the folder that says "my music" that i used to get my music onto kubuntu, but it won't let me delete them. I get the error:
Access denied to /Media/SB2/.Trash-1000/files/My Music

---

### Post by tdrusk on 2006-10-22
Okay. I think I know what the problem is. When I used Ubuntu I remember those specific folders having locks on them. So I am thinking I may have to delete them using sudo through the command line right? What would I have to type in the terminal?

---

### Post by raul_ on 2006-10-22
```
sudo rm -rf <dir>
```

Why would u want to delete folders from the iPod anyway?

---

### Post by tdrusk on 2006-10-22
> **raul_ said:**
> ```
sudo rm -rf <dir>
```

Why would u want to delete folders from the iPod anyway?

They are not the firmwares folders, just folders I used to get my music from XP to Kubuntu. It is taking up about 35 gigs and with it there I can't get all  of my music on the iPod firmware.

Thanks for the code!:-D

---

