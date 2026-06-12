---
title: "Xubuntu and Apache HTTP Server"
date: 2006-09-22
forum: Absolute Beginner Talk
---

### Post by tombstone on 2006-09-22
Having an issue with installing Apache Web Server on my fresh Xubuntu install.

i used the sudo apt-get install apache2 command and it lists dependencies.

I apt-get those dependencies and they have there own. When i go to get the SSL dependency it fails. 

I also tried goign to apache.org and downloading the tar.bz file and then extracted it. I run the ./configure and no luck it to errors out, any ideas on what i could try. Thanks in advance

,
Tombstone

---

### Post by tombstone on 2006-09-22
This question must be really uncommon.

---

### Post by crokett on 2006-09-22
> **tombstone said:**
> Having an issue with installing Apache Web Server on my fresh Xubuntu install.

i used the sudo apt-get install apache2 command and it lists dependencies.

I apt-get those dependencies and they have there own. When i go to get the SSL dependency it fails. 

I also tried goign to apache.org and downloading the tar.bz file and then extracted it. I run the ./configure and no luck it to errors out, any ideas on what i could try. Thanks in advance

,
Tombstone

Does apt-getfail to get the SSL dependency or does it fail to install it?  

run ```
sudo apt-get install <whateverthepackageis> | foo
```

This will post all status msgs and errors to a file called foo in  whatever directory you happen to be in.  Post it here.

---

### Post by jamesr on 2006-09-22
Hi,

The only comment that I can make that Adding Apache2 was the first addition I made to my Xubuntu 6.06 installation. All I had to do was 

```
sudo apt-get install apache2
```

and let apt-get complete it's task. I did not need to download anything from the Apache web site.

Edit the apache2.conf file to reflect the directories that I needed to use.

Edit a file in sites_available directory (redirect command needed to be commented out)

Restart Apache and my webserver was working. The hardest problem was finding the file in the sites_available directory.

---

