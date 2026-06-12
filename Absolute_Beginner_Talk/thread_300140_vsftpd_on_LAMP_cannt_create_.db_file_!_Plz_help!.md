---
title: "vsftpd on LAMP cannt create *.db file ! Plz help!"
date: 2006-11-15
forum: Absolute Beginner Talk
---

### Post by Dr.Jobo on 2006-11-15
Hi Allz!
Im new to Ubuntu and i still try to setup a LAMP Ubuntu server, everything worked fine, since i want to install a FTP server (vsftpd). I only want to use allowed user and so i have to create a .db File wich is used by pam. But db_load or db3 or db4 doesnt exist. How can i solve this problem ? Have i to install the Berkley packages ? If yes HOW :) ???
Or is there another command to create .db files in the same way like db_load ?
Plz plz help me and thx´s a lot, greetz
Dr.Jobo

---

### Post by Bachstelze on 2006-11-15
Yes, you have to install it. How ? With apt-get :)

---

### Post by Dr.Jobo on 2006-11-15
Okay, that helps a lot. But i´m not able to set it up alone =(!

I downloaded libdb3-util_3.2.9-20_i386.deb (I run a LAMP LST server on i386 distribution). I copied it to my usb stick, still mountet it on the server, okay everything wrked fine, but then .. =(

# sudo apt-get libdb3-util_3.2.9-20_i386.deb does nothing

Have i to copy the packe to a location on the server or not ?
Or is the package wrong ?

i use 
# sudo dpkg -i packagename, too but i got an Error Message, somthing like dependency problems!

Okay im a step closer now!

#sudo dpkg -i libdb4.... worked well
#sudo dpkg -i db4-util... worked well, too :)


but i cannot use db_load or db4.1_load =(
have i to do someting else ?

---

