---
title: "FTP Problem"
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by azarius on 2007-06-11
Im using pro FTP i got it installed, working fine, set all the permissions, except when i put the files in the folder none of the files are able to be downloaded, i keep getting permission denied, i  changed the permisson on the folder to 777 but every file in the folder did not change i can download the folder but when it gets to the files in the folder it says permission denied, is there a way to set all the files in the folder to 777 at the same time, should i have to do this. or did i do something wrong i followed the instructions on this forum on how to set it up.

---

### Post by azarius on 2007-06-11
i got it just has to modify the proftpd.conf file and all is good

---

### Post by DBStevens on 2007-06-11
From a teminal session one level above the directory structure you wish to make world accessable (note I do not recommend doing this)

chmod -R 777  directory/ 

will make every single entry in directory and all enties below it open to all for all operations.   I can assure you that you really do not want to do this as it allows anyone that can see that directory to replace files as well as download them.

---

