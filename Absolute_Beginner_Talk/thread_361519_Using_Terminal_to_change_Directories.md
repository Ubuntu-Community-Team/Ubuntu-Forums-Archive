---
title: "Using Terminal to change Directories?"
date: 2007-02-14
forum: Absolute Beginner Talk
---

### Post by kittyhawk63 on 2007-02-14
I am trying to install Google Earth. I can see that the .bin file for installing Google Earth is in my Home Folder. Howver, I do not know how to use Terminal to install the .bin file. How do I get Ubuntu to recognize where I have the .bin file stored? I do not know how to write the cd command. Please, be clear in your instructions. I am going to write your instructions down for future use. Thank you so much. :)

---

### Post by konst88 on 2007-02-14
Type
sudo ./[name of file]
This means to run the binary file which in the current directory, using root permitions.
If this doesn't work then type first:
sudo chmod a+x [name of file]
This makes the file executable, and the run the first command I wrote.
Good luck.

[name of file]- write here the name of the file, without the [].

---

### Post by kittyhawk63 on 2007-02-14
Thanks! :) :) :)

---

### Post by g3k0 on 2007-02-14
As far as the cd command this is how it is used.

using just cd  will bring you back to your home directory

if you want to go to the directory /usr/local you would type
cd /usr/local

if you are currently in a directory (/usr/local for the example) and you want to go to /usr/local/bin all you need to type is cd bin 

if you want to go up a directory (say you are in /usr/local/bin and you want to go to /usr/local) type cd ..

.. signifies  parent directory

while in a directory you can type ls to see its contents

---

### Post by Maestro23 on 2007-02-14
1. cd /home/usersname  : you should see the .bin file
    cd /home/username/Desktop: (if the file is on your Desktop)

2. chmod +x GoogleEarth.bin (makes the file executable)

3. ./GoogleEarth.bin (runs the installer)


A site you need to read/bookmark: [http://www.linuxcommand.org/lts0020.php#cd](http://www.linuxcommand.org/lts0020.php#cd)

---

### Post by kittyhawk63 on 2007-02-14
Got it working. It is being installed. Thanks for all the good information.

---

