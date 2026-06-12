---
title: "can't empty /media .Trash"
date: 2008-02-04
forum: Absolute Beginner Talk
---

### Post by inanethings on 2008-02-04
When I go to unmount my hard drive it asks me to empty trash.

When I try to, it won't let me:
"cannnot be deleted because it is on a read-only disk"

but it won't let me change the execute check box

What do I do?

Thanks

---

### Post by jan quark on 2008-02-04
try this command to empty the trash

```

sudo rm -Rf ~/.Trash/*
```

---

### Post by nynoah on 2008-02-04
you must have moved something to your trash file while you were using the SUDO option.  When this happens to me I hit Alt F2 and then type sudo nautilus and do it from there.  Now.......BE CAREFUL because everything you do under sudo nautilus is as a super user.  So just do that one task and nothing else.  Because you could open up pandoras box if you start doing too much as SUDO.  That command to run nautilus should only be done sparingly.

Noah

---

### Post by Vadi on 2008-02-04
> **jan quark said:**
> try this command to empty the trash

```

sudo rm -Rf ~/.Trash/*
```

But he doesn't need his home trash cleaned, he needs the drive's trash.

Try doing alt+f2, "**gksudo nautilus**", then go to /media, find your drive, and try deleting the trash then.

---

### Post by jan quark on 2008-02-04
good catch it is late here in germany and my brain is getting slooooww

---

### Post by nynoah on 2008-02-04
Oops  I meant to say  "gksudo nautilus"  Thanks for the catch on that one.

---

### Post by inanethings on 2008-02-05
Thank you.  However even when logged in as root using 
gksudo nautilus 

It tries deleting to delete then says:
"Error while deleting.

"media/HD-...xt21.html" cannot be deleted because it is on a read-only disk"

I hadn't set permissions to read-only.

---

### Post by legend2440 on 2008-02-05
Looks like you need to change the permissions on the /media folder
So gksudo nautilus then go to / directory and right click on media then properties then permissions

Mine are set as follows for the media folder

Owner   root
Folder Access  Create and delete files

Group   root
Folder access   Access files

Also I would think 
sudo rm /media/HD-...xt21.html
would work

---

### Post by inanethings on 2008-02-05
Tricky.

When I:
"So gksudo nautilus then go to / directory and right click on media then properties then permissions

Mine are set as follows for the media folder

Owner root
Folder Access Create and delete files

Group root
Folder access Access files"

My owner is set as suggested.  

However Root is set to "none".  I select "Access"  and it immediately jumps back to none.  It is overridden somehow.

The sudo rm command does not work.  I had tried that before.

Any ideas why I can not change the root or group privileges.  Also the execute checkbox can't be clicked.  It has a line through it and when clicked bounced back to the line.

Thanks.

---

### Post by inanethings on 2008-02-05
Also.  When ever I go to unmount, it says that it can't unmount and then powers down.

Maybe something with that fstab file?

---

### Post by sigmarhophi on 2008-02-05
What is the name of the drive to which you wish to empty the trash on?
 
try: ls /media/

this should list the drives on your computer.

The graphical ownership way, and sudo evolution way seem not to have worked, try changing permisions using chmod.

try: sudo chmod 777 'name of drive'

Then attempt deleting the trash or files.

---

### Post by inanethings on 2008-02-05
> **sigmarhophi said:**
> What is the name of the drive to which you wish to empty the trash on?
 
try: ls /media/

this should list the drives on your computer.


The graphical ownership way, and sudo evolution way seem not to have worked, try changing permisions using chmod.
 
try: sudo chmod 777 'name of drive'

Then attempt deleting the trash or files.

Thanks.  I have tried that before.  Tried that before I got the responses suggesting nautilus.

Here is what happens when I do as you suggest.  Nothing changes:
inane@inane-laptop:/media/HD-HCU2$ ls -la
total 27836932
drwx------ 11 inane root      32768 1969-12-31 19:00 .
drwxr-xr-x  7 root  root       4096 2008-02-05 22:08 ..
-rwx------  1 inane root   23309959 2007-11-12 11:47 Acronis True Image v8.0.764 Inc Paradox Keygen.rar
drwx------  9 inane root      32768 2007-11-12 14:19 astro_newly_compiled
drwx------  5 inane root      32768 2007-12-07 12:05 backup
drwx------  5 inane root      32768 2007-11-25 11:25 inane_comp
drwx------  3 inane root      32768 2008-02-05 11:41 lectures
-rwx------  1 inane root 4294966784 2007-11-13 22:35 linux1.tib
-rwx------  1 inane root 4294966784 2007-11-13 22:44 linux2.tib
-rwx------  1 inane root 4294966784 2007-11-13 22:54 linux3.tib
-rwx------  1 inane root 4294966784 2007-11-13 23:05 linux4.tib
-rwx------  1 inane root 4294966784 2007-11-13 23:25 linux5.tib
-rwx------  1 inane root 4294966784 2007-11-13 23:35 linux6.tib
-rwx------  1 inane root 1365255168 2007-11-13 23:38 linux7.tib
drwx------  2 inane root      32768 2008-02-05 11:53 .Trash-inane
drwx------  2 inane root      32768 2008-02-05 11:53 .Trash-kelvin
drwx------  8 inane root      32768 2008-02-05 11:54 .Trash-root
drwx------  2 inane root      32768 2008-02-05 11:54 .Trash-samuel
drwx------  2 inane root      32768 2007-11-25 11:20 vids
-rwx------  1 inane root 1346256896 2007-11-13 22:26 windows.tib

inane@inane-laptop:/media/HD-HCU2$ cd ..

inane@inane-laptop:/media$ sudo chmod 777 HD-HCU2/
Password:

inane@inane-laptop:/media$ ls -la
total 60
drwxr-xr-x  7 root  root  4096 2008-02-05 22:08 .
drwxr-xr-x 21 root  root  4096 2007-06-10 16:04 ..
lrwxrwxrwx  1 root  root     6 2007-06-07 10:24 cdrom -> cdrom0
drwxr-xr-x  2 root  root  4096 2007-06-07 10:24 cdrom0
drwxrwxrwx  1 root  root  4096 2008-02-01 16:53 disk
-rw-r--r--  1 root  root  1662 2008-02-05 22:08 .hal-mtab
--wxr-x---  1 root  root     0 2007-04-15 07:56 .hal-mtab-lock
drwx------ 11 inane root 32768 1969-12-31 19:00 HD-HCU2
drwx------  2 root  root  4096 2008-02-05 16:07 LEXAR MEDIA
drwxr-xr-x  2 root  root  4096 2007-10-08 10:15 WINKEY

inane@inane-laptop:/media$ cd HD-HCU2/

inane@inane-laptop:/media/HD-HCU2$ ls -la
total 27836932
drwx------ 11 inane root      32768 1969-12-31 19:00 .
drwxr-xr-x  7 root  root       4096 2008-02-05 22:08 ..
-rwx------  1 inane root   23309959 2007-11-12 11:47 Acronis True Image v8.0.764 Inc Paradox Keygen.rar
drwx------  9 inane root      32768 2007-11-12 14:19 astro_newly_compiled
drwx------  5 inane root      32768 2007-12-07 12:05 backup
drwx------  5 inane root      32768 2007-11-25 11:25 inane_comp
drwx------  3 inane root      32768 2008-02-05 11:41 lectures
-rwx------  1 inane root 4294966784 2007-11-13 22:35 linux1.tib
-rwx------  1 inane root 4294966784 2007-11-13 22:44 linux2.tib
-rwx------  1 inane root 4294966784 2007-11-13 22:54 linux3.tib
-rwx------  1 inane root 4294966784 2007-11-13 23:05 linux4.tib
-rwx------  1 inane root 4294966784 2007-11-13 23:25 linux5.tib
-rwx------  1 inane root 4294966784 2007-11-13 23:35 linux6.tib
-rwx------  1 inane root 1365255168 2007-11-13 23:38 linux7.tib
drwx------  2 inane root      32768 2008-02-05 11:53 .Trash-inane
drwx------  2 inane root      32768 2008-02-05 11:53 .Trash-kelvin
drwx------  8 inane root      32768 2008-02-05 11:54 .Trash-root
drwx------  2 inane root      32768 2008-02-05 11:54 .Trash-samuel
drwx------  2 inane root      32768 2007-11-25 11:20 vids
-rwx------  1 inane root 1346256896 2007-11-13 22:26 windows.tib

Any ideas what is going on?

---

