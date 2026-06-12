---
title: "How Do I Update Eclipse to 3.2?"
date: 2006-09-16
forum: Absolute Beginner Talk
---

### Post by groberts1980 on 2006-09-16
I have Eclipse 3.1.2 installed, and I just downloaded and unpacked the tar file containing Eclipse 3.2. The unpacked Eclipse folder is sitting on my desktop.

When I originally installed Eclipse, I used Synaptic, but 3.2 is not listed in Synaptic, which is why I downloaded the tar.gz.

How do I update my installation of Eclipse to the new version? The launcher for Eclipse in my Applications menu shows a file in /usr/bin, but its just a shell script. Synaptic shows the old version installed in /usr/share/eclipse, and a few other folders.

Will replacing the folder /usr/share/eclipse with the new eclipse folder on my desktop work? How should I go about updating my version of Eclipse?

---

### Post by baldy1324 on 2006-09-16
ok you installed eclipse by using apt, which uses ubuntus repositories of packages. so just run ```
sudo apt-get update && sudo apt-get upgrade
``` this will upgrade all the packages on your system:)

---

### Post by Anduu on 2006-09-16
> **groberts1980 said:**
> I have Eclipse 3.1.2 installed, and I just downloaded and unpacked the tar file containing Eclipse 3.2. The unpacked Eclipse folder is sitting on my desktop.

Will replacing the folder /usr/share/eclipse with the new eclipse folder on my desktop work? How should I go about updating my version of Eclipse?

No you cant just replace files...

What you have downloaded/unpacked is the source which must be compiled/installed manually.

So you have 2 options:
1. Wait for the version in the repos to be updated(your best bet...)
2. Compile/install yourself(not newbie friendly...no insult intended ;) )

If you want to try to compile/install yourself see here for details...
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by groberts1980 on 2006-09-18
What I downloaded and unpacked is the actual program, not source code. I unpacked the tar.gz file on the desktop, which put a folder on the desktop. I can open that folder and run Eclipse 3.2 from there.

I guess I was asking if I can replace the eclipse folder that Synaptic put there, and the launcher in Applications would just run the new version.

Here's a (somewhat) unrelated question. Before I downloaded Eclipse 3.2, I created a folder, and created a new file, named it whatever.c. Opened it up in gedit, typed up a C program. I'm able to go into that folder and compile and run the program. Once I got Eclipse 3.2 set up with the C/C++ development options, I created a project for the file, dragged and dropped the .c file onto thep project. Now, when I go to the command line, navigate to workspace/project, I can't run the file. I can compile it, but when I try to run it, it says "permission denied." I did a "sudo cmhod 777 project.c", and then it says "cannot execute binary file."

What's the deal there?

---

