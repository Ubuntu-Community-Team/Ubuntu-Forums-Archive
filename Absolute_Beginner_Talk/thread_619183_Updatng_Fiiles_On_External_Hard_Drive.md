---
title: "Updatng Fiiles On External Hard Drive"
date: 2007-11-21
forum: Absolute Beginner Talk
---

### Post by tdrusk on 2007-11-21
I have  an ipod with rockbox on it. I am putting my filles on it. I need an easy way to update it when I get more music. How can I do this?
For the record, when using rockbox, you use your ipod like an external hard drive. So any way to easily update an external hard drive is my answer.

---

### Post by p_quarles on 2007-11-21
Not sure exactly what you're asking for. You could easily do this with any number of file managers, but I suspect that's not what you're looking for. 

If you're looking for a quick way to sync the iPod with your current hard drive music collection, I'd suggest using the rsync command. You could easily make a custom command, and save it either as a script or as a Bash alias, and then be able to update the iPod with a simple command. If you need any assistance with the rsync options, I'm happy to try to help.

---

### Post by Giradman on 2007-11-21
Completely new to Ubuntu 7.1, but wanted a GUI backup program for my data folders - the *rsync* command looked like another good option, but I currently know little about BASH (of course, need to correct that deficiency!); however, I did download *Simple Backup* (listed as 'sbackup' in a Synaptic PM search) - currently, just doing manual backups, but automation & incremental backups are options (can't vouch whether this is 'what' you want, but maybe worth a look?); good luck in your search & choice! :)

---

### Post by Inxsible on 2007-11-21
+1 on rsync.

Just make sure you DO NOT use the archiving option. I think -W is the option to transfer whole files. Use```
man rsync
``` to get the entire list of options that you can use.

I have create an alias to sync my pictures to my external backup drive, so that I do not have to type in the long command over and over. I simply type in "rsyncpics" in ther terminal and I am done :D

---

### Post by p_quarles on 2007-11-21
> **Giradman said:**
> Completely new to Ubuntu 7.1, but wanted a GUI backup program for my data folders - the *rsync* command looked like another good option, but I currently know little about BASH (of course, need to correct that deficiency!); however, I did download *Simple Backup* (listed as 'sbackup' in a Synaptic PM search) - currently, just doing manual backups, but automation & incremental backups are options (can't vouch whether this is 'what' you want, but maybe worth a look?); good luck in your search & choice! :)
Yes, and rsync is one of the more new user-hostile Bash commands. Other options for those wishing to avoid are some GUI frontends for rsync, such as Grsync and [Flyback]("http://code.google.com/p/flyback/") [code.google.com].

Nothing beats a good rsync command for efficiency, though.

---

### Post by p_quarles on 2007-11-21
> **Inxsible said:**
> +1 on rsync.

Just make sure you DO NOT use the archiving option. I think -W is the option to transfer whole files.
Good point. I don't think Rockbox has added support for the .tar.gz format yet. :D

---

### Post by tdrusk on 2007-11-21
> **Inxsible said:**
> +1 on rsync.

Just make sure you DO NOT use the archiving option. I think -W is the option to transfer whole files. Use```
man rsync
``` to get the entire list of options that you can use.

I have create an alias to sync my pictures to my external backup drive, so that I do not have to type in the long command over and over. I simply type in "rsyncpics" in ther terminal and I am done :D
I'm going to install linux mint and do this. Debian doesn't have it  and linux mint has access to the rt kernel, so it's win win.

Update in a few.

---

