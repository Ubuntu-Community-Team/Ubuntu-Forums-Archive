---
title: "Tarball installation"
date: 2007-08-26
forum: Absolute Beginner Talk
---

### Post by byrneb on 2007-08-26
I just did my first manual tarball installation:

tar zxvf linktheaterx-p10.tar.gz

It is a media server software (reported to have been tested on Red Hat) by Buffalo Technology for use with the LinkTheater DVD device.

Seemed to install fine (no errors).

How do I run the program????

Thank you.

---

### Post by Majorix on 2007-08-26
You didn't install it: You only extracted the program to a folder.

What I can suggest is that you go to that folder and find the readme inside that and follow the instructions in it.

---

### Post by finer recliner on 2007-08-26
extracting a tarball does not install a file. a tarball is similar to a zipped file, its just a compressed set of files. all you did was uncompress it. now you have to cd to the extracted folder and figure out how to install the program. look for a readme file or seomthing. if you need to build from source, you most likely will run the following commands in this order:

./configure
make
make install

---

### Post by S15_88 on 2007-08-26
make sure u have build-essential,  that's required to use make and it does not come preinstalled with 7.0.4.  do: sudo apt-get install build-essential

Thanks, Alain

---

### Post by byrneb on 2007-08-27
Many thanks to all.  I found .sh file in folder and remembered reading about command "sh filename.sh".  Works fine now.  Program runs a media server.  It seems that closing terminal application window stops the software/server.  Is there a way to run "sh startserver.sh" on every computer startup and leave the terminal window closed???  Thanks again.

---

### Post by paulgault on 2007-09-25
Hi, to automatically start a program when you login go to 
System -> Preferences -> Sessions
make sure the "Startup Programs" tab is selected and press the new button.
give your action a name and put the command that will start your aplication in the "command" box.
Paul.

---

