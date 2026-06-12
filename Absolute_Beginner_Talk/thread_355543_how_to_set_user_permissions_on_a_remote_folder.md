---
title: "how to set user permissions on a remote folder"
date: 2007-02-07
forum: Absolute Beginner Talk
---

### Post by xpan on 2007-02-07
hi,

I have managed to successfully mount a remote folder using this:
```

//192.168.1.65/public   /mnt/pub        cifs    iocharset=utf8,file_mode=0777,dir_mode=0777,uid=1000 0 0
```

and this:
```

sudo mount /mnt/pub
```

However, when I try to create a file in that folder I get this:
```

xpan@xpan-laptop:/mnt/pub/Documents$ touch file.txt
touch: cannot touch `file.txt': Permission denied
```

but user 'xpan' successfully creates a new directory.

I have created a user 'xpan' on the remote machine having a user id of 1001. Locally the userid is 1000.

What is the problem?

---

### Post by borris.morris on 2007-02-07
Don't know about that, but in your signeture it says, "with 1MB RAM" which ought to be 1GB, am I right?

---

### Post by xpan on 2007-02-08
thanks, you were right. I changed that.

However I see that there are no responses on my question. I will return with more information (maybe some ls -l commands). I am not at home right now.

---

### Post by borris.morris on 2007-02-08
Just out of curiosity, what file sytem are you using? I could help if it's Samba or NFS. Otherwise I wouldn't know.

---

### Post by xpan on 2007-02-09
I use cifs (samba).

I just did an ls 
```

xpan@xpan-laptop:/mnt$ ls -l
total 12
drwxr-xr-x 2 root root 4096 2007-02-06 10:30 pub
dr-x------ 1 xpan root 8192 2007-02-03 15:35 win

```

so if /mnt/pub has root as owner, I cannot modify anything in it as user xpan, even if the remote folder that "mounts" on /mnt/pub has different permissions, no?

---

### Post by borris.morris on 2007-02-09
I have an "X Drive" and an "I Drive" set up using these commands, 
"sudo smbmount //Share Computer/"I Drive" /home/jessie/idrive/ -o rw,fmask=777,dmask=777" and
"sudo smbmount //Share Computer/"X Drive" /home/jessie/xdrive/ -o rw,fmask=777,dmask=777" I think the thing you need to change is the option using -o rw,fmask=777,dmask=777

---

### Post by xpan on 2007-02-10
will do that right now, and report back if any problems appear, thanks!

---

### Post by xpan on 2007-02-10
I came back with the same errors (did what you said, tho)

this is what I get:

```

xpan@xpan-laptop:/mnt/pub$ ls -l
total 21252
drwxr-xr-x  13 1001 users        0 2007-02-06 15:22 Documents
-rwxr--r--   1 1001 users 21618415 2007-01-23 12:26 GoogleEarthLinux.bin
drwxr-xr-x   2 1001 users        0 2007-02-09 17:03 iso
-rw-rw-rw-   1 1001 users   110592 2007-01-24 21:34 klasmatatest.doc
drwxr-xr-x 134 1001 users        0 2007-01-04 19:51 Palm Programs
drwxr-xr-x  40 1001 users        0 2007-01-04 19:38 Personal
drwxr-xr-x   4 1001 users        0 2007-01-04 19:42 wallpapers
drwxr-xr-x   7 1001 users        0 2007-01-04 19:42 Z_Other
xpan@xpan-laptop:/mnt/pub$ touch test.t
touch: setting times of `test.t': Permission denied
xpan@xpan-laptop:/mnt/pub$ ls -l
total 21252
drwxr-xr-x  13   1001 users          0 2007-02-06 15:22 Documents
-rwxr--r--   1   1001 users   21618415 2007-01-23 12:26 GoogleEarthLinux.bin
drwxr-xr-x   2   1001 users          0 2007-02-09 17:03 iso
-rw-rw-rw-   1   1001 users     110592 2007-01-24 21:34 klasmatatest.doc
drwxr-xr-x 134   1001 users          0 2007-01-04 19:51 Palm Programs
drwxr-xr-x  40   1001 users          0 2007-01-04 19:38 Personal
-rw-r--r--   1 nobody nogroup        0 2007-02-10 13:27 test.t
drwxr-xr-x   4   1001 users          0 2007-01-04 19:42 wallpapers
drwxr-xr-x   7   1001 users          0 2007-01-04 19:42 Z_Other

```

---

### Post by mendingo84 on 2007-02-10
if you created the remote directory as root, only root will have writing rights on it. try to give writing rights to all users (chmod...). not sure it will work, but you could give it a try.

---

### Post by xpan on 2007-02-10
this is the ls ouput of the remote machine's folder:

```

root@rubini-desktop:/home/xpan# ls -l
tot al 4
lrwxrwxrwx 1 xpan xpan    26 2007-02-07 17:49 Examples -> /usr/share/example-content
drwxrwxrwx 9 xpan users 4096 2007-02-10 13:27 public

```

public/ is the remote folder that "mounts" locally at /mnt/pub

---

### Post by borris.morris on 2007-02-10
i don't know. sorry.

---

