---
title: "HELP:  Made a HUGE ERROR with ROOT installing JAVA"
date: 2007-08-06
forum: Absolute Beginner Talk
---

### Post by bettyhills on 2007-08-06
After two days and many failed attempts, I finally figured out how to install JRE-6u2-linux-xxx.bin.  I needed the AMD64 version for two new linux boxes.   The java.com instructions would not work for me, so I used some from Snap Backup.

 The first installed flawlessly, but I got mixed up installing on the second and logged in as ROOT superuser.  Thus, all the instructions were followed from the root location.  The box squealed on reboot, but is up and running.  

I am attaching the instructions here in hope that someone can tell me how to undo this mess.  I did exactly as follows on the snapbackup instructions EXCEPT that I logged in as ROOT, so all actions occurred from root@linuxboxname:~$ instead of <username>@linuxboxname:~$

Here is what I did:

A: Install Java on Ubuntu
1) Go to the Java Download Page
Open [http://www.java.com](http://www.java.com) and click on Download NOW!  Now click the Download button for "Linux (self-extracting file)".

2) Save Installer to "~/apps/java" Folder
From the save window in your web browser, create a folder called apps in your home folder and then create a sub-folder within that folder called java.  Download the installer file to this new folder (/home/<username>/apps/java).

3) Launch Terminal
You need to run the Java installer from the command-line, which you access with Terminal.  In the Applications menu, go into Accessories and select Terminal.

4) Run Installer
From the Terminal, enter these commands: 
$ cd apps/java
$ ls -l
$ chmod +x jre*.bin
$ ./jre*.bin
$ ln -s jre*/bin bin

The chmod command makes the file executable so you can run it.  The ln command creates a symbolic link to the bin folder so it's easier to access.

5) Add Java to Your PATH
While still in the Terminal, enter these commands: 
$ cd ~
$ echo 'PATH=~/bin:$PATH' >> .gnomerc
$ cat .gnomerc
$ mkdir bin
$ cd bin
$ ln -s ~/apps/java/bin/java java

The echo command tells the GNOME desktop startup script to add your bin folder to the PATH.  The cat command displays the startup script so you can verify your update.  If the mkdir command reports that the folder already exists, that's ok.

6) Log Back On
Because the PATH variable is set on startup, you need to log out and then log back in for the Java installation to be complete.

___

Perhaps this is not a disaster?  Does it all need to be undone?  Just parts of the install?  Whatever...  please tell me what to do. Gently and step by step, please.

BTW I understand fully how dangerous it is to log in as root and would never have done it, except that the instructions at java.com said to do so during the install, and I got mixed up (forgetting I was no longer using those instructions) after so many attempts.

---

### Post by Jose Consuervo on 2007-08-06
I am not sure that this would be a problem. Have you tried using a java application since you installed the java?

---

### Post by bettyhills on 2007-08-06
Can you suggest an app to try?  (Apparently Firefox does not like Jre64.)

I am assuming that the software was installed with the **wrong permissions **and in the **wrong place**.

For example, at the root directory there now exists a bin directory with a broken link, owner = root. 

When I explore other software on this machine, it shows owner = <ownername> under permissions. Java components in the java directory show owner = root under Properties/permissions.  When I check out the java directory in the first linux box, all components show owner = <ownername>.  Does ownership affect the way software behaves?

Am I alarmed about nothing? 

If this were a Windows situation, MS would have put garbage all over my machine making cleanup impossible. 

Since this is Ubuntu, can I simply delete the java directory and re-do the install?

---

