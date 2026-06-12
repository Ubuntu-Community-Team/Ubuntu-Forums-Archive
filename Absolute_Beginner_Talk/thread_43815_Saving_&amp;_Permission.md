---
title: "Saving &amp; Permission"
date: 2005-06-23
forum: Absolute Beginner Talk
---

### Post by focuz on 2005-06-23
Hi there,

I have being trying to save screen shots of the Ubuntu interface using 'The Gimp'. However, I want to save the file on either my removable drive (pen drive) or my hard drive on the computer.

When I attempt to do this I receive an error that explains I do not have permissions or the correct rights to do this.

I'm not extremely familiar with Linux based systems and therefore aren't too sure how to handle this. I looked at the properties on the removeable drive folder and there check boxes were selected - Read, Write and Execute.

Hope someone can help,

Regards,

J

---

### Post by frodon on 2005-06-23
can you post your /etc/fstab file ?

---

### Post by focuz on 2005-06-23
I'm sorry to appear ignorant, but what is this file? The problem I face is that I use Ubuntu from bootable disc and therefore can't copy this file if that's what you meant. Can't copy this file to a removable device either!

Jamie

---

### Post by equal on 2005-06-23
Hey , I'm pretty new here, and I had a similar problem a few days back. Here's a copy/paset of the response I got, it helped me:

In Ubuntu, you run the OS as you- a normal user. Unlike most Windows installs, the main user does not have root priviledges in Ubuntu. This is to avoid a major problem in Windows- programs installing without the user knowing. Plus it makes it harder to mess things up.

I bet you are thinking "whats the point of NO admin account?"The answer is that Linux's multi-user set up is VERY elegant. At any time you- a normal user- can become an admin with two commands:

"sudo" for commandline apps.

"gksudo" for graphical apps. 

Lets say you wanted to fix that problem- you wanted to browse the file manager as the admin. run this command:


> gksudo nautilus  


now you have the power. Notice how it asked for you password. That is the big security feature. Macs do the same thing. If you ever are doing something that shouldn't need be admin to do (say surf with Firefox) and its asks for a password you then KNOW that something fishy is going on. 

With this protection, malware on Ubuntu may never exist.

---

### Post by frodon on 2005-06-23
[QUOTE=focuz]I'm sorry to appear ignorant, but what is this file? The problem I face is that I use Ubuntu from bootable disc and therefore can't copy this file if that's what you meant. Can't copy this file to a removable device either!

Jamie[/QUOTE]

sorry, my answer was to quick !

the fstab file specify all the devices to be mounted when you boot on ubuntu, it also mount your hard drive and specify mask and permission, you can set in the permission field to allow user to write data on hard drive.
Indeed you can use sudo to write but isn'it easier to allow users to  write on hard drive.

open a terminal and use this line to open the file : ```
gedit /etc/fstab
``` then copy and paste here the content of the file.

---

### Post by poofyhairguy on 2005-06-23
its not the best solution, but starting the gimp this way from the commandline:

> gksudo gimp

should clear up any permissions issues.

---

### Post by focuz on 2005-06-24
Just to inform you that the issue has now been rectified. The problem was not resolved, but I used an alternative way to obtain the information that I required.


Thanks to everyone for their input on this thread.

Regards,

Jamie

---

