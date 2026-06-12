---
title: "Setting up a wireless card"
date: 2007-05-12
forum: Absolute Beginner Talk
---

### Post by dw_bell on 2007-05-12
Hi Everyone, newbie alert, ha ha.

Just started down the road to getting my first Ubuntu Server up and running.  I'd like to use it for development in my home network.  PHP and MySQL.  Been working on Windows for years, so this is quite an adjustment.

Anyway,  I've got my install of Fiesty Fawn running nicely on a dual boot with XP.  My current problem has to do with getting my network card running.  I have an Edimax EW-7128g Wireless Card using the RT61 chipset.  The auto detect feature when installing did not pick it up.  I've found some instructions on how to get this card running on the forums.

My newbie question is the following:  how do I get my drivers from a CD onto my install?  I just cannot work that bit out.  I have no internet yet so all files need to be saved on my windows PC and then read from the CD in Ubuntu.  Thanks in advance for your help.

Dave

---

### Post by Metacarpal on 2007-05-12
hi Dave.  Welcome to Ubuntu!

I see you're running as a server - does that mean you're working entirely from the command-line, or do you have the graphical desktop set up?

If you're working from command line, you'll need to copy the files from your CD-ROM with the following command.  (Substitute your actual directory structure for the italics)
```
cp /media/cdrom/*path/to/file /path/to/destination/*
```

If you have a graphical desktop, like gnome, you should be able to drag-and-drop just like back in Windows.

---

### Post by dw_bell on 2007-05-12
Hi Metacarpal, thanks for that.  I'm going to give that a try.  I am running only with the command line at the moment.  Having struggled to get something simple like this done I'm considering using a GUI until I have a bit more experience.

On a side note, I'm using the ls command to view directories.  So "ls -a" and I'm expecting to see any directory I may have created.  I this case I have used "sudo mkdir /temp" to setup a temporary area.  When I go back a level the temp directory does not seem to be listed.  Is that because its empty?

Thanks so much for your help, so many questions!

---

### Post by Kobalt on 2007-05-12
Beware : the* sudo mkdir* command line will create a directory in /, not in /home/<username>

---

### Post by dw_bell on 2007-05-12
Right, so any new directories should be placed under my /home/<username>?  I'll keep that in mind.  I assume then that by dropping the "sudo" I am using the permissions of the default user?  Does that user have the right permissions to create directories?

Thanks

---

### Post by Kobalt on 2007-05-12
> **dw_bell said:**
> Right, so any new directories should be placed under my /home/<username>?  
Not really, I was just pointing that out so you might manage to find your created directories... :) 
Indeed if you drop *sudo* you only have regular user rights, which exclude directories creation.

---

### Post by dw_bell on 2007-05-12
OK Thanks, that makes sense.

---

