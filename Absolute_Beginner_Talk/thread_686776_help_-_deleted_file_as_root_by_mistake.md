---
title: "help - deleted file as root by mistake"
date: 2008-02-03
forum: Absolute Beginner Talk
---

### Post by garyed on 2008-02-03
Well I did the inexcuseable experimenting as root in Nautilus & deleted a file & maybe more.
My mouse pad on my laptop has been actIing unpredictable & browsing some files in Nautilus
I accidentally moved or deleted at least a hidden file.
The owner & group was root. When I checked in trash  I didn't find it there.
I do know the name but it doesn't show up on locate after  sudo -u locate to update the data base.
Any ideas

---

### Post by forestpixie on 2008-02-03
check root's trash and make sure you enable view hidden files

---

### Post by garyed on 2008-02-03
> **forestpixie said:**
> check root's trash and make sure you enable view hidden files

How do I do that ?
All I know to do is click on the trash icon in Nautilus

---

### Post by wolfen69 on 2008-02-03
h

---

### Post by taurus on 2008-02-03
Applications -> Accessories -> Terminal
```
sudo ls -la /root/.Trash
```
Since you said you know the name of that file, what is it anyway?

---

### Post by wolfen69 on 2008-02-03
```
sudo nautilus
```
go to root folder
view>show hidden files
look for .trash folder

---

### Post by dhysk on 2008-02-03
ctr+H or go to view and click on show hidden files

---

### Post by floke on 2008-02-03
> **wolfen69 said:**
> ```
sudo nautilus
```
go to root folder
view>show hidden files
look for .trash folder

gksu nautilus - not sudo!

---

### Post by garyed on 2008-02-03
Thanks to everybody!!

It worked both ways.
I didn't realize but I deleted 9 files that I wanted to keep & didn't realize it until I saw them.
The one file I knew was full of personal info that I didn't want just anyone who used the computer to be able to be able to read or write to. I decided I would change the owner to root
& hide it. Then I was experimenting with how I could hide it in Nautilus but I couldn't find a way.
Is there a way that only root could view a hidden directory or file in Nautilus & no other user?

---

