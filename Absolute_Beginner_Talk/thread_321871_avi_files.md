---
title: "avi files"
date: 2006-12-19
forum: Absolute Beginner Talk
---

### Post by huviduc on 2006-12-19
everything used to work fine when i double clicked an avi file it wold open up and play. I was not happy with the totem player so i went ahead and did some searching and got VLC player and kaffiene. I uninstalled VLC and kept kaffiene, but when i double click the avi file, i get a strange error :
Cannot open The.Devil.Wears.Prada[2006]DvDrip[Eng]-aXXo.avi
The filename "The.Devil.Wears.Prada[2006]DvDrip[Eng]-aXXo.avi" indicates that this file is of type "avi document". The contents of the file indicate that the file is of type "AVI video". If you open this file, the file might present a security risk to your system.

Do not open the file unless you created the file yourself, or received the file from a trusted source. To open the file, rename the file to the correct extension for "AVI video", then open the file normally. Alternatively, use the Open With menu to choose a specific application for the file. 

how can i fix this problem? also, after i uninstalled VLC with synaptic, it still shows up on the open with list, but it does nothing when clicked, did it not uninstall correctly?

---

### Post by huviduc on 2006-12-19
P.S. all other files open correctly. and i went to properties and it is set to open with kaffiene. but it gives me the same error no matter what player i set as default. thanks

---

### Post by antofthy on 2008-07-01
I have been battling this problem for years, on and off. but no one seemed to have an answer.   However I have now finally found the solution in a 'fedora' forum.

The problem is that you personal 'mime' settings do not match the system mime settings.  I have no idea what cases this but it screws up my thumbnails and double-left clicking of AVI documents.  The solution is simple.
```
rm ~/.local/share/mime/globs
```
Now logoff and log back in.  Suddenly AVI's and even AVI thumbnailing is working properly!!!  :D

If this does not work you can also try running
```
update-mime-database /usr/share/mime
```
as the root user.   I myself did not need this.

PS: AVI thumbnailing in Fedora requires the "totem-xine" package from the livna repository.  No idea about this in Ubuntu.

---

