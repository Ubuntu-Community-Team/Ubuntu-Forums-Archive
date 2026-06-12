---
title: "ubuntu server help"
date: 2006-09-21
forum: Absolute Beginner Talk
---

### Post by Th3N@tive on 2006-09-21
okay i finally gave up on installin ubuntu sever on my other pc so i did it on this one and got it installed im using the ubuntu desktop and im tryin to install webmin but when i try to install it using the command it tells me i have insufficient permission to do this.

> requested operation requires superuser privilege

how can i gain permission to install this thanks.

---

### Post by Tomosaur on 2006-09-21
Easy, just stick 'sudo' in front of the command:

'sudo apt-get install webmin'

The password it will ask for is the same one you use to log in. You will not see your password being typed, so make sure to spell it properly.

---

### Post by kidders on 2006-09-21
Log into a console as root or use sudo.

Edit: Missed the boat!

---

### Post by Th3N@tive on 2006-09-21
k i tried hat and i got this error
> : Couldn't find package webmin_1.300_all.deb

---

### Post by kidders on 2006-09-21
Is your package database up to date?

---

### Post by Th3N@tive on 2006-09-21
umm whats that mean i pdated akk ny poackages

---

### Post by kidders on 2006-09-21
Hey again,

It looks like you need to read up on working with Ubuntu's package manager ... there's plenty about it in other posts and in Ubuntu's documentation :-)

To install software, you need to have root privileges, access to the required packages and an up-to-date package list on your own PC.

---

### Post by Th3N@tive on 2006-09-21
ok tryin to use the package installer i get this error
> Error: Dependency is not satisfiable: libauthen-pam-perl

---

### Post by YeahBuntu on 2006-09-22
You should download the latest webmin from their website at:


[http://prdownloads.sourceforge.net/webadmin/webmin_1.300_all.deb](http://prdownloads.sourceforge.net/webadmin/webmin_1.300_all.deb)

using firefox or something and then simply double click it and follow the prompts

My guess is you will then have to create a webmin password like I had to ... do a search for webmin password I explained it.

Looks like webmin wants you to install perl first ... 

It may be easier for you to start over and use the server install wich should install most of any depenedancy problems you will run into and then follow the steps to install the gui ... rest of webmin [from this helpful guide]("http://howtoforge.org/lamp_installation_ubuntu6.06")

---

