---
title: "Totally Frustrated"
date: 2005-12-08
forum: Absolute Beginner Talk
---

### Post by boetheus on 2005-12-08
I am new to the whole linux stuff.  I just installed Ubuntu and have configured it for webserving.  I want to extract files to the WWW folder but I don't have permission.  Everything I have searched for about sudo is  leaving me more an more confused.  Give me the exact steps to give myself permission to extract to the www folder and how to use sudo.  :confused:

---

### Post by cstudent on 2005-12-08
Assuming the archived file is a tar.gz file.

sudo tar xzvf /path_to_file/filename.tar.gz -C /path_to_extract_to/

You are probably looking more for information on tar as opposed to sudo.
Learn more by entering "man tar" in a terminal or Google "man tar"

---

### Post by Brunellus on 2005-12-08
"sudo" is just a command to tell the system to give you temporary administrative rights.  to use it, open up a terminal window and type

sudo COMMAND

where COMMAND is the command you want to execute.  then hit return.  you will be prompted for your password.  type it (your letters will not appear.  don't panic.  This is to prevent people from reading your password over your shoulder.  sneaky.) and hit return

the program should then run, with the necessary permissions.

that's as exact as I can be, without knowing what kind of file you are trying to extract, and what this WWW folder is.  

Take some courage and inspiration from your namesake, Boethius:

"Sed medicinae...tempus est quam querelae" (*De consolatione philosophiae, Liber I, Prosa II*)-- It is now the time for making things right, rather than complaining.

---

### Post by boetheus on 2005-12-08
Okay, I understand the command line point.  Is there no way in the GUI to do it?  Be patient with me, I've still got Windows on the brain.

---

### Post by Brunellus on 2005-12-08
SOmewhere in the menus you'll find a "run as different user" item.  that'll do the trick.

---

### Post by boetheus on 2005-12-08
Yes, I know where that is.  What is the syntax for using that?  Do I say run *my username* as root ? or what?

---

### Post by Brunellus on 2005-12-08
to tell you the truth, I've never used it.  

It's just a lot easier for me to do it from the terminal....

you still haven't described exactly what you're trying to do.  If you described the task more clearly, we could give specific instructions and save a lot of frustration.

---

### Post by boetheus on 2005-12-08
Fair enough,  I am trying to install Joomla (CMS).  I have the tar that I am trying to put into /var/www/  to run the install.  My next question is, is there a way to have GUI access to MYSQL to set up  the db's.

---

### Post by Chayak on 2005-12-08
Something thats a bit easier for the beginner is to go to disk management select the root disk and the browse files button within the disk manager, it will open a window with root permissions.

---

### Post by boetheus on 2005-12-08
Yep, that did it.  Now, what is the best way to set up the Mysql databases for the program?

---

### Post by aysiu on 2005-12-08
[QUOTE=boetheus]Okay, I understand the command line point.  Is there no way in the GUI to do it?  Be patient with me, I've still got Windows on the brain.[/QUOTE] Create a launcher on the panel. For "command," put ```
gksudo nautilus
```

By the way, for the /var/www folder, what I would do is put a folder in your /home folder for the www documents you want there, then middle-click-drag that folder to /var/www and select "link here."

Then you can just put stuff in, say, /home/boetheus/web, and it'll automatically show up in /var/www/web

---

### Post by boetheus on 2005-12-08
Okay, I realized my mistake.  I am looking for phpmyadmin. I have found it on the package website but the package manager does not see it . If I download it, where do i put it and how do i install it?

---

### Post by steve.horsley on 2005-12-09
phpmyadmin is in the Universe repository. Use the menu:
System ->Administration -> Synaptic Package Manager
then pull down the menu:
Settings -> Repositories
Then add the Miltiverse and Universe repositories.
Now in Synaptic you can click Search and find phpmyadmin. Mark it for installation and then click Appply. I can't help you from there - I've never used it.

Steve

---

### Post by skaboss on 2005-12-09
One thing to mention : Joomla doesn't seem to work with PHP5, so stay with PHP4.
And you may install Joomla to windows first : i think it's to much work if you have to learn Joomla, and Linux in the same time, unless you have a lot of time to spend ;)

---

