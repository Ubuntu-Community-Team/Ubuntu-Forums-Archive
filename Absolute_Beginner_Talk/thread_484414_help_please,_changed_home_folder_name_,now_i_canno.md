---
title: "help please, changed home folder name ,now i cannot get in."
date: 2007-06-25
forum: Absolute Beginner Talk
---

### Post by Sweet00th on 2007-06-25
hi, i am embarresed to say that yes i went into user's & groups through pref. and changed the name of my home folder ,now when i try to log in i get errors saying my home directory doesn't exist ,and it will not let me in.
Is there any way to fix this without me reinstalling.I got alot of prgms installed ,basically took me weeks to get it where i want it.
also i should note i dual boot with windows on a 10 gig partion ,1st then a 512 swap and the rest for linux.

thanks if anyone can help me......

---

### Post by wormser on 2007-06-25
Do you have another user you can log in as?  Another option is to boot from the live CD or from recovery mode in the boot menu.  Then change the name back.

---

### Post by Sweet00th on 2007-06-25
i tried booting in recovery mode but am not knowledgeable enough to change it back, & no i only had 1 user.

---

### Post by Sweet00th on 2007-06-25
can you tell me how to change it back in recovery mode ,,please 
i would be very greatful.

---

### Post by hsweet on 2007-06-25
Don't know if this will work, but it might.

At the graphical login screen instead of logging in, type ctrl/alt/F1
This will bring you to a text login in which you can type in your username and password.
If you get in, you can re-rename your home folder.
Assuming its in /home..

```

cd/home
sudo mv stupidbadname goodoldname

```

Not sure if you need sudo, but it shouldn't hurt

---

### Post by Sweet00th on 2007-06-25
i am at the next login ,but when i type in cd/home it says no such file or directory.

---

### Post by nphx on 2007-06-25
I think what he did was change it from config files, not the home directory itself. I think the home directory is still under it's old name.

What I recommend you do is boot into safe mode when you get the grub menu. Once your booted up use nano to edit the /etc/passwd file. This is where the Ubuntu paths are stored for users. Towards the end of the file find your username and chage it accordingly.

First backup the /etc/passwd:
```
cp /etc/passwd /etc/passwd.backup
```

Edit the file:
```
nano /etc/passwd
```
-to save changes press CTRL+X. Yes. Enter to confirm the name.

For example:

```
nphx:x:1000:1000:nphx,,,:/home/nphx:/bin/bash
gdm:x:109:119:Gnome Display Manager:/var/lib/gdm:/bin/false
```

---

### Post by Sweet00th on 2007-06-25
is safe mode & recovery mode the same, i dont see safe mode .

---

### Post by nphx on 2007-06-25
Yes Recovery Mode, sorry. I was using Windows terminology.

---

### Post by Sweet00th on 2007-06-25
ok i will try .
thank you very much i have to be away for 2 hours ,i will repost then.

---

### Post by Sweet00th on 2007-06-25
hats off to you nphx!
i am back ,able to log into my much luved ubuntu.
Thank You!!!

---

