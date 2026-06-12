---
title: "How to make gedit or any editor programm work in FileZilla?"
date: 2008-03-24
forum: Absolute Beginner Talk
---

### Post by yngens on 2008-03-24
Hi to all,

I have already posted this here: [http://ubuntuforums.org/showpost.php?p=4575103&postcount=50](http://ubuntuforums.org/showpost.php?p=4575103&postcount=50) But then I thought it will have better chances to catch your attention if I start a new thread, bkz it is about specific problem.

I am on Hardy now and using FileZilla 3.0.7.1. This version has an option to make associations for editor programm, but unfortunately I could not make it work. Pointing to '/usr/bin/gedit' did not help. And it requires putting path to programm, it does not accept a command.

I would appreciate if anyone could advice how to make editor programm work. I am tired of switching between two windows all the time - FileZilla and Browser - to edit my files.

---

### Post by Oldsoldier2003 on 2008-03-25
> **yngens said:**
> Hi to all,

I have already posted this here: [http://ubuntuforums.org/showpost.php?p=4575103&postcount=50](http://ubuntuforums.org/showpost.php?p=4575103&postcount=50) But then I thought it will have better chances to catch your attention if I start a new thread, bkz it is about specific problem.

I am on Hardy now and using FileZilla 3.0.7.1. This version has an option to make associations for editor programm, but unfortunately I could not make it work. Pointing to '/usr/bin/gedit' did not help. And it requires putting path to programm, it does not accept a command.

I would appreciate if anyone could advice how to make editor programm work. I am tired of switching between two windows all the time - FileZilla and Browser - to edit my files.
Edit>Settings
default file editor:
```
/usr/bin/gedit
```

you can also play with some more advanced options once you get it set up

---

### Post by rowinggolfer on 2008-04-28
> **Oldsoldier2003 said:**
> Edit>Settings
default file editor:
```
/usr/bin/gedit
```



as per original poster... we've tried this, and it doesn't work for editing the LOCAL files.

It does, however, work for editing the remote files.

Sigh. Very nice, but I wish it worked on the local files too.

---

### Post by michaeel on 2008-04-28
> **rowinggolfer said:**
> as per original poster... we've tried this, and it doesn't work for editing the LOCAL files.

It does, however, work for editing the remote files.

Sigh. Very nice, but I wish it worked on the local files too.

right mouse click on the file -> open with -> #choose your editor#

---

### Post by yngens on 2008-04-29
> **michaeel said:**
> right mouse click on the file -> open with -> #choose your editor#

michaeel, if it was that easy! there is no such an option as 'file -> open with' on right click in filezilla!

---

### Post by michaeel on 2008-05-02
> **yngens said:**
> michaeel, if it was that easy! there is no such an option as 'file -> open with' on right click in filezilla!

you won't find this option in filezilla, use nautilus to right click on it.

---

### Post by yngens on 2008-05-03
> **michaeel said:**
> you won't find this option in filezilla, use nautilus to right click on it.

thank you michaeel, that i know since long. we are discussing filezilla here, not nautilus. how it would be much comfortable to have fully functional filezilla, the way it works for windows.

imho, you don't really have to tutor what is very much logical by itself here. though thank you for your attention and your time anyway.

---

### Post by chaz_winter on 2008-05-08
Actually,I'm using Hardy and I've got FileZilla editing both local & remote files using GEdit.  I use JEdit when I'm working, but for quick modifications  the FileZilla GEdit combo is pretty darned convenient.

Charles

---

### Post by yngens on 2008-05-08
> **chaz_winter said:**
> Actually,I'm using Hardy and I've got FileZilla editing both local & remote files using GEdit.  I use JEdit when I'm working, but for quick modifications  the FileZilla GEdit combo is pretty darned convenient.

Charles
I am on Hardy too and I do reconfirm that it is not possible to use GEdit to edit local files within Filezilla. No problems for remote files.

When trying to open or edit local files WITHIN Filezilla (not Nautilus) it gives this error:

The file '/home/yngens/test.php' could not be opened:
No program has been associated on your system with this file type.

Of course, edit programm associations in Filezilla are set up corrently, because they run with no problems for remote files.

---

### Post by yogo on 2008-05-08
Just a guess here but I think if you have Notepad working in Wine, you should be able to set it as an editor with it's path.

---

### Post by snagaslas on 2008-05-13
Bump, I still can't resolve this problem.

Anyone have any idea? Perhaps manually change a configfiles as it doesn't seem it saves it or is doing something wrong when calling gedit from /usr/bin/gedit.

Ty

---

### Post by snagaslas on 2008-05-14
Bump, noone found solution?

---

### Post by yngens on 2008-05-14
> **yogo said:**
> Just a guess here but I think if you have Notepad working in Wine, you should be able to set it as an editor with it's path.

yogo, why bother using windows application when you have gedit?! the problem raised here is to make Filezilla work as it should work, and not finding ways around!

i would really prefer some people attentively read the subject matter before they start to show their intelligence.

---

### Post by snagaslas on 2008-05-16
> **yngens said:**
> yogo, why bother using windows application when you have gedit?! the problem raised here is to make Filezilla work as it should work, and not finding ways around!

i would really prefer some people attentively read the subject matter before they start to show their intelligence.

Agreed, I have not found any solution so far tried almost everything :(

---

### Post by Kazimieras on 2008-06-12
Hello, I´m new here, and also had the same problem with fileZilla. 
I googled it a little more and found this answer to our problem:

[http://forums.x10hosting.com/tutorials/63337-configuring-filezilla-file-editing-ubuntu-8-04-hardy-heron.html](http://forums.x10hosting.com/tutorials/63337-configuring-filezilla-file-editing-ubuntu-8-04-hardy-heron.html)

The trick is, that you must leave a SPACE after your editing program's dir -
write:
"/usr/bin/screem " in the editing program's field (I use "screem" instead of "gedit"), and it will work. It worked for me.
Good luck.

---

### Post by odoketa on 2008-06-29
I almost wish the space trick had worked, even though I would find it slightly embarrassing that it had.

I've had this problem with filezilla under Hardy. Does anyone have anything new to report?

---

