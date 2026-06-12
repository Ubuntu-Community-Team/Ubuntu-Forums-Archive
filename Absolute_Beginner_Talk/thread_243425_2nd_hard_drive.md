---
title: "2nd hard drive"
date: 2006-08-25
forum: Absolute Beginner Talk
---

### Post by gentlemanmasher on 2006-08-25
I have two hard drives and was able to get access to my windows files on the first one, but when I try to get access to my seagate HD I get this error:

The Folder contents Could not be Displayed

You do not have the permissions necessary to view the contents of "disks-conf-hdb1".

can anyone help please

---

### Post by anaconda on 2006-08-25
try the same with root rights. To get them type

gksudo nautilus

to terminal.. (it opens file-manager with root rights..)

---

### Post by catlett on 2006-08-25
as stated above, enter this to launch nautilus as root
```
gksudo nautilus
```
Now browse to the media folder (at the top of the window computer<filesystem<media) and find your folder for the seagate hd. (it should be hdb1.
When you get to the folder, "right-click" on it to open the options menu. Select "properties". When the window opens, select the "permissions" tab. You will see the boxes for owbner and group. They will look something like this
Owner
Group 
Others
Yours most likely only has Owner checked off after it. To give your self accesss to the drive, check off Read, Write and Execute after Others. If you are the only one, you can check them all off so that any way the drive is accessed, it will be availqable.

Hit close and that is it. You can change the permissions on any file/folder  in this manner.

---

### Post by gentlemanmasher on 2006-08-25
(nautilus:30916): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.


this is the error I received after putting the command in the terminal.
Its not only windows files I cannot get access to in my second drive.  I cannote even get into the drive.

this is what I get when trying to access the drive

You do not have the permissions necessary to view the contents of "disks-conf-hdb1".

---

