---
title: "Lamp Download"
date: 2007-11-14
forum: Absolute Beginner Talk
---

### Post by yotta on 2007-11-14
I am using Ubuntu Desktop Edition (Gutsy) and I am having trouble setting up a LAMP server. Is there any direct downloads which don't give me 404 errors and once downloaded acctually work.

If i can find 1 i think Linux will deffiently be my defualt OS. (Windows is only just there becuase of WAMP)

Yotta

---

### Post by mcduck on 2007-11-14
Just install it from the package management. System/Preferences/Synaptic Package Manager.

[How to install ANYTHING in Ubuntu]("http://monkeyblog.org/ubuntu/installing/")

In Linux you don't usually download programs from web pages. There are better ways to handle installing of applications. ;)

---

### Post by InsertNameHere on 2007-11-14
[http://www.supriyadisw.net/2006/12/lamp-installation-on-ubuntu](http://www.supriyadisw.net/2006/12/lamp-installation-on-ubuntu) 

is what I followed and it works perfectly (except mysql, the installer asks for a password now)

[http://www.howtoforge.com/lamp_installation_ubuntu6.06](http://www.howtoforge.com/lamp_installation_ubuntu6.06)
Dedicated server here....

---

### Post by yotta on 2007-11-15
> **mcduck said:**
> Just install it from the package management. System/Preferences/Synaptic Package Manager.

[How to install ANYTHING in Ubuntu]("http://monkeyblog.org/ubuntu/installing/")

In Linux you don't usually download programs from web pages. There are better ways to handle installing of applications. ;)

What should i search for in Synaptic Package Manager?

---

### Post by indytim on 2007-11-15
Yotta,

I did this a couple of weeks ago on my LAMP install on Kubuntu 7.10.  It went incredibly easy:

```

sudo tasksel install lamp-server

```

IndyTim

---

### Post by yotta on 2007-11-15
I have got it set up but the folder it is in will not let me edit create files for else...

---

### Post by InsertNameHere on 2007-11-15
Try

sudo nautilus 

go to /var
right click on www and go to properties and permission tab

The 2nd setting (admin) click can create and delete files
Click apply permissions for enclosed folders and close.

DO NOT BROWSE FILES UNDER SUDO NAUTILUS!!!!!!!!

Once I accidentally deleted a system folder and had to reinstall...

---

### Post by indytim on 2007-11-15
Using the command line (terminal):

$ cd /var/www
$sudo chown /var/www <login id>
$sudo chgrp /var/www <login id>

IndyTim

---

### Post by yotta on 2007-11-16
Thanks for the help everyone!

Hopefuly now i can start devolping aswel as i did on Windows :D

---

### Post by yotta on 2007-11-17
ok another problem, I have set my domain up so a subdomain DNS IP is my IP, it displays but i need to be able to set it so if i am accessing it from [http://localhost](http://localhost) it shows one page if i access it directly through my IP it shows another page and if i access it through my domain (Yottagames.net) then it shows another page.

Thanks
Yotta

EDIT: Sorry i googled it  and got the answer i wanted, i should have tried at the begging thanks guys anyways

---

