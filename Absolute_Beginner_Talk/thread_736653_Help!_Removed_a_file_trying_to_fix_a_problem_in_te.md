---
title: "Help! Removed a file trying to fix a problem in terrentflux."
date: 2008-03-26
forum: Absolute Beginner Talk
---

### Post by hfnd on 2008-03-26
How do I get back this file? /usr/share/php/adodb/drivers/adodb-mysql.inc.php

---

### Post by aktiwers on 2008-03-26
Did you empty the trash or delete with sudo?

If you deleted with root (sudo) then its in /root/.Trash/

---

### Post by hfnd on 2008-03-26
> **aktiwers said:**
> Did you empty the trash or delete with sudo?

If you deleted with root (sudo) then its in /root/.Trash/

I removed with root , sudo rm. How do I retreive?

---

### Post by aktiwers on 2008-03-26
In terminal:
```
sudo cp /root/.Trash/adodb-mysql.inc.php /usr/share/php/adodb/drivers/
```
Or this way is another way you can do it,  gui way, open Nautilus with root:
```
gksudo nautilus
```Hit CTRL+L and type /root/.Trash

Copy the file to /usr/share/php/adodb/drivers/

Terminal is much faster! :)

---

### Post by northern lights on 2008-03-26
Navigate to /root/.Trash/

/.****/ folders are hidden, but copy/pasting the above into any address bar oughta do it.

---

### Post by aktiwers on 2008-03-26
By the way, if its not there I sadly have no idea how to get it back..

---

### Post by hfnd on 2008-03-26
Hey aktiwers, I get a "cannot stat" message. Keep in mind I'm a nube. Thanks

---

### Post by aktiwers on 2008-03-26
Okay..  lets make sure the file is in Root's trash folder.. Please post the output of:
```
sudo ls -a /root/.Trash
```

---

### Post by hfnd on 2008-03-26
No such file or directory.

---

### Post by aktiwers on 2008-03-26
Please copy/paste the command (CTRL+C and Shift+Insert or middle-click your mouse)..

Did you type Trash with a BIG "T"?

---

### Post by Oldsoldier2003 on 2008-03-26
> **hfnd said:**
> I removed with root , sudo rm. How do I retreive?
The command rm bypasses the trash. Unless you are willing to go to extraordinary measures the file is gone

---

### Post by hfnd on 2008-03-26
Yes, I copied and paste your code with uppercase T.

---

### Post by hfnd on 2008-03-26
Hello Oldsoldier2003,
Can I  get it back if I reinstall an app, and what app would I need to reinstall?

---

### Post by aktiwers on 2008-03-26
> **Oldsoldier2003 said:**
> The command rm bypasses the trash. Unless you are willing to go to extraordinary measures the file is gone

This is what I was afraid of..  thanks for sorting it out..   Also its just a php file? Cant you find it else where?
[http://www.koders.com/php/fid5931985E61313CAE5D719480E4659D785FAEBE5B.aspx](http://www.koders.com/php/fid5931985E61313CAE5D719480E4659D785FAEBE5B.aspx)

or something..?

---

### Post by aktiwers on 2008-03-26
> **hfnd said:**
> Hello Oldsoldier2003,
Can I  get it back if I reinstall an app, and what app would I need to reinstall?

Okay I donwloaded the file for you.. hope its the right version and everything..

1) Download the attached file.

2) Right-click and pick "extract here"

3) Type this in Terminal:
```
cd Desktop
```
```
 sudo cp adodb-mysql.inc.php /usr/share/php/adodb/drivers/
```

And you should be done. :)

---

### Post by hfnd on 2008-03-26
I've got the file sitting on the desktop but my privleges won't let me paste it were it needs to  go.

---

### Post by aktiwers on 2008-03-27
That is the last command.
```
cd Desktop
```
```
 sudo cp adodb-mysql.inc.php /usr/share/php/adodb/drivers/
```That will paste the file with sudo (root) rights. Follow the 3 steps above and the file should be in place.

Explanation:
cd Desktop  = Go to desktop
sudo = get root rights
cp = copy
adodb-mysql.inc.php = the file to copy
space /usr/share/php/adodb/drivers/ = copy to this directory

---

### Post by hfnd on 2008-03-27
Hello aktiwers,

Thanks for the help I was getting cross-eyed last night, I followed your advice this evening and it worked. Now maybe you can help me with my original problem that caused the last one. when I try to access Torrentflux from a web brawser I get this:

TorrentFlux Database/SQL Error  
 
Database error: Access denied for user 'torrentflux'@'localhost' (using password: YES)

Always check your database variables in the config.php file.

 I'm assuming I screwed up my password.

---

### Post by Oldsoldier2003 on 2008-03-27
> **hfnd said:**
> Hello aktiwers,

Thanks for the help I was getting cross-eyed last night, I followed your advice this evening and it worked. Now maybe you can help me with my original problem that caused the last one. when I try to access Torrentflux from a web brawser I get this:

TorrentFlux Database/SQL Error  
 
Database error: Access denied for user 'torrentflux'@'localhost' (using password: YES)

Always check your database variables in the config.php file.

** I'm assuming I screwed up my password**.

yep, if worse comes to worse you can reset your SQL password.

---

