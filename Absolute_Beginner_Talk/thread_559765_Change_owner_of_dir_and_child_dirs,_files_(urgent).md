---
title: "Change owner of dir and child dirs, files? (urgent)"
date: 2007-09-25
forum: Absolute Beginner Talk
---

### Post by neander on 2007-09-25
How can I change a dir and all it's child objects owner? I don't see a way to do this in nautilus (which I'd prefer). When I copy stuff off a cd with one user's login, another use can't use those files.

---

### Post by notwen on 2007-09-25
Right click said folder, select Properties.  Go to the Permissions tab and modify permissions to your liking.  Towards the bottom of this Permissions window you should see a check-box to apply changes to all files/folders within said folder. Hope this helps. =]

---

### Post by master_kernel on 2007-09-25
Or run in a terminal:
```
sudo chown -R $USER:$USER **folder**
```
```
sudo chgrp -R $USER** folder**
```

---

### Post by neander on 2007-09-25
The nautilus thing, I tried that before I posted and it didn't do anything to the perms on objects below. Not sure why, and odd if it's supposed to do what I thought it should do. There are couple hundred files below, it should take a sec or two to alter all perms I'd think, but there is no pause etc when I click that button.

---

### Post by funrider on 2007-09-25
if you dun own the file, u cant change the permission.....

you can get around it by running:

sudo chown -R owner folder

---

### Post by neander on 2007-09-25
Thanks btw

I tried this

chown -R $"meas-admin":$az /home/az/sol33-server/local/deployments/app01

from terminal when logged in as meas-admin and got 'operation not permitted'. The files are currently owned by meas-admin and I want them to be owned by another user az. Also I wonder if this will handle all subdirs and files down the stack?

---

### Post by neander on 2007-09-25
Oooo I didn't man chown, so my syntax was bad re the user:grp I'll try again

---

### Post by neander on 2007-09-25
Still didn't change any child dirs or files owners

chown -R $az:$az /home/az/sol33-server/local/deployments/app01

group and user I want are both az. I'm doing with from terminal with the current owner.

---

### Post by bodhi.zazen on 2007-09-25
Should that not be : ```
sudo chown -R az.az /home/az/sol33-server/local/deployments/app01
```

You can use user.group (. instead of : ) if you wish
You do not need sudo if you are logged in as the owner, but it does not hurt if you are having problems.

---

### Post by neander on 2007-09-25
I can't understand why this is so difficult. I tried az.az and no perms are changed, no errors.

---

