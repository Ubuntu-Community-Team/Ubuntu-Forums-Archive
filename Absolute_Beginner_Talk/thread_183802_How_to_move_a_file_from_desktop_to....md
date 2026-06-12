---
title: "How to move a file from desktop to..."
date: 2006-05-28
forum: Absolute Beginner Talk
---

### Post by Trocisp on 2006-05-28
/usr/share/pixmaps


Since the /usr/share/pixmaps file is protected and I can't move stuff from my desktop there, what's the sudo command, if you don't mind helping?


Thank you,

Marc.

---

### Post by popkid on 2006-05-28
[QUOTE=Trocisp]/usr/share/pixmaps


Since the /usr/share/pixmaps file is protected and I can't move stuff from my desktop there, what's the sudo command, if you don't mind helping?


Thank you,

Marc.[/QUOTE]

As a one off, you can copy the file by issuing the command below in a terminal window, obviously substitute the filename for the right one!

sudo mv /home/marc/Desktop/filename /usr/share/pixmaps/.

More generally I think you can set up the file manager to allow you to do this in the gui using gksudo, if you search the forums for "nautilus gksudo" you should find how to do that

pK

---

### Post by tartarian on 2006-05-28
the sudo command for copy is cp 

example :

sudo cp [file you want to move] [where you want to move it to]

So:

sudo cp /home/oliver/Desktop/myfile.doc /usr/share/pixmaps

would copy myfile.doc to usr/share/pixmaps

(to move - substitute cp with mv)

---

### Post by araz on 2006-05-28
1.Open a terminal
2.Go to Desktop folder
3. type: sudo mv <filename> /usr/share/pixmaps
(sudo is to execute a command as super user)
(mv is move command)

---

### Post by Trocisp on 2006-05-28
Thank  you for the help guys.

---

