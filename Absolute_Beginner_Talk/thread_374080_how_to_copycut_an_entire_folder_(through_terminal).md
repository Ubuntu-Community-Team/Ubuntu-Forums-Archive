---
title: "how to copy/cut an entire folder (through terminal)?"
date: 2007-03-02
forum: Absolute Beginner Talk
---

### Post by the_nomad on 2007-03-02
is there any way to copy/cut an entire folder in another location THROUGH Terminal? i dont wanna use 
```

cp source source source directory
``` to copy each file in a folder and paste it in a directory... there are too many files :P
and the second question, how do i cut/paste files/folders through terminal? :)


thanx in advance.

---

### Post by timjayko on 2007-03-02
Basic Unix Commands To Remember

The basic commands used in the Unix shell are:

 * cd (directoryname)
      (Changes directories to the one named. In Unix, you change directories one level at a time.)
    * cd ..
      (Changes back up to the previous directory)
    * pwd
      (Prints -- displays to the screen -- the "working" or current directory)
    * ls
      (Lists the contents of the current directory to the screen)
    * ls -l
      (Same as above, but it lists like the DOS DIR command with more information)
    * mkdir
      (Make a directory -- same as DOS "md")
    * rmdir
      (Remove a directory -- same as DOS "rd")
    * cat
      ("Concatenate," or show a files contents to the screen -- same as DOS "type.")
    * cp
      (Copy -- same as DOS "copy")
    * mv
      (Rename [or "move"] a file -- same as DOS "ren")
    * rm
      (Remove [or "delete"] a file -- same as DOS "del")
    * logout
      (Terminates a Unix Shell session)
    * |more
      (When entered at the end of a command such as "cat" or ls -l", this displays a page of text, then stops and waits for you to issue the command to go on) 

most of the time you have to type sudo prior to a command to get root access.. hope i helped

---

### Post by omrsafetyo on 2007-03-02
**cp -r** 
The -r flag will recursively copy the folder, and all sub-directories and files.

The -r flag will work with other commands as well, such as rm: **rm-r dirname** which is the only way to delete a folder with files in it.  It will recursively delete the directory, all subdirectories and files in the directory, and finally delete the directory.

---

### Post by scxtt on 2007-03-02
try:

cp -R /path/to/copy_directory/* /path/to/paste_directory/

---

### Post by phansiizwe on 2007-03-02
In order to find out what more you can do with **cp** (or any other command), type:

```
man cp
```

---

