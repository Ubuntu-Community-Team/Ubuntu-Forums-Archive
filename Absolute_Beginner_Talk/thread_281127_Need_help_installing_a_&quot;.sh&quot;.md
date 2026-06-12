---
title: "Need help installing a &quot;.sh&quot;"
date: 2006-10-20
forum: Absolute Beginner Talk
---

### Post by voodoonirvana on 2006-10-20
I'm trying to install some BOINC software for the SETI@home here:

[http://setiathome.berkeley.edu/](http://setiathome.berkeley.edu/)


Well Im not quite sure how to install this. It is called "boinc_5.4.9_i686-pc-linux-gnu.sh" and I would assume that I need to put it into my home folder, but then I really have no idea how to install it from the terminal.

---

### Post by konst88 on 2006-10-20
if it in the home dir, and has execute permitions, write:
sudo ./boinc_5.4.9_i686-pc-linux-gnu.sh

---

### Post by voodoonirvana on 2006-10-20
> **konst88 said:**
> if it in the home dir, and has execute permitions, write:
sudo ./boinc_5.4.9_i686-pc-linux-gnu.sh

Thanks! :)

---

### Post by Foudre on 2006-10-20
sudo sh insert_file_name

our of habbit i always put -i at the end, alot of the first sh thingys i learned to install said to do that in the instructions, but it seams you almost never have to

---

### Post by avihappy on 2006-10-20
1. Go the the .sh file, right click it, click "Properties", goto the "Permissions" tab and check all the "Execute" boxes.
2. Goto Applications > Accesories > Terminal
3. Type in "sudo" but dont hit enter.
4. Drag and drop the .sh file into the terminal so your terminal looks like "sudo /Your/File/Here.sh"
5. Press enter in terminal
:)

---

