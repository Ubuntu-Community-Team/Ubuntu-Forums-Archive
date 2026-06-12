---
title: "can't boot after gtk install"
date: 2008-01-01
forum: Absolute Beginner Talk
---

### Post by silicon_chipper on 2008-01-01
Hi I am on gutsy 7.10 and I just ran apt-get install libgtk2.0-common libgtk2.0-dev. Well, gedit stopped working and now I can't boot. I can use ctrl-alt-f1 but sudo apt-get update can't get anything etc. Thanks.
silicon

---

### Post by daengbo on 2008-01-01
What were you doing before you installed libgtk2.0-dev? How did you install it? When you say gedit doesn't work, what do you mean? What is the error?

---

### Post by silicon_chipper on 2008-01-01
I was trying to install it manually. I installed glib and tried to install atk, the atk configure complained that the glib version returned from pkg_config (or something like that) was 2.12 and the version found was 2.14 so I googled the problem and found out i could just install gtk with apt. One thing I noted was that someone on this forum said never use rm -rf when someone tells you to. Well the glib documentation specifically said to use rm -rf /install-prefix/include/glib.h and something else .h. The error with gedit was a symbol look up error. I am really sorry I don't have the errors in front of me anymore. :-(
If can't solve this is there a way to put something on a usb flash drive from the command line. I just need to save my bsp project and I can reinstall. Thank you.
Apollo

---

### Post by Xavieran on 2008-01-01
To copy something from your home folder to your usb do this ...

```
cp /home/usernamehere/mybspproject /media/disk
```

P.S. What that person meant was:Make sure you know that that command is what you should be using (rm -rf removes directories)if the glib documentation said to do that however,you can probably trust them...

EDIT:Woohooo...123 beans..xD

---

### Post by silicon_chipper on 2008-01-01
Thank you, but I'm not sure Ubuntu is aware of the flash drive at this point. I just booted and hit ctrl-alt-f1 then after I logged in I tried to cp the project files to /media/disk but it said media/disk is not a directory so i looked in media and the only folder is cdrom. can i mount it manually somehow. Am I doomed?
Apollo

---

### Post by Xavieran on 2008-01-01
Sorry about the lag..I just had dessert ...You can mount it manually I think ...type in sudo mount /dev/sdb /media/disk ...if that does not work change sdb to hdb...

---

### Post by silicon_chipper on 2008-01-01
I have to specify a file system with that command. It says you must specify the file system type. I tried mount /dev/sdb alone and it said can't find /dev/sdb in /etc/fstab or /etc/mtab. Thanks.

silicon

---

### Post by Xavieran on 2008-01-01
Try this```
 sudo mount /dev/sdb1 /media/disk
```

If that doesn't work and it says something like ```
mount: mount point /media/disk does not exist

```

then do this:
```
cd /media && sudo mkdir disk
```

EDIT:You shouldn't have to specify a filesystem ... I just ran it and it worked fine...sorry but I have to go to bed (parents...)...if that still doesn't work replace sdb1 with hdb or hdb1

---

### Post by silicon_chipper on 2008-01-01
You are cool, it worked. Thank you so much. Now I am going to reinstall. When I have done that do you know how I can properly install gtk? I posted what I tried at the top of this thread.

silicon

---

### Post by Xavieran on 2008-01-01
Glad I can be of service :)

It's nice to know that I am actually helping people xD

Night...

---

