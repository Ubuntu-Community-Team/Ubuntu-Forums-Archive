---
title: "Mount samba folder"
date: 2007-07-06
forum: Absolute Beginner Talk
---

### Post by Martje_001 on 2007-07-06
I've set up SAMBA using [this]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_share_public_folders_with_read.2Fwrite_permissions_.28Authentication.3DNo.29")

But what's the URL of my folder? The IP (on my local network) is: 192.168.1.66...

Thanx!

---

### Post by mjwhitfield on 2007-07-06
Would it be?```
smb:/192.168.1.66/
```

---

### Post by tbresson on 2007-07-06
The URL of your folder is the same as that of the name you wrote in the config file, in the example file it's:

[public]

So the path to your folder should be: \\192.168.1.66\public (if you connect from Windows to Ubuntu)

Remember you have to have a folder called public in your homedir (se the path in the config file).

If you're having problems with connecting due to a login/username then remember to add the user to Samba with the smbpasswd command. This might not be the case .. but if it is then that command might help you get started :)

---

### Post by Martje_001 on 2007-07-06
Aah... thank you! It was 'smb://192.168.1.66/public' :p

---

