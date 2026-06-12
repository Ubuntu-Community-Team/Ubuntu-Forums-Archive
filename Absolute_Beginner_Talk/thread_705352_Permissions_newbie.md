---
title: "Permissions newbie"
date: 2008-02-23
forum: Absolute Beginner Talk
---

### Post by GLMnet on 2008-02-23
Hi, I have an ubuntu box

I have installed torrentflux on it and samba too.

I mostly can read every file via samba, directly on the /var/cache/torrentflux (where it puts the files)
I figure out that samba only let me write/delete files which are owned by my user (glm) but torrentflux requires the folder to by owned by 'www-data' 
How can I setup this so I can write to these files via samba?

Thanks

---

### Post by taurus on 2008-02-23
You mean something like

Applications -> Accessories -> Terminal
```
sudo chown -R www-data:www-data /var/cache/torrentflux
ls -la /var/cache/torrentflux
```

---

### Post by GLMnet on 2008-02-23
I think this is the way it is now.
To samba let me write I'll have to do something like
sudo chown -R glm:glm /var/cache/torrentflux

---

### Post by taurus on 2008-02-23
Or you can change permissions so both torrentflux, owner of www-data, and samba, owner of glm, can write to it without changing ownership all the time.

```
sudo chmod -R 777 /var/cache/torrentflux
ls- la /var/cache/torrentflux
```
p.s.  Try not to go too crazy with the "sudo chmod -R 777" okay.  Applying that to a wrong directory could cause some serious problems.

---

### Post by GLMnet on 2008-02-23
Yes, it works now :D

Do you think it could also worked adding glm to www-data group? It was something i did not try yet

---

### Post by taurus on 2008-02-23
It doesn't matter what group you add to it, everybody can write to that directory now.

---

### Post by mrsteveman1 on 2008-02-23
Ideally you would rather add your user name to the group owner of that directory. You don't want to get in the habit of 777'ing everything to get stuff to work, though i do it sometimes until i can figure out why something quit working.

So if your user was sam and the group is www-data you want to go into the user manager in ubuntu and add yourself to that group. This way you aren't granting permissions to everyone (Thats what the last 7 does), and you can still use it as if you were the owner of the directory.

---

