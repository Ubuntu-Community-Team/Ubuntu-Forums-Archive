---
title: "changing permissions in /"
date: 2006-05-29
forum: Absolute Beginner Talk
---

### Post by mrvgarg on 2006-05-29
How can I change permissons in / plz?

---

### Post by zhoux on 2006-05-29
i suggest that you shouldn't change the permissions in /, because of safety reasons both from the internet and the user. If you want to change something in / you should use the sudo command or the gksu command

---

### Post by mostwanted on 2006-05-29
For the entire root directory? Not possible. For folders and files in /

sudo chmod xxx

where xxx are the permissions.

---

### Post by frodon on 2006-05-29
Are you sure you want to do that since all the "/" is only writable with root rights (except for your home directory),  which is enough secure for most users.
Anyway, the command is : ```
sudo chmod -R xxx /
```Replace xxx by the rights you want to set (777 = full rights).

---

### Post by mrvgarg on 2006-05-29
Well actually I wanted to install a plug-in for gimp but the site said that I need to copy it to the gimp folder but when I do that I get permission denied.

---

### Post by frodon on 2006-05-29
Where is located your gimp folder ?
Run nautilus with root rights, it will allow you to copy your plugin where you want, you can do that with this command : ```
gksudo nautilus
```Or if you use command lines add "sudo" before your "cp" command.

---

### Post by mrvgarg on 2006-05-29
Ok got it now. Thanks

---

### Post by airtonix on 2006-06-05
I did a stupid thing.....I accidentally did this ......

 sudo chmod 775 / -R

now i cant login or get the gdm up!

can i reverse this?

---

