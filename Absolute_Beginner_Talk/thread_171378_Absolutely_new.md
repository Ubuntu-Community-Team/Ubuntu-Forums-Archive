---
title: "Absolutely new:"
date: 2006-05-06
forum: Absolute Beginner Talk
---

### Post by cgeyik on 2006-05-06
Im triying to install vmwaretools in my ubuntu virtual desktop but it seems i dont have the rights. the icons of vmwaretools have slot and a pointer pointing to the upperleft corner.

I dont know what this means.

And may i get the answer: how do i log in as root

---

### Post by gr0kzer0 on 2006-05-06
If you go to a terminal and type ```
sudo passwd root
``` that'll set a password for root so you can login as root in a console.

But in Ubuntu it's set up to use the sudo command instead of logging in as root. This means you type the word "sudo" before the command you want to run as root. Ubuntu asks for your user password, then runs the command with root privileges. This saves you messing your system up by mistake as root.

---

### Post by cgeyik on 2006-05-06
yep it worked

but why cant i log in from the log-in screen....i need to do that so i can make a folder within the bin folder.

---

### Post by mostwanted on 2006-05-06
DON'T LOG IN AS ROOT! (in all caps for your viewing pleasure)

It is not needed *at all*.

[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

