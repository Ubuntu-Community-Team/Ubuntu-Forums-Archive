---
title: "NVU Crash as user not as root.. is there an alternative?"
date: 2007-01-27
forum: Art &amp; Design
---

### Post by sanone on 2007-01-27
I'm an experienced html/php/js/etc. coder but sometimes I need to create some layouts. I prefer doing this with a WYSIWYG editor and improve/replace the code later with my own php functions etc.

Since I knew about NVU I installed that one and it seems to do what I need. The problems is that it crashes at the moment I try to work in the code view. This problem doesn't appear when I run the application as root (sudo nvu from the console)... so this may be a workaround but this as you understand ugly and in conflict with all security rules.

The other thing I noticed when I first started this application from the console was this message (which made me try it as root):
> Extension System Warning: Failed to set up default extensions files probably because you do not have write privileges to this location. While you can run Firefox like this, it is recommended that you run it at least once with privileges that allow it to generate these initial files to improve start performance. Running from a disk image on MacOS X is not recommended.

Well I tried several other tools like bluefish, kompozer and amaya but none of them have this easy WYSIWYG editor which I need. And I know there is quanta plus (which seems quite nice) but I dislike having kde apps since those KIO-slaves and the Gnome Virtual Filesystems do not intergrate so I can't access my ssh shares without installing KDE (or any other hackerish solution).

Does anyone know what I can do about this? Or does anyone have a nice nvu alternative?

Thanks in advantage,
San

---

### Post by sanone on 2007-01-29
I also installed the nvu version (tar.gz) from their website and the same crash occurs. Is this only happening to me? 

*BUMP*

---

### Post by ComplexNumber on 2007-01-29
in your home partition, you will see a directory called .nvu. close down nvu, then delete the directory.

---

### Post by Jengu on 2007-01-31
Did you launch nvu with root the first time you used it? Then it probably created the .nvu settings  folder inside your home directory but with the owner set to root. Do:

cd ~
sudo rm -r .nvu

And try again as a normal user.

---

