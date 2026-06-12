---
title: "file permitions"
date: 2008-03-20
forum: Absolute Beginner Talk
---

### Post by Xenoc on 2008-03-20
hello,


I'm trying to install nwn plat. using [this]("http://ubuntuforums.org/showthread.php?t=113259&highlight=neverwinter+nights") guide, but when I get to step 5 it says that I can't install to my chosen directory because of permissions. How can i alter this or get around it? I'm trying to install to the /home/<username>/nwn directory. Please help me out of this noobish pit.

---

### Post by Iandefor on 2008-03-20
You replaced <username> with your own username, right?

---

### Post by uberlube on 2008-03-20
:lolflag:

---

### Post by Xenoc on 2008-03-20
> **Iandefor said:**
> You replaced <username> with your own username, right?

of course.... I just want to play the game and I understand enough about the file system to do that, but my computer says that i cant access the file because of user permissions.

---

### Post by OffAxis on 2008-03-20
you can see what the file permissions for anything is by navigating to the folder and issuing a 

```
ls -l
```

command.

To change file or folder permissions you can use the command **chown**.

```
sudo chown username:groupname filename
```

chown = change ownership

you can leave out username or groupname and it'll just change what is there. For example

```
sudo chown :groupname filename
```

would only change the group ownership, not the username/owner.

---

### Post by Xenoc on 2008-03-20
ok, I've tried those commands but I can't seem to change the permissions to allow me to write to the folder. Is there a way I could login as the root user to change the permissions?

---

### Post by lswest on 2008-03-20
you want to add read/write permissions for a folder and it's subfolders & files?

do this:

```
sudo chmod -R o+rw+x [foldername]
``` this command will change the modification options for group "other" (e.g. anyone other than the owner) to read/write/execute abilities, and will do so Recursively (-R) so that it applies it to all folders.

---

### Post by Xenoc on 2008-03-20
i managed to get the permissions and changed them so i could write to the folders in question, but I still get the same error. 

```
/home/xenoc/nwn
[: 64: ==: unexpected operator
-e Possible write error
-e Please try a different folder or change permissions on /home/xenoc/nwn
```

---

### Post by lswest on 2008-03-20
hmm the output of this:
```
cd /home/xenoc/nwn
ls -l
``` might help (unless nwn is a file, then CD to a directory above that, so /home/xenoc/)

---

### Post by Xenoc on 2008-03-20
all i get is the fallowing, but remember I'm trying to install to this directory, so as of now it's an empty folder.
```
total 0

```
or at the higher directory i get this
```
drwxrwxrwx 2 xenoc root       4096 2008-03-20 11:08 nwn

```

---

### Post by lswest on 2008-03-23
sorry, forgot about this thread :P  what you can do is create the folder manually with ```
mkdir /home/xenoc/nwn
chmod -R o+rw +x /home/xenoc/nwn
```

(first line creates the folder, second line sets the permissions)

---

