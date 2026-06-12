---
title: "Help me mount iso files"
date: 2007-12-03
forum: Absolute Beginner Talk
---

### Post by BigFoofieMan on 2007-12-03
Hi everyone, ive finally switched to linux. This time i dont even have a windows partition :-)!

The thing that i needed help with was that when i goto mount iso files, it first requires me to have an entry in **etc/fstab**.
The problem comes when i try to alter the files in etc/fstab that it wont let me. Is it as simple as running to root or is it something else?

Also i need to be able to set permisions on accessing files in /home , so if anyone could explain that to me or give me links that would be great. 

In fact any links about understanding the terminal and bash would be helpful because i want to learn as much as i can.

Thanks alot in advance.

---

### Post by maybeway36 on 2007-12-03
If you know the magic words, you don't need an fstab entry. You do, however, need to mount an iso with sudo. Here's what I do to mount the ISO in folder ~/temp::
```
sudo mount -o loop,uid=1000,gid=1000 ~/name-of-iso-file.iso ~/temp
```
The folder has to exist first, though. To unmount:
```
sudo umount ~/temp
```
Note that it's umount, NOT unmount. This tripped me up the first time I saw it.

---

### Post by Billy_McBong on 2007-12-03
[http://www.psychocats.net/ubuntu/permissions]("http://www.psychocats.net/ubuntu/permissions")

---

### Post by BigFoofieMan on 2007-12-03
Thanks for the speedy replies!
If the file is on my desktop and is named iso1 for example would it be:

sudo mount -o loop,uid=1000,gid=1000 ~/iso1.iso ~/home/user/desktop

-----------------------------------------------------------------------------------------

Ok never mind:
I just ran sudo mount -o loop,uid=1000,gid=1000 ~/iso1.iso ~/temp
and i think it worked, the only thing was that i needed a copy of the iso in both username/temp and username

---

### Post by Aseld on 2007-12-03
No, it would be

```
sudo mount -o loop,uid=1000,gid=1000 ~/Desktop/iso1.iso ~/home/user/desktop
```

assuming you had a folder called "desktop" in your home folder and that's where you want the .iso mounted.

---

### Post by alphaniner on 2007-12-03
> **BigFoofieMan said:**
> Thanks for the speedy replies!
If the file is on my desktop and is named iso1 for example would it be:

sudo mount -o loop,uid=1000,gid=1000 ~/iso1.iso ~/home/user/desktop

-----------------------------------------------------------------------------------------

Ok never mind:
I just ran sudo mount -o loop,uid=1000,gid=1000 ~/iso1.iso ~/temp
and i think it worked, the only thing was that i needed a copy of the iso in both username/temp and username
I'm a noob like you but I think the ~/temp in

> sudo mount -o loop,uid=1000,gid=1000 ~/name-of-iso-file.iso ~/temp

is where the mounted CD will 'appear' for lack of a better word, not the path of the .iso.  Also, I don't know if it is the case in Ubuntu, but in Xubuntu the desktop folder is not actually located at ~/home/user/desktop (I think).  Move your .iso to your user directory, make sure the ~/temp folder exists, and try

> sudo mount -o loop,uid=1000,gid=1000 ~/home/user/iso1.iso ~/temp

But again, I'm a noob so...

---

### Post by daimaru on 2007-12-03
@[BigFoofieMan]("http://ubuntuforums.org/member.php?u=387810")
if you might like a graphical interface for mounting iso's. 
check out gmountiso 
```
sudo apt-get install gmountiso
```hope that helps
EDIT:_ check out ubuntuguide.org for nice infos. 
for shell commands google "bourne shell" which is the standard in ubuntu terminal .

---

### Post by daimaru on 2007-12-03
umm by the way the ~ sign means your home directory, so ~/home/anything is unnecessary because ~/ gets you to your users home directory

---

### Post by Vadi on 2007-12-03
Here's a useful script to ease your pains: ([click]("https://help.ubuntu.com/community/NautilusScriptsHowto?highlight=%28nautilus%29#head-223a741145896f9ca455db28a455c26206552814"))

---

### Post by BigFoofieMan on 2007-12-04
Thanks alot, ive got it!

---

### Post by daimaru on 2007-12-04
@[BigFoofieMan]("http://ubuntuforums.org/member.php?u=387810")
please mark all of your threads that you solved as "solved" from the "thread tools" menu 
thanks

---

