---
title: "Unknown id:"
date: 2007-03-31
forum: Absolute Beginner Talk
---

### Post by Dakotakid on 2007-03-31
I'm trying to install the Nvidia drivers and I keep getting this error.

Unknown id: NVIDIA-Linux-x86-1.0-9755-pkg1.run

What does this mean?

---

### Post by johnc4510 on 2007-03-31
If you downloaded it to the desktop, you need to do this first before the sh command:

cd /home/your_user_name/Desktop

Your should now see something like this in your terminal:

johnc@Feisty:~$ cd /home/johnc/Desktop
johnc@Feisty:~/Desktop$ 

Now inter the sh command given at the nvidia web page where you downloaded from

---

### Post by Dakotakid on 2007-03-31
I gave that a try but I seem to be getting the same error. This is what it said.

na@na-desktop:~$ ls
Desktop  Examples  NVIDIA-Linux-x86-1.0-9755-pkg1.run
na@na-desktop:~$ sudo su NVIDIA-Linux-x86-1.0-9755-pkg1.run
Unknown id: NVIDIA-Linux-x86-1.0-9755-pkg1.run
na@na-desktop:~$

---

### Post by SIXAXIS on 2008-02-04
Does anyone know the answer to this? I have this exact same problem with the driver for the ATI Radeon XPRESS 200m.

---

### Post by sailtoad on 2008-03-01
I to have the same problem.  After going through the steps to prepare for the nvidia driver installation and attempting to install in terminal, I get the error:

user@user-desktop:~$ su NVIDIA-Linux-x86-96.43.05-pkg1.run
Unknown id: NVIDIA-Linux-x86-96.43.05-pkg1.run

I don't know what su is looking for.  The file is on my desktop.
Can someone help?

---

### Post by scrooge on 2008-03-25
The su command is used to switch users. So to become root you would type in 
$ su
and you'll be root, for any other user you type
$su *username*
and you are logged in as that user.

To install the nvidia file you either have to type
$ sh NVIDIA-Linux-x86-96.43.05-pkg1.run
or just
$ ./NVIDIA-Linux-x86-96.43.05-pkg1.run
probably as root, so it will really be
$ sudo sh NVIDIA-Linux-x86-96.43.05-pkg1.run
(I think both sh and ./ will work, it's been a while since I installed these drivers manually so I really don't remember.)

To clarify these commands: sh is a shell (the Bourne shell to be exact, normally you're running bash, the Bourne Again Shell), when you type sh *something* then *something* is executed. Typing ./*something* is almost the same, it executes *something* located in the current directory (which is the dot, as parent directory is two dots [..]).

I hope this helps.

---

