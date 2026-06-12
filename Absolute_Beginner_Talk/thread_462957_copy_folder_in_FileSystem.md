---
title: "copy folder in FileSystem"
date: 2007-06-03
forum: Absolute Beginner Talk
---

### Post by strutz323 on 2007-06-03
hello

i want to copy a folder in the FileSystem...i tried "cp" but it copies only files and there are many files and subfolders that i want to copy...

how can i do that?...how can i log on as root?

thanks...

---

### Post by whizbaby on 2007-06-03
First, you DONT login as root. Use 'sudo' instead (sudo <command-to-be-executed-by-root>, e,g, sudo mount /foo)
Next, cp has a nice option called -r (recursive) that copies dirs and subdirs too
cp -r /myfolder /yourfolder
copies /myfolder and its contents into /yourfolder and you end up with
/yourfolder/myfolder/...
Try man cp for a complete list of options (resp. man sudo).
(of curse u can combine cp and sudo, e.g. sudo cp -r /etc /foo)

---

### Post by BaffledMollusc on 2007-06-03
> **whizbaby said:**
> First, you DONT login as root. Use 'sudo' instead (sudo <command-to-be-executed-by-root>, e,g, sudo mount /foo)
Next, cp has a nice option called -r (recursive) that copies dirs and subdirs too
cp -r /myfolder /yourfolder
copies /myfolder and its contents into /yourfolder and you end up with
/yourfolder/myfolder/...
Try man cp for a complete list of options (resp. man sudo).
(of curse u can combine cp and sudo, e.g. sudo cp -r /etc /foo)
Yes, that will work. 

But you don't have to use the command line. Why not just use a file manager like Nautilus? I.e. Choose Places->Home Folder from the top menu, and go from there. That way you can just right click and choose copy, and the entire directory and everything under it will be copied.

---

### Post by vanadium on 2007-06-03
You should probably wait copying files in the fileystem until you are more proficient with Linux. With root privileges, you can create great havoc in your system. At first, limit yourself at just exploring the system as a normal user. Learn a bit about the system and how to customize your own account. Only a more experienced user should be copying with root privileges outside of his home folder.

---

### Post by whizbaby on 2007-06-03
> **BaffledMollusc said:**
>  Why not just use a file manager like Nautilus? 
Because it suXX when you really have to manage files. Console is much more powerful than a bunch of drag and drop thingys. So its better to learn console approach from beginning on. Thats, of course, only my opinion.

---

### Post by BaffledMollusc on 2007-06-03
> **whizbaby said:**
> Because it suXX when you really have to manage files. Console is much more powerful than a bunch of drag and drop thingys. So its better to learn console approach from beginning on. Thats, of course, only my opinion.

It is more powerful if you want to do involved stuff like copying all files whose second letter is x and which were created on a Wednesday, but I find a GUI useful for normal stuff. Certainly when I have deep and involved directory structures I find a GUI tree view more helpful than using the command line. 

Just my personal preferences, of course.

---

