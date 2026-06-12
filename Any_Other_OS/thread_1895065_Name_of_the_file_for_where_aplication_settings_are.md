---
title: "Name of the file for where aplication settings are stored"
date: 2011-12-14
forum: Any Other OS
---

### Post by Jon Anderson on 2011-12-14
I have to name a file to store application settings. video settings being one of them, you know all the things you put into the program that you want to save so you don't have to put it in every time you go on line. Were is a good place to keep them and what would that address be.

---

### Post by lechien73 on 2011-12-14
Hi,

I'm not sure if I've understand your question correctly, but do you mean that you're writing an application and want to know where would be a good place to store its configuration file?

If that's the case, and if the settings may differ on a per-user basis, then the ~/.config folder is a good place to start. If the settings are global, system configuration options, then possibly somewhere beneath the /etc directory would be more appropriate.

I hope this helps, but please let me know if I've misunderstood!

---

### Post by audiomick on 2011-12-14
> **lechien73 said:**
> Hi,
If that's the case, and if the settings may differ on a per-user basis, then the ~/.config folder is a good place to start. 

Further to this, if you want a folder specific to your application, you could make the application create it's own. Look in your /home/user folder with "view hidden files" enabled in the "view" menu. There are a number of files with a dot at the front of the name, e.g. .mozilla  , which contain configuration files for various applications. If you make your application create a file whose name starts with a dot, it will also be a hidden file.

---

### Post by Jon Anderson on 2011-12-14
> **audiomick said:**
> Further to this, if you want a folder specific to your application, you could make the application create it's own. Look in your /home/user folder with "view hidden files" enabled in the "view" menu. There are a number of files with a dot at the front of the name, e.g. .mozilla  , which contain configuration files for various applications. If you make your application create a file whose name starts with a dot, it will also be a hidden file.
******************************************I hate having to "re-invent" all of my settings, passwords, etc., each  time I go on linux (Dam Small Linux). It has a place to store it but it  wants me to name it ,everything I put in there for a name it comes back  that it won't work or thats not a address for the settings. It has to be  in /home is that correct. then what would be the rest of the address.  What can it be called. .(dot) what

---

### Post by audiomick on 2011-12-16
I have no idea about Damn Small Linux, but I found these two pages that might help quite easily on their website.

[http://www.damnsmalllinux.org/wiki/index.php/Persistence](http://www.damnsmalllinux.org/wiki/index.php/Persistence)
[http://www.damnsmalllinux.org/wiki/index.php/Local_Startup_Documentation#Saving_Your_Configuration](http://www.damnsmalllinux.org/wiki/index.php/Local_Startup_Documentation#Saving_Your_Configuration)

---

### Post by oldos2er on 2011-12-16
Moved to Other OS/Distro Talk.

---

