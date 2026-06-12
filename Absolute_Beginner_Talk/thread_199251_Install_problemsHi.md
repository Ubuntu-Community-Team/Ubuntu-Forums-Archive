---
title: "Install problemsHi"
date: 2006-06-18
forum: Absolute Beginner Talk
---

### Post by niteblind on 2006-06-18
Hi all,

I am a little confused. i am trying to install programs. I download the binary file to my desktop and i have been advised to extrace them to usr/local/bin folder. Every time i try to extract to this location i get an error telling me i do not have the correct permissions.

So what do i do? i have been told to use sudo to extract but i have no idea how. is the above location the best place to be putting these things anyway?

---

### Post by Rui Pais on 2006-06-18
hi,
what kind of programs are you talking about (you speek like a MS Window user ;))

Here, either you want a program from the Ubuntu Repository and just do on a command line:
sudo apt-get install *program_name_i_want*

or, RECOMENDED, use synaptic that is a graphical interface for the above, try 
sudo synaptic 

or search for synaptic entry in the menus.

If you are talking of some program you get from the internet that are not in repo, you probabilly need ot compile them... a more complicated thing, or install a binary packet... but i don't think you are talking of this, so

hope that helps

---

