---
title: "File transfers over network"
date: 2007-05-21
forum: Absolute Beginner Talk
---

### Post by 1fastredsc on 2007-05-21
How can i transfer files from my PC to one that has windows over the network?

---

### Post by Jimmyfj on 2007-05-21
Hi

You should be able to do that through Samba on your GNU/Linux-box.

I get files from Windows-computers by Places/Network and, just as in Windows, by clicking my way toward the Win-drive I want to obtaine files from.

---

### Post by ruy_lopez on 2007-05-21
The easiest way would be to use SSH on the Ubuntu box and Putty on the Windows box. 

Get Putty here: [http://www.chiark.greenend.org.uk/~sgtatham/putty/](http://www.chiark.greenend.org.uk/~sgtatham/putty/)

Less trivially you could set up a samba share on the Ubuntu box and have windows mount the samba share. Its really not that difficult. But there are a lot of steps involved, and if you make a mistake its hard to debug. But if you are interested in using samba there's more here:

[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

I'd try Putty first.

---

### Post by 1fastredsc on 2007-05-21
Well i tried that and it couldn't connect to the pc for some reason. I got through the windows network part, but after clicking on MSHome i get the message "The folder contents could not be displayed" then under it "Sorry, couldn't display all the contents of "Windows Network: mshome"."

---

### Post by ruy_lopez on 2007-05-21
Did you enable sharing in Windows? Right click on the folder you want to share, choose the sharing tab, and check the box that says "Share this folder on the network" (WinXP). If this section is grayed out, you might have to disable the bit above, "Make this folder private."

---

### Post by 1fastredsc on 2007-05-21
Yeah i double checked that part too and enabled sharing of the hard drive on the windows PC, still no dice.

---

### Post by steve.horsley on 2007-05-21
The windows network browsing is still badly broken on Ubuntu (last time I looked - haven't even tried in Feisty). But it is real easy to open a connection from Ubuntu to a Windows share. Bang this into the address bar of nautilus:
**smb://domain;username@1.2.3.4/C$**
or similar. You can put this in a launcher entry if you use it frequently - the command in the launcher looks like:
**nautilus smb://domain;username@1.2.3.4/C$**

---

