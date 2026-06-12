---
title: "Hoary HEDGEHOG KERNEL"
date: 2005-09-06
forum: Absolute Beginner Talk
---

### Post by Nyati on 2005-09-06
I'm trying to create a customised kernel using the original Kernel from the 5.04 Release. The problem I'm having is, working from the steps out of Wiki I have to uncomment 2 lines of code in the source.list(the code appears to be links):

"For this procedure you must ensure that the following lines are uncommented in /etc/apt/sources.list:

deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main restricted
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) warty-security main restricted[/B]"

I don't seem to have/be able to access this list. This is what I did:

damuaskari@damuaskari:~$ l /etc/apt/sources.list.d/
bash: l: command not found
damuaskari@damuaskari:~$ ls /etc/apt/sources.list.d/
ls: /etc/apt/sources.list.d/: No such file or directory
damuaskari@damuaskari:~$ ls /etc/apt/sources.list
/etc/apt/sources.list

I have no idea, help...newbie!

---

### Post by Nyati on 2005-09-06
To anyone attepting to resolve this small gliche, I worked out that the solution is:

cat /etc/apt/sources.list (Many thanks to a clued up fella: jayeola)

This however presents another problem, that is editing the file ie: commenting out the #'s.

I presume I need to copy the text into a txt editor, but it appears to be read only?

Any suggestions?

---

### Post by TestDummy! on 2005-09-06
Run the text editor with sudo 

For example 

**sudo gedit /etc/apt/sources.list** 

You should be able to edit it without the read only restriction

---

### Post by Nyati on 2005-09-06
Great, thanks for the help!

---

