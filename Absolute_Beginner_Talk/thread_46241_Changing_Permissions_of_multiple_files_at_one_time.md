---
title: "Changing Permissions of multiple files at one time"
date: 2005-07-03
forum: Absolute Beginner Talk
---

### Post by kolya on 2005-07-03
Hi I just moved a lot of file from my Windows hard drive which was NTFS and now I want to allow all users to read, write and execute the files.  Is there a way to do this without having to go through and manually do it to each file, because there are 5,000+ files.  Thanks in advance.

---

### Post by crashtest on 2005-07-03
[QUOTE=kolya]Hi I just moved a lot of file from my Windows hard drive which was NTFS and now I want to allow all users to read, write and execute the files.  Is there a way to do this without having to go through and manually do it to each file, because there are 5,000+ files.  Thanks in advance.[/QUOTE]

Are they all in one directory?  If so, cd to that directory, then enter chmod 777 *

If there is a large directory structure, you can make the command recursive:  for example you have a directory /home/username/win_files which has several subdirectories below it:  chmod -R 777 /home/username/win_files

---

### Post by crashtest on 2005-07-03
I just realized you might be wanting to do this in a gui rather than at the command line.  Here's how:

-open nautilus (the file browser)
-navigate to the directory which has the files
-click 'edit', then select all
-right click on one of the files, then select properties
-on the properties page, select the permissions tab
-select read, write, and execute for 'group' and 'others'

See how this is a lot faster at the command line?  :-)

---

### Post by kolya on 2005-07-03
That is awesome thank you!

---

### Post by kolya on 2005-07-03
Ya I like the command line way better.  Thanks for the help. :)

---

