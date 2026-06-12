---
title: "User problem...[Resolved]"
date: 2007-05-03
forum: Absolute Beginner Talk
---

### Post by _mOrgoth_ on 2007-05-03
Every time I reset my PC i get this message at system start: "User's $HOME/.dmrc file is being ignored. This prevents default session and language from being saved. File should be owned by user and have 644 permissions. User's $HOME directory must be owned by user and not writable by others user's"

WTF???!!!!:confused:

---

### Post by Nekiruhs on 2007-05-03
Well the error message is pretty clear. How many users do you have on your comp? It seems somehow another user has access to your home directory.

---

### Post by _mOrgoth_ on 2007-05-03
impossible. I install it 2h ago. Only me as admin

---

### Post by Sef on 2007-05-03
Then it seems something was not set up right.   Check System > Adiministration > Users and Groups.

---

### Post by Nekiruhs on 2007-05-03
Never forget that you are never the only user. Root/Superuser is always there regardless. Hence why we use Sudo

---

### Post by dondad on 2007-05-04
This happened to me. Not sure, but I think it was created by using sudo rather than gksudo on a graphical app by mistake. When I checked, my home directory was owned by root rather than me. I changed the owner to my username, then used chmod to make it 644. That fixed it.

---

### Post by _mOrgoth_ on 2007-05-04
> **dondad said:**
> This happened to me. Not sure, but I think it was created by using sudo rather than gksudo on a graphical app by mistake. When I checked, my home directory was owned by root rather than me. I changed the owner to my username, then used chmod to make it 644. That fixed it.

WTF??!!!
Ok... I used sudo nautilus, I set me in permissions of home floder, and then I used command:
sudo chmod 644 home
Now is everithing  DEAD!!!!!  Can't accses to nothing, after restart can't even login!!!! HELP!!!

---

### Post by Nekiruhs on 2007-05-04
you doubled the problem. Dondad saied that using sudo with a graphical app CAUSED the problem.  Nautilus is a graphical app. Use gksudo instead. Btw, can you get to a terminal/command line? if so try sudo chown <USER NAME HERE> /home/<USER NAME HERE>

---

### Post by _mOrgoth_ on 2007-05-04
Tried... It didn't help... when it comes to login wimdow it sas:"Your home directory is listed as : '/home/admin' but it does not appear to exist. Do you wont to login with the /(root) directory as your home dorectory? It is unlikely anything will work unless you use a fail safe session."

---

### Post by _mOrgoth_ on 2007-05-04
I fix it!!!:) :) :)  I used command:
sudo chmod 755 home

---

### Post by chinocracy on 2007-05-31
Scuse me, but I have the same problem. I added a user, also for myself, and put it in the same group as my accoutn (same user name as in this forum). Then the $home/.dmrc problems started. Tried 'chmod 755 user name', didn't work. Will try the latest one posted by Morgoth above.

---

