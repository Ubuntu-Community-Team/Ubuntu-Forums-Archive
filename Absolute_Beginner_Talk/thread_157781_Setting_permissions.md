---
title: "Setting permissions"
date: 2006-04-09
forum: Absolute Beginner Talk
---

### Post by EBAR on 2006-04-09
Hello, I've done some searching regarding permission in linux and it appears to be  confused by new people like myself often.

I've been wondering how to change my permissions for folders and file in the GUI.

I have a folder that houses my pictures. Inside the folder the pictures are set so that I can view them, but I cannot write to them. I changed the folder permissions by right click-->Properties-->Permissions.

But all the pictures inside the folder are still set to 555. Is there a way to change them all at once instead of having to go through and change all 89 of them?

Thanks in advance for the help.

EBAR

---

### Post by aysiu on 2006-04-09
I think KDE has recursive GUI permissions, but I don't believe Gnome does yet.

It's not that difficult to do by command-line, though. ```
sudo chmod -R 755 /pictures
```

---

### Post by EBAR on 2006-04-10
Cool, I'll just do it through the command line then. Thanks a lot for the help!

---

