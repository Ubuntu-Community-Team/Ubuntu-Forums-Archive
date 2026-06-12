---
title: "can't change any file associations"
date: 2007-05-27
forum: Absolute Beginner Talk
---

### Post by obb2007 on 2007-05-27
when i click on open with, i cant change the default application to open the file with. i have all the permissions and i'm in the root group. i can do it if i log in as root, but when i return to my user it doesnt change. please help. thanks

---

### Post by throntax on 2007-05-27
Are you using Gnome or KDE? Sometimes it asks you to find a file rather than show a list of programs, so you have to know where the program file is...

---

### Post by obb2007 on 2007-05-27
i use gnome and the program is on the list. but nothing happens when i click it. it won't change. it's very frustrating

---

### Post by throntax on 2007-05-27
I know you should have to use the terminal, but open it up and type the program name and then the file name. There may be some problem between them that has an error message...

---

### Post by obb2007 on 2007-05-27
no error massages at all. it just won't let me change the default open with program. i created a new user and it's working. thats the only solution i could find but now i have to define everything again.

---

### Post by Bluecircle on 2007-06-13
Right click on file -> properties, select "open with" tab, there are all programs that will read the file extension, then pick the one you want and apply. A file is always assigned to a default program, if you want to just open it seperately this time click right click and choose "open with..." then select your choice.

Make sure you are doing this with a file you own and have permissions for. Ex: a file in your home directory. If you login or change it as root, the settings will only be changed for the root user.

---

### Post by bobbob1016 on 2007-06-19
I have the same issue.  When I try to change the default in the Open With tab it still doesn't let me select anything else.

---

### Post by Radicc on 2007-06-22
I too have this same problem.  
Right click my file on the desktop. 
Select the open with tab.
Try to select one of the other options to open the file with, but it won't let me.
In my case I was trying to change my music player to beep.  Its on the list but when I try to pick that option the radio dot won't move there.  I don't remember having any trouble with this before I upgraded to 7.04.  I assume it probably has something to do with messed up permissions on the file association, but I haven't been able to find which file that is.  

I don't know about you but I much rather open my musc files with beep than with movie player.

Thanks for any help that anyone can provide.

edit -- Using gnome btw.

---

### Post by phr0ze on 2007-06-22
start nautilus or whatever with gksudo and try this again. Once it's set, close the gksudo nautilus.

---

### Post by Radicc on 2007-06-23
> **phr0ze said:**
> start nautilus or whatever with gksudo and try this again. Once it's set, close the gksudo nautilus.

This did allow me to change the option but it only worked for root and not my user account.

---

### Post by Radicc on 2007-06-24
Well looks like this is a gnome problem.  Hopefully they sort it out in the future.   I  did however find the file names I was looking for to change the default.
Depending on what you are trying to do you need to change one of these files:
/usr/share/mime/packages/freedesktop.org.xml
/usr/share/mimeinfo.cache
/usr/share/applications/mimeinfo.cache
/usr/share/applications/defaults.list

My issue was fixable in the /usr/share/applications/defaults.list file.  Still can't change it the easy way but at least I can change it.

Hope this helps someone else out.

---

