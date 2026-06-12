---
title: "Desktop files"
date: 2007-10-01
forum: Absolute Beginner Talk
---

### Post by abuzakour on 2007-10-01
Hi guys, 

i just installed ubuntu today and i have very simple questions .. 
1)
when i download a package and save the file on my desktop and i want to install the package from the terminal, what do i type? is it: sudo ./filename.extension ?? i am just having problems telling the ubuntu to install the package that is on my desktop :(


2) what is the default installation folder for the apt-get? 

 thanks a lot in advance 
abuzakour

---

### Post by peabody on 2007-10-01
Depends on what you're installing.  If it's a deb you can simply double click it.

As for the default installation folder, that really depends on the package.  Most packages install the majority of their data under the /usr hierarchy.  There's usually no easy way to change that from a deb.

---

### Post by abuzakour on 2007-10-01
thanks for the reply

regarding the second question, when i ask get-apt to download a package without installing it, when is the package usually downloaded to? 

thanks again 

abuzakour

---

### Post by shad0w_walker on 2007-10-01
Apt normally downloads files to /var/cache/apt/archives
Not 100% sure on if it does this if it is just told to download the file, but it makes sense that it would.

---

### Post by Het Irv on 2007-10-01
Many times a package that is downloaded to the desktop needs to have its permissions changed so that it can be run as a program.  To change the permissions just right click and then Properties>(not sure of the name of this tab but its the third one)> then halfway down the page is what you are looking for. After that you sould be okay.

Sorry about the vauge bit I will try to edit it later when I get on my 'buntu

---

### Post by peabody on 2007-10-01
> **Het Irv said:**
> Many times a package that is downloaded to the desktop needs to have its permissions changed so that it can be run as a program.  To change the permissions just right click and then Properties>(not sure of the name of this tab but its the third one)> then halfway down the page is what you are looking for. After that you sould be okay.

Not for debs, although this is good advice for installers such as google earth.

---

