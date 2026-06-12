---
title: "Accessing hard drive..."
date: 2016-11-12
forum: Apple Hardware Users
---

### Post by Furycd001 on 2016-11-12
HI guys

I have a hard drive that is formatted as Mac os extended. It originally had journaling enabled, but I went and disabled that. Would anyone have any ideas why I can still only access the drive through sudo :? Also any files that I copy from the drive have a lock symbol beside them and I need to be sudo to access them too.

Your help is very much appreciated as I'd like to copy all my files from this drive to my new ubuntu system.

---

### Post by howefield on 2016-11-12
Thread moved to the "*Apple Hardware Users*" forum.

---

### Post by ajgreeny on 2016-11-12
If you can navigate to them on a mounted folder/partition in terminal what does **ls -l** tell you when you run it on the folder?

I think that mac filesystems (HFS) use permissions a bit like Linux permissions so you may get some clues from the output of that and be able to **chown** or **chmod** the files to make them what you want.

---

### Post by SeijiSensei on 2016-11-12
I'd try this route:
```

$ cd 
$ mkdir macdata
$ cd macdata
$ sudo mount .... [use whatever you're using now; mount it to /mnt]
$ sudo rsync -av /mnt/* .
$ sudo chown -R username:username *

```
That will mount the drive at /mnt and copy all the files to /home/username/macdata.  The "chown" line will change the ownership of all the files (using the -R "recursive" switch) from root:root to username:username.

---

### Post by Furycd001 on 2016-11-13
> **howefield said:**
> Thread moved to the "*Apple Hardware Users*" forum.
Ok my hard drive is a western digital element. Whenever I connect it to my laptop the icon for it appears automatically on the desktop. All I have to do is to double click on it to mount it. Whenever I cd into the drive location inside terminal and run ls -l I get what appears below.

```

furycd001@Openbook:~$ cd /media/furycd001/Element/
furycd001@Openbook:/media/furycd001/Element$ ls -l
total 0
drwx------ 1 99 99  5 Feb  8  2016 Applications
drwx------ 1 99 99 16 Mar 12  2016 Documents
drwx------ 1 99 99  7 Mar 19  2016 Downloads
drwxr-xr-x 1 99 99 11 Apr 23  2016 Games
drwx------ 1 99 99 55 Mar 27  2016 Movies
drwx------ 1 99 99  7 May  2  2016 Music
drwxr-xr-x 1 99 99 25 Mar 17  2016 Operating Systems
drwx------ 1 99 99 45 Mar 30  2016 Pictures
drwxr-xr-x 1 99 99 12 Apr 30  2016 Sites
drwxr-xr-x 1 99 99 14 Jun 15 19:23 Terminal
drwxr-xr-x 1 99 99  9 May  3  2016 Web
furycd001@Openbook:/media/furycd001/Element$ 

```

---

### Post by Furycd001 on 2016-11-13
Ok so while in terminal I used the chown command on the directory and I seem to have full read / write access now :-) Thank you very much for your help :-)

---

