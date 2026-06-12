---
title: "Can't remove items from .Trash!"
date: 2008-03-22
forum: Absolute Beginner Talk
---

### Post by EleFlameMax on 2008-03-22
I deleted some items, they are in my trash can, but when I try to remove them, it says that I don't have permission. So I tried to remove them via the command line, but when I try to delete an item it gives me this:

```
rm: cannot remove `swfmill-0.2.12': Is a directory
```

---

### Post by Oldsoldier2003 on 2008-03-22
> **EleFlameMax said:**
> I deleted some items, they are in my trash can, but when I try to remove them, it says that I don't have permission. So I tried to remove them via the command line, but when I try to delete an item it gives me this:

```
rm: cannot remove `swfmill-0.2.12': Is a directory
```

```
rm -r swfmill-0.2.12
``` or```
 sudo rm -r swfmill-0.2.12
``` if its not owned by you

---

### Post by poosietgp on 2008-05-17
ummmm.... i dunno but this worked for me...
ehem... 

go to terminal type... sudo nautilus (ummm... a file browser with unlimited privilege will appear...) 

then go to filesystem... then go to home... then go to your <Whatever your name is folder>... then hit ctrl+H... hidden files will appear :popcorn: then look for the .local folder... go to share folder... then go to Trash folder... ok here goes...

inside the Trash folders are 2 folders namely files and info in the files folder are your deleted files while the info folder contains information files about the files recently or you've already sent to the trash... example: allreadydeletedbutitsstillthere.info... 

now lets say allreadydeletedbutitsstillthere file is the file that wont go away. what i did was i went first to the info folder then I right-clicked allreadydeletedbutitsstillthere.info then clicked MOVE TO TRASH then i went back to the files folder... there you will see that the info file is sent to the trash... delete the info file and the actual file you want to delete and voila...:popcorn: i hope my solution helps... only took me a few seconds...:popcorn:

---

