---
title: "Apache2 WWW permssion"
date: 2006-01-17
forum: Absolute Beginner Talk
---

### Post by Mission 10 on 2006-01-17
I can get permission to copy any files to the /var/www folder. 
Here's what I've done so far...

sudo nautilus to change permission to write
went to system/admin/users and groups and added www-data to my group
opened up apache2.conf and changed user and group to my user name

Is there something that I'm missing?

---

### Post by aPello on 2006-01-17
What i did was just change the www folder to belong to me,

sudo chown <Username> /var/www

Works fine, tho obviously im not 100% positive on any security issues this might cause, any one else know? (The server is just for my personal development use)

---

### Post by Mission 10 on 2006-01-17
Still the same problem. Permissions in the properties display show ok, but keeps giving me the error.

---

### Post by hen3rz on 2006-01-17
> sudo chown <Username> /var/www

I just did that changing the username for the name of my account and now i cant get any access to it... how do i put it back to normal?

---

### Post by aPello on 2006-01-17
Can you post the exact error?

---

### Post by Mission 10 on 2006-01-17
Error While Moving

Error while moving items to "/var/www/apache2-default".
You do not have the permission to write to this folder.

---

### Post by hen3rz on 2006-01-17
I think the easiest solution is to just run nautilus as root then you can go anywhere u like and edit wat ever you like and not have to worry about permissions.

To do this you can either type:
```
sudo nautilus
```
In the terminal or you can create a "launcher" (right click on dekstop and slect  Create Launcher...)

And type this in the respective boxes:
> Name: Nautilus (Root)
Generic Name: Nautilus
Comment: Open nautilus as root
Command: gksudo nautilus
Type: Application
Icon: Choose one.
Run In terminal Unchecked

That will prompt for a password when u click on the link, simply enter your root pasword and nautilus will load as root.

(Oh and thank 23meg for this as it was from his thread i learnt how to do this.)

---

### Post by Mission 10 on 2006-01-17
D'oh! Forgot to add the apache2-default folder in the chown. It works now. I'm used to working with apache on Windows. I use this also for personal web development, but is there any security issue if accross a WAN?

---

### Post by aPello on 2006-01-17
oh lol, do 

sudo chown -r <USERNAME> /var/www

the -r flag makes it recursive making it for EVERY file there. Tho you should delete that folder anyway, Its just the default that comes with Apache (read its contents first, it gives you some usefull information)

EDIT: you replied b4 i did, As i said im not sure at all of any security issues. You could use firestarter to only allow people at a certain host to access it. (atm any one can access mine, but im having friends test the website etc)

---

### Post by Mission 10 on 2006-01-17
I love the launcher! Good idea.

---

### Post by hen3rz on 2006-01-17
> I love the launcher! Good idea.
Yeah, 23meg is a smart dude!

---

