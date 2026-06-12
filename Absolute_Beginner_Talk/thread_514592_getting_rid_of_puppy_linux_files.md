---
title: "getting rid of puppy linux files"
date: 2007-07-31
forum: Absolute Beginner Talk
---

### Post by orwellus on 2007-07-31
Hello:

I have ubuntu 6.10. I was playing around with the Puppy Linux cd, and stupidly installed the puppy files into Ubuntu. Now I can't get rid of the puppy files. I tried to delete them, and move them into trash but I get prompt that says I'm not the owner and files cannot be removed. The files are:

pup_217.sfs
pup_save.2fs
zdrv-217.sfs

So is there any way to delete these files?  They are taking up a lot of disk space.

Thanks

---

### Post by nichipet on 2007-07-31
Take a look at:

```
ls -l pup_217.sfs
```

and the same for the other files. It will help to know who the owner is and what the permissions are. Most likely you can:

```
sudo rm pup_217.sfs
```

but the previous command keeps everything safe by doublechecking first.

---

### Post by orwellus on 2007-07-31
Thanks for the reply. Well I opened a terminial and pasted the first code you gave me, but it gave a message that said no such file or directory. I tried the second code, with the same result. I should have mention that the files were saved in PLACES>HOME FOLDER>FILE SYSTEM. So I'm not sure what's going on.

---

### Post by orwellus on 2007-08-01
I right clicked one of the files and look under permissions. It says the owner of the file is root. If that helps

---

### Post by nichipet on 2007-08-01
I'm guessing the files are in /home/yourusername/"File System" ? If so:

```
cd "File System"
sudo rm pup_217.sfs
```

---

### Post by jediborger on 2007-08-01
The "File System" is the same as / (also called root, though not to be confused with the root user) Puppy installs those file to /. So open a terminal and type:
```
cd /
sudo rm pup_217.sfs pup_save.2fs zdrv_217.sfs
```
If a file is owned by the root user then you need to use the sudo prefix to the command you want to execute and provide the root/admin password, which is usually the same as yours if you're the only/first user on an Ubuntu machine.

---

### Post by orwellus on 2007-08-01
Thank you jediborger. That worked.

---

