---
title: "Apache2-Default folder and Index.en"
date: 2006-04-13
forum: Absolute Beginner Talk
---

### Post by tsharpe62 on 2006-04-13
Okay, I thought this was going to be the easy part. I created a basic web page using the open2 wizard and tried saving it to root/var/www and I'm getting an error saying "The local target directory '/var/www/apache2-default' is not empty. Som files might be overwritten. Do you want to continue?"
After clicking "yes" I'm getting Settings already exist under the given name. Do you want to overwrite the existing settings?"
After clicking "yes" I'm getting :"The web site could not be copied to the folling destination: file:///var/www/apache2-default."
Then just to rub my nose it it, I'm getting "one or more errors occurred."
I go to the Apache material and it says please please please change the default index.en file. I try clicking on the Apache2-default folder properties to make it so I can edit the files and it tells me that I'm not the "owner" so I can't change the properties.
This has got to be something simple but I can't figure it out. ](*,)

---

### Post by oscar on 2006-04-13
I'm not sure if this is the correct way to go about it, whether it is unsecure or not, but what I do, instead of sudo editing all of the files whenever I want to edit them, I just change it so that I am the owner of /var/www
```
sudo chown -R USERNAME /var/www 
```
Change USERNAME to your name and you are now the owner of that folder and all files and folders within it.
Also the root of your webserver is actually /var/www not /var/www/apache-default . When you want to create an index file just make it /var/www/index.html (or whatever).

[update]corrected mistake

---

### Post by tsharpe62 on 2006-04-13
Here is what I got Oscar
tsharpe@ubuntuTara:~$ sudo chown -R /var/www tsharpe
chown: `/var/www': invalid user
tsharpe@ubuntuTara:~$

---

### Post by oscar on 2006-04-13
oops, I got the user and file the wrong way round...sorry. Have corrected my post.

---

