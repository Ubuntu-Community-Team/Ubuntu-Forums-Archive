---
title: "Help with Keyboard Shortcuts for student set up"
date: 2007-10-23
forum: Absolute Beginner Talk
---

### Post by rcsfloater on 2007-10-23
We're setting up a student computer in our school, and we want to lock down student activity to just browsing the web. The computer is running ubuntu 7.04. I have set up opera web browser since I noticed it had a built-in kioskmode that seemed to do what we at the school were wanting it to do. I'm going to make a start up script to execute opera at login. 

My question is the keyboard shortcuts...

I read an article about how to disable the ctlr + alt + backspace and was able to turn that off.
The problem I'm having is finding how to disable the other keyboard shortcuts within ubuntu. I don't want the students to have any access to any files or a way to get onto our network at all. That is why we are wanting to disable all keyboard shortcuts completely.

How do I go about doing this? Is there a file or GUI I can edit to make this happen? And am I approaching this the best possible way with locking down student permissions? I wasn't sure of other options, but I look forward to seeing what you guys have to suggest I do here. Thanks!

---

### Post by Griffiss on 2007-10-23
For disabling the global shortcuts, you can get gconf-editor

open it, then go to 'Apps->Metacity->Global Keybindings'

and disable all the commands.

I think that'll do it.

Don't know if this will really 'lock down' the system though.

---

### Post by rcsfloater on 2007-10-24
Ok, I'm scratching the kiosk concept. I've decided just to create an underprivileged student log in account with about everything I can disable taken off. I was able to disable those gloabl keys like you mentioned. However, I can still ctrl + o and find files. I really need to cut off any possible way for the students to just browse the file system and/or the network. Not sure if there is a way to do this or not. Any suggestions?

---

### Post by Griffiss on 2007-10-24
You should be able to change the permissions settings on admin folders so that only the root user can view them. (gksudo nautilus in terminal then right-click on the folder and set the permissions)

But why do you want the students to not even *see* the files? they won't be able to write or execute the files owned by root anyway, and they may learn something if allowed to explore...

---

