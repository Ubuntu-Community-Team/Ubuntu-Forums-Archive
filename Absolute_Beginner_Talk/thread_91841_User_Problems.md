---
title: "User Problems"
date: 2005-11-18
forum: Absolute Beginner Talk
---

### Post by SychoSly on 2005-11-18
I have just set-up Ubuntu 5.10, I was previously using Ubuntu Server 5.4.

I have created my user account and set the password. I let root account login to GNOME. 

I don't want to be logging in everytime as root to do some file maintenece. If I login as my regular user I can't access all the files, specifically in the /var/www/ . 

What can I change so that I can make my normal account access those files, give my account root privileges.

---

### Post by adwait on 2005-11-18
Well, giving your account full root previleges is not advisable. If you want to edit the files in /var/www as the normal user, just change their ownership.
```
sudo chown <username> /var/www
```

Alternatively, you can use/edit/do anything as root, be just prefixing the word sudo to the command. 
eg:
```
sudo mkdir /var/www/a
sudo <whatever>
```

---

### Post by ubuntu_demon on 2005-11-18
don't login as root but use sudo

for example :
sudo pico foo.txt

gives you root priviliges while editting the file foo.txt

---

### Post by SychoSly on 2005-11-18
What if I want to move files around by dragging and dropping them. I wouldn't want to do it through command line. How would I do that, just change the ownership, chown it?

---

### Post by ubuntu_demon on 2005-11-18
[QUOTE=SychoSly]What if I want to move files around by dragging and dropping them. I wouldn't want to do it through command line. How would I do that, just change the ownership, chown it?[/QUOTE]
to start nautlius with root permissions :
sudo nautilus

But I do those kinds of stuff in the terminal :-P. For example :
$sudo mv ~/foo-application /opt

---

