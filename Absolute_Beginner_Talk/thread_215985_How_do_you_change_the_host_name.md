---
title: "How do you change the host name???"
date: 2006-07-14
forum: Absolute Beginner Talk
---

### Post by ovimunt on 2006-07-14
Hi,

I've just reinstalled Ubunutu and I've set a really silly host name. So now my command line, and not only, looks really dumb i.e.

> user@something_really_stupid:~$ 

How can this be changed? :confused: 


Thanks

---

### Post by qdvubun on 2006-07-14
go to system, administration, networking, click on gerneral tab, and you can change it there.

---

### Post by tjb4u on 2006-07-19
To make the change from the terminal:
sudo gedit /etc/hostname
sudo gedit /etc/hosts
(change occurences of the old host name to the new host name)

You will likely need to reboot after doing this or use:
sudo hostname your.new.hostname

As for me, I just reboot.

---

### Post by MrHorus on 2006-07-19
> **tjb4u said:**
> To make the change from the terminal:
sudo gedit /etc/hostname
sudo gedit /etc/hosts
(change occurences of the old host name to the new host name)

Or even simpler:

```
sudo hostname <new hostname>
```

Where <new hostname> is the hostname that you want to use :D

---

### Post by tjb4u on 2006-07-19
> **MrHorus said:**
> Or even simpler:

```
sudo hostname <new hostname>
```

Where <new hostname> is the hostname that you want to use :D

I am admittedly a Linux newb but my understanding is that the above change won't stick after a reboot. 

I just tested doing
```
sudo hostname <new hostname>
```
Afterwards the files /etc/hostname and /etc/hosts still showed the old host name and my ability to sudo was messed.
After a hard reboot the host name had reverted to the old host name but sudo worked again.

---

