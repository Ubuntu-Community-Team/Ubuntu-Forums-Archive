---
title: "Getting to a nework folder in Terminal"
date: 2008-02-17
forum: Absolute Beginner Talk
---

### Post by Bill Bickley on 2008-02-17
I have a folder named smb://freenas/shared/HP_Ubuntu set up on a FreeNAS server on my home network.  What's the command to switch to that folder in Terminal?

I tried cd /smb://freenas/shared/HP_Ubuntu,  but no go...

Bill

---

### Post by zerhacke on 2008-02-17
If you install the smbfs package in the repositories you can mount the shares to your computer so they will act like any other folder on your computer.

In a terminal, this would be as follows:

sudo apt-get install smbfs

sudo mkdir /media/sharename

sudo mount -t cifs //1.2.3.4/share /media/sharename

Replace 1.2.3.4 with the ip address of your server.  Contrary to public opinion, you do not need to install the samba server to access shares on a remote machine.

---

### Post by Bill Bickley on 2008-02-18
After completing the earlier steps you mentioned, using freenas instead of sharename (see my original post), I got this:

dad@dad-ubuntuHP:~$ sudo mount -t cifs //192.168.1.250/share /media/freenas
Password: 
retrying with upper case share name
mount error 6 = No such device or address
Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)
dad@dad-ubuntuHP:~$ 

Any thoughts would be much appreciated.

Bill

---

### Post by justleen on 2008-02-18
i ran into the same @work, mounting a windows drive..

for me, what worked, was to mount it to just the host, not to the share. even though im VERY sure im not authorized om the root of that drive, i could mount it, and browse to the folder i needed.

$ sudo mount -t cifs //192.168.1.250/ /media/freenas

---

### Post by zerhacke on 2008-02-18
> **Bill Bickley said:**
> dad@dad-ubuntuHP:~$ sudo mount -t cifs //192.168.1.250/share /media/freenas

Replce "share" on the server side with the name of the share.  It's case sensitive, too.

---

