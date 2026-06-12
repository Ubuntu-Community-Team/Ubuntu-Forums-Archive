---
title: "[SOLVED] Asserting Permissions over folder's contents?"
date: 2007-08-04
forum: Absolute Beginner Talk
---

### Post by Gary.M on 2007-08-04
I have a Virtual machine running (Vmware Player w Windows XP) and when I write files from it to a network shared folder on my Kubuntu home folder they are written with permissions set to user "nobody" owner "nobody"

I then have to use root privileges to make them accessible. A nuisance!

Is there a way I can make the shared folder's permissions such that anything written there immediately inherits the attributes of the folder itself so that I don't have to repeat this process every time I write out a file?

---

### Post by apswartz on 2007-08-04
Potentially dangerous advice follows...

Okay, check the /etc/passwd file and see if there is a listing for vmware and see what the owner and group ids are. Maybe you can change them to your own, probably 1000 and 1000.

---

### Post by HermanAB on 2007-08-04
Uhmmmm, I think you should rather change the owner and group of the directory to yourself, add the vmware user to your group and make the directory sticky so that all files will inherit the owner and group of the directory.

'Hope that helps!

Herman

---

### Post by apswartz on 2007-08-04
Okay, I will second HermanAB's suggestion.

---

### Post by Gary.M on 2007-08-05
Hi, and thanks. I've had a look, and there isn't a "vmware" user or group on the system. I think when the Vmware player is run it runs as the user who starts it. How will adding a vmware user help if this is the case?

---

### Post by apswartz on 2007-08-05
It won't help. I'd go with HermanAB's suggestion.

> **HermanAB said:**
> Uhmmmm, I think you should rather change the owner and group of the directory to yourself, add the vmware user to your group and make the directory sticky so that all files will inherit the owner and group of the directory.

'Hope that helps!

Herman

---

### Post by Gary.M on 2007-08-05
OK, well the folder is in my home directory, and both owner and group are already me... how do I make it "sticky"... I want the owner and group attributes to be applied to any files written there, even as in this case when these are written via a samba network  connection... (I'm relatively new to this Linux stuff, so please bear with me...)

---

### Post by apswartz on 2007-08-05
```
chmod 7777 NameOfFolder
```

where **NameOfFolder** is the actual name of the folder

---

### Post by Gary.M on 2007-08-06
Thanks for this, and I've done some reading on chmod

Can you explain the 4th 7. I can only find references to chmod 777

When I try this, it doesn't act recursively, the permissions on folders within the one I am referencing don't change.

Can't I do this via a filemanager run with sudo?

---

### Post by Dr Small on 2007-08-06
chmod -R 777 NameOfFolder

---

### Post by bodhi.zazen on 2007-08-06
that should be chmod u+t <directory> 

or

chmod 1777 <directory>

[http://www.newlinuxuser.com/explain-what-is-setuid-and-setgid/](http://www.newlinuxuser.com/explain-what-is-setuid-and-setgid/)

[http://hep.pa.msu.edu/user/groups.html](http://hep.pa.msu.edu/user/groups.html)

[http://www.unix.com/unix-for-dummies-questions-and-answers/9964-help-with-permissions.html](http://www.unix.com/unix-for-dummies-questions-and-answers/9964-help-with-permissions.html)

---

### Post by apswartz on 2007-08-06
> **bodhi.zazen said:**
> that should be chmod u+t <directory> 

or

chmod 1777 <directory>

[http://www.newlinuxuser.com/explain-what-is-setuid-and-setgid/](http://www.newlinuxuser.com/explain-what-is-setuid-and-setgid/)

[http://hep.pa.msu.edu/user/groups.html](http://hep.pa.msu.edu/user/groups.html)

[http://www.unix.com/unix-for-dummies-questions-and-answers/9964-help-with-permissions.html](http://www.unix.com/unix-for-dummies-questions-and-answers/9964-help-with-permissions.html)

He said he wanted user and group ids of any new file to be applied to him. Just making it sticky won't do that.

---

### Post by Gary.M on 2007-08-06
Thanks for all the help, I've solved this via Samba setup with help from this guide here

[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

The shared config looks like this...

The force user seems the critical part as everything written is with my user credentials...

[Documents]
    path = /home/gary/Documents/
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = gary
    force group = gary

---

### Post by apswartz on 2007-08-06
great!

---

