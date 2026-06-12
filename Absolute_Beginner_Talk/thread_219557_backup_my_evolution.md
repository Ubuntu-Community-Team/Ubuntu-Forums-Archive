---
title: "backup my evolution"
date: 2006-07-20
forum: Absolute Beginner Talk
---

### Post by half_lif3 on 2006-07-20
i need to transfer my evolution mail and mail account
to another ubuntu pc...
how to back up my mail n account?
i've try to search all d feature there but i cant find a way to do it..
some1 pls enlighten me,..
thankx:(

---

### Post by matthew on 2006-07-20
If there is nothing in the evolution database on the computer you will transfer **to**, then this is really easy.

Copy the folder /home/username/.evolution (including all its contents) to some sort of removable media (cdr, usb drive, etc)

Copy the folder to /home/username/.evolution on the new computer while Evolution is not running

Start Evolution on the new computer.

---

### Post by half_lif3 on 2006-07-21
but i cant find evolution folder in my new computer..
i already copied all my data jus duno where to paste it ](*,)

---

### Post by m83 on 2006-07-22
Just copy the folder .evolution from your old computer to the home directory of the user in your new computer. If the folder .evolution exists on your new computer, then delete it and copy the old .evolution. If the .evolution folder doesn't exist, then just copy the old one. That's all there is to it.

---

### Post by bscbrit on 2006-08-13
You might experience problems if you don't also transfer the contents of ~/.gconf/apps/evolution.

---

### Post by grizz_granlien on 2006-08-19
Ya the folders are there but if you can't see them click on places then click on home then a window pops up and shows you files etc. simply go to the top of the window look for VIEW and click it and then click Show Hidden Files and then look you will see all the files you couldn't see before

Hope this helps!!!


From Grizz (Walter L. Granlien) of the Grizz's Den Computers [www.grizzsden.ca](www.grizzsden.ca)

I wish I new how to set up my Ubuntu to have my owne E-Mail at my owne address and etc as well as have my own BBS up and running I had one in Windows but I can't get one in Ubuntu.... I wanted forums and E-Mail and chat fro the BBS as well as E-Mail for the Bus. Webpage and Upload and Download areas for both...

---

### Post by borobudur on 2007-11-07
Hey guys, can I ask you something? What if the file structure changes in a newer version of evolution?

---

### Post by hyper_ch on 2007-11-07
borobudur:
Then there will most likely be a conversion tool.

---

### Post by mivo on 2007-11-07
The newer versions of Evolution have a "Backup Settings ..." option in the "File" menu. This puts all settings, tasks, filters etc, *and* mail into one handy file. Evolution can restore everything from this one file, so the previous, manual method is no longer needed. :) (It still works, though, you just might have to manually re-setup the accounts.)

---

