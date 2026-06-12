---
title: "How to install/use .deb files? (Solved)"
date: 2006-06-04
forum: Absolute Beginner Talk
---

### Post by bigben on 2006-06-04
hello 
Im trying to install the new version of aMSN and downloaded the 0.95 ubuntu.deb file but i cant open the file nor know how to install it..could someone point me in the right direction?
TIA :)

---

### Post by blimpyboy on 2006-06-04
dpkg -i <filename> = install package
dpkg -r <filename> = remove package
dpkg -P <filename> = remove package + config files
dpkg -I <filename> = show some info about the package

---

### Post by bigben on 2006-06-04
dpkg: requested operation requires superuser privilege

how do i get around that?

---

### Post by _simon_ on 2006-06-04
add sudo at the front

e.g.

sudo dpkg -i <filename>

You will then be prompted for your password.

sudo = superuser do

---

### Post by bigben on 2006-06-04
thanx guys,works and just learned a new lesson...just loving linux more n more :)

---

### Post by GarethMB on 2006-06-04
If you are using dapper you can just double click the deb file to start gdebi a graphical installer for debs. It takes care of all the dependencies as well if they are in the repositories.

---

### Post by migla on 2006-10-12
> **GarethMB said:**
> If you are using dapper you can just double click the deb file to start gdebi a graphical installer for debs. It takes care of all the dependencies as well if they are in the repositories.

Can I "sudo click" somehow?

---

### Post by h2gofast on 2006-10-12
you don't need to, it will ask you for your password if it needs it.  

I recommend the gdebi route because it handles dependencies (if any) for you.

---

### Post by tommcd on 2006-10-12
Just right-click on the .deb file and select 'open with GDebi package installer'. It will warn you of any needed dependancies and fetch them for you.

---

