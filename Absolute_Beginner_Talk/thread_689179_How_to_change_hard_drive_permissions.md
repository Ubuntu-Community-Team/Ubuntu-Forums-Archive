---
title: "How to change hard drive permissions?"
date: 2008-02-06
forum: Absolute Beginner Talk
---

### Post by Kurosaki_Ichigo on 2008-02-06
Hi I just want to know how to change the permissions on one of my hard drives.
I've called the hard drive "Expanded" also its NTFS I dunno if that matters.

I'm guess in the terminal I type "sudo..." and I just need to know the rest so that I can change the permissions so that I can read and write to the hard drive,  as at the moment I can just access the files on it and thats all.

Any help would be great
Thanx

---

### Post by imT on 2008-02-06
start nautilus with sudo and do whatever you want,
i believe is ```
sudo nautilus
```
be careful thou, you can screw up your pc if you play as root :) (just do what you need)

---

### Post by Kurosaki_Ichigo on 2008-02-06
Kewl Beans! Thanx!

---

### Post by jken146 on 2008-02-06
> **imT said:**
> start nautilus with sudo and do whatever you want,
i believe is ```
sudo nautilus
```
be careful thou, you can screw up your pc if you play as root :) (just do what you need)

You should use ```
gksudo nautilus
``` not sudo nautilus.  For an explanation: [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by Trail on 2008-02-06
If I understand right, and if my memory server right, check this out:

Open a terminal and type
```

ls -l /media/

```

This will give a list that looks like this:
```

...
drwxrwx--- 1 root plugdev 8192 2008-02-05 11:32 sda1
...

```

The first column is permissions, the third is the owner and the fourth is the owner's group. If it looks like "drwxr--r--" it means that the owner had **r**ead, **w**rite and e**x**ecute permissions, users in the same group as the owner have read permissions, and other users have read permissions (the d indicates a directory if you are wondering).

If that is the case, and you are not the owner, you can add permissions for writing and executing.
```
sudo chmod a+wx /media/<expanded> # replace <expanded> with the correct name
```
This means "**ch**ange **mod**ifiers so that **a**ll get(+) **w**rite and e**x**ecute permission.

(or you can use chown instead)

---

### Post by imT on 2008-02-06
> **jken146 said:**
> You should use ```
gksudo nautilus
``` not sudo nautilus.  For an explanation: [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)
for changing permissions the sudo is good, read that article you linked, the gksudo is for something else.

---

### Post by imT on 2008-02-06
@Trail
keep it simple :)

---

### Post by jken146 on 2008-02-06
> **imT said:**
> for changing permissions the sudo is good, read that article you linked, the gksudo is for something else.

You're right -- it may not make a difference in this case, but it is good practice to use gksu  instead of sudo for running graphical apps.  Aysiu points out the reason for this on the page I linked to.

---

### Post by imT on 2008-02-06
yeah, thanks for the link by the way, was useful :)

---

### Post by yizuman on 2008-02-10
How do I step by step change the permission to access ALL files?

I am trying to extract some wallpapers to a background folder and it won't let me. I'm trying to understand the directions and still getting nowhere.

---

