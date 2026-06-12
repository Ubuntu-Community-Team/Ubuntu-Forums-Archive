---
title: "[SOLVED] file sharing on windows pc not working right"
date: 2008-02-17
forum: Apple Intel Users
---

### Post by psfelgate on 2008-02-17
Hi, I am having a problem trying to setup a file share. I have 2 pc's and a laptop. The 2 pc's are running windows vista and the laptop is running ubuntu.

There is a shared folder on the 1st pc that I would like to access from the laptop. It is working fine if I access it from the other vista pc, but I get the following problems when trying to access it from the laptop:

First I click on places... connect to server... and type in the name of the pc and the share and click connect. It creates a new folder on the desktop with the name of the pc. I then open the folder and it views all the shares on the pc witch is good. I can then open one of the shares and view all the folders inside but - as soon as I try to open a subfolder it will say "nautilus cannot open smb://pc-name/share/folder, please select another viewer and try again.

At this point after I click ok, the same folder that I tried to open icon will change into some blank file instead of the normal folder icon. If I click refresh that same folder dissapears and if I click refresh again then it comes back again as a folder icon but the same thing happens when I try to open it again.

Please help me

---

### Post by cyberdork33 on 2008-02-17
I have always had trouble using the samba bowser in nautilus. Try mounting the share in the filesystem. 
[http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534)

---

### Post by psfelgate on 2008-02-17
Excellent! It is working 100% now. Thank you so much.

---

