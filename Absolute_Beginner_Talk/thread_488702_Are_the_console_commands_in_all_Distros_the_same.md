---
title: "Are the console commands in all Distros the same?"
date: 2007-06-30
forum: Absolute Beginner Talk
---

### Post by Xs1t0ry on 2007-06-30
Hi,

I was just wondering if the console commands in all distros of Linux were the same. I was led to believe they were but following a guide (aimed at Ubuntu users) to install ndiswrapper, my console (in Xubuntu) told me that 3 certain commands didn't exist. I don't know why a different Desktop Environment would changed the commands, so I'm asking this question. 
     Also, with a command like ```
 sudo apt-cdrom add 
``` the sudo is on the same line, right?

---

### Post by hyper_ch on 2007-06-30
Well, you have different shell... bash, dash, .... they may use different syntax and what also differs is how "root" is executed... in ubuntu you need to make use of the "sudo" command... in other distros you may be required to change your user to "root" and then run the commands without the "sudo"...

---

### Post by Vajra Vrtti on 2007-06-30
All GNU/Linux use the bash shell and so their line commands are the same. Ubuntu and Xubuntu are basically the same distro. What may happen is that you may have a package installed in one system but not in the other.
What are those 3 commands?

---

### Post by annda on 2007-06-30
also, all commands are basically programs and they mean "run this program now". some of them, like ls, touch, grep etc. are inbuilt in bash and common to all linux distros, unix and mac (although i believe they have modified a lot of the original unix commands). other things you type into the terminal invoke other programs. for example, apt-get & co. invoke a debian package manager. firefox runs firefox and so on. your success will depend on whether those programs are installed.

as to the difference between su and sudo (i think that is behind your question about sudo being on the same line): sudo is su for just the one command following it, so it is entered on the same line - but it remembers your password for a couple of minutes, so you don't have to type your password every time.

---

