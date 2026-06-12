---
title: "Themes"
date: 2006-10-05
forum: Absolute Beginner Talk
---

### Post by fontenot_1031 on 2006-10-05
Where's the best place for downloading new themes?

---

### Post by GStubbs43 on 2006-10-05
[http://www.ubuntuforums.org/showthread.php?t=269867](http://www.ubuntuforums.org/showthread.php?t=269867)
[http://www.ubuntuforums.org/search.php](http://www.ubuntuforums.org/search.php) ;)

---

### Post by SoggyCornflake on 2006-10-05
tar.gz means you have an archive file (tar) that has been compressed (gz).  It doesn't nessarily mean that the file is a program to be compliled.

If you want a particular program and don't feel like compiling it, first check to see if has already been compiled and archived in a .deb file for Ubuntu.  you can search for programs packaged for Ubuntu by going to [http://packages.ubuntu.com/]("http://packages.ubuntu.com/").

If it's not there and you want to compile something you got from another source such as your tar.gz files, you'll need to install the packages to compile programs as Ubuntu doesn't necessarily install them (use the  above link to get the names you need to install)

To prepare a tar.gz file for compiling you need to first expand and unpack it.  you can use an archive GUI program to do that (most will handle .tar.gz files) or from a command line type

gunzip foo.tar.gz

then type

tar -xvf foo.tar


then follow instructions from the file you just expanded.


note you could also do it by typing 

tar -jxvf foo.tar.gz

The j option unzips it.  The x option pulls the file from the archive. the v option displays the results, and the f option forces the command so you don't have to keep hitting y

---

### Post by civic_si on 2006-10-05
it depends on the version of your desktop i use GNOME so i use gnome-look.org  
for kde use kde-look.org and theres many others.

---

