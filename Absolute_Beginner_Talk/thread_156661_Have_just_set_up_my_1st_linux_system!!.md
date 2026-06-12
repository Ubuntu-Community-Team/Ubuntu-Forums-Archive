---
title: "Have just set up my 1st linux system!!"
date: 2006-04-07
forum: Absolute Beginner Talk
---

### Post by alexukalex on 2006-04-07
Hi everyone. I thought I'd just introduce myself as a complete Linux newbie BUT... I've just finished setting up my laptop with UBUNTU and am really enjoying the whole process.
Having tried SUSE, RED HAT and FEDORA and Mandriva with limited success I was about to throw in the towel when I stumbled across Ubuntu. Well one last try I thought, and installed it on my laptop. Great install routine, and after a bit of tinkering finally managed to get my THOMSON SPEEDTOUCH modem up and running, my floppy drive working and access to ROOT sorted.... So it can be done (and I'm a complete I.T. MUPPET8-[ ) ANYHOO... I'd be grateful if some kind person could answer my (probably ssshhtuooopid) questions...
1) Why (unlike other distros) do you create a user account in Ubuntu but not a ROOT account? (I had to tinker around with account passwords to set up a fixed password for root)
2) Why did I have to tinker with Ubuntu to get the floppy drive working? (I could format a disk in it but couldnt mount the drive).
and 3) How do I go about defragmenting my drive with Ubuntu ? (or is that just a Bill Gates type of thing?!)
Anyway.... I am truly hooked on Ubuntu now and am very keen to learn about Linux.... I was only able to get my modem going, my root account sorted and my floppy drive working by following step by step guides off the net... so a lot to learn.......
All the best
alexukalex

---

### Post by aysiu on 2006-04-07
[QUOTE=alexukalex]
1) Why (unlike other distros) do you create a user account in Ubuntu but not a ROOT account? (I had to tinker around with account passwords to set up a fixed password for root)[/quote] Let's turn that question around--why do you need a separate root account? Mac OS X and Ubuntu user the *sudo* model, and it makes a lot more sense. Read more here:

[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

> 
2) Why did I have to tinker with Ubuntu to get the floppy drive working? (I could format a disk in it but couldnt mount the drive).
and Because your hardware wasn't designed for Ubuntu. It was probably designed for Windows. It's a miracle Ubuntu works as well as it does on so many systems. > 3) How do I go about defragmenting my drive with Ubuntu ? (or is that just a Bill Gates type of thing?!) You don't need to.

---

### Post by alexukalex on 2006-04-07
Hi,
thanks for the link... useful stuff.
re sudo: as I am really completely new to linux I found that using the gui was easier to navigate around and find files to edit or to right click and select run in terminal (to install)... so I created a Root account as some of the files were hidden in my user account. I know that Linux is much more secure with the terminal and Sudo approach.
Glad to hear that the old defrag is not necessary.
Re floppy: its working now and it was fun to get it going.
Another point about Ubuntu is that it accepted my USB memory pen with no problems at all (unlike some of the other distros I tried earlier). It does seem that Ubuntu is the perfect mix of newbie friendly with options available to you more experienced users.
I'll be loading it on my desktop next I think....

---

### Post by aysiu on 2006-04-07
[QUOTE=alexukalex]
re sudo: as I am really completely new to linux I found that using the gui was easier to navigate around and find files to edit or to right click and select run in terminal (to install)... so I created a Root account as some of the files were hidden in my user account. I know that Linux is much more secure with the terminal and Sudo approach.[/QUOTE] You should create a launcher then. It's easier than logging out of user, logging in as root, making changes, logging out of root, and then logging back in as user again.

Create a launcher you can click on. For the title, use *Browse as Root*. For the command, use ```
gksudo nautilus
``` if you're using Ubuntu or ```
kdesu konqueror
``` if you're using Kubuntu.

Read more here:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by Sef on 2006-04-07
> 2) Why did I have to tinker with Ubuntu to get the floppy drive working?

There is a bug in Breezy that is fixed in Dapper.

---

### Post by alexukalex on 2006-04-08
Aysiu: Thanks for the tip about a Root Launcher... y'see its easy when you know how! Great help.
Sef: Thanks for the info, thought I'd done something wrong:roll: 

As I said before, I'm very new to Linux but would like to start to learn more about Linux "under the hood".
Can anyone recommend a particular programming language that I could start to learn??? One that would be of most use with Linux in the future?
It'd be great if I could write my own app in the future......[-o<

---

### Post by dvarsam on 2006-04-08
[QUOTE=alexukalex]As I said before, I'm very new to Linux but would like to start to learn more about Linux "under the hood".
Can anyone recommend a particular programming language that I could start to learn??? One that would be of most use with Linux in the future?
It'd be great if I could write my own app in the future...[/QUOTE]

Start with the basics!!!

Learn how to make "scripts" & if you would like to create a nice looking Web Page, learn "PHP" & "MySQL".

---

### Post by alexukalex on 2006-04-08
Thanks dvarsam, will have a look at PHP & MySQL

---

