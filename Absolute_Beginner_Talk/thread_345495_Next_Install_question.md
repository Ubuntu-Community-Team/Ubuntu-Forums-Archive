---
title: "Next Install question"
date: 2007-01-24
forum: Absolute Beginner Talk
---

### Post by willbur on 2007-01-24
Next newbie question....

I'd like to install the chess program Jose from here:

[http://jose-chess.sourceforge.net/index_download.html](http://jose-chess.sourceforge.net/index_download.html)

I get a skype_debian-1.3.0.53-1_i386.deb file on my desktop after the download. The instructions on the website then say:

# Unpack the tar file into a directory of your choice, e.g. tar xzf jose-13-linux.tar.gz -C /usr/share/games

# Start jose with the script jose.sh

# Or start jose from the command line with java -jar jose.jar

Does the first command work with .deb files or do I need to modify it?

Must the install be to /usr/share/games, or can I put it anywhere?

can I miss out the 'script' stage?

Does 'java -jar jose.jar' complete the install or run the program?

How would I uninstall this program afterwards?

Many thanks, once again :D

---

### Post by geokok1981 on 2007-01-24
i believe u have downloaded the wrong file.
The file u mention is not a zipped file (which is what tar.gz is) but a deb file and I am pretty sure it is skype, the voip application.........

---

### Post by willbur on 2007-01-24
Sorry! I'm doing 2 things at once here! I mean this file:

jose-144-linux.zip

The rest of my post is correct....

Many thanks

---

### Post by geokok1981 on 2007-01-24
If you have the correct file just unzip it as instructed in a directory of your choice. 
Without being to sure, I guess that the game is not installed at all. Instead it runs directly from the file you are told to run . 
To run the file navigate to the folder containing it through the terminal and the issue the command:
./type_application_name_here

It should just work. So if that is the case u uninstall just by deleting the folder.

---

### Post by willbur on 2007-01-24
Thanks, geokok1981! I'd like to extract it to /usr/share/games but am unable to do so using the graphical unzip program as 'I do not have the right permissions'. How can I do this, or would you just leave it in your home folder and run it from there?

---

### Post by geokok1981 on 2007-01-25
> **willbur said:**
> Thanks, geokok1981! I'd like to extract it to /usr/share/games but am unable to do so using the graphical unzip program as 'I do not have the right permissions'. How can I do this, or would you just leave it in your home folder and run it from there?

usr/share/games is part of the filesystem and you need super user rights to modify it (i.e. you need to issue a command by adding "sudo" at the beginning of it). It is advisable to leave the filesystem alone in general, unless you are aware of what you are doing. Home folder should be all you need in your case. The best thing to do is create a "Games" folder in your home directory (or name it any way you like) and unzip it there.

---

### Post by willbur on 2007-01-26
OK - will do. Many thanks for your help :D

---

