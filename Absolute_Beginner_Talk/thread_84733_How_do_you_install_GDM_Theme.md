---
title: "How do you install GDM Theme"
date: 2005-10-31
forum: Absolute Beginner Talk
---

### Post by Micro Rotors on 2005-10-31
How do you install a file you download to a flash drive from work and put on my Ubuntu Breezy desktop from a site. This is the file;

GDM-BlueBuntu.tar.gz

I have other files that I have D/L that I also want to install so it would be helpfull to learn.

---

### Post by teaker1s on 2005-10-31
a good 90% of compiling stuff from source follows this procedure

   1. Download the Tarball
   2. Extract the Tarball- if your lazy like me just use ark to untar it by clicking
   3. (console)    Change into the directory that the Tarball should have made eg. 
cd /home/teaker1s/desktop/myprog
   4. run ./configure
   5. run make
   6. run sudo make install

Of course its always good to read the README file to find out any quirks with the package.

---

### Post by Kapre on 2005-10-31
[QUOTE=Micro Rotors]How do you install a file you download to a flash drive from work and put on my Ubuntu Breezy desktop from a site. This is the file;

GDM-BlueBuntu.tar.gz

I have other files that I have D/L that I also want to install so it would be helpfull to learn.[/QUOTE]

Micro Rotors - What teaker1s stated above is correct for files or apps that you've d/l. But if the files are specific for an app already (say files from Gnome-look.org); you can just open the app (say Gnome Theme), click on Install Theme and look for the file that you've d/l and it will open up the tar file and install it.

K

---

