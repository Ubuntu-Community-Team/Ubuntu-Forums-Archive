---
title: "[SOLVED] More Joomla Help"
date: 2008-04-18
forum: Absolute Beginner Talk
---

### Post by RadiationHazard on 2008-04-18
how do i make everything that says unwritable writable?

---

### Post by msayed2004 on 2008-04-18
Use **[COLOR=RoyalBlue]chmod[/COLOR]** to change permissions of the Joomla folder.

---

### Post by seepage87 on 2008-04-18
You need to change the permissions.  You can do this in nautilus if you like, but you have to start it with root permissions, I think.  Alt+f2 > gksu nautilus.  If you go to properties of those folders you should be able to add write permissions for the user.  You can also use sudo chmod +w FILESTOALTER in the command line.  That will probably do the trick.

---

### Post by RadiationHazard on 2008-04-18
thanks guys!
i got it!! 
:)
it's installed now

---

### Post by adamos on 2008-04-24
maybe you wanna practice the ftp layer account.. if you want to deploy a real website with joomla you dont wanna do that. or for now make the dirs 755 and files 644. sometimes its bitching when you are trying to install something and you have to make chmod -R 777 a dir regarding what you are trying to install but maybe you will run in other issues. there are other issues also with suexec mod if you run things 777. so do the ftp layer and call it a day.

Adam

---

