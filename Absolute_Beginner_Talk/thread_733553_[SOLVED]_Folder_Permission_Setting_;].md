---
title: "[SOLVED] Folder Permission Setting ;]"
date: 2008-03-23
forum: Absolute Beginner Talk
---

### Post by hungryOrb on 2008-03-23
So, ye, this is old I know. But I've read through a bunch of posts, and can't find the exact help I wanted. 
I'd like to edit my boot list, but upon saving, I'm told I dont have the priveleges. I'm wondering how to pass all permissions to my user for all time :)
Thanks for any help

---

### Post by Belliinator on 2008-03-23
As far as i know you can only edit the boot list if you run gksudo nautilus and find it. I dont think you can permanantly allow admin priveledges to a folder or user, but if you can I dont reccommend it.

---

### Post by smartboyathome on 2008-03-23
Actually, just do gksudo gedit and then open it. This is more direct, and has less dangers of deleting something important etc.

---

### Post by Belliinator on 2008-03-23
Even better
```
 sudo gedit /boot/grub/menu.lst

```

---

### Post by gorf 99 on 2008-03-23
What I do is: open Terminal and a Browser window side by side

In the Browser window go to [computer>filesystem>boot>grub].  You should see menu.lst file

In terminal type sudo gedit  

then drag the menu.lst and hit enter

It will ask for the admin password and open your boot loader in gedit.  Then you should be able to edit it and save it.  It saves the old menu.lst as menu.lst~ (that is a hidden file)

Hope this helps

---

### Post by smartboyathome on 2008-03-23
Please use gksudo for graphical apps instead of sudo, for there could be potential problems with sudo and a graphical app.

---

### Post by hungryOrb on 2008-03-23
Thankyou guys, those answers were all I hoped for :] <3

---

### Post by Belliinator on 2008-03-23
Mark the thread as solved

---

