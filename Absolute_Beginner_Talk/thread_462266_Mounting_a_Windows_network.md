---
title: "Mounting a Windows network"
date: 2007-06-02
forum: Absolute Beginner Talk
---

### Post by Mark Raymond on 2007-06-02
I have a shared folder on a Windows network (no username/password), which I can access via smb://raymond1/Mark/
How do I mount this so I can access it via /home/mark/ ? (my username is mark)
Either so /home/mark/mark/ points to smb://raymond1/Mark/, or /home/mark/ points to smb://raymond1/Mark/.

---

### Post by kevdog on 2007-06-02
Here is how I do it, but Im no expert;

sudo mount -t smbfs -o username=user,password=pass,uid=????,gid=???? //raymond1/Mark /home/mark/mark



Obviously you need to fill in the appropriate user,pass,uid and gid

---

### Post by Mark Raymond on 2007-06-03
I tried this:
sudo mount -t smbfs //raymond1/Mark /home/mark/mark
and it came up with this:
mount: mount point /home/mark/mark does not exist

There is no username or password for the network, so those aren't applicable, but what are uid and gid?

---

### Post by shearn89 on 2007-06-03
I have a similar network set up at home, and i access my documents by putting a launcher on the desktop. I think i made it into a link to a URL and put the equivalent of "smb://raymond1/Mark/" as the URL it pointed to.
Perhaps you could create a hidden launcher on the desktop (or in the desktop folder) and then create a symbolic link to it in the /home folder? 
unfortunately I tried to upgrade to feisty using an install disc that died half way through the base install, and so I cannot go "hands on" and try anything out for you...

---

### Post by Mark Raymond on 2007-06-03
I can already access it through smb://raymond1/mark/
and I have a link to it in the 'Places' menu at the top, so usually, in OpenOffice programs for example, I can choose Home Folder, Floppy, Filesystem and Mark, or something like that, so I can access it easily there, but if I'm downloading something, I can only save it to places which are in the file system, so I can't save it to smb://raymond1/mark/ which is a little irritating.

---

### Post by kolslorr on 2007-06-03
> **Mark Raymond said:**
> I tried this:
sudo mount -t smbfs //raymond1/Mark /home/mark/mark
and it came up with this:
mount: mount point /home/mark/mark does not exist

There is no username or password for the network, so those aren't applicable, but what are uid and gid?

Have you created this folder? 

/home/mark/mark

---

### Post by Mark Raymond on 2007-06-03
No, I hadn't.
Do you have to have an empty folder to mount to, then?
I tried mounting to /home/mark and that didn't work...

---

### Post by vanadium on 2007-06-03
Take a look on Ubuntu guide:

[http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty)

---

### Post by Mark Raymond on 2007-06-08
Here's the terminal output:

markr@mark-desktop:~$ sudo mount //192.168.2.2/Mark /home/markr/mydocs
mount: wrong fs type, bad option, bad superblock on //192.168.2.2/Mark,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

192.168.2.2 is the correct IP address, Mark is the right share name, /home/markr/mydocs does exist and it is empty, the network has no username or password.

What do I do?

I can still access everything on smb://raymond1/Mark

--EDIT--

It's working now...smbfs wasn't installed, or something like that. Anyway, everything seems to be working.

---

