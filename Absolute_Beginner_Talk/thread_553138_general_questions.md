---
title: "general questions"
date: 2007-09-17
forum: Absolute Beginner Talk
---

### Post by phoenix24x on 2007-09-17
I think I can work around it, but as myself I cannot edit certain files although I have admin privileges; I don’t understand why?

as root I cannot access the gui? 

in a terminal window if i:

cd /etc

and then 

ls

i see all the directories/files and they are different colors why is this?

also in a terminal window if i:

cd /etc

and then:

ls /phpwiki

i get a "no such file or directoory," but if i:

ls /etc/phpwiki

it works...my question is why cant i ls straight to /phpwiki if i am already in the /etc directory?

---

### Post by ExSuSEusr on 2007-09-17
You tried gksudo nautilus in terminal?

---

### Post by nb123 on 2007-09-17
I don't think I understand your first question very well, but if you type  'sudo gedit (filename here) ' , you should be able to edit any file. 

As for your second question, just type 'ls \phpwiki' , i.e. with a forward slash, not a backslash. Hope this helps

---

### Post by bigboy_pdb on 2007-09-17
Which files are you not able to edit with administrative privileges? I'm guessing that the files are owned by root and they are probably set so that they don't have write permissions. If this is the case then you probably shouldn't be changing the contents.

**[EDIT]**After noticing something that I had previously missed in your post, I realized that you might be thinking that you've logged into GNOME desktop manager using root. This is not the case. The root account is disabled by default in Ubuntu. Two posts after this one I explained how to perform tasks as root.**[/EDIT]**

The colours are meant to provide information about a file without you typing "ls -l" to get it.

Grey is a regular file
Blue (dark blue) is a folder
Cyan (light blue) is a symbolic link
Green is an executable file (a file that has the execution bit enabled)
Red is a compressed archive that is recognized
Purple is an image format that is recognized

There might be other colours, but I can't think of them right now.

When you type "ls /phpwiki" you are telling the program "ls" to look for the folder "phpwiki" in the root directory not in the current directory (which is "/etc"). Remove the forward slash at the front so that it checks in the current directory.

---

### Post by bigboy_pdb on 2007-09-17
If you're looking at files that you've copied from a Windows partition or that were created by Windows, they might be green. I've noticed this with my files that were originally on an NTFS or FAT32 partition. For some reason Ubuntu copied all of the files and enabled the bit that indicates they are executable files.

---

### Post by bigboy_pdb on 2007-09-17
Sorry, I didn't notice your question about accessing the GUI as root at first.

In Windows, when an account is created, by default it is an administrative/root account. This is why so many people have problems with malware in Windows. When I used to use Windows, I didn't have those problems because I made one account for administrative tasks and another for everything else and I changed its type from "Administrative Rights" to "Limited Privileges".

In Ubuntu, you are not allowed to log in as the root user because it is a huge security risk and because you can corrupt your system if make a mistake using an account with root privileges. If you want to run a program from the command line as root you can append "sudo " to the front of the command. If you want to run a program with a GUI as root, either run the command from the command line or in the "Run Application" window (which can be opened by pressing ALT-F2) and append "gksudo " to the front of it. Some examples are as follows. If you want to see information on your partitions (which requires root privileges), from the command line type "sudo fdisk -l". If you want to open a file browser as root, type "gksudo nautilus" in either the command line or "Run Applications" window. If you want to edit a file as root while in the command line and in the directory the file is located in, use "gksudo gedit *filename*".

---

### Post by phoenix24x on 2007-09-17
thank you for your help..

it is all helping me get comfortable with the environment. 
:KS

---

### Post by oldos2er on 2007-09-17
> **phoenix24x said:**
>  in a terminal window if i:

cd /etc

and then:

ls /phpwiki

i get a "no such file or directoory," but if i:

ls /etc/phpwiki

it works...my question is why cant i ls straight to /phpwiki if i am already in the /etc directory?

 If you're already in /etc, you'd type "ls phpwiki" without the "/". "/phpwiki" causes bash to look in the root for phpwiki, and of course it's not there.

 The "Tab" key is extremely useful in the terminal; it gives file name completion ability.

---

