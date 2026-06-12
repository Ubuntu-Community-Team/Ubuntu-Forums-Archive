---
title: "USB thumb drive"
date: 2008-04-20
forum: Absolute Beginner Talk
---

### Post by nishanthgc on 2008-04-20
Hi ppl ,
     I am having trouble mounting a usb drive on thin clients in edubuntu ...
but i am having no trouble mounting the same usb drive opn the server though ..
if someone can help me out on how to mount on thin clients that will be more than helpful

--NC

---

### Post by Rocket2DMn on 2008-04-20
If the thin clients do not allow for root privileges with regular users (or perhaps don't have HAL setup to automount), you can try installing a program called pmount, it is available from the repos and allows you to mount without root permissions.

---

### Post by nishanthgc on 2008-04-21
pmount is already installed on the system

---

### Post by timcredible on 2008-04-21
does your thin client allow for local usb on the thin client, or is it only allowed on the host?  some of them only look at the mouse, keyboard, and monitor on the client.

---

### Post by nishanthgc on 2008-04-22
hey the mouse keyboard are not connected through the usb drive they are connected normally 
and i have checked the repositories pmount is already installed on the server 
is there anyother solution for using flash drives on the clients

---

### Post by Rocket2DMn on 2008-04-22
What happens when you try to mount it using the mount or pmount command?
Plug one into a thin client and post
```
dmesg
lsusb
sudo fdisk -l
```
With that information I will give you the mount command(s) to try.

---

### Post by nishanthgc on 2008-04-23
Hi i have just checked up eduubuntu documentation ltsp 4 doesnt support local block mounting on thin clients guess i have to upgrade

---

