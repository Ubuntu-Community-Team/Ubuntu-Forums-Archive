---
title: "how do i unlock files"
date: 2007-01-06
forum: Absolute Beginner Talk
---

### Post by STREETURCHINE on 2007-01-06
how do i unlock files.my dev file,proc file,sys file,and root file'have paddlocks on them 

i think this is why i cant get internet access i could be wrong 
but before the locks appeared i could access the internet 

correct me if i am looking in the wrong direction

---

### Post by ajmorris on 2007-01-06
list them with permissions in a shell. If only root can access them then do
[PHP]sudo chmod 777 "filename"[/PHP] so everyone has read write and execute.

---

### Post by STREETURCHINE on 2007-01-06
how do i list them in a shell,what is a shell,
my command line knowledge is very thin

please in basic terms 

thanks

---

### Post by ajmorris on 2007-01-06
It is called Terminal if you are using Gnome
It is called Konsole if you are using KDE
Just look for either in the start menu. Or go to run command (ctrl+F2) and type either in (no capitals) Then go to the folder they're in and type "ls -l." Then it gives the permissions.

(to go to the folder they're in type "cd" then the directory)

---

### Post by STREETURCHINE on 2007-01-06
ah terminal i know what that is.  :-D 

dos'nt  look like that is the problem,so back to finding the answer to why i have lost the use of the net .

---

### Post by steve.horsley on 2007-01-06
Do **NOT** change the permissions of files outside your home directory. You will likely wind up having to reinstall everything. If you need to edit files outside your home folder (and you may in order to get nwtworking going), use **gksudo gedit filename** to borrow root's privileges, or perhaps **gksudo nautilus** if you are doing heavy rearrangements (be careful - you can trash the system).

Read this link for an explanation of root sudo: [http://help.ubuntu.com/community/RootSudo](http://help.ubuntu.com/community/RootSudo)

---

### Post by notepad on 2007-01-06
streeturchine the lock appearing on the files indicates that you dont have access to them. this is not the reason why your internet connection isnt working.
you should tell us some about your internet connection.

---

