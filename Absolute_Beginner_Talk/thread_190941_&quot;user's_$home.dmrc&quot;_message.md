---
title: "&quot;user's $home/.dmrc&quot; message"
date: 2006-06-06
forum: Absolute Beginner Talk
---

### Post by zambotti on 2006-06-06
When I boot Ubuntu, as soon as I enter password, the following appears:

User's $home/.dmrc file is being ignored.  This prevents the default session and language from being saved.  File should be owned by user and have 644 permissions.  User's $home directory must be owned by user and not writable by other users.

After I click OK, Ubuntu starts and seems to run alright.  What does it mean, and how do I clear it?  Thanks.

---

### Post by adwait on 2006-06-06
Change the permissions of the file with
```
chmod 644 /home/<your username>/.dmrc 
```

The file sotres your preferences etc. and the message simply means that the file hasn't got the right permissions and hence UBuntu can't use it to store your preferences.

---

### Post by unnes on 2006-06-09
Sometimes its not specifically dmrc, try the following:

```
sudo chmod 755 /home/{your username}
```

---

### Post by brentoboy on 2006-06-09
I had this issue when I tried mounting one of my harddrives into /home/brent/docs instead of /home because I wanted all the space to myself.

it turns out that, in my case, setting the mount point to /home/brent/docs created my home folder with root only permission durring installation before it even knew who /home/brent should belong to.

then I couldnt even boot until I reinstalled and mounted the drive as /media/docs (or some other remote place that wasnt in my home folder.

this sounds related, but I am not entirely sure what could be causing the problem on your end.

---

### Post by zambotti on 2006-06-10
Thank you all for your input.  unnes---you rock!  That did it!  Thanks again.

---

### Post by patrick295767 on 2006-06-10
[QUOTE=zambotti]When I boot Ubuntu, as soon as I enter password, the following appears:

User's $home/.dmrc file is being ignored.  This prevents the default session and language from being saved.  File should be owned by user and have 644 permissions.  User's $home directory must be owned by user and not writable by other users.

After I click OK, Ubuntu starts and seems to run alright.  What does it mean, and how do I clear it?  Thanks.[/QUOTE]
  

  
What's distro do you have : Breezy or Dapper ?

---

### Post by zambotti on 2006-06-10
Dapper

---

### Post by garner_nc on 2006-06-10
My machine started doing this right after upgrading from Hoary to Breezy. I finally fixed it last night after reading this post. It was the permissions for my /home directory.

All the Best,
Doug White

---

### Post by patrick295767 on 2006-06-10
[QUOTE=zambotti]Dapper[/QUOTE]
 
Interesting 'cos I have been said that this problem was corrected under dapper :-( :(

---

### Post by matach on 2008-04-29
I had this same problem using ubuntu 7.10.

```
sudo chmod 755 /home/[username]
```

Command fixed it.

Cheers,
Matach

---

### Post by MaddMatt on 2008-04-29
Holy crap I've been having this problem ever since upgrading to Feisty, and I just ignored it - was definitely home permissions. Crazy! Thanks!

---

### Post by MaddMatt on 2008-04-30
> **unnes said:**
> Sometimes its not specifically dmrc, try the following:

```
sudo chmod 755 /home/{your username}
```

Holy crap I've been having this problem ever since upgrading to Feisty, and I just ignored it - was definitely home permissions. Crazy! Thanks!

---

