---
title: ":: XP FILES TO UBUNTU 2 diff hard drives ::"
date: 2005-08-09
forum: Absolute Beginner Talk
---

### Post by mohsin on 2005-08-09
well i have installed ubuntu on different hard disk i use net over xp and download files as dont know about ubuntu .. well now use some basics


      i want those files to shifted to 2nd hard disk but when i attach it to pc it dint visibile on xp 

  is this due to filesystem .. (i auto configure the partition) it make it own way using ubuntu setup 

 the filesystem is not compatible .. 


 well could you plz tell me how i can transfre my files of xp hard drive to ubuntu hard drive or all in vain 

 thnx  :---)

---

### Post by dave9191 on 2005-08-09
I'm guessing that you mean that you have some files in windows on an ntfs partion and you tried to copy them to your linux ext3 partion. Of course windows is nice and doesnt recognise other partions then its own. So you will have to mount the windows partions in ubuntu and copy the files over. You can find instructions on how to mount ntfs partions on ubuntuguide.org 

Dave

---

### Post by poofyhairguy on 2005-08-09
Look at this thread:

[http://www.ubuntuforums.org/showthread.php?t=55648](http://www.ubuntuforums.org/showthread.php?t=55648)

---

### Post by mohsin on 2005-08-09
xp is fat32 its not ntfs .. 


 whats the ubuntu default filesystem ... 

 i want xp to boot with and then copy those file .. okz .. if i wish to boot with ubuntu and xp hard 1st one to secondary .. then what i have to do mounting .. or something else more 

?

---

### Post by dave9191 on 2005-08-10
You can still can still mount the windows fat32 partition in ubuntu, instrutctions on ubuntuguide.org. And like I said, ubuntu probably has ext3. And you can't mount that in windows. 

You can boot into ubuntu and copy the windows files to ubuntu, or copy the ububtu files to windows. But you can do that in windows. 

Dave

---

