---
title: "Can't access Ubuntu directories from Win Xp - password?"
date: 2006-11-27
forum: Absolute Beginner Talk
---

### Post by flameproof on 2006-11-27
I can't access Ubuntu directories from Win Xp!

I can see the Ubuntu machine from my Xp PC - but when I want to access them I get hit with a login and password.

First question would be, how do I get rid of the login and password (non of the other Windows PC in the workgroup have that). We share via a network router.

After that I am not sure if other questions remain.


BTW, the Ubuntu PC can access Xp directories, however, it can not send Xp files as an attachment in email. Xp can do that.

---

### Post by mssever on 2006-11-27
Look at your Samba settings in /etc/samba/smb.conf. There should be a section labeled [ShareName] (replace ShareName with the name of the share in question. I believe that if you change public to yes, it will solve your problem, although I haven't tried it. Of course, you should restart Samba after making changes ```
sudo /etc/init.d/samba restart
```

You can control the password and related stuff with the smbpasswd command. ```
man smbpasswd
``` for details.

---

### Post by flameproof on 2006-11-28
I works now, I followed EXACTLY this old 6.06 WIKI, which works for Edgy anyway:

[http://easylinux.info/wiki/Ubuntu_dapper#How_to_share_public_folders_with_read_only_permission_.28Authentication.3DNo.29](http://easylinux.info/wiki/Ubuntu_dapper#How_to_share_public_folders_with_read_only_permission_.28Authentication.3DNo.29)

Now I can see and access the Ubuntu PC from my Win Xp PC!

---

### Post by flameproof on 2007-05-03
I am back again with a similar problem. I am using Feisty now.

I followed exactly as above. However, I can write into 1 directory and one of it's subdirectory. All are in the smb.conf file. So it looks like: 


```

[public]     #works fine
  comment = Public Folder
  path = /home/public
  public = yes
  writable = yes
  create mask = 0777
  directory mask = 0777
  force user = nobody
  force group = nogroup

[public1]    #works fine
  comment = Public Folder
  path = /home/public/public1
  public = yes
  writable = yes
  create mask = 0777
  directory mask = 0777
  force user = nobody
  force group = nogroup


[public2]    #does not work, can see, open, but not write to
  comment = Public Folder
  path = /home/public/public1/public2
  public = yes
  writable = yes
  create mask = 0777
  directory mask = 0777
  force user = nobody
  force group = nogroup

```

Any ideas?

---

### Post by flameproof on 2007-05-03
Nobody has Feisty shared with Windows Xp here?

PS: what is the sharing folder function for? it doesn't share anything.....

---

### Post by flameproof on 2007-05-03
solved. I had to change the individual permissions in the directories.

---

