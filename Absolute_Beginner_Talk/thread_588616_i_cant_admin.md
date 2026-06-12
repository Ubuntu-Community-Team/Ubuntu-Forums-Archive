---
title: "i cant admin"
date: 2007-10-23
forum: Absolute Beginner Talk
---

### Post by TheSlayerIsBack on 2007-10-23
well i installed ubuntu and i made my accound and today i was trying to install my wireless card, and when i tried to extrac the exe file it gave me a access denied msg, and i tried to install a linux file aMSN which is a messeger for linux but it gave me the same message, and i think i might not be on an admin account, how can i get on admin account or how can i check

---

### Post by Crooksey on 2007-10-23
First off, linux dosent run .exe files.

Second, please open a terminal and type in "man sudo".

---

### Post by Maestro23 on 2007-10-23
> **TheSlayerIsBack said:**
> well i installed ubuntu and i made my accound and today i was trying to install my wireless card, and when i tried to extrac the exe file it gave me a access denied msg, and i tried to install a linux file aMSN which is a messeger for linux but it gave me the same message, and i think i might not be on an admin account, how can i get on admin account or how can i check

**sudo**

RootSudo: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by TheSlayerIsBack on 2007-10-23
> **Crooksey said:**
> First off, linux dosent run .exe files.

Second, please open a terminal and type in "man sudo".

yes i know that but a tutorial that i was using lets me install it but i keep getting access denied on the extracting point

---

### Post by bapoumba on 2007-10-23
The error messages could be helpful to help you out.

---

### Post by TheSlayerIsBack on 2007-10-23
> **TheSlayerIsBack said:**
> yes i know that but a tutorial that i was using lets me install it but i keep getting access denied on the extracting point 
ok let me get some stuff done and i'll boot linux up and get some screens of the error

---

### Post by TheSlayerIsBack on 2007-10-23
> **TheSlayerIsBack said:**
> yes i know that but a tutorial that i was using lets me install it but i keep getting access denied on the extracting point

i get this msg

[I]E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?[/I]

---

### Post by christianxxx on 2007-10-23
> **TheSlayerIsBack said:**
> i get this msg

[I]E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?[/I]

I got a similar error after my /etc/group file got messed up. Apparently, my user was no longer a member of the admin group, which made it impossible to perform admin-tasks, or even use sudo for anyting.
So you might want to check that.


Christian

---

### Post by aysiu on 2007-10-23
> **TheSlayerIsBack said:**
> i get this msg

[I]E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?[/I]
That message means one of two things:

1. You have two processes trying to access *dpkg* (Ubuntu's package management tool) at the same time. Only one process can use it at any given time. Examples of processes that use *dpkg* are the Update Manager, Synaptic Package Manager, Add/Remove, and gDebi.

2. You are not prefacing your command with *sudo*. So instead of doing ```
sudo apt-get install *ndiswrapper*
``` you're doing ```
apt-get install *ndiswrapper*
```

If you really believe you are not in the admin group, however, [this tutorial](http://www.psychocats.net/ubuntu/sudo) should help you fix that problem.

---

### Post by TheSlayerIsBack on 2007-10-26
> **aysiu said:**
> That message means one of two things:

1. You have two processes trying to access *dpkg* (Ubuntu's package management tool) at the same time. Only one process can use it at any given time. Examples of processes that use *dpkg* are the Update Manager, Synaptic Package Manager, Add/Remove, and gDebi.

2. You are not prefacing your command with *sudo*. So instead of doing ```
sudo apt-get install *ndiswrapper*
``` you're doing ```
apt-get install *ndiswrapper*
```

If you really believe you are not in the admin group, however, [this tutorial](http://www.psychocats.net/ubuntu/sudo) should help you fix that problem.

thanks man i got it working but i need a text editor to well edit some files but the text editor that comes with ubuntu doesnt paste what i copy, i'm using this command to copy he files and edit it, 

*cp /etc/ndiswrapper/bcmwl5/14E4:4324.5.conf /etc/ndiswrapper/bcmwl5/.conf*



but it wont open in the editor, and i was trying to install the nano editor and i DL it and try to install it and it opens like a folder and i dont know what to do

---

### Post by Maestro23 on 2007-10-26
> **TheSlayerIsBack said:**
> thanks man i got it working but i need a text editor to well edit some files but the text editor that comes with ubuntu doesnt paste what i copy, i'm using this command to copy he files and edit it, 

*cp /etc/ndiswrapper/bcmwl5/14E4:4324.5.conf /etc/ndiswrapper/bcmwl5/.conf*



but it wont open in the editor, and i was trying to install the nano editor and i DL it and try to install it and it opens like a folder and i dont know what to do

Use gedit.

> gksudo gedit .....

To install nano

> sudo apt-get install nano

Edit with nano:

> sudo nano ....

---

### Post by tw0shoes on 2007-10-26
It should come with a text editor called gedit 
cp is actually creating a physical copy of the file, not copying the contents of the file.

---

### Post by oldos2er on 2007-10-26
"cp" copies files on your hard drive, not to the clipboard. You can easily copy and paste text to/from the clipboard with your mouse in a terminal window.
 The nano editor is installed by default in Ubuntu.

---

### Post by TheSlayerIsBack on 2007-10-26
> **Maestro23 said:**
> Use gedit.



To install nano



Edit with nano:



well i got gedit to open the file but when i try to save it i get this msg
[IMG]http://i163.photobucket.com/albums/t313/madmike666/Screenshot.png[/IMG]

---

### Post by Maestro23 on 2007-10-26
Are you using** gksudo**, in front of gedit when you open the file?  It give you admin privileges.

---

### Post by TheSlayerIsBack on 2007-10-26
> **Maestro23 said:**
> Are you using** gksudo**, in front of gedit when you open the file?  It give you admin privileges.

i dont know what to do that

---

### Post by Maestro23 on 2007-10-26
> **TheSlayerIsBack said:**
> i dont know what to do that

Put the command **gksudo** in front of gedit when you go to edit a file.

> gksudo gedit /path to filename

---

### Post by TheSlayerIsBack on 2007-10-26
> **Maestro23 said:**
> Put the command **gksudo** in front of gedit when you go to edit a file.

ok thanks man it worked

---

