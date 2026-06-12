---
title: "Wine question"
date: 2006-06-27
forum: Absolute Beginner Talk
---

### Post by underworld288 on 2006-06-27
I installed Wine, then I installed Steam the only problem is that I cant seem to find the installation folder or how to open Steam. Can anyone lead me in the right direction.

---

### Post by dtfinch on 2006-06-27
Go to you home folder in nautilus. Press ctrl-h. You should find a .wine folder, and a drive_c folder under that.

---

### Post by underworld288 on 2006-06-27
nope, its not there.:confused:

---

### Post by underworld288 on 2006-06-27
maybe i dont have wine installed correctly? But in that case i shouldn't have been able to install Steam, right.

---

### Post by Apple 101 on 2006-06-28
The .wine folder is hidden.  You will need to configure wine first.  Open a terminal shell.  Type *sudo winecfg* and configure wine to your needs.  Then you can *cd /home/<your username>/.wine/drive_c* to get to your wine C:\.

---

### Post by underworld288 on 2006-06-28
ok i had to reinstall Ubuntu, dont ask why, but I installed wine and now when i try to install steam i get this error....

"Could not initialize installation. C:\windows\temp\GKC1bc.tmp File not found"

i dont know what to do, could any of you help me?

---

### Post by underworld288 on 2006-06-28
someones gotta know whats wrong.

---

### Post by richbarna on 2006-06-28
[QUOTE=underworld288]someones gotta know whats wrong.[/QUOTE]

I had problems with the repo version, so i did this :-

[http://www.ubuntuforums.org/showthread.php?t=149585&highlight=howto+install+wine]("http://www.ubuntuforums.org/showthread.php?t=149585&highlight=howto+install+wine")

---

### Post by underworld288 on 2006-06-28
well I used that guide and when I try to install DCOM98 a window pops up and says "OK to install DCOM98 for Windows 98" then I click "yes" then the license aggreement pops up I click "yes" then nothing (but when I look at the konsol it says "waiting for wineserver to exit..." but i wait and after 600 seconds a message pops up saying that winetools is still running you can exit out of it by typing wineserver in the konsol. I dont know what to do I need to install DCOM98, can anyone find out how to overcome this problem?

---

