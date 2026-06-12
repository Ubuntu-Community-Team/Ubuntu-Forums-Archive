---
title: "Setting Up a Server"
date: 2007-07-02
forum: Absolute Beginner Talk
---

### Post by cranshinibon on 2007-07-02
Alright after a few days of playing around and with the help of many of the members I finally got clamav and webmin to work properly. (except clamav won't allow me to update but i think thats a firewall problem)

I need help with the following:

Adding my computer to a domain controller on my switch (the dc is running Windows Server 2003)
and be able to ping the other members.

Setting up FTP, NFS, and HTTP for my ubuntu server 

Making a cronjob to update my computer (i cant find the exact command to type to set it up.)

---

### Post by cranshinibon on 2007-07-02
bump

---

### Post by cranshinibon on 2007-07-02
can anyone help? :(

---

### Post by darrenm on 2007-07-02
What do you need to know?

---

### Post by cranshinibon on 2007-07-02
i need help :
Adding my computer to a domain controller on my switch (the dc is running Windows Server 2003)
and be able to ping the other members, every time i try and ping after changing my static IP it times out.

How do you set up FTP, NFS, and HTTP on an ubuntu server

How do you make a cronjob to update my computer (i cant find the exact command to type to set it up.)

---

### Post by meatpan on 2007-07-02
Have you installed NFS, FTP, HTTP, etc...? Are you looking advice regarding configuration, installation, or both?  

The ubuntu server guide has some excellent information to get started: [https://help.ubuntu.com/ubuntu/serverguide/C/index.html](https://help.ubuntu.com/ubuntu/serverguide/C/index.html)

Also, you might get a better response in the server forum.

---

### Post by darrenm on 2007-07-02
You need to provide a bit more information though mate ;)

Its like asking what do I do to fix a car, you need specifics to know where to start.

1. You can't add a Linux machine to a Windows DC in the same way as Windows. You can get Samba to authenticate against the DC and various other things but what functionality do you need from the DC? Its only a fancy LDAP server. 

2. FTP = apt-get install vsftpd or any other you prefer, post if you can't get anything working.
3. NFS = apt-get install nfs-server, post if you can't get anything working.
4. HTTP = apt-get install apache2 assuming you want apache2, post if you can't get anything working.
5. cron = crontab -e then add 0 21 * * * /usr/bin/apt-get update && /usr/bin/apt-get dist-upgrade -y assuming you want to update the computer with bug fixes, updates and security fixes at 9pm every night. Or just go into Synaptic and set the auto update options there.

---

### Post by darrenm on 2007-07-02
Few extra tips.

to see what files a package installs:

dpkg-query -L package-name

to see what packages are available with a certain name, eg to find apache2:

apt-cache pkgnames | grep pattern

---

