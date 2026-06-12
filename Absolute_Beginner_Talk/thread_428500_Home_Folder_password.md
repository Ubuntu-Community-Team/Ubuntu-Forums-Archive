---
title: "Home Folder password"
date: 2007-04-30
forum: Absolute Beginner Talk
---

### Post by ACF1 on 2007-04-30
I would like to be able to make it so that you have to use a password to look at anything in the home folder or file system.  Is this possible?  Thanks.

---

### Post by zetsumei on 2007-04-30
You already need a username and password to login, why would you wnat another password on your home folder?

---

### Post by Skrynesaver on 2007-04-30
Do you mean you want to encrypt the partition that the home directory is on ? [http://koeln.ccc.de/archiv/drt/crypto/linux-disk.html](http://koeln.ccc.de/archiv/drt/crypto/linux-disk.html) gives a rundown of the various options available, encrypt partition, individual directories ...

---

### Post by Churnd on 2007-04-30
Just configure your permissions correctly, and then nobody without the correct password can get in at all.

For example, these are the default permissions in most Unix systems:

heatv4@osmium:~/Music> ls -l
total 24
drwxr-xr-x 2 heatv4 users 4096 2007-03-20 15:30 Binaural
drwxr-xr-x 5 heatv4 users 4096 2007-03-20 15:27 Blind Melon
drwxr-xr-x 3 heatv4 users 4096 2007-03-20 15:28 Dave Matthews Band

This part:  **drwxr-xr-x** is who can access what.  **d** means it's a directory (or a folder).  the first **rwx** is the **owner's** permission set.  It means you can **r**ead, **w**rite, and e**x**ecute.  The next is the group permissions, which have the ability to read and execute.  Finally there's everybody permissions, which also are read and execute.

If you were to make it:  **drwx------**, then ONLY the owner could do anything.  The group and everyone else couldn't even read into it.  Your options here are very flexible

For example, to make your home directory drwx------, you could issue the command:
```
sudo chmod -R 700 ~
```
(the ~ stands for your home directory)

The problem is, you also need to modify your default access control lists (ACLs) so anything new takes the same permissions also.  I'm not sure how to do this, so hopefully someone else will chime in.  I'm actually going to look it up now, because I need to know!  :)

Read up on **chmod** (see *man chmod*) for more info on how to change these permissions.

---

### Post by milesbh on 2007-04-30
actually it may be that he wants to stop other people from messing with his machine while he's not on it.

---

### Post by Skrynesaver on 2007-04-30
I suspect this is the case, your password protected account is no use if someone else can pop a live CD in the drive, mount the home partition and do what they like

---

### Post by Churnd on 2007-04-30
> **Skrynesaver said:**
> I suspect this is the case, your password protected account is no use if someone else can pop a live CD in the drive, mount the home partition and do what they like

Ah, I see.  In that case, an encrypted partition would work well.  I like TrueCrypt:  [http://www.truecrypt.org/](http://www.truecrypt.org/)

---

### Post by michux on 2007-05-07
Here is another Encrypted partition howto that has proven to work fine in many cases:

[http://polishlinux.org/howtos/encrypted-home-partition-in-linux/](http://polishlinux.org/howtos/encrypted-home-partition-in-linux/)

(encrypted home partition with DM_Crypt + auto-mounting it when logging in)

---

### Post by Mr.Beast on 2007-05-07
> **ACF1 said:**
> I would like to be able to make it so that you have to use a password to look at anything in the home folder or file system.  Is this possible?  Thanks.

Can I just get some clarification on what, or why on this?

are you the only user of the system?  if the answer is yes, then does it matter? (If it does, then an idea of why you think it's needed would be helpful?
If the answer is no, and you have others using your system then perhaps your issue is that the other person needs an account (even if it is a generic account, i.e. an account called anyone with a password of Passw0rd)

I'm quite sure that this additional account should not be able to make system wide changes without the Sudo password / root password.  They should be abole to change their environment, but not global changes to the system.

Is this the end goal of what you are looking for?  or have a got the wrong end of the stick.

---

