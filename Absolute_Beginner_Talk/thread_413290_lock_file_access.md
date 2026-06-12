---
title: "lock file access"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by sankarv on 2007-04-19
Normally in linux for a given user we can set rwx permissions for any of their files. 


suppose im giving my user name and password to my friend and he logins and works with it. i have a particular file in my user which i dont want him to read(or write or execute). i can set permission normally using chmod for that. But he too can change the permission for the file since he is logged in as me now. so is it  possible to have an authentication(such as password) for accessing a particular file so that even if one is logged in as me cannot access some specific files which are authenticated/password protected.

thankx in advance for the answer....

---

### Post by deadgobby on 2007-04-19
I would just set up the person as a different user. Yet, here is a link 
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_change_files.2Ffolders_permissions](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_change_files.2Ffolders_permissions)

---

### Post by TheWizzard on 2007-04-19
> **deadgobby said:**
> I would just set up the person as a different user. Yet, here is a link 
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_change_files.2Ffolders_permissions](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_change_files.2Ffolders_permissions)

i agree. don't give usernames & passwords to others. 
it's a good thing to have a guest account. you can make a seperate folder for shared files (/home/shared).

---

