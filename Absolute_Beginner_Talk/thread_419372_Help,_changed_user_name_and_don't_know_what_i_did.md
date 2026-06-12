---
title: "Help, changed user name and don't know what i did"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by ssc351 on 2007-04-22
So I was messing around with ubuntu on a plane ride and i changed my login user name at some point...since i have done this i can't log in with the original user name.  Also, (and the bigger problem) I can't get into any of the adminstration tools ie. synaptic, users/groups, etc. When I click on system tab and then administration there are only like 5 things that show up. 

This sounds like and I hope this is a simple fix!

---

### Post by 5-HT on 2007-04-23
Yup, simple fix. 

1. Boot into recovery mode 
2. Find out what you changed your username to
  ```
 cat /etc/passwd 
```  Look at the last line, it will start off with your username (UID 1000)
3. Change your username back to what you want it to be (from old_username to new_username)
```
usermod -l new_username old_username 
```4. reboot and you should be good to go
```
 reboot 
```HTH

---

### Post by ssc351 on 2007-04-23
Ok I was able to rechange the username but that was all. Still, most of the admistration icons are gone ie synaptic and users/groups, as well as add/remove programs is still missing.  Anyone? Anyone? Thanks!

---

### Post by fazza on 2007-05-30
hi people
I did kinda the same thing but I wasn't on a plane and I changed the uid instead. Now I have no access to any programs except the ones that were open (nautilus, terminal, gnome-panel etc), and any new terminal windows I open come up with 'I have no name!@*****-desktop:~$'. I cannot run anything, not even a sudo or a gksu(do) because it doesn't like my uid. Is there any way I can change this back at all (bearing in mind there is only one username aside from root, which I don't know the password for)?
Suppose I may have to do the same commands as was said in post #2 - as long as I don't need the root password!
Any help would be greatly appreciated.
Thanks

---

### Post by zvacet on 2007-05-30
You can create new user with admin privileges and start from there.Boot in recovery mode and that will set you as root.Type

```
adduser username admin
```

---

### Post by fazza on 2007-05-31
thanks, did that and it worked
:)

---

