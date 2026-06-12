---
title: "Windows MOUNT permission issue"
date: 2006-07-11
forum: Absolute Beginner Talk
---

### Post by flub on 2006-07-11
Hi all.

I've been using the following command successfully to connect to my Windows Servers MUSIC share. 

sudo mount -t smbfs -o username=vector_pc //SERVER/music /mnt/music/

However, I'm totally stuck as to how to make this Writeable for the normal logged on user. Ie I can SUDO stuff to the directory but I would like to enable it for Write Access for my non-root account

Any thoughts?

---

### Post by Paerez on 2006-07-11
I think its :
```
# sudo mount -t smbfs -o username=vector_pc,umask=0000,rw //SERVER/music /mnt/music/
```

---

### Post by flub on 2006-07-11
> **Paerez said:**
> I think its :
```
# sudo mount -t smbfs -o username=vector_pc,umask=0000,rw //SERVER/music /mnt/music/
```

I tried that but it made no difference, sorry.

---

### Post by flub on 2006-07-11
Any other ideas?

---

### Post by flub on 2006-07-12
Anyone?

---

### Post by flub on 2006-07-13
One last bump

---

### Post by Paerez on 2006-07-13
ok how about:
```
# sudo mount -t smbfs -o username=vector_pc,gid=users,dmask=777,fmask=777,rw //SERVER/music /mnt/music/
```

---

