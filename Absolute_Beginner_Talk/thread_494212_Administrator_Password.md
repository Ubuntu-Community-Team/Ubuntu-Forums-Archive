---
title: "Administrator Password"
date: 2007-07-06
forum: Absolute Beginner Talk
---

### Post by JimmyVptx on 2007-07-06
We just installed Ubuntu on a pc and my helper set the administrator password to something too simple. how can I change it.

Two more questions: 
how can I map a windows server network drive like I do in XP?
I want to make a folder where all users can share data - I can't see how.

Thanks

---

### Post by Raineer on 2007-07-06
Google information on setting up "Samba", there are tons of guides on how to setup network drives with that and it works very well.

The password can be changed with "passwd" command, but I can't tell you the syntax.  You can type 
```
man passwd
```, scroll around and press 'q' to exit.

To note, there is no "root" password in Ubuntu as you always just use your current user's password.

---

### Post by bodhi.zazen on 2007-07-06
To change your password :

```
sudo passwd <user_name>
```

For file sharing use either NFS or samba (you can mount a nfs share on windows)

[http://doc.gwos.org/index.php/Share_files_using_Samba](http://doc.gwos.org/index.php/Share_files_using_Samba)

[http://doc.gwos.org/index.php/NFS_Easy_Way](http://doc.gwos.org/index.php/NFS_Easy_Way)

---

### Post by Cypher on 2007-07-06
The first account createf during installation is the "Adminstrator" account, so while logged in, just type "passwd" at the prompt and follow the prompts..

SAMBA is what you're looking for as far as mapping Windows drives go..

---

### Post by forrestcupp on 2007-07-06
To share a folder with all users, just find that folder in nautilus, right click it and choose properties.  In the properties dialog, click the permissions tab and change the part about others or all users to whatever you want.

---

