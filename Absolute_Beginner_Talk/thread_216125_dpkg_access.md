---
title: "dpkg access"
date: 2006-07-15
forum: Absolute Beginner Talk
---

### Post by olking on 2006-07-15
I am trying to install a printer driver for brother mfc210c
The instruction says to give the following command but when I do I am told that I need read write permission for dpkg area
this is the command

dpkg -i --force-all mfc210clpr-1.0.2.1.i386.deb

I found a folder called dpkg in etc and this permission is for owner only.
How can I become the owner, or otherwise install this driver:(

---

### Post by [S|G] on 2006-07-15
try using ```
sudo dpkg -i --force-all mfc210clpr-1.0.2.1.i386.deb
```

---

### Post by Sandlst on 2006-07-15
In ubuntu, adding the word 'sudo' before commands gives you temporary root (highest) access to all files on your system.

---

### Post by olking on 2006-07-15
thanks bery much.
The sudo works fine.
Unfortunately after unpacking the file it then wanted to make a directory and was unable to do this so I am still stymied.
Any advice?](*,)

---

### Post by [S|G] on 2006-07-15
When does it want to create a directory? When you run the program for the first time?

You can try running it as root (using sudo command) but you should make sure the program won't break your system. Most programs are able to install their stuff into your home folder, which doesn't represent a system security risk.

So, if it asks before actually creating the directory, point it somwhere into your home directory ( /home/youruser/directory or simply ~/directory ). If you can't do that, try ```
sudo program
```

---

### Post by olking on 2006-07-15
Hi,
I ran it again and it seemed to go through ok, it said it had created a symbolic link /usr/lib/librcompi/filename  and the file exists

and after two repeats it went out to prompt

I went to the printer admin and asked it to add a printer.
It brought up the list of drivers for the mfc210, but this didn,t include the new driver

I am embarrased to keep on asking, but what should I do now?
:(

---

### Post by [S|G] on 2006-07-15
Did it return an error while creating the symbolic link? Or did it create it successfully? Try to do this: ```
ls -l /usr/lib/librcompi/filename
``` It should be pointing somewhere (since it is, after all, a link). Do the link exist and is the correct file? Try to ls the file that the link points to so you can check that it indeed exists.

From what you told, you WILL need to run as root in order to create the symbolic link, since it will be outside your home folder. Therefore you HAVE to ```
sudo command
``` 

If you did this and the symbolic link is correctly set up then I believe it is a matter of configuring your printer admin to recognize it. If you run as root (using sudo) and even so it doesn't work, don't feel embarrassed to ask again: this is what the forums are meant for.

EDIT: I have found this guide (I'm not sure if it's the one you've been following, but it's worth a try): [http://www.ubuntuforums.org/showthread.php?t=105703](http://www.ubuntuforums.org/showthread.php?t=105703)

---

### Post by olking on 2006-07-15
Thanks again, I have to go off line, but will try this on Monday when I return:)

---

