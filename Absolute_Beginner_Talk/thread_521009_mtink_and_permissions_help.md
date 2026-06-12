---
title: "mtink and permissions help"
date: 2007-08-08
forum: Absolute Beginner Talk
---

### Post by Mark Phelps on 2007-08-08
Have installed mtink to monitor Epson ink levels and it works fine when invoked as root.  BUt I want to be able to add a menu item and run it as a normal user.

When I run mtink as a normal user, I get "Error, No access to printer device file.  Please make sure that mtink has enough right for accessing the device files."

My Epson printer uses the first USB port, so it's device file entry is /dev/usblp0. The file persmissions on /dev/usblp0 are 660 (-rw-rw----), So, it looks like I already have r/w permissions for that character device file.

I've read several forum posts on this, and they all say essentially the same thing -- make sure the my user account is added to the group "lp".  There is a group "lpadmin", and checking /etc/group/, I find the line "lpadmin:x:113:bill" But there is no group "lp" on my installation. 

One forum post said to run System --> Admin --> Users and Groups, click Manage Groups and scroll down to the "lp" group.  But since I have no such group, it's not in the list. That forum post said to check a box that enabled the display of all users and groups but there's no such box in the window. When I click the lpadmin group, and properties, it lists the group ID as 113, and my account is checked as a Group Member.

What do I do now -- I'm out of ideas.

---

### Post by Mark Phelps on 2007-08-10
No one? No suggestions at all??

---

### Post by RedSquirrel on 2007-08-11
I found your [other post]("http://ubuntuforums.org/showpost.php?p=3166430&postcount=6") first, so I posted [my answer]("http://ubuntuforums.org/showpost.php?p=3172800&postcount=7") in that [thread]("http://ubuntuforums.org/showthread.php?t=28175").

---

### Post by holdup on 2007-11-11
Here's how I got around the problem

1) Open up a terminal  type gksudo nautilus
2) Navigate to the /dev/usb directory
3) My printer in there is called lp0 I suspect yours will be too if it is the only usb printer.  Right click on the lp0 file and click ***Properties*** then click on the ***Permissions*** tab.  You will probably have Owner - root, Group lp, Others : None or Read only,  set the others tab to be Read and Write.
4) now run mtink from the command line as a user (i.e. without sudo) or from a shortcut in the menu/panel.

Hope this helps


Andyb

---

### Post by stella2657 on 2008-03-13
:biggrin: thank you - your solution finaly fixed my very frustrating problem tried a number of fixes, this one did the trick.

---

