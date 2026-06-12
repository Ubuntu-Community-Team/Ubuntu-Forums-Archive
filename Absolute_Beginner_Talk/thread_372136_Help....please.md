---
title: "Help....please"
date: 2007-02-27
forum: Absolute Beginner Talk
---

### Post by PryorDaniel on 2007-02-27
I don't know how to login as "root". I want to move some fonts into my WINE font folder but I get an error messege. I checked the properties of the folder and it said only "root" can create/delete files in that folder. So can someone please tell me how to login as root?

---

### Post by Maestro23 on 2007-02-27
> **PryorDaniel said:**
> I don't know how to login as "root". I want to move some fonts into my WINE font folder but I get an error messege. I checked the properties of the folder and it said only "root" can create/delete files in that folder. So can someone please tell me how to login as root?

How Ubuntu handles "root": [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by ddom87 on 2007-02-27
use gksudo nautilus in your terminal to open a root file browser and you can then put your fonts into that folder be careful not to delete anything.

---

### Post by PryorDaniel on 2007-02-27
Thank you for the help. I'll try it out in a few minutes once my desktop loads everything.

---

### Post by luke411 on 2007-02-27
You need to go to the System panel and then to "Administration" from there click on "Users and Groups" and put in your password. When you see the user's list there, click on "root" and change the password to something you won't forget. Then close it all out. When you open the terminal window, type "su" and enter the password you just created. If you want to be able to log onto root in X, like you do your own name, after you create your password for root, go back to "System" and then to "Administration" and then to "Login Window". Go to the tab that reads "Security' and check the box that reads "A;;ow local system administrator log on" and close. 

Be careful using the root though, there are a mess of problems and security issues involved and you are far better off only using it in the terminal window with the "sudo" command.

---

### Post by PryorDaniel on 2007-02-27
Thank you very much for all the help. I got the fonts into the right folder now. Once again, thanks for the help.

---

