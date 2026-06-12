---
title: "Permission issue of my partition"
date: 2007-10-07
forum: Absolute Beginner Talk
---

### Post by babacan on 2007-10-07
Hello
I divided my harddisk to 3 partitions : 2 gb linux swap , 120 gb "storage" folder for videos music etc and a 25gb for ubuntu (system and home folder)

And now I am facing an issue of using my "storage" folder , I cannot write to it. All these 3 partitions are ex3.

heres my fstab output:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=d277dc98-c10a-4189-832a-59baea697d54 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda2
UUID=ec3d5a6f-446c-487c-a514-0eeb1c095ba6 /media/sda2     ext3    defaults        0       2
# /dev/sda1
UUID=598a31b5-f3fd-4709-91f7-d89a8da0fcd0 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
```

Checked some guides to fix this but none worked so please help.

---

### Post by Pumalite on 2007-10-07
sudo chmod 777 /dev/???

---

### Post by runemaste644 on 2007-10-07
Try this command:
```
gksu nautilus
```
Or, if you use KDE (Kubuntu):
```
kdesu konqueror
```
Either way, it will lead you to a root file browser where you have ALL write permissions. If you STILL can't write, then make sure it is a ext3 partition.

---

### Post by babacan on 2007-10-07
> **Pumalite said:**
> sudo chmod 777 /dev/???

Well what to write to "??"  ? I can see the partition at desktop and when I click it , it says "unmount it" so seems like it is mounted already. All permissions to root.

---

### Post by bodhi.zazen on 2007-10-07
I assume the partition in question is /dev/sda2 mounted at /media/sda2

First make sure the partition is mounted :

```
sudo mount /media/sda2
```

OK if you get a message that the partition is already mounted.

Now change ownership and permissions :

```
sudo chown user.users /media/sda2 #change "user" in this line to your log-in name
sudo chmod 770 /media/sda2
```

@Pumalite : no, /dev/xxx is the physical device and you should not change the ownership or permissions of /dev/sdax

---

### Post by Pumalite on 2007-10-07
OK. Thanks.
(dumb of me)

---

### Post by babacan on 2007-10-07
> **bodhi.zazen said:**
> I assume the partition in question is /dev/sda2 mounted at /media/sda2

First make sure the partition is mounted :

```
sudo mount /media/sda2
```

OK if you get a message that the partition is already mounted.

Now change ownership and permissions :

```
sudo chown user.users /media/sda2 #change "user" in this line to your log-in name
sudo chmod 770 /media/sda2
```

@Pumalite : no, /dev/xxx is the physical device and you should not change the ownership or permissions of /dev/sdax

Thanks alot for the detailed help , finally working! :KS

---

### Post by runemaste644 on 2007-10-07
> **bodhi.zazen said:**
> I assume the partition in question is /dev/sda2 mounted at /media/sda2

First make sure the partition is mounted :

```
sudo mount /media/sda2
```OK if you get a message that the partition is already mounted.

Now change ownership and permissions :

```
sudo chown user.users /media/sda2 #change "user" in this line to your log-in name
sudo chmod 770 /media/sda2
```@Pumalite : no, /dev/xxx is the physical device and you should not change the ownership or permissions of /dev/sdax
Good point, why do gksu nautilus every time when you can just give all write permissions to yourself?

---

### Post by bodhi.zazen on 2007-10-07
> **Pumalite said:**
> OK. Thanks.
(dumb of me)

LOL, no problem. Just trying to help ...

> **babacan said:**
> Thanks alot for the detailed help , finally working! :KS

\o/

Would you be so kind as to mark this thread as solved ?

---

### Post by babacan on 2007-10-07
Done :)

---

### Post by qpieus on 2007-10-07
> **bodhi.zazen said:**
> I assume the partition in question is /dev/sda2 mounted at /media/sda2

First make sure the partition is mounted :

```
sudo mount /media/sda2
```

OK if you get a message that the partition is already mounted.

Now change ownership and permissions :

```
sudo chown user.users /media/sda2 #change "user" in this line to your log-in name
sudo chmod 770 /media/sda2
```

@Pumalite : no, /dev/xxx is the physical device and you should not change the ownership or permissions of /dev/sdax

bodhi.zazen - could you clear up something for me? The "chown user.users" syntax is not what I expected. The man page says it should be "chown user:user" to change the owner and group. Your sample uses a dot instead of the semicolon and adds an s to the username.   ???

---

### Post by bodhi.zazen on 2007-10-07
> **qpieus said:**
> bodhi.zazen - could you clear up something for me? The "chown user.users" syntax is not what I expected. The man page says it should be "chown user:user" to change the owner and group. Your sample uses a dot instead of the semicolon and adds an s to the username.   ???

LOL good question.

I know the man page for chown uses the format "owner:group" , but you can use a . and I am lazy (: requires me to hit the shift key as . does not... )

users = group (so, in my example, the mount point is now owned by the group "users") {and not user_name with an s}

---

### Post by qpieus on 2007-10-07
Thanks bodhi. Love undocumented stuff!

---

### Post by Jofaba on 2007-10-27
Thanks for this info. I'm curious why I the permissions didn't stick when I opened Nautilus as root and right clicked, then permission set SDA2. It pushed ownership over to me (Jofaba) but the "read and write" reverted back to null. 

This isn't a bug of course but it's definitely not user-friendly to people coming new to Ubuntu. I've been using it for a while but it still feels quirky. I created a root mount, swap partition, and then a media partition for my files. Then not being able to access that main data partition without looking for help online is a little odd, but this works , and thanks for fixing it for us!

---

