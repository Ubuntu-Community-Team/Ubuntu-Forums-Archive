---
title: "[SOLVED] file deletion"
date: 2008-02-11
forum: Absolute Beginner Talk
---

### Post by linux phreak on 2008-02-11
Hi.I am running ubuntu 7.10.I would like to know if i can delete files directly ie without moving them to .trash.I would like to delete files immediately without the creation of a hidden folder named .trash which wastes space. Thanks

---

### Post by FrozenFox on 2008-02-11
[http://maketecheasier.com/how-to-bypass-the-trash-and-delete-a-file-completely/2008/01/09](http://maketecheasier.com/how-to-bypass-the-trash-and-delete-a-file-completely/2008/01/09)

---

### Post by skymera on 2008-02-11
well try the terminal

```
 sudo rm *filename* 
```

make sure your in the right directory.

if you want to remove whole directories *be warned use wisely!!*

```
 rm -rf /*dir name* 
```

that will delete the folder and its contents, use it very carefully.

---

### Post by xc3RnbFO8P on 2008-02-11
You can use Pcman filemanager (Add/Remove , All Available Application)
Pcman > tool > open as root

---

### Post by linux phreak on 2008-02-11
Thank you all for replies.The .trash is still appearing even when preferences are changed as per the link given by frozenfox.I want that .trash to be absent.It is so annoying and a hindrance to privacy.

---

### Post by xc3RnbFO8P on 2008-02-11
Do wnt to remove trash from panel or remove ./trash in home folder

---

### Post by linux phreak on 2008-02-11
The .trash folder creation is the one to be stopped.Is it possible

---

### Post by hyper_ch on 2008-02-11
in Konqueror, when you right-click the files, then hold shift and then select delete, it will not be put into the trash bin.

---

### Post by linux phreak on 2008-02-11
But i use Gnome and Nautilus

---

### Post by Bodsda on 2008-02-11
im not sure if this will help, but open a terminal and type 

man shred        or       shred --help

or

man rm             or        rm --help

for more insight into deleting things, hope this helps

---

### Post by hyper_ch on 2008-02-11
> **linux phreak said:**
> But i use Gnome and Nautilus

there is surely a way to do that in nautilus also...

---

### Post by linux phreak on 2008-02-11
Thanks .But i am not that well versed in linux commands so can you kindly guide me?.I dont need another folder containing the same thing that i deleted that is hidden or in view.Rightnow i am having to delete the thing twice.Or can you tell me a way to put the crap into the trash directly so that i can delete all the things from one place just before shutting down the system.

---

### Post by lswest on 2008-02-11
to delete things and skipping the trash in any GUI is <shift> + <Del> works in windows, kde, gnome, etc.  Otherwise the terminal commands listed before would work too.

---

### Post by linux phreak on 2008-02-11
Thank you man.So i will press shift+del when i delete files.Thank you all.

---

### Post by lswest on 2008-02-12
no problem, always happy to help^^

---

