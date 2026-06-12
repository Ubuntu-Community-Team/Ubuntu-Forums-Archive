---
title: "sudo VS root -- how to create a shared folder for Samba"
date: 2007-03-28
forum: Absolute Beginner Talk
---

### Post by MJWhiteDerm on 2007-03-28
Hello, one and all.

My name is Michael White and my email is [email]michael.white@gemair.com[/email].  Like most other people here, I'm a relative newcomer.  I am running several computers in my house, on a lan.  I'm running two with Suse linux 10.1, a couple of Windows boxes (work related stuff and my wife still prefers Windows-XP), and now an unbuntu box and a xunbuntu system.

I have been running one of my Suse systems as a file server on the Windows nextwork for my wife and stepson, and to allow me to share digital pictures, etc.  I know how to invoke root privileges in Suse Linux to set up a new folder in the /home directory.  But, I can't figure out how to do it in ubuntu or xubuntu.  There is no obvious menu choice to run File Manager as root.  I read the "sudo vs. root" page in the help files and that doesn't help me much.  Do I need to go into terminal mode to set up the folder?  How do I then set the permissions?

My goal is create a new folder:  /home/shared-files that can be read and modified by all over Samba.  Any hints on where to go to find out how to do that?

Thanks!

Michael

---

### Post by Famicommie on 2007-03-28
Yes, you can do it from terminal mode. Open up a terminal.

```
cd /home
sudo mkdir shared-files
<system asks for your root password>
sudo chmod -R 766 shared-files
```

The numbers "766" are the permissions. 

The first number sets the permissions for the user, the second for the group, and the third for "others". The number 4 is used for read permission, 2 is used for write permission, and 1 is used for executable permission. You can add them together to combine permissions. So, in the example provided:

The file owner has read/write/executable permission.
The group and others have read/write permission.

From there, I *believe* that you can set up the Samba sharing options through nautilus - the file browser by right clicking on the folder.

---

### Post by MJWhiteDerm on 2007-03-28
That seems to have worked well.  Thank you!

The following is **not** a complaint about ubuntu.  Having to go into the terminal mode and enter Command Line commands seems to defeat one of the goals of ubuntu, that is, to be user-friendly enough to entice Windows-frustrated people to abandon the lure of Windows for the functionality and stability of linux systems.

I have worked with Red Hat (through 8.0, Mandrake / Mandriva, Suse, and now ubuntu.  I never have enough time to really get into the nitty gritty of the Command Line interface, but now I am finally starting to.

I host a ocuple of web pages and actually have a static IP at this point, so I can host one to several in the house.  But I'm trying to get into the details of networking / etc. under different linux distributions and things are getting more complicated.  

Patience, Grasshopper ...

Thanks, again.  

Michael

---

