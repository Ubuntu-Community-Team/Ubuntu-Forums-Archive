---
title: "chmod or chgrp?"
date: 2007-07-27
forum: Absolute Beginner Talk
---

### Post by sim085 on 2007-07-27
Hi,

Unfortunately being still very new to Ubuntu i still have some trouble to use the chmod and chgrp commands from the terminal. 

Basically I want to provide 'rwx' permissions on a particular directory to every user account in a particular user group. I have created the user group and added the user accounts. 

I then tried to run the following command when logged in as administrator (which is also a member of this group): sudo chmod -R 775 /myfolder. This from what I read on the internet should give 'rwx' to the administrator account and its group, and 'rx' to all others. However I still have problems writing in this folder when I logout and login with another user account also of the same group.

I therefore thought of using the chgrp command which I also found on the internet. I passed the command from the terminal as follows: sudo chgrp mygroup /myfolder. However again I still had problems writing in this folder when I logout and login with another user account also of the same group.

Now I do not know what I need to do so that to only give permission to all user accounts in a particular user group to 'rwx' in a particular folder.

Thanks for any comments,
Regards,
Sim085

---

### Post by Rocket2DMn on 2007-07-27
Did you use the recursive -R for the chgrp command as well?
```
sudo chgrp -R mygroup /path/to/directory
sudo chmod -R 775 /path/to/directory
```

---

### Post by sim085 on 2007-07-27
> **Rocket2DMn said:**
> Did you use the recursive -R for the chgrp command as well?
```
sudo chgrp -R mygroup /path/to/directory
sudo chmod -R 775 /path/to/directory
```Hi Rocket2DMin,

Yes the chgrp with -R worked finally :) however chmod did not want work. I think because I am not understanding what it actually does!

Thanks a lot again!! :)

Regards,
Sim085

---

### Post by Rocket2DMn on 2007-07-27
for the 3 digits it is OwnerGroupWorld
If chmod isn't working, perhaps somebody outside the group owns the file(s) you want the group to have full access to
```
sudo chown -R user:group /path/to/directory
```
more details:
```
man chown
```
Good luck!

---

