---
title: "How to Massively change CHMOD permissions on a FTP"
date: 2007-08-21
forum: Absolute Beginner Talk
---

### Post by Kosimo on 2007-08-21
I'm installing Joomla! 1.5RC1 on a ftp. And I need to change permissions of all files to 755. But it seems I do have to do manually for each file inside each folder!!!!  
Somebody knows some easy way to change permissions to all files in all folders?
I'm using gFTP. (A full bugged program I guess anyway)
Thank you

---

### Post by wormser on 2007-08-21
Try adding the -R switch to the directory.  

> -R 	 Descends only directories recursively, as specified by the pattern File...|Directory.... The -R flag changes the file mode bits of each directory and of all files matching the specified pattern. See Example 6.

When a symbolic link is encountered and the link points to a directory, the file mode bits of that directory are changed but the directory is not further traversed.

> 6.  To recursively descend directories and change file and directory permissions given the tree structure:

./dir1/dir2/file1

./dir1/dir2/file2

./dir1/file1

enter this command sequence:

chmod -R 777 f*

which will change permissions on ./dir1/file1.

But given the tree structure of:

./dir1/fdir2/file1

./dir1/fdir2/file2

./dir1/file3

the command sequence:

chmod -R 777 f*

will change permissions on:

./dir1/fdir2

./dir1/fdir2/file1

./dir1/fdir2/file2

./dir1/file3

More [here]("http://www.unet.univie.ac.at/aix/cmds/aixcmds1/chmod.htm").  You will need to ssh in to use the commands.

---

