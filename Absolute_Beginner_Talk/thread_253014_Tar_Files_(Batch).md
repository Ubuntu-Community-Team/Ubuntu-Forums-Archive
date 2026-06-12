---
title: "Tar Files (Batch)"
date: 2006-09-07
forum: Absolute Beginner Talk
---

### Post by wsun on 2006-09-07
Hi, what do I type so that .tar files on a CD can be untarred to a directory on my desktop? Thanks, I have about 100 on there so the last thing I want to do is to go through one by one and extract it.

---

### Post by jordanmthomas on 2006-09-07
```
cd *wherever your cd is mounted*
tar -C /home/username/Desktop/folder -xvf *.*tar extensions*

```

according to your post, tar extensions will just be tar

Let someone verify that before you try though because I'm not too confident in my answer. ;)

---

### Post by wsun on 2006-09-08
it keeps saying *filename* not found in archive... :(

---

### Post by jordanmthomas on 2006-09-08
Give me an example name of one of the tarballs (because this does work for me).  Really, I just need the extension
ie.
.tar
.tar.gz
.tar.bz2
etc

---

### Post by shanek on 2006-09-08
I'm not sure if this will answer your question, but here's what I think you're asking:

You want to untar (sorta like unzip) a bunch of somethingOrOther.tar files to your desktop. 

To do one at a time from the command line you would:

```
$ cd ~/Desktop
$ tar xf /path/to/file.tar
```

cd changes you to a directory. In this case, it changes you to the current user's desktop (~ is used as a shortcut to /home/yourusername)

the tar command is used to manipulate or make tarballs. Those random letters after the tar command are 'switches' 'x' tells tar to extract (untar) a 'f' or file. Some other common switches for untarring are 'j' for tar.bz2 files and 'z' for tar.gz files. Another common one is 'v' which stands for verbose. which means that tar will tell you what it's working on when it's running. More info about tar can be found using the 
```
$ man tar 
```
command.

To do this in a batch, you use something like this:
```
$tar xf /path/to/*.tar
``` 

the '*' is a wildcard. Wildcards let you say somthing like "everything that ends with .tar". In this case, it will untar everything in the specified directory that ends with tar to the directory you're currently in. (you can verify your current directory by typing 'pwd' (print working directory) into the command prompt. 

You can also specify where the untarred files would go by doing something like:
```
$ tar xf /path/to/tarfile.tar/ ~/Some/Directory/
```
the first path is where the tar file(s) is and everything after the space is where the files will be untarred to.,

---

