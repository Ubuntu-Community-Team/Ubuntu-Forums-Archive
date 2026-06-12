---
title: "Locked folder on Desktop; can't delete"
date: 2007-05-27
forum: Absolute Beginner Talk
---

### Post by mrmark24 on 2007-05-27
Hi everyone,

I'm new to Ubuntu, just having recently switched from Mepis Linux for various (none negative) reasons.  I had been told about how great Ubuntu is and how easy it is to operate and, for the most part, this has proven to be true.

I had been trying to install a modem in my computer, and I'd tried four different modems and downloaded drivers for all, and all but one worked; unfortunately, it was the "last" one!  (On a side note, installing modems on Linux really is like PULLING TEETH!!!)

Anyway, here's my problem: I downloaded the latest known working PCtel modem driver's tar.gz file, and tried it out, yada, yada, yada.  Well, that modem didn't work (an older Conexant using Linuxant drivers ended up working for me), but the folder that was untarred, or whatever it's really called, to my desktop has a little picture of an encircled lock at the top right of the icon, and I cannot delete it.  When I right-click on the folder icon and select properties, then go to the permissions tab, it says "Owner: 500" and also says I'm NOT the owner, so I cannot change these permissions.  Does anyone know what "Owner: 500" means?  And how do I get rid of this pesky little folder!?!

thanks,
mrmark24

---

### Post by taurus on 2007-05-27
Run nautilus with root privilege to remove it.

Applications -> Accessories -> Terminal
```
gksudo nautilus
```
Or post the output of this command here, from a terminal.

```
ls -la ~/Desktop
```

---

### Post by mrmark24 on 2007-05-27
taurus,

I tried using the Nautilus program, but couldn't find the file because it was logged into root, and I don't know how to find the files of specific users from there.

Here is the output from the second terminal post you showed me:

drwxr-xr-x  3 sari sari  4096 2007-05-27 15:37 .
drwxr-xr-x 37 sari sari  4096 2007-05-27 15:37 ..
-rw-r--r--  1 sari sari  2698 2007-04-10 10:10 gnome-sudoku.desktop
-rw-rw-rw-  1 sari sari   654 2000-01-06 11:09 ltinst~
-rw-r--r--  1 sari sari  7716 2007-04-10 20:54 ooo-writer.desktop
drwxr-xr-x  4  500 staff 4096 2007-03-10 12:21 pctel-0.9.7-9-rht-7
-rw-r--r--  1 sari sari  6473 2007-04-10 10:10 sol.desktop

Now when I look at the actual screen, the "pctel-0.9.7-9-rht-7" file is blue colored, and the rest are black.  And on top of it saying "500" for the owner, it says "staff" to the right of it.  What could that mean???

Thank you for your prompt response.  Also, I see you live in Jacksonville.  I live down in St. Augustine ;)

mrmark24

---

### Post by mrmark24 on 2007-05-27
taurus,

Oops.  Nevermind.  I "did" find the individual users in the "/home" folder of "root," and it let me delete it.

I would like to know how so many users are so darned knowledgeable when it comes to Linux?  Once I learn something, it tends to stick.  The learning process, on the other hand, can be quite tedious!!!

Thanks again for the help.

mrmark24

---

### Post by taurus on 2007-05-27
If you run "gksudo nautilus", you need to navigate over to /home/sari/Desktop.  However, I assume you want to remove the pctel-0.9.7-9-rht-7 directory in /home/sari/Desktop, right?

```
cd ~/Desktop
sudo rm -rf pctel-0.9.7-9-rht-7
ls -la
```

p.s.  Got any rain down there you end?

---

