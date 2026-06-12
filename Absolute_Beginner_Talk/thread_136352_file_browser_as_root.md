---
title: "file browser as root"
date: 2006-02-25
forum: Absolute Beginner Talk
---

### Post by talonsnow on 2006-02-25
*note: only started linux yesterday, so very new to the jargon

Here is the problem im encountering:
    I have enabled most all my drivers and learned how to install app's using synapsis. However, when i install a program, in this case TinyFugue, and then want to add a file or move a file into it's directoy I can't because of permissions, since it is owned by root. 
   It would make it easy for me at this point to be able to somehow use the file manager as root to gain access to things like /usr/share/games etc..  How is this possible?
   If I can't then I dont mind using command line, but I am failing in my attempts. I tried doing sudo cp <filename> /usr/share/games/tf/<filename> but it's not letting me. Thinking I have the directory structure wrong.

Any help is appreciated in advance ;)

---

### Post by Xian on 2006-02-25
Just issue this command from a terminal to use the Nautilus file manager with admin priviledges:

$ sudo nautilus

---

### Post by aysiu on 2006-02-25
Slight modification of the other answer: create a launcher with the command ```
gksudo nautilus
```

---

### Post by talonsnow on 2006-02-25
Thanks Xian,

 Worked perfectly!

---

