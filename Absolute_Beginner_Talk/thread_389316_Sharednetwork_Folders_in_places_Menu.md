---
title: "Shared/network Folders in places Menu"
date: 2007-03-20
forum: Absolute Beginner Talk
---

### Post by ProjectWhat on 2007-03-20
How would I make a network folder from here:
```
smb://vmware/Windows_Shared
```
show up in my places folder callled Windows Shared?

--

And how would I make a shared folder from here:
```
/media/samba
```
show up in the places menu as Ubuntu Shared?

I hope this all make sense. I found the menu manager but it only allows me to change the applications and the system menu.

---

### Post by dannyboy79 on 2007-03-20
If you want folders to show up in the places menu, you need to first go into Nautilus(the file manager), and navigate to the folder that contains the folder you want in the places menu.
For example, if I wanted /home/tbodine/this/folder to be in the places menu, I would go to /home/tbodine/this
Now click and drag the folder that you want in the places menu, over to the left side (where it should say Home, Desktop, Filesystem, etc.
Then your folders should appear in the places menu automagically. i think they'll show up as the name of the folder though but not sure as I don't do it. good luck

---

### Post by steve101101 on 2007-03-20
here is a guide for just that 

[http://www.ubuntuforums.org/showthread.php?t=255872&highlight=mounting+smbfs+shares](http://www.ubuntuforums.org/showthread.php?t=255872&highlight=mounting+smbfs+shares)

---

