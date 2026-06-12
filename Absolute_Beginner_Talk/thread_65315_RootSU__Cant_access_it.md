---
title: "Root/SU ? Cant access it?"
date: 2005-09-13
forum: Absolute Beginner Talk
---

### Post by dragge on 2005-09-13
Ok... im new to Ubuntu and havent been using linux for quite some time so bare with me.

During the install of ubuntu i did create a user and set a passwd for it, but no root pwd?

now i need to mount some drives and so on with root/su and not my "normal" user but i have no password for the root/su . How can i login with root when i dont have a password for it?

---

### Post by sethmahoney on 2005-09-13
Ubuntu doesn't use root accounts.  To access something that requires root privileges, type sudo before it:

sudo mount whatever

It will ask for your password, just enter your normal user password.

---

### Post by djib on 2005-09-13
[QUOTE=dragge]Ok... im new to Ubuntu and havent been using linux for quite some time so bare with me.

During the install of ubuntu i did create a user and set a passwd for it, but no root pwd?

now i need to mount some drives and so on with root/su and not my "normal" user but i have no password for the root/su . How can i login with root when i dont have a password for it?[/QUOTE]
 Hello,

In ubuntu you do everything with 'sudo'.
If you really want a root access, you can type in "sudo konsole" or "sudo -s /bin/bash" or something like "sudo -s -h" (not sure...)
You can also enable root access (but I don't think you should) with sudo -s passwd.

When you are asked for a password, it is always your user password.

---

### Post by red_Marvin on 2005-09-13
You can get root access by typing su and then entering the root password
sudo desn't need the root bassword it seems, but your own.

But there is a root user login and you can change the password in the user control
panel (only if you have administrative rights AFAIK) this is needed because the root 
password is randomized by default I think.

To be able to login as root at the login screen you have to check that option
in the login configuration panel.

---

### Post by dragge on 2005-09-13
Ok... ive gotten so far that i have made a mount point and trying to mount the hard drive but get this error:

" Failed to run disks-admin as user root:
Child terminated with 211 status"

now why is that? :(

---

### Post by Nequeo on 2005-09-13
[QUOTE=dragge]Ok... ive gotten so far that i have made a mount point and trying to mount the hard drive but get this error:

" Failed to run disks-admin as user root:
Child terminated with 211 status"

now why is that? :([/QUOTE]
 No idea! :)

What command did you type to get that error message?

---

