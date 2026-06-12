---
title: "unable to log in ubuntu :("
date: 2007-12-25
forum: Absolute Beginner Talk
---

### Post by saurabh kakkar on 2007-12-25
Hi
I m not able to log into my ubuntu account whenever i try to login ubuntu gives the following error: 
> 
GDM. could not write to your authorization file.this could mean that you r out of disk space or that your home directory could not be opened for writing.
in any case ,it is not possible to login.plz contact your system admin


this happend when i transfered lot of data in my small ubuntu partition 

writting this post from my friends P.C

plz help me fast what can i do ? I can only go to ubuntu recovery mode but no GuI from there :(

---

### Post by arijarot on 2007-12-25
> **saurabh kakkar said:**
> Hi
I m not able to log into my ubuntu account whenever i try to login ubuntu gives the following error: 


this happend when i transfered lot of data in my small ubuntu partition 

writting this post from my friends P.C

plz help me fast what can i do ? I can only go to ubuntu recovery mode but no GuI from there :(

can you log in through the tty (ctl+alt+f1)? if so, you'll need to move some of the files you transfered to your home partition onto an external hd, e.g.

---

### Post by saurabh kakkar on 2007-12-25
> **arijarot said:**
> can you log in through the tty (ctl+alt+f1)? if so, you'll need to move some of the files you transfered to your home partition onto an external hd, e.g.

Dont know will try plz post any other method also i m the admin

---

### Post by The Cog on 2007-12-25
You don't need a GUI to delete files - it can be done from the command line. You need to be aware of the "currnent directory" - the directory you are in at the moment. I don't know off hand where recovery mode puts you, but the command
**pwd**
(print working directory) will tell you where you are.
You can change directory with cd, like this:
**cd /home/my-name**
and you can change up one directory with 
**cd ..**
You can list the files and directories in the current directory with 
**ls -l**
and you can delete files with
**rm filename**
(rm for remove).
You can even remove entire directories with 
**rm -rf directoryname**
but be careful what you remove - it won't ask are you sure.

Or if the command line is just too uncomfortable, you can always use a live CD with a GUI, but you will probably have to use a command line there in order to mount the hard drive so you can delete files.

As an afterthought, this command from recovery mode might delete enough to allow you to use a GUI again, if you're lucky:
**rm -rf /tmp**

EDIT:
Nooooo! That will delete the /tmp directory. I should have said:
**rm -rf /tmp/***
which will delete everything in /tmp.

---

### Post by arijarot on 2007-12-25
> **saurabh kakkar said:**
> Dont know will try plz post any other method also i m the admin

I think the method of transferring the files off of the partition should be sufficient given your description; Give it a try.

---

### Post by terminal on 2007-12-25
you can delete a few files from recovery mode . Use rm -fr "dir name" to delete . Warning: rm-fr will delete a directory and all files and folders inside it , without throwing any notice :)

---

### Post by arijarot on 2007-12-25
Note that if you choose to remove [rm] a file/directory, to be safe, add the ```
-i
``` option in order to be prompted before any removal.

---

### Post by saurabh kakkar on 2007-12-25
> **The Cog said:**
> You don't need a GUI to delete files - it can be done from the command line. You need to be aware of the "currnent directory" - the directory you are in at the moment. I don't know off hand where recovery mode puts you, but the command
**pwd**
(print working directory) will tell you where you are.
You can change directory with cd, like this:
**cd /home/my-name**
and you can change up one directory with 
**cd ..**
You can list the files and directories in the current directory with 
**ls -l**
and you can delete files with
**rm filename**
(rm for remove).
You can even remove entire directories with 
**rm -rf directoryname**
but be careful what you remove - it won't ask are you sure.

Or if the command line is just too uncomfortable, you can always use a live CD with a GUI, but you will probably have to use a command line there in order to mount the hard drive so you can delete files.

As an afterthought, this command from recovery mode might delete enough to allow you to use a GUI again, if you're lucky:
**rm -rf /tmp**

Thanks buddy that solved my problem 
 i think there should be some kind of restriction that ubuntu should throw to users so that  this kind of situation do not arrive

---

