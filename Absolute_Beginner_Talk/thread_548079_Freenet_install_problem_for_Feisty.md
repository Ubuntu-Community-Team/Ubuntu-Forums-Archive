---
title: "Freenet install problem for Feisty"
date: 2007-09-10
forum: Absolute Beginner Talk
---

### Post by fiskking on 2007-09-10
hello
I installed Freenet using the instructions given on the website.  My problem is when after installing Freenet using the command:

cd /home/user/download               (1st.)then....

wget [http://downloads.freenetproject.org/alpha/installer/new_installer.jar](http://downloads.freenetproject.org/alpha/installer/new_installer.jar)


Now within the /download directory I attempt to change (following the directions mind u) it says to input the following command:

         cd /home/user/Freenet

This directory cannot be found so should I need to create this ( was not stated on the website)?  Also, by accident I downloaded the initial Freenet file within the starting directory before realizing my mistake and downloading to the appropriate file ( /download).  My second question is if there are two copies on here?  If so, how to get rid of the right one.

---

### Post by diatribe on 2007-09-10
you have to replace user in /home/user/Freenet with whatever your login name is, ie

/home/fiskking/Freenet

---

### Post by lisati on 2007-09-10
Suggestion: have a look for a directory called "freenet" (small f)

---

### Post by fiskking on 2007-09-10
thanks diatribe and lisati but both were tried with no success ( even tried again after reviewing replies)

---

### Post by diatribe on 2007-09-10
in a terminal type 

cd ~/
ls

and post output

---

### Post by fiskking on 2007-09-10
Desktop  
download  
Examples
new_installer.jar  
new_installer.jar.1  
pics

---

