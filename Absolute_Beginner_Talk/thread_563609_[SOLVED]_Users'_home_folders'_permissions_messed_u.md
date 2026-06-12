---
title: "[SOLVED] Users' home folders' permissions messed up"
date: 2007-09-30
forum: Absolute Beginner Talk
---

### Post by Ebuntor on 2007-09-30
Hi everyone,

I upgraded one of my pc's from Dapper to Feisty.  All the files were replaced except for the /home dir which was on a separate partition.

After the installation I re-created the user accounts as they were on Dapper; same account names same home folders.  I tried to login to one of the new accounts but I got a message the .dmrc file permissions were wrong. It turned out  that for some reason all the permissions to user A's home folder were assigned to user B, B's home folder to user C and C's home folder to user A. 

I tried manually changing the permissions to their correct owners but they'd pop back every time I tried to log back in. Next I removed all the new user accounts and re-created them again but now they don't show up in the groups menu so I can't even login nor change the folder permissions. Only the first original admin account still works.
Seems the user groups are totally messed up. Is there any way I can fix this?

Thanks in advance.

---

### Post by philinux on 2007-09-30
just done this myself after system restore

sudo chmod 644 ~/.dmrc
sudo chown philcb /home/philcb/.dmrc
sudo chmod 700 /home/philcb
sudo chmod 700 /home

Replace philcd with your user name

---

### Post by Ebuntor on 2007-09-30
> **philinux said:**
> just done this myself after system restore

sudo chmod 644 ~/.dmrc
sudo chown philcb /home/philcb/.dmrc
sudo chmod 700 /home/philcb
sudo chmod 700 /home

Replace philcd with your user name

Thank you, however as I mentioned in my original post the problem is the user accounts can no longer be recreated, they don't show up  in the "groups" list and when i try  "sudo chown <username> /home/<username>/.dmrc" I get an error that it's an invalid user while I did create the account.

---

### Post by louieb on 2007-09-30
I've run into a similar problem when sharing home between different distros. the problem has to do with the UID, the UID is a number that is assigned to each user. Both need to match up.  Not real sure where to look to get the original UID. You might try if you can remember  to add your users in the same order as you did in the original installation. Hope this points you in the right direction.

---

### Post by Ebuntor on 2007-09-30
> **louieb said:**
> I've run into a similar problem when sharing home between different distros. the problem has to do with the UID, the UID is a number that is assigned to each user. Both need to match up.  Not real sure where to look to get the original UID. You might try if you can remember  to add your users in the same order as you did in the original installation. Hope this points you in the right direction.

Yeah that was my first idea, no luck unfortunately. Is there some way to edit the file where the user account data is stored? If there is such a file.

---

### Post by Ebuntor on 2007-09-30
Just to be 100% clear what my problem is. If I startup the "Users and Groups" GUI the other users (except the original admin user) aren't listed. When I add all the users they are listed as well as in the "groups" list. 

However when I right-click their home dir to change the permissions they're not listed (same story with the CLI).

---

### Post by Ebuntor on 2007-09-30
I fixed it! Apparently there were two different problems. 

After removing all the new users the first time their accounts were deleted but they were still listed in the "groups" list for some reason. That is why I couldn't properly re-create their accounts.

After deleting their "group" entry, re-creating their accounts and using Philinux' chown and chmod commands I was able to login.

Thanks everyone. :)

---

### Post by BlackBaron1024 on 2008-07-07
> **philinux said:**
> just done this myself after system restore

sudo chmod 700 /home

Replace philcd with your user name

My original /home is owned by 'root' and thus has permissions 755, changing them to 700 renders the system more or less useless (since that makes /home impossible to access to anyone but 'root'.

P.S. Sorry this doesn't adress the original question.

---

