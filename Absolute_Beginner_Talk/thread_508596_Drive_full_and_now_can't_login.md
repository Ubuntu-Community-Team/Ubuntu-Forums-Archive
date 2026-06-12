---
title: "Drive full and now can't login"
date: 2007-07-24
forum: Absolute Beginner Talk
---

### Post by BW~Merlin on 2007-07-24
Hi, I have been running Ubuntu 7.04 under VMware for about two weeks and things have been going great. However I have now run into a problem and have been unable to find away around it. Originally when I created Ubuntu under VMware I specified for it to have a 4GB hdd size. After using Ubuntu for about a week I realised that I was running out of space to I increased the hdd size to 8GB but did not increase the partition size from within Ubuntu. Now I have run into a problem where I can't login to Ubuntu because of lack sufficient free space. I know that I have a few things in the Trash/Recycling/Garbage bin but I don’t know where it is located to be able to delete the files within it.  Can someone please tell me how to delete the files from within the Trash/Recycling/Garbage bin so I can login to Ubuntu?

---

### Post by testube_babies on 2007-07-24
rm ~/.Trash/*

---

### Post by BW~Merlin on 2007-07-24
Wow that was fast.  I get this error message.  Cannot remove '/root/.Trash/*' : No such file or directory.

---

### Post by Rocket2DMn on 2007-07-24
Do you always login using root?  You should have a regular user account if possible and use sudo to temporarily act as a superuser when necessary.
If you do have other users, you can probably clean out everybody's trash by running
```
sudo rm /home/*/.Trash/*
```

---

### Post by BW~Merlin on 2007-07-24
Ok now I'm getting an error message about not being able to remove some of the items because they are directories.

---

### Post by MrHippocampus on 2007-07-24
```

sudo rm -r /home/*/.Trash/*

```
that should work.

---

### Post by Rocket2DMn on 2007-07-24
Try
```
sudo rm -r /home/*/.Trash/*
```
and/or
```
sudo rmdir --ignore-fail-on-non-empty /home/*/.Trash/*
```

---

### Post by BW~Merlin on 2007-07-24
Thanks that worked and I am now able to log back in.

---

