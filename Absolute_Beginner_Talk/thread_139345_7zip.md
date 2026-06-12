---
title: "7zip?"
date: 2006-03-03
forum: Absolute Beginner Talk
---

### Post by mhl12 on 2006-03-03
I installed 7zip through the synaptic package manager. The problem is I don't know how to use it or where to find it.

Does it have a graphical interface or does it only work through the terminal? If it only works through the terminal, what are the command lines? Thanks for your help.

---

### Post by majikstreet on 2006-03-03
I don't think you need to install 7zip to unzip files... What types of files are you looking to uncompress? .tar.gz ? .tar.bz2 ? .zip ? For .zip you can do sudo apt-get install unzip
then
unzip whatever.zip

and for tar.gz
tar xvzf whatever.tar.gz

and for tar.bz2
tar xvjf whatever.tar.bz2

hth,
majikstreet

---

### Post by mhl12 on 2006-03-03
well i had some split zip files that I need to unzip but I couldn't figure out how to unzip them using the program that came with ubuntu so I wanted to try 7zip out seeing that it works on windows to unzip split zip files.

---

### Post by Ptero-4 on 2006-03-03
get KIO7zip. It's a great GUI for zipping/unzipping, and splitting/unsplitting zips.

Edit: Oops. I forgot that it requires Konqueror.

---

### Post by mhl12 on 2006-03-03
well can 7zip unzip split archives on ubuntu?.. since i already have it.

---

### Post by rameez on 2006-04-10
Can you use 7ZIP via GUI interface?
If no what is the command line syntax?

---

### Post by rameez on 2006-04-11
anyone?

---

### Post by Kimm on 2006-04-11
You could allways run 7zip though wine to unzip whatever you need to unzip. That should work.

---

### Post by trent dillman on 2006-04-11
try running 'p7zip' from the command line...

---

### Post by htinn on 2006-04-11
If you use GNOME, you can easily make 7zip files with "Archive Manager" (file-roller). Open Archive Manager and create a new archive with the "7z" extension.

If you don't already have it, you'll need to get "p7zip" (in the universe repo).

If you use KDE, you can easily handle archives with Konqueror or Krusader.

---

### Post by danielcaraj on 2008-04-21
I ave a 7zip file divided in "7" parts. so only 7zip can gather them again.
I'm using 7zip throw Wine, and works great!  only contextual menus are not working.

[CENTER]Ubuntu 8.4, 3 days to go [/CENTER]

---

### Post by Tom--d on 2008-04-21
If you are using GNOME and installed 7zip it will be built into the archive manager. 

Once you have a compressed 7zip folder you can right click it and press extract here. 

Done. 
Also, this work with the .rar compression

---

### Post by aparigraha on 2008-04-21
whenever i reinstall, the first thing i do is install every form of archive manager that i ever need through this command:

> sudo aptitude update && sudo aptitude install rar unace unrar p7zip arj unzoo lha libarchive1 libarchive-tar-perl libarchive-zip-perl dpkg-dev

and then go to [http://rarlabs.com/download.htm]("http://rarlabs.com/download.htm") and download the latest Linux version, extract it and copy the file "rar" to /usr/bin/.
all set

---

### Post by disturbedite on 2008-04-21
just thought i'd give everyone a heads-up...
there is a p7zip frontend i use called Q7Z/Q7Zip.  its great.  you guys should give a look.
its available on kde-looks.org.

---

### Post by lanchongzi on 2008-05-08
also this one seems nice

[http://www.howtoadvice.com/7zipHelper/](http://www.howtoadvice.com/7zipHelper/)

---

