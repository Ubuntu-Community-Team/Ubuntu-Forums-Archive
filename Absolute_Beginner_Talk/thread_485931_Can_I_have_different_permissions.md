---
title: "Can I have different permissions"
date: 2007-06-27
forum: Absolute Beginner Talk
---

### Post by begbie on 2007-06-27
Can each folder within a Samba share have different permissions?
I have a share called FIles.  Within it are four folders.  I like that these four folders are part of the same share, because if someone needs to transfer a larger file between the folders, the transfer is quick, without rewriting the file.  (otherwise the shares are treated like separate drives; file transfers from one to the other are slower)

---

### Post by Maxtorm on 2007-06-27
You can assign permissions at the folder/file level using smbcacls.  Do
```
man smbcacls
```
for usage details.

---

### Post by advoss on 2007-06-27
They can, with out knowing exactly what your goal is I can't tell you the exact commands but I'll give a few general examples and hopefully you will get the idea

For the first example let there be 4 users:
[B]sally
earl
joe
kris[/B]
all of them are configured in samba to be able to log on to the server

The shared folder that has the 4 subfolder I will call **Files**

In Files there are 4 subfolders
[B]Music
Movies
Docs
Pictures[/B]

the commands you will find use full are
[B]chmod
chown
chgrp[/B]
it might be helpful to read the man pages for them (ex. type "man chgrp" in the terminal)
also "ls -l" will be helpful because it will print out the current permissions (there are other guides around to explain how to read that so i wont talk about it here) as well as the current owner of the file/folder and the group it belongs to.
__

I use the -R option so it functions recursively meaning it changed the permissions on all sub folders and files aswell

replace <parent_directory> with the path leading up the the folder, or if you have changed directory in terminal to be there then omit.

if you ran
```
chmod -R a=rwx <parent_directory>/Files
```
everyone would be able to read, write, and execute files in the folder files and all its subfolders

if you ran
```
chown -R sally <parent_directory>/Files/Music
chmod -R u=rwx <parent_directory>/Files/Music
chmod -R go=  <parent_directory>/Files/Music
```
sally would have full control over music and no one else could access the files

if you ran the previous command and then ran:
```
chmod -R o=rx  <parent_directory>/Files/Music
```
then anyone who can connect to the server can access see and read the files, however only sally (the owner of the files) would have power to add, change, or delete the files

if say joe and kris are working together on some documents and sally and earl shouldn't see them then make a group ex.
```
addgroup sharedocs
```
make joe and kris part of it
```
adduser joe sharedocs
adduser kris sharedocs
```

then change the group of the Documents folder to share docs
```
chgrp -R sharedocs <parent_directory>/Files/Documents
```
then change the permissions so the group can read, write, and execute and everyone else can't do anything
in this example i first take permissions away from everyone and then give it back to the group
```
chmod -R a= <parent_directory>/Files/Documents
chmod -R g+rwx <parent_directory>/Files/Documents
```
then joe and kris can do whatever they want in the folder and no one else will even know its there

Using combinations the the above techniques you could be able to change the permissions to have only the people you want seeing only the files you want.  The ch* commands mentioned also function on individual files (remember to remove the recursive (-R) tag).  So for example in the Picture you could have 4 file.  Each photo of a different user and if you set permissions on the files right when each user opens the Pictures folder they will only see 1 file: a picture of themself.

Best of luck :)

---

### Post by begbie on 2007-06-27
EDIT  (hadn't read the above)
thank you advoss, seems the chmod, chown and chgrp would probably be better than using smbcacls (for which I can not find a single example)

---

### Post by Maxtorm on 2007-06-27
This page has some usage examples (though the purpose is different than yours): [http://archives.free.net.ph/message/20060420.164952.4a948524.en.html](http://archives.free.net.ph/message/20060420.164952.4a948524.en.html)

---

### Post by begbie on 2007-06-27
thanks
what are the differences between using the chmod type commands and smbcacls?
(I also will have OS 9 and OS X systems connecting to these shares.)

to advoss:
i entered:
chmod -R a=rwx /media/files/FileServer/Office
and then:
chown -R store /media/files/FileServer/Office
which returns:
chown: changing ownership of `/media/files/FileServer/Office/tyiotio': Operation not permitted
chown: changing ownership of `/media/files/FileServer/Office': Operation not permitted

can you tell what i'm doing wrong?
what is "tyiotio" ?

---

### Post by begbie on 2007-06-27
got it.

I used sudo and it worked

---

