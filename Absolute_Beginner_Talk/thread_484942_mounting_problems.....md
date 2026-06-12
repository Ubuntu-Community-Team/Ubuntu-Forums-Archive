---
title: "mounting problems...."
date: 2007-06-26
forum: Absolute Beginner Talk
---

### Post by someguy91 on 2007-06-26
So I'm trying to mount 2 partitions right now... the first one being my vista partition.. so this is what i do..

sudo mkdir /media/vista
sudo mount /dev/sda2 /media /vista

i think that worked cuz i got no error messages....

when i use the command 

dir /media/vista

it says permission denied..... i dont know how to set permissions or what not.. how do i do it?? Also the vista mount does NOT show up in my "computer - filebrowser"

secondly i have a partition for data... how do i set permissions for that too? I know linux gets really explicit with everything :p

---

### Post by Cypher on 2007-06-26
You are mounting a single partition, not two. Your command should be
```

sudo mount /dev/sda2 /media/vista

```

---

### Post by sargeras on 2007-06-26
To set permisions, use a variation of the following command.

```
$ sudo chmod ugo+rwx /media/vista 
```

ugo means 'user, group, other'
rwx means 'read, write, execute'

I don't know if you want write or execute options on the vista partition, but it's up to you.  Remove any of the letters to ugo/rwx to suit your purpose. 

 Hope this helps.

---

### Post by someguy91 on 2007-06-26
> **Cypher said:**
> You are mounting a single partition, not two. Your command should be
```

sudo mount /dev/sda2 /media/vista

```

> **sargeras said:**
> To set permisions, use a variation of the following command.

sorry that was a forum typo on my part

```
$ sudo chmod ugo+rwx /media/vista 
```

ugo means 'user, group, other'
rwx means 'read, write, execute'

I don't know if you want write or execute options on the vista partition, but it's up to you.  Remove any of the letters to ugo/rwx to suit your purpose. 

 Hope this helps.

ok still when i type cd /media/vista it says

bash: cd: /media/vista: Permission denied

edit: but I DID mount my other "data" partition and it works fine now

edit2: i didnt want to make a new thread.. but how do i tell the absolute path to the directory i am in?

---

### Post by sargeras on 2007-06-27
Use the following command to find out what directory you are currently in.  

```
$ pwd 
```

Sorry, if the chmod command didn't work, then I don't know what else to do.  

Hopefully someone else can be more helpful.

---

