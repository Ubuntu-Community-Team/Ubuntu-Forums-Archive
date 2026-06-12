---
title: "Mount Network Share Help"
date: 2007-04-25
forum: Absolute Beginner Talk
---

### Post by captainnoob on 2007-04-25
I'm trying to mount a network share using the following:
 sudo mount -t cifs -o username=myUserName,password=myPassword,dmask=777,fmask=777 //192.168.1.22/ron /media/Music


it appears to mount properly but when I click on the directory in the file browser, I get the following error:
The folder contents could not be displayed.
you do not have the permissions necessary to view the contents of Music.
the directory /media/Music is set to 777

I can successfully connect to the share using Places -> connect to server using:
service type = Windows Share
server = 192.168.1.22
share = ron
username = myUserName

I do get prompted for my password, but I supply the one in the mount command above and everything works fine.

what am I doing wrong???

Thanks

---

### Post by stmiller on 2007-04-26
that should be -t smbfs
you are specifying the wrong file system type.

You can do this through nautilus, you know. Just browse to the network Go>Network

And for samba to work, you must create a samba user on your local Linux machine. Make it the same username/passwd as your samba share machine.
As root (sudo -s to get to root), type

$ smbpasswd -a yourusername

---

