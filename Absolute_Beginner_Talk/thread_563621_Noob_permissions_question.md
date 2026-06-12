---
title: "Noob permissions question"
date: 2007-09-30
forum: Absolute Beginner Talk
---

### Post by Gavbuntu on 2007-09-30
I'm at total linux noob, rushed into things and installed ubuntu over the top of windows xp. Once I realised what I'd done (lost all my films, audio, pdfs etc etc) I started googling for a solution to recover them.
I found photorec and used it. I now have lots of folders that I don't have the permission to open. Could someone please tell me how to make the files available. Bear in mind I know nothing about using a terminal so assume you're talking to a linux idiot :-(

Thanks

Gav

---

### Post by az on 2007-09-30
The problem is that you recovered those files as root and so they have root ownership.  You can change the ownership of all the files in a directory by runningn


sudo chown -R youruser:youruser /recoveredfilesdirectory

Where youruser is your user and recoveredfilesdirectory is the directory.  Unix/Linux is case sensitive, so be sure to use a capital R.

See here for more data recovery software:
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

---

### Post by kellemes on 2007-09-30
Maybe it's a stupid question but.. are you sure your Windows data is overwritten?
Isn't it just you have to setup the bootloader again?

---

### Post by Gavbuntu on 2007-09-30
AZ,

thank you so much, you've saved my life. I'm going to be really cheeky and ask one more question. Seeing I have 160 folders to do, is there any way of doing it all in one go instead of 160 goes?

Kellemes,

I'm not sure because I used the whole disk for the ubuntu install.

---

### Post by az on 2007-10-01
-R means "recursive" which means to go through all the subfolders within the folders.  Just run it on the top level folder.

EDIT:  Not the "/" directory!  Just the top-level to the bunch of folders in which you stored your recovered files.

---

