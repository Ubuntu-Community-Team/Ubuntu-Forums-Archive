---
title: "Open Office Error on Feisty"
date: 2007-05-29
forum: Apple PPC Users
---

### Post by tyminator on 2007-05-29
So i have a good version of fesity going on my powermac g3.  I have one problem. I am yet to succesfully open Open Office 2.2  

Everytime i try to open an OpenOffice program, it says
"The Application cannot be started.  An internal error occurred."
And there is a button labeled "OK"

How can i fix this? can i uninstall and reinstall?

---

### Post by stmiller on 2007-05-29
Hmm weird. You can remove it by typing

$ sudo apt-get remove openoffice.org

in a terminal. Then install it again with

$ sudo apt-get install openoffice.org


If that doesn't fix things, start it in a terminal and tell me the output

Like this:

$ oowriter

---

### Post by tyminator on 2007-05-29
tyler@ubuntu:~$ oowriter

** (process:8339): WARNING **: Unknown error forking main binary / abnormal early exit ...
tyler@ubuntu:~$

---

### Post by Prisma on 2007-05-30
i am getting the same error massage described above. i cant open open office. Any ideas?

---

### Post by stmiller on 2007-05-30
There is a bug report here:

[https://bugs.launchpad.net/openoffice/+bug/103079](https://bugs.launchpad.net/openoffice/+bug/103079)

Very weird. Openoffice works fine on my TiBook in Feisty. 

Look at this thread:

[http://www.oooforum.org/forum/viewtopic.phtml?p=226075](http://www.oooforum.org/forum/viewtopic.phtml?p=226075)

---

### Post by tyminator on 2007-05-31
i found a solution

 first removed all of the packages of openoffice.org from the Synaptic Package Manager
then i used the code
sudo apt-get install openoffice.org

then i loaded open office off of teh original ubuntu install disk.

it is working now. thanks for the help/

---

### Post by Prisma on 2007-05-31
I found the solution in another thread, the same that you posted here. I want to report that now OpenOffice is working fine.

---

### Post by stmiller on 2007-05-31
I noticed on the debian mailing list a few are having this problem. It looks like it is font related, specific to the debian packaging of OO.o. (Ubuntu packages are built from debian). So a fix is likely to filter down soon...

---

