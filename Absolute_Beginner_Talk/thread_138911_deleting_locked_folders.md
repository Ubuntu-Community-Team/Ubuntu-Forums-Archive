---
title: "deleting locked folders"
date: 2006-03-02
forum: Absolute Beginner Talk
---

### Post by inovermyheadd on 2006-03-02
I want to delete a folder, but it won't allow me to put it in the trash b/c I don't have root permission.

I tried to go into the terminal and type
rmdir *name of folder*  but I guess b/c I have stuff inside the folder it won't let me delete it.

Is there a way to delete an entire folder in the terminal?

---

### Post by andrewsawyer on 2006-03-02
sudo rm -R *name of folder*

Should do it.  Be careful though - there may very well be a reason this is set as a root folder.  Can I ask what it is your are trying to delete?  Which directory?

---

### Post by inovermyheadd on 2006-03-02
I was trying to install daimonin and I unzipped it to my Desktop and it locked it there for some reason

---

### Post by andrewsawyer on 2006-03-02
Hmmm... shouldn't be locked.  Unless you unzipped it through terminal and were using sudo to do it.  Anyway, that post from before should do it for you.

---

