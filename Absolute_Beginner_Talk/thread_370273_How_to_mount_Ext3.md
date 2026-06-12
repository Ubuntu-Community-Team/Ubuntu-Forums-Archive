---
title: "How to mount Ext3?"
date: 2007-02-25
forum: Absolute Beginner Talk
---

### Post by Frydenlund on 2007-02-25
Hi there. I just recently installed ubuntu (like 2 hours ago) for the very first time, so I'm kinda newbie with ubuntu. So please be polite if I say something wrong or something.

Anyways... My problem is that I divided my HD in 3 partitions. All of them are in the Ext3 format. When I look in "computer" I can only find one of the partitions, I can't enter open it sinces its not mounted, nor are the two other partitions, the only difference between the two is that only one of them shows up on "computer" and the two others arent there at all!

However, I do find all 3 partitions in Gparted, but as said... I need help with the mounting. 

Thanks for reading.

---

### Post by solar george on 2007-02-25
Did you set mount points for them during the install, e.g. /home

If so then they are already in use. Under Linux the partitions can be mounted transparently at any point in the file system instead of a a: c: ect. under window$.

---

### Post by highneko on 2007-02-25
To open a terminal: Applications > Accessories > Terminal
```
df -h
sudo fdisk -l
ls / 

```

---

### Post by Frydenlund on 2007-02-25
> **solar george said:**
> Did you set mount points for them during the install, e.g. /home

If so then they are already in use. Under Linux the partitions can be mounted transparently at any point in the file system instead of a a: c: ect. under window$.

This may sound a bit stupid... But I forgot where I putted the Mount Points, I forget easily. Is there anyway for me to check?

---

### Post by highneko on 2007-02-25
> **Frydenlund said:**
> This may sound a bit stupid... But I forgot where I putted the Mount Points, I forget easily. Is there anyway for me to check?

Yep. You just gotta type those commands I mentioned and you'll likely remember.

---

### Post by solar george on 2007-02-25
```
mount
```

This will give you a list of the currently mounted partitions.

---

### Post by Frydenlund on 2007-02-25
Well I tried the commands and I got this:

[http://img413.imageshack.us/my.php?image=skjermdumpzg1.png](http://img413.imageshack.us/my.php?image=skjermdumpzg1.png)

A bit big picture...

Edit: I found out that my boot partitions mouting point is:    /

---

### Post by steve.horsley on 2007-02-25
OK, we can see that your root fiesystem is on /dev/hdc, and the no other partitions are mounted.

The command **sudo fdisk -l** has a lower-case L (for list) at the end, not a vertical bar. Also, what version of Ubunti are you running?

---

### Post by highneko on 2007-02-25
Looks to me like you typed "sudo fdisk -|" instead of "sudo fdisk -l". It's a good idea to copy and paste sometimes. n_n

My knowledge of the fstab file isn't good so someone should else should help you with that, but first you should figure out what you're wanting to add to the fstab with the "mount" and "sudo fdisk -l" commands. Good luck. n_n

---

### Post by Frydenlund on 2007-02-25
I am running the newest one... 6.10. 

Sorry my bad^^ I wrote a | instead of a lower case l. But I didn't get any wiser when I did write l.

---

### Post by george29 on 2007-02-25
check out the how to below... it should explain all you need about mounting partitions.

[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

---

