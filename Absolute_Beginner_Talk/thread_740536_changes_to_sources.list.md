---
title: "changes to sources.list"
date: 2008-03-30
forum: Absolute Beginner Talk
---

### Post by mikeymouse on 2008-03-30
I need to add a new repository to the sources.list.
 Could anyone explain how to do this, when i add the line i want added to the sources.list I cannot save it.
 How do i save a change to the sources.list..
 All help will be gratefully excepted..
 I really no little about sudo  and how to enter the information to save the file
thanks 
 mikeymouse

---

### Post by scragar on 2008-03-30
I'd recomend backing it up first:
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
```
then launch using gksudo:
```
gksudo gedit /etc/apt/sources.list
```
when your done update the list:
```
sudo apt-get update
```

---

### Post by Tatty on 2008-03-30
the sources.list file is owned by root, so you will need to give yourself superuser privilages to edit it.  to do this you need to open it using the sudo command (or gksudo for a graphical text editor)

this should work:

```
gksudo gedit /etc/apt/sources.list
```

---

### Post by mikeymouse on 2008-03-31
Thanks all for the help it worked just fine.
 I now have the remastersys program in my ubuntu .
 If your interested in the remastersys program you can add the address at:
 [www.remastersys.klikit-linux.com](www.remastersys.klikit-linux.com)

---

