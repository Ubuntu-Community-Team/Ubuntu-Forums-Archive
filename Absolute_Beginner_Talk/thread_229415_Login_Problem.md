---
title: "Login Problem"
date: 2006-08-04
forum: Absolute Beginner Talk
---

### Post by jgeeting on 2006-08-04
I couldn't login this morning after a shut down. After a little research I realize it was because my partion is full. My bit torrent client warned me that the partion was full and it had to stop. So I got rid of some files and rebooted but I didn't empty the trash. So the drive is still full. One poster said he logged in as root and deleted files to fix this. I tried to login as root but don't know the password, I don't remember setting one up. Any advice for me on how to get into the system.

---

### Post by MaximB on 2006-08-04
the password is the  **FIRST** password you setup during the installation of ubuntu. 
it is the password you use when you go to the system>administrator

---

### Post by jgeeting on 2006-08-04
... user name is root? It keeps telling me the passord is incorrect, I am pretty sure I have the right one...

---

### Post by FenrisAbraxas on 2006-08-04
> **jgeeting said:**
> ... user name is root? It keeps telling me the passord is incorrect, I am pretty sure I have the right one...

not sure if it will work never ran into that problem before:

when you are in the login promt press ctrl + alt + F1, there log with your user account and see what you can do.

Don't know if the console will let you login.

if you can just look for something to delete using rm /path/file
or rm -rf /path/to/directory/

---

### Post by greybirds on 2006-08-04
By default, Ubuntu locks root so it can't log in. You can unlock it by setting a password, but in order to do that you have to log in as your normal account. It's also not something recommended, but here's how, just in case ("going back to a traditional root"): [https://help.ubuntu.com/community/RootSudo#head-8352bb412ccfc81b89a48144986e8690c66e338c]("https://help.ubuntu.com/community/RootSudo#head-8352bb412ccfc81b89a48144986e8690c66e338c")

Another possibility is to boot with the Ubuntu cd and mount your hard drive (that might even happen automatically?). From there, you should be able to remove files from your hard drive.

---

### Post by jgeeting on 2006-08-04
I'll try those suggestions... thank
s for your help.

---

