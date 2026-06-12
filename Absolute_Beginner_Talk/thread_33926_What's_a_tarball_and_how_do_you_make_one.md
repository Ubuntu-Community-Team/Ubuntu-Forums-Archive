---
title: "What's a tarball and how do you make one?"
date: 2005-05-12
forum: Absolute Beginner Talk
---

### Post by YourSurrogateGod on 2005-05-12
I've never really understood what it is or what it should do or how to make it. Could anyone please explain it?

---

### Post by Xian on 2005-05-12
This is a good and basic intro to this subject: [Archiving and Compressing Files In Linux](http://floppix.ccai.com/targzip.html)

---

### Post by dave9191 on 2005-05-12
A tarball, or .tar is an archieve file. You can group lots of files and directories into one file for easier handeling. Like making a download. Its like a zip file or any other compressed file without the compression. Its usually compressed later. Like .tar.gz is an archieve file thats been compressed using gzip.

---

### Post by crmanski on 2005-05-12
This is a pretty comprehensive definition.
[http://en.wikipedia.org/wiki/Tarball](http://en.wikipedia.org/wiki/Tarball)

---

### Post by GrumpySmurf on 2005-05-12
A tarball is an archive created using the 'tar' command.  'tar' stands for "(t)ape (ar)chive" and was originally used as a backup tool to write data to magnetic tape drives. A tarball is akin to a zipfile on Windows.

To create a tarball, here is a sample command.
```
$ tar -cvf project-tarball.tar /home/user/project
```
This would create a file called project-tarball.tar in the current directory of the /home/user/project directory contents.  The 'c' option tells tar to create an archive, 'v' displays the files added to the tarball and 'f' specifies the filename.  After the filename, all other parameters are the files or directories to add to the archive.

Tarballs are commonly compressed using gzip or bzip2 using the -z or -j command options. 

For complete details, see the tar man page 
```
$ man tar
```
Or the official GNU tar web page: [http://www.gnu.org/software/tar/tar.html](http://www.gnu.org/software/tar/tar.html)

---

### Post by YourSurrogateGod on 2005-05-12
Domou mina-san :) .

---

### Post by Quest-Master on 2005-05-12
If you like GUIs, you can also take advantage of the Archive Manager program in Ubuntu. Lots of archiving goodness there :)

---

### Post by stoffe on 2005-05-15
[QUOTE=Quest-Master]If you like GUIs, you can also take advantage of the Archive Manager program in Ubuntu. Lots of archiving goodness there :)[/QUOTE]
 Two questions about that:

* Is there any way to make it take directories?
* Is there any intergration somehow with Nautilus, as in "create archive" on say right-click? Or any way to at least fake it? ;-)

---

### Post by Xian on 2005-05-15
It's not a specific integration but the 'Create Archive' on right-click does exist, and can be expanded to multiple directories in Nautilus by selecting the desired folders and files, then choosing them for archive inclusion.

---

