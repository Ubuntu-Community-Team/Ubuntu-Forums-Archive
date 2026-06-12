---
title: "Limiting access to folders/programs"
date: 2007-06-29
forum: Absolute Beginner Talk
---

### Post by Scyron on 2007-06-29
This is probably very easy to solve, but after fooling around with permissions a bit, I'm stumped.

How do you set something on your computer to administrator-only access&#12289;thus requiring root password entry? If that's not possible, are there any applications that can set passwords on specific files? (If it's at all important, I'm using Ubuntu 7.04)

Thanks.

---

### Post by phizikal on 2007-06-29
Is this possible, if so; please explain. I want it to ask for a password upon opening. I really need this to hide my generated sha1 and md5 encripted passwords and such.

---

### Post by bodhi.zazen on 2007-06-29
You are best off with permissions ...

Put it in /home/<user_name>

chmod <directory> 700

If you need password protection you are talking encryption.

---

### Post by vikram on 2007-06-29
use the command below to change the owner of a file/dir
chown user filename 

this command for ensuring that only the owner can access the file
chmod 700 filename

you can change permissions in konqueror (KDE file manager- default in kubuntu) by right clicking a file. I am pretty sure an equivalent functionality exists in GNOME.


the -R flag is recursive i.e updates allthe files and dir below the target directory. open the terminal and type 
man chmod
or info chmod
for more information/options

---

### Post by bodhi.zazen on 2007-06-29
> **Scyron said:**
> This is probably very easy to solve, but after fooling around with permissions a bit, I'm stumped.

How do you set something on your computer to administrator-only access&#12289;thus requiring root password entry? If that's not possible, are there any applications that can set passwords on specific files? (If it's at all important, I'm using Ubuntu 7.04)

Thanks.

If you want a directory to be accessed by root only :

sudo chown root.root <directory>
sudo chmod 700 <directory>

If you need a password you will need to look at encryption, but the above should be sufficient.

---

### Post by phizikal on 2007-06-29
Well, I need it password encrypted. Seriously, I have alot of stuff in that folder that can make a little "w@nn@b3 h@x0rzz"  have control of alot of my important stuff. Espectually  all  my FTP infos and stored passwords. But I don't wanna use a password manager.

---

### Post by Pollywoggy on 2007-06-29
> **phizikal said:**
> Is this possible, if so; please explain. I want it to ask for a password upon opening. I really need this to hide my generated sha1 and md5 encripted passwords and such.


Google for "encfs".  Perhaps that will meet your needs

---

### Post by Dokatz on 2007-06-29
I also heard some good things about Truecrypt

[http://ubuntuforums.org/showthread.php?t=346549](http://ubuntuforums.org/showthread.php?t=346549)

It's been suggested before for the same stuff I'd reckon.

---

### Post by bodhi.zazen on 2007-06-29
Threads merged as it is essentially the same question/answer to both. reduces duplication of effort by those trying to help the OP's

---

### Post by phizikal on 2007-06-29
Thanks!

---

