---
title: "deleting an .htaccess file?"
date: 2007-04-02
forum: Absolute Beginner Talk
---

### Post by Dr.Jeckyl on 2007-04-02
i'm pretty new to Ubuntu so this is pretty puzzling to me.

while i was fooling with a website i admin i created an empty file via right click > Create Document > Empty file then i named it .htaccess. when i was done with uploading it to my website i no longer needed it so i tried to delete it and it spit out this error:

[[IMG]http://img508.imageshack.us/img508/6921/shotyw7.th.gif[/IMG]](http://img508.imageshack.us/my.php?image=shotyw7.gif)

my question is how do i delete the file that is obviously on my desktop? i tried clicking Retry and Skip and still get the error.

any help is appreciated.

---

### Post by joeycbulk on 2007-04-02
File not found, which means that the file does not exist or file was already been deleted. Refresh your screen by pressing (ctrl + r) or reset your desktop environment by pressing (ctrl + alt + backspace).

---

### Post by airtonix on 2007-04-02
or if that still doesnt work, try this : 

open a terminal and type : 

> sudo nautilus --no-desktop /home/joeycbulk/Desktop

then if the file is still there....delete it by : 

> shift+delete

other wise if you just right click > move to trash.. it will go into a folder called .trash or .Trashes or .trash-root...etc.etc...

so shift delete when you dont a file to exist anymore at all.

---

### Post by Dr.Jeckyl on 2007-04-02
ctl + r worked. thanks for the quick response.

---

