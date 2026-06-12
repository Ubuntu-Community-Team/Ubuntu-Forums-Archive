---
title: "Lost Admin Access on Desktop"
date: 2007-09-07
forum: Absolute Beginner Talk
---

### Post by Gorlinux on 2007-09-07
I was trying to install Java JRE 6.0 following the recommendation in one of the threads posted here.  I followed exactly as instructed, being new in Ubuntu and Linux, I did not really understand  what I was doing.  The thread did forewarned about Java as having a lot of kinks to install in Fiesty but I continued anyway with best hope that I would be among the few who succeeded in instaling it - I was wrong. :(

Now, I have somehow lost my admin access to my desktop. I could no longer remove or add files there. I could not even rename files or move them to trash. All the downloaded Java files and pakages as well as the recommended gtk-qt-engine are somehow stuck in my desktop. Even when I switch work space I could still see the files. Also, I could not add files I downloaded online unless I put it under my home folder. 

I would love to undo everything I did and get rid of Java packages from my desktop. I would truly appreciate your assistance to fix this problem. Thanks.

---

### Post by zvacet on 2007-09-07
To restore admin access ctrl+F1 and type

```
sudo adduser username admin
```

After this you will be able to remove Java packages from your desktop.To install Java and other things you will probably need 

> Click Applications &#8594; Add/Remove. In the top right, change the setting to All available applications. Then select Other in the left panel and then select the Ubuntu restricted extras package. Click OK.

---

### Post by Gorlinux on 2007-09-10
Thanks. I tried as advised, but I get the message below:

gorlinux@gorlinux:~$ sudo adduser username admin
Password:
adduser: The user 'username' does not exist.
gorlinux@gorlinux:~$

I recall I had to change some settings to allow me to download JAVA and I though I had to change my root or something like that (frankly I don' t know what's root either). By the way, I can't use Add/Remove program which is another issue.

---

### Post by diatribe on 2007-09-10
username has to be changed to your user name :D and rootis basically just the admin of the computer, it will give you access to every directory and allow you to make changes to files regular users can not alter

---

### Post by Dr Small on 2007-09-10
> **diatribe said:**
> username has to be changed to your user name :D and rootis basically just the admin of the computer, it will give you access to every directory and allow you to make changes to files regular users can not alter
Example:
```
sudo adduser gorlinux admin
```

---

### Post by diatribe on 2007-09-10
you may also want to do a sudo chown username:username /home/username

REPLACE ALL INSTANCES OF USERNAME WITH YOUR LOGIN

---

### Post by Gorlinux on 2007-09-11
Thanks.  I tried all of your suggestions:

1/ Adding myself as admin, but I get the message below:

gorlinux@gorlinux:~$ sudo adduser gorlinux admin
The user `gorlinux' is already a member of `admin'.
gorlinux@gorlinux:~$ 

2/ tried to do sudo chown [maybe I did it all wrong sorry:( ] and this is what I got:

gorlinux@gorlinux:~$ sudo chown username:username /home/username
chown: `username:username': invalid user
gorlinux@gorlinux:~$ 

When I tried deleting (i.e. moving to trash) the items on my desktop, I got still got an error this message:
Cannot move "/home/gorli...jre1.6.0_02" to the trash because you do not have permissions to change it or its parent folder.

---

