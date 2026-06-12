---
title: "[SOLVED] Help with user permissions"
date: 2008-03-25
forum: Absolute Beginner Talk
---

### Post by DaleHUtch on 2008-03-25
Greetings,

I have been going through the forums looking for an answer but I haven't found one that answers my needs. 

Here we go..

I just install Ubuntu Server 7.10 (LAMP)
I made the necessary changes to get Webmin 1.370 up and running.
I also installed proftpd.

All I want now is to get my username I created during the installation process (admininistrator) access to the /var/www directory with permissions to create folders and upload files using FTP.

I tried to create folder on the machine itself (mkdir /var/www/something)  and I get "permission denied"

I can create directories using "sudo mkdir something" 

Any help would be appreciated.

Thanks

---

### Post by phidia on 2008-03-25
I think [this]("http://ubuntuforums.org/showthread.php?t=731878&highlight=root+permissions") 
thread should help.

---

### Post by DaleHUtch on 2008-03-25
That's the ticket!!!

THANKS!!!!!!!

---

