---
title: "Associate an extension file to an application"
date: 2008-03-30
forum: Absolute Beginner Talk
---

### Post by tirengarfio on 2008-03-30
Hi,


is possible associating an **extension** file to an application?

Regards

---

### Post by Ripfox on 2008-03-30
Well when you right click on a file with a certain KIND of extension and choose properties then the tab "open with" a certain application, it seems to associate that extension with that application.

---

### Post by tirengarfio on 2008-03-30
Thanks RIpfox, but i work a lot with files with the extension .pd that i open with an application called Puredata.

If i do what you say (associate a .pd file to puredata with the right click over the file and then "open with"), when I open a .txt fle with a double click over it, this .txt file is opened with puredata too!!!! That's the problem, because I would like to open the .txt file with the Text Editor app when i do double click over it.

Do you understand me?

---

### Post by drs305 on 2008-03-30
tirengarfio,

you could always associate the txt files to the editor of your choice using the same method as above ;)   This will work as long as the associations are looking at the extension and not the structure of the file (if a pd file is indeed a type of text file).

---

### Post by tirengarfio on 2008-03-30
Thanks drs305, but i don't understand you. Can you explain "better" ?

---

### Post by drs305 on 2008-03-30
In nautilus or your file manager, I assume you found a .pd file, right clicked, selected Properties, Open With, and told ubuntu to open this type of file with Puredata. Now find a file that ends in .txt, right click,select Properites, Open With, and tell ubuntu to open files of this type with 'text editor' or whatever program you use (such as gedit).

Note: If you don't see the program you want to open the file with listed, you can select the "Add +" button to use another program.

---

### Post by tirengarfio on 2008-03-31
> **drs305 said:**
> In nautilus or your file manager, I assume you found a .pd file, right clicked, selected Properties, Open With, and told ubuntu to open this type of file with Puredata. Now find a file that ends in .txt, right click,select Properites, Open With, and tell ubuntu to open files of this type with 'text editor' or whatever program you use (such as gedit).


After doing what you say, when I will try to do double click over a .pd file, Gedit will open it.

My problem I think is Puredata files are also text files...

---

### Post by drs305 on 2008-03-31
I didn't think that when you linked a file association in ubuntu that the system actually looked at the type of file rather than just the extension. 

The only other thing I can think of is a permission issue which isn't allowing the file associations to 'stick'. You might try opening nautilus as root ( gksu nautilus ) and then trying to link the associations one more time;  .pd to Puredata and  .txt to gedit.

Perhaps someone will have a solution for your problem.

---

### Post by waspbr on 2008-03-31
ripfox already solved the problem , you just have to right click , say in  a .pd file , then select properties. this open a dialog, in there you will see a series of tabs, go to the tab named "open with"
then you select or add the program you wanna open it with.

the same thing can be done with a .txt file or any other file for that matter

happy hunting

---

